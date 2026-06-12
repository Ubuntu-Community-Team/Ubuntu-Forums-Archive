---
title: "Python get users home folder"
date: 2008-06-05
forum: Programming Talk
---

### Post by mevets on 2008-06-05
How do I get the home folder of the current user's home folder on linux? Google searches for this topic only gave me results on how do this on win32.

---

### Post by LaRoza on 2008-06-05
```

>>> import os
>>> os.getenv("HOME")
'/home/laroza'
>>> 

```

Odd your results, as Windows has no home folder.

---

### Post by mevets on 2008-06-05
I was getting results for how to get the current user, but thanks I hope this works.

---

### Post by slavik on 2008-06-05
yes it does (well, WinNT has it).

in Win XP/2k/2k3 it is C:\Documents and Settings\%username%\
in Vista, it is C:\Users\%username%\

---

### Post by LaRoza on 2008-06-05
> **mevets said:**
> I was getting results for how to get the current user, but thanks I hope this works.
```

>>> import os
>>> os.getlogin()
'laroza'
>>> 

```

---

### Post by LaRoza on 2008-06-05
> **slavik said:**
> yes it does (well, WinNT has it).

in Win XP/2k/2k3 it is C:\Documents and Settings\%username%\
in Vista, it is C:\Users\%username%\

It isn't normally called "home" though. it is called %HOMEPATH%.

---

### Post by Can+~ on 2008-06-05
If you get some of this questions, open a python shell (gnome-do for extra speed :KS) and do
>>> import os
>>> dir(os)
```
['EX_CANTCREAT', 'EX_CONFIG', 'EX_DATAERR', 'EX_IOERR', 'EX_NOHOST', 'EX_NOINPUT', 'EX_NOPERM', 'EX_NOUSER', 'EX_OK', 'EX_OSERR', 'EX_OSFILE', 'EX_PROTOCOL', 'EX_SOFTWARE', 'EX_TEMPFAIL', 'EX_UNAVAILABLE', 'EX_USAGE', 'F_OK', 'NGROUPS_MAX', 'O_APPEND', 'O_CREAT', 'O_DIRECT', 'O_DIRECTORY', 'O_DSYNC', 'O_EXCL', 'O_LARGEFILE', 'O_NDELAY', 'O_NOCTTY', 'O_NOFOLLOW', 'O_NONBLOCK', 'O_RDONLY', 'O_RDWR', 'O_RSYNC', 'O_SYNC', 'O_TRUNC', 'O_WRONLY', 'P_NOWAIT', 'P_NOWAITO', 'P_WAIT', 'R_OK', 'SEEK_CUR', 'SEEK_END', 'SEEK_SET', 'TMP_MAX', 'UserDict', 'WCONTINUED', 'WCOREDUMP', 'WEXITSTATUS', 'WIFCONTINUED', 'WIFEXITED', 'WIFSIGNALED', 'WIFSTOPPED', 'WNOHANG', 'WSTOPSIG', 'WTERMSIG', 'WUNTRACED', 'W_OK', 'X_OK', '_Environ', '__all__', '__builtins__', '__doc__', '__file__', '__name__', '_copy_reg', '_execvpe', '_exists', '_exit', '_get_exports_list', '_make_stat_result', '_make_statvfs_result', '_pickle_stat_result', '_pickle_statvfs_result', '_spawnvef', 'abort', 'access', 'altsep', 'chdir', 'chmod', 'chown', 'chroot', 'close', 'confstr', 'confstr_names', 'ctermid', 'curdir', 'defpath', 'devnull', 'dup', 'dup2', 'environ', 'error', 'execl', 'execle', 'execlp', 'execlpe', 'execv', 'execve', 'execvp', 'execvpe', 'extsep', 'fchdir', 'fdatasync', 'fdopen', 'fork', 'forkpty', 'fpathconf', 'fstat', 'fstatvfs', 'fsync', 'ftruncate', 'getcwd', 'getcwdu', 'getegid', 'getenv', 'geteuid', 'getgid', 'getgroups', 'getloadavg', 'getlogin', 'getpgid', 'getpgrp', 'getpid', 'getppid', 'getsid', 'getuid', 'isatty', 'kill', 'killpg', 'lchown', 'linesep', 'link', 'listdir', 'lseek', 'lstat', 'major', 'makedev', 'makedirs', 'minor', 'mkdir', 'mkfifo', 'mknod', 'name', 'nice', 'open', 'openpty', 'pardir', 'path', 'pathconf', 'pathconf_names', 'pathsep', 'pipe', 'popen', 'popen2', 'popen3', 'popen4', 'putenv', 'read', 'readlink', 'remove', 'removedirs', 'rename', 'renames', 'rmdir', 'sep', 'setegid', 'seteuid', 'setgid', 'setgroups', 'setpgid', 'setpgrp', 'setregid', 'setreuid', 'setsid', 'setuid', 'sos.pathpawnl', 'spawnle', 'spawnlp', 'spawnlpe', 'spawnv', 'spawnve', 'spawnvp', 'spawnvpe', 'stat', 'stat_float_times', 'stat_result', 'statvfs', 'statvfs_result', 'strerror', 'symlink', 'sys', 'sysconf', 'sysconf_names', 'system', 'tcgetpgrp', 'tcsetpgrp', 'tempnam', 'times', 'tmpfile', 'tmpnam', 'ttyname', 'umask', 'uname', 'unlink', 'unsetenv', 'urandom', 'utime', 'wait', 'wait3', 'wait4', 'waitpid', 'walk', 'write']
```

