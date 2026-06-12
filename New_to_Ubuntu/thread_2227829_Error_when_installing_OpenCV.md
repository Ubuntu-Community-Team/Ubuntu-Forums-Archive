---
title: "Error when installing OpenCV"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by tanmanh0707 on 2014-06-04
Hi all,

I tried to install OpenCV library under instruction from [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

But when opencv.sh run, I got an error like this

```
tanmanh@blackdragon:~/Desktop$ ./opencv.shInstalling OpenCV 2.4.9
Removing any pre-installed ffmpeg and x264
[sudo] password for tanmanh: 
E: Unable to locate package libx264-dev
Installing Dependenices
E: Unable to locate package ffmpeg
Downloading OpenCV 2.4.9
--2014-06-04 16:37:48--  http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.4.9%0D/opencv-2.4.9%0D.zip/download%0D
Resolving sourceforge.net (sourceforge.net)... 216.34.181.60
Connecting to sourceforge.net (sourceforge.net)|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2014-06-04 16:37:49 ERROR 500: Internal Server Error.


Installing OpenCV 2.4.9
.ZIP.or OpenCV-2.4.9or open OpenCV-2.4.9
: No such file or directorypencv-2.4.9
" does not exist.source directory "/home/tanmanh/Desktop/OpenCV
Specify --help for usage, or press the help button on the CMake GUI.
make: the `-j' option requires a positive integral argument
Usage: make [options] [target] ...
Options:
  -b, -m                      Ignored for compatibility.
  -B, --always-make           Unconditionally make all targets.
  -C DIRECTORY, --directory=DIRECTORY
                              Change to DIRECTORY before doing anything.
  -d                          Print lots of debugging information.
  --debug[=FLAGS]             Print various types of debugging information.
  -e, --environment-overrides
                              Environment variables override makefiles.
  -f FILE, --file=FILE, --makefile=FILE
                              Read FILE as a makefile.
  -h, --help                  Print this message and exit.
  -i, --ignore-errors         Ignore errors from commands.
  -I DIRECTORY, --include-dir=DIRECTORY
                              Search DIRECTORY for included makefiles.
  -j [N], --jobs[=N]          Allow N jobs at once; infinite jobs with no arg.
  -k, --keep-going            Keep going when some targets can't be made.
  -l [N], --load-average[=N], --max-load[=N]
                              Don't start multiple jobs unless load is below N.
  -L, --check-symlink-times   Use the latest mtime between symlinks and target.
  -n, --just-print, --dry-run, --recon
                              Don't actually run any commands; just print them.
  -o FILE, --old-file=FILE, --assume-old=FILE
                              Consider FILE to be very old and don't remake it.
  -p, --print-data-base       Print make's internal database.
  -q, --question              Run no commands; exit status says if up to date.
  -r, --no-builtin-rules      Disable the built-in implicit rules.
  -R, --no-builtin-variables  Disable the built-in variable settings.
  -s, --silent, --quiet       Don't echo commands.
  -S, --no-keep-going, --stop
                              Turns off -k.
  -t, --touch                 Touch targets instead of remaking them.
  -v, --version               Print the version number of make and exit.
  -w, --print-directory       Print the current directory.
  --no-print-directory        Turn off -w, even if it was turned on implicitly.
  -W FILE, --what-if=FILE, --new-file=FILE, --assume-new=FILE
                              Consider FILE to be infinitely new.
  --warn-undefined-variables  Warn when an undefined variable is referenced.


This program built for i686-pc-linux-gnu
Report bugs to <bug-make@gnu.org>
: command not found
: command not found
 ready to be used

```

So, what's the problem here???

---

### Post by steeldriver on 2014-06-04
it looks like there's an error in the script that is causing the zip file not to get downloaded?

```

--2014-06-04 16:37:48--  http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.4.9%0D/**opencv-2.4.9[COLOR=#ff0000]%0D[/COLOR].zip/download[COLOR=#ff0000]%0D[/COLOR]**

```

```

Installing OpenCV 2.4.9
.ZIP

```

---

