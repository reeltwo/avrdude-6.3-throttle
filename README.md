Custom version of avrdude 6.3 that adds an optional -T command line parameter that will throttle ser_send() to a single byte with a microsecond sleep interval. This resolves communications problems with optibootloader based boards like the Pololu AStar 328pb that frequently go out of sync. Throttle is only implemented for POSIX and the stk500 (Arduino) programmer.

This version also adds asserting DTR for the Butterfly programmer.

===============================================

See the documentation file for the details.

The latest version of AVRDUDE is always available here:

  http://savannah.nongnu.org/projects/avrdude


Important environment variables for ./configure:
================================================

CPPFLAGS: C preprocessor flags (*not* "C++")

This is the place to put additional (non-standard) -I options into.
For example, if your Windows system has LibUSB-Win32 installed into
\\WINDOWS\ProgramFiles\LibUSB-Win32, use

CPPFLAGS=-I/WINDOWS/ProgramFiles/LibUSB-Win32/include

to tell configure where to search for the header files.  (The use of
forward slashes rather than backslashes can often simplify things.
Note that the Windows system services internally treat both the same.
It's only cmd.exe which requires backslashes as the directory
separator.)

LDFLAGS: Linker options

This is the place to make additional library locations known to the
linker.  To continue the above example, use

LDFLAGS=-L/WINDOWS/ProgramFiles/LibUSB-Win32/lib/gcc

to make the linker search for "libusb.a" in that directory.


Linux users: make sure the header files are installed
=====================================================

While many Linux distributions install the libraries needed by AVRDUDE
(libusb, libelf) by default, they leave out the corresponding header
files.  Consequently, the configure script won't find them, so these
libraries could not be used.

Usually, the packages with the header files (and static libraries) are
derived from the regular package name by appending "-devel".  Thus,
make sure you have "libusb-devel" and "libelf-devel" installed before
running the configure script.  (Same goes for libftdi.)