Also is good to check the [FONT="Courier New"]os.path[/FONT] for path-related tools, like join "a/b/c" + "d" = "a/b/c/d" (which makes it multiplatform. And the [FONT="Courier New"]sys[/FONT] module

---

### Post by slavik on 2008-06-05
> **LaRoza said:**
> It isn't normally called "home" though. it is called %HOMEPATH%.
well, do you want to argue on the technicality of what the home directory is called or whether there exists a place in which user's data is supposed to go to? (supposed to, because some programs don't follow the guidelines).

---

### Post by LaRoza on 2008-06-06
> **slavik said:**
> well, do you want to argue on the technicality of what the home directory is called or whether there exists a place in which user's data is supposed to go to? (supposed to, because some programs don't follow the guidelines).

I would love to, but I am in the middle of a movie downstairs.

(I was merely pointing out that the users personal directory isn't normally called "home" not that it isn't an appropriate term for it0

---

### Post by rikxik on 2008-06-06
User's home dir - works for windows/unix/linux:

```

home = os.getenv('USERPROFILE') or os.getenv('HOME')

```

---

### Post by skeeterbug on 2008-06-06
> **LaRoza said:**
> It isn't normally called "home" though. it is called %HOMEPATH%.

No it isn't normally called home, but it has roughly the same concept. The user can write to that directory without an Administrator account. This is why it is recommended for applications to store their data there, and not in Program Files (which a normal user account can NOT write to). So a poorly written program would force the user to run the application using Administrator. I still find it amazing how many manufactures send computers to people with an Administrator account with no password, etc.

Back when I lived with my parents, I created a normal user account for them to use on their computer. Anything that required an installation, they had to log off, and log on to the Administrator account. They used an old Compaq Pentium II on Windows XP for a couple of years (using IE 6), with no malware or virus problems. When I was 20 I moved out of state, and they purchased a new Dell. Within a month they had gotten a virus that forced them to re-install windows. I walked my dad through setting up a normal user account, and they have not yet had a problem since he re-formatted. Maybe I should have sent them a Ubuntu CD, but I don't have the patience to explain things to them. They are not tech savy at all. :mad:

/rant off

---

### Post by LaRoza on 2008-06-06
> **skeeterbug said:**
> No it isn't normally called home,

Back when I lived with my parents, I created a normal user account for them to use on their computer. Anything that required an installation, they had to log off, and log on to the Administrator account. They used an old Compaq Pentium II on Windows XP for a couple of years (using IE 6), with no malware or virus problems. When I was 20 I moved out of state, and they purchased a new Dell. Within a month they had gotten a virus that forced them to re-install windows. I walked my dad through setting up a normal user account, and they have not yet had a problem since he re-formatted. Maybe I should have sent them a Ubuntu CD, but I don't have the patience to explain things to them. They are not tech savy at all. :mad:


I already said I understand that.

I make sure people I know have such a setup also. Now, they have a good computer, no "anti-virus" and no viruses.

---

### Post by marcosconio on 2008-08-12
> **mevets said:**
> How do I get the home folder of the current user's home folder on linux? Google searches for this topic only gave me results on how do this on win32.

Hello.

You can try this
```

In [1]: import os

In [2]: os.path.expanduser('~')
Out[2]: '/home/marcos'

```

It works in linux & in Win too.

Bye!

Marcos Alcazar
Mendoza. Argentina.

---

### Post by red_Marvin on 2008-08-12
The good thing with os.path.expanduser() is that it can take subfolders in one go, IE: abspath = os.path.expanduser("~/.yourprogram/settings.cfg")

I don't know how the . for hidden folders are interpreted on windows machines though...

---

### Post by samjh on 2008-08-12
> **red_Marvin said:**
> I don't know how the . for hidden folders are interpreted on windows machines though...

The "." is just treated as part of the directory's name in Windows.  It has no special meaning like it does on Linux.

---

### Post by red_Marvin on 2008-08-12
^ Thought so, but it were possible that os.py provided a compability layer or somithing.

---

### Post by xuampy on 2010-11-14
> **red_Marvin said:**
> The good thing with os.path.expanduser() is that it can take subfolders in one go, IE: abspath = os.path.expanduser("~/.yourprogram/settings.cfg")

I don't know how the . for hidden folders are interpreted on windows machines though...

Be careful with that use of os.path.expanduser(), since it's not portable. i.e. 

On Linux:

```

>>> os.path.expanduser("~/.yourprogram/settings.cfg")
'/home/juan/.yourprogram/settings.cfg'
>>> 

```

Which is perfectly OK on Linux. But if you do that on Windows, you'll get the following:

```
>>> os.path.expanduser("~/.yourprogram/settings.cfg")
'C:\\Documents and Settings\\Juan/.yourprogram/settings.cfg'
>>>
```

Which is not what we'd want. So, the most "proper" way I think there is to solve this is:


```
>>>os.path.expanduser(os.path.join("~",".yourprogram","settings.cfg))
'/home/juan/.yourprogram/settings.cfg'
>>> 
```

And the Windows version:
```
>>> os.path.expanduser(os.path.join("~",".yourprogram","settings.cfg"))
'C:\\Documents and Settings\\Juan\\.yourprogram\\settings.cfg'
>>>
```

I know that this is an Ubuntu Forum and no one cares about the Win implementation, but for the sake of Python's portability, I thought it was good to mention the difference.

---

### Post by Tony Flury on 2010-11-15
One word of warning - not all Linux systems have the users home directory to "home/<username>" - since the directory can be set idenpendently.

Also some environment variables may not exist - for instance USERPROFILE does not exist on my machine.

Better to expand "~", rather than rely on the usersname or an env variable - in my opinion anyway.

---

### Post by StephenF on 2010-11-15
os.path.expanduser("~")

---

### Post by rgomes1997 on 2011-09-11
This is platform independent:

```

import os
os.path.expanduser("~")

```

Have fun :)

---

### Post by ofnuts on 2011-09-11
> **slavik said:**
> yes it does (well, WinNT has it).

in Win XP/2k/2k3 it is C:\Documents and Settings\%username%\
in Vista, it is C:\Users\%username%\
When you are lucky... with roaming users it's not... and in system maintained by enlightened users it's not either (user data on a separate partition).  

There are several environment variables that can help (looking at an XP machine, but things are likely the same on Vista/Seven or the Server editions):

[LIST]
[*]APPDATA (points directly to the "Application Data" for the user, which is the right place to store profile stuff, especially for roaming users...)
[*]A combination of HOMEDRIVE and HOMEPATH
[*]USERPROFILE (same as $HOMEDRIVE/$HOMEPATH)
[/LIST]
Specific directories usually found below the user profile (Application Data, My Documents, My Pictures, My Music, etc...) may be renamed or moved elsewhere and the appropriate key in the registry will indicate this.

---

