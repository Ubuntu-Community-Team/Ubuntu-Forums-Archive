---
title: "Environment variable in Ubuntu"
date: 2016-02-25
forum: New to Ubuntu
---

### Post by krishna19 on 2016-02-25
Hi All,


I know this is gonna be a silly question.:-P


In Windows world you have to set Environment path or run it from the specific folder to run an application.


For example:


C:\OpenSSL-Win32>openssl
'openssl' is not recognized as an internal or external command,
operable program or batch file.


C:\OpenSSL-Win32>**cd bin**


C:\OpenSSL-Win32\bin>openssl
OpenSSL>


It works when I move to bin folder.




But in my Ubuntu it works without any extra config:


ubuntu@hostname:~$ openssl
OpenSSL> 


How does it work?


Krishna

---

### Post by sisco311 on 2016-02-25
In Ubuntu (like in all Unix-like systems) the PATH environment variable contains a list of directory paths.  When the user types a command without providing the full or relative path, this list is checked to see whether it contains a path that leads to the command.

Unlike in Windows, by default the current working directory is not included in PATH. 



For more details, check out:
[http://www.howtogeek.com/137096/6-ways-the-linux-file-system-is-different-from-the-windows-file-system/](http://www.howtogeek.com/137096/6-ways-the-linux-file-system-is-different-from-the-windows-file-system/)
and
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
and
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

