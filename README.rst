=====================================
Save, Restore, Diff versions of files
=====================================

Easily save and restore files while preserving the access
and modification times of the original file.

Installation
============
::

    $ sudo python setup.py install


Version save
============
::

    $ vsav file ...
    
Saves each *file* by making a copy.  The saved filename is
*file.v.nnn* where *nnn* is the highest version number plus one.

Version numbers consist of 3 decimal digits with leading zeros if
necessary.  The initial version number is '000'.

The saved file retains the access and modification times of the 
original file.

Use vres to restore saved files.

Version restore
===============
::

    $ vres file ...
    
Restores each *file* from the indicated version.  If *file* has
the form *dest.v.nnn* where *nnn* is a version number, then the
file is restored from this version.  Otherwise,the file is restored
from its highest version.

Version numbers consist of 3 decimal digits with leading zeros if
necessary.

The source file was presumably created using vsav.  The destination
file retains the access and modification times of the source file.

Version Diff
============
::

    $ vdif file [diff-OPTION]...

Compares a previous version to the current version of the file
using diff.  Arguments after *file* are passed to diff.

If *file* has the form *dest.v.nnn* where *nnn* is a version number,
then this version is compared to the current version::

    $ diff [diff OPTION]... dest.v.nnn dest

otherwise the highest version is compared to the current version::

    $ diff [diff OPTION]... file.v.nnn file

where *nnn* is the highest version number.

