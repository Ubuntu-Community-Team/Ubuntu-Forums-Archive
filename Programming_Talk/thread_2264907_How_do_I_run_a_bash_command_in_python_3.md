---
title: "How do I run a bash command in python 3?"
date: 2015-02-11
forum: Programming Talk
---

### Post by lance bermudez on 2015-02-11
Hi I'm trying to learn how to use python. What I want to do it change some of my bash scripts into python 3 scripts as I learn python. I have a bash script that does apt-get update and want to now I would do that in python?

I installed python 3 with apt-get install idle3 to learn python3

found this but I think it is old
import subprocess

def bash_command(cmd):
    subprocess.Popen(cmd, shell=True, executable='/bin/bash')

bash_command('a="Apples and oranges" && echo "${a/oranges/grapes}"')

I get this error message in idle3 
SyntaxError: multiple statements found while compiling a single statement
with a red line after import subprocess

---

### Post by TheFu on 2015-02-11
[https://docs.python.org/3/library/os.html](https://docs.python.org/3/library/os.html) - says os.system().

---

### Post by ian-weisser on 2015-02-11
I use subprocess a lot. It's not old.
See [https://docs.python.org/3/library/subprocess.html](https://docs.python.org/3/library/subprocess.html) . Some helpful examples in there.

---

### Post by Erik1984 on 2015-02-11
Importing the subprocess module should work. I recently used that import statement (and subprocess.call()) in a python 3 application.

What if you open the Python 3 interpreter:
```
python3
```
And then
```
import subprocess
```
?

---

### Post by lance bermudez on 2015-02-12
ok I did a test and get no output to show

import subprocess
subprocess.call(["ls", "-l"])

all I get in the python shell is
>>> ================================ RESTART ================================
>>> 
>>> ================================ RESTART ================================
>>> 

when I do F5 run module. Should it not be giveing me the ls -l of my /home/user directory?

---

### Post by ian-weisser on 2015-02-12
It does work as expected when I do it in terminal. A lovely list of my /home/me
I have not tried it in IDLE.

---

### Post by ofnuts on 2015-02-13
> **lance bermudez said:**
> ok I did a test and get no output to show

import subprocess
subprocess.call(["ls", "-l"])

all I get in the python shell is
>>> ================================ RESTART ================================
>>> 
>>> ================================ RESTART ================================
>>> 

when I do F5 run module. Should it not be giveing me the ls -l of my /home/user directory?

No, it should be listing the contents of the current directory, whatever it is. Try with "subprocess.call(['echo','Hello!'])" (or "subprocess.call(['pwd'])" to see what the current directory is).

---

### Post by lance bermudez on 2015-02-25
is subprocess.call python 3?

#/usr/bin/python
import subprocess
subprocess.call(['rsync -vaPhz /home/lance/bin/ -e \"ssh -p 2222\" 192.168.2.2:/home/lance/Downloads/bin/'])

$python 1.py
Traceback (most recent call last):
  File "1.py", line 3, in <module>
    subprocess.call(['rsync -vaPhz /home/lance/bin/ -e \"ssh -p 9455\" 192.168.2.2:/home/lance/Downloads/bin/'])
  File "/usr/lib/python2.7/subprocess.py", line 522, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.7/subprocess.py", line 710, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1327, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

---

### Post by ofnuts on 2015-02-26
You have to use a list, with every element of your command (executable, parameters) as a list item:
 ```

subprocess.call(['rsync','-vaPhz','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/'])

```

(actual syntax for your command not guaranteed)

---

### Post by lance bermudez on 2015-03-04
the syntax for the above command worked. It even showed the output form rsync as it copied over the files just like I wanted. now I have a new proplem in that I need to see the files as they are copied over but need to be able to have a log flie so is their a was to write the output into a file as you are watching it go across the screen?

my python 3 scripts looks like this

import subprocess
command_process=subprocess.call(['rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/','--log-file=test0.txt'])
command_output = command_process.communicate()[0]
log_file=open('command.log', 'a')
log_file.write(command_output)
log_file.close()

and the output is this

sending incremental file list

Number of files: 217 (reg: 193, dir: 9, link: 15)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 0
Total file size: 10.26M bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 0
File list generation time: 0.133 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 6.82K
Total bytes received: 20

sent 6.82K bytes  received 20 bytes  1.05K bytes/sec
total size is 10.26M  speedup is 1,501.03
Traceback (most recent call last):
  File "rsync1.py", line 10, in <module>
    command_output = command_process.communicate()[0]
AttributeError: 'int' object has no attribute 'communicate'

Do I enven have the right idea? what am I doing wrong?

---

### Post by ofnuts on 2015-03-05
The return value of subprocess.call(...) is the return code of the process once finished.

If you want to capture the output have you tried subprocess.check_output(...)?

---

### Post by lance bermudez on 2015-03-05
```

import subprocess
command_process=subprocess.check_output('rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/')
command_output = command_process.communicate()[0]
log_file=open('command.log', 'a')
log_file.write(command_output)
log_file.close()

```

output
$ python3 rsync2.py 
Traceback (most recent call last):
  File "rsync2.py", line 2, in <module>
    command_process=subprocess.check_output('rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/')
  File "/usr/lib/python3.4/subprocess.py", line 603, in check_output
    with Popen(*popenargs, stdout=PIPE, **kwargs) as process:
TypeError: __init__() got multiple values for argument 'stdout'


so what am I doing wrong? and thank you for your help.

---

### Post by ofnuts on 2015-03-05
> **lance bermudez said:**
> 
  File "rsync2.py", line 2, in <module>
    command_process=subprocess.check_output('rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/')
  File "/usr/lib/python3.4/subprocess.py", line 603, in check_output
    with Popen(*popenargs, stdout=PIPE, **kwargs) as process:
TypeError: __init__() got multiple values for argument 'stdout'

You aren't using check_output correctly at all... Please [RTFM]("https://docs.python.org/3/library/subprocess.html") a bit, check what it needs as arguments and in what form, and what the return value is. Documentation is there for a reason...

---

### Post by lance bermudez on 2015-03-05
thank you for your help and for reminding me about the manuel but if the manuel made sence to me I would not be asking questions here.
```

import subprocess
command_output = subprocess.check_output (['rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/'], shell=True)

log_file = open ('command.log', 'a')
log_file.write (command_output)
log_file.close ()

```

output is
```

$ python3 rsync2.py  
Traceback (most recent call last):
  File "rsync2.py", line 2, in <module>
    command_process=subprocess.check_output('rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/')
  File "/usr/lib/python3.4/subprocess.py", line 603, in check_output
    with Popen(*popenargs, stdout=PIPE, **kwargs) as process:
TypeError: __init__() got multiple values for argument 'stdout'
lance@bermudezl:~/upgrade/Downloads/More Python Programming for the Absolute Beginner/Introduction to Python Programming/PythonBookSourceCode/PythonChapter6Source$ python3 rsync2.py 
rsync  version 3.1.0  protocol version 31
Copyright (C) 1996-2013 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 32-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.

rsync is a file transfer program capable of efficient remote update
via a fast differencing algorithm.

Usage: rsync [OPTION]... SRC [SRC]... DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
  or   rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
  or   rsync [OPTION]... [USER@]HOST:SRC [DEST]
  or   rsync [OPTION]... [USER@]HOST::SRC [DEST]
  or   rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]
The ':' usages connect via remote shell, while '::' & 'rsync://' usages connect
to an rsync daemon, and require SRC or DEST to start with a module name.

Options
 -v, --verbose               increase verbosity
     --info=FLAGS            fine-grained informational verbosity
     --debug=FLAGS           fine-grained debug verbosity
     --msgs2stderr           special output handling for debugging
 -q, --quiet                 suppress non-error messages
     --no-motd               suppress daemon-mode MOTD (see manpage caveat)
 -c, --checksum              skip based on checksum, not mod-time & size
 -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
     --no-OPTION             turn off an implied OPTION (e.g. --no-D)
 -r, --recursive             recurse into directories
 -R, --relative              use relative path names
     --no-implied-dirs       don't send implied dirs with --relative
 -b, --backup                make backups (see --suffix & --backup-dir)
     --backup-dir=DIR        make backups into hierarchy based in DIR
     --suffix=SUFFIX         set backup suffix (default ~ w/o --backup-dir)
 -u, --update                skip files that are newer on the receiver
     --inplace               update destination files in-place (SEE MAN PAGE)
     --append                append data onto shorter files
     --append-verify         like --append, but with old data in file checksum
 -d, --dirs                  transfer directories without recursing
 -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
     --munge-links           munge symlinks to make them safer (but unusable)
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir
 -H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials
 -t, --times                 preserve modification times
 -O, --omit-dir-times        omit directories from --times
 -J, --omit-link-times       omit symlinks from --times
     --super                 receiver attempts super-user activities
     --fake-super            store/recover privileged attrs using xattrs
 -S, --sparse                handle sparse files efficiently
     --preallocate           allocate dest files before writing them
 -n, --dry-run               perform a trial run with no changes made
 -W, --whole-file            copy files whole (without delta-xfer algorithm)
 -x, --one-file-system       don't cross filesystem boundaries
 -B, --block-size=SIZE       force a fixed checksum block-size
 -e, --rsh=COMMAND           specify the remote shell to use
     --rsync-path=PROGRAM    specify the rsync to run on the remote machine
     --existing              skip creating new files on receiver
     --ignore-existing       skip updating files that already exist on receiver
     --remove-source-files   sender removes synchronized files (non-dirs)
     --del                   an alias for --delete-during
     --delete                delete extraneous files from destination dirs
     --delete-before         receiver deletes before transfer, not during
     --delete-during         receiver deletes during the transfer
     --delete-delay          find deletions during, delete after
     --delete-after          receiver deletes after transfer, not during
     --delete-excluded       also delete excluded files from destination dirs
     --ignore-missing-args   ignore missing source args without error
     --delete-missing-args   delete missing source args from destination
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --max-size=SIZE         don't transfer any file larger than SIZE
     --min-size=SIZE         don't transfer any file smaller than SIZE
     --partial               keep partially transferred files
     --partial-dir=DIR       put a partially transferred file into DIR
     --delay-updates         put all updated files into place at transfer's end
 -m, --prune-empty-dirs      prune empty directory chains from the file-list
     --numeric-ids           don't map uid/gid values by user/group name
     --usermap=STRING        custom username mapping
     --groupmap=STRING       custom groupname mapping
     --chown=USER:GROUP      simple username/groupname mapping
     --timeout=SECONDS       set I/O timeout in seconds
     --contimeout=SECONDS    set daemon connection timeout in seconds
 -I, --ignore-times          don't skip files that match in size and mod-time
 -M, --remote-option=OPTION  send OPTION to the remote side only
     --size-only             skip files that match in size
     --modify-window=NUM     compare mod-times with reduced accuracy
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare destination files relative to DIR
     --copy-dest=DIR         ... and include copies of unchanged files
     --link-dest=DIR         hardlink to files in DIR when unchanged
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level
     --skip-compress=LIST    skip compressing files with a suffix in LIST
 -C, --cvs-exclude           auto-ignore files the same way CVS does
 -f, --filter=RULE           add a file-filtering RULE
 -F                          same as --filter='dir-merge /.rsync-filter'
                             repeated: --filter='- .rsync-filter'
     --exclude=PATTERN       exclude files matching PATTERN
     --exclude-from=FILE     read exclude patterns from FILE
     --include=PATTERN       don't exclude files matching PATTERN
     --include-from=FILE     read include patterns from FILE
     --files-from=FILE       read list of source-file names from FILE
 -0, --from0                 all *-from/filter files are delimited by 0s
 -s, --protect-args          no space-splitting; only wildcard special-chars
     --address=ADDRESS       bind address for outgoing socket to daemon
     --port=PORT             specify double-colon alternate port number
     --sockopts=OPTIONS      specify custom TCP options
     --blocking-io           use blocking I/O for the remote shell
     --stats                 give some file-transfer stats
 -8, --8-bit-output          leave high-bit chars unescaped in output
 -h, --human-readable        output numbers in a human-readable format
     --progress              show progress during transfer
 -P                          same as --partial --progress
 -i, --itemize-changes       output a change-summary for all updates
     --out-format=FORMAT     output updates using the specified FORMAT
     --log-file=FILE         log what we're doing to the specified FILE
     --log-file-format=FMT   log updates using the specified FMT
     --password-file=FILE    read daemon-access password from FILE
     --list-only             list the files instead of copying them
     --bwlimit=RATE          limit socket I/O bandwidth
     --outbuf=N|L|B          set output buffering to None, Line, or Block
     --write-batch=FILE      write a batched update to FILE
     --only-write-batch=FILE like --write-batch but w/o updating destination
     --read-batch=FILE       read a batched update from FILE
     --protocol=NUM          force an older protocol version to be used
     --iconv=CONVERT_SPEC    request charset conversion of filenames
     --checksum-seed=NUM     set block/file checksum seed (advanced)
 -4, --ipv4                  prefer IPv4
 -6, --ipv6                  prefer IPv6
     --version               print version number
(-h) --help                  show this help (-h is --help only if used alone)

Use "rsync --daemon --help" to see the daemon-mode command-line options.
Please see the rsync(1) and rsyncd.conf(5) man pages for full documentation.
See http://rsync.samba.org/ for updates, bug reports, and answers
rsync error: syntax or usage error (code 1) at main.c(1556) [client=3.1.0]
Traceback (most recent call last):
  File "rsync2.py", line 2, in <module>
    command_output = subprocess.check_output (['rsync','-vaPhz','--stats','/home/lance/bin/','-e','ssh -p 9455','192.168.2.2:/home/lance/Downloads/bin/'], shell=True)
  File "/usr/lib/python3.4/subprocess.py", line 616, in check_output
    raise CalledProcessError(retcode, process.args, output=output)
subprocess.CalledProcessError: Command '['rsync', '-vaPhz', '--stats', '/home/lance/bin/', '-e', 'ssh -p 9455', '192.168.2.2:/home/lance/Downloads/bin/']' returned non-zero exit status 1

```

---

### Post by ofnuts on 2015-03-05
Remove the shell=True. You don't need it.

---

### Post by lance bermudez on 2015-03-07
when I remove the shell=True the output I get is "TypeError: must be str, not bytes"
```

$ python3 rsync2.py
Traceback (most recent call last):
  File "rsync2.py", line 5, in <module>
    log_file.write (command_output)
TypeError: must be str, not bytes

```

---

### Post by ofnuts on 2015-03-07
With shell='True' you are telling Python to ignore the output, so you don't get an error because you have nothing to work with.

The output from the shell is a sequence of bytes. In the modern world, that includes more languages than just English, the old one-byte-equals-one-character mindset is no longer valid. Non ASCII characters are represented by a sequence of bytes. This is called an "encoding", the best known and most universal one being "UTF-8" (which has the nice property that the pure ASCII characters are represented by a one-byte sequence which is coincidentally their ASCII encoding). 

I'll let you google how to transform a sequence of bytes into a string.

---

