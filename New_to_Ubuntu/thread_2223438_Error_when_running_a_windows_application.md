---
title: "Error when running a windows application"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Godwin_Omolola on 2014-05-11
Hello All,
I got this error when trying to lauch an application executable LdapBlindExplorer.exe in ubuntu.

Can  anyone tell me how to resolve this issue.

Thanks.

Godwin.

Error:
  
Archive:  /home/user/Downloads/LdapBlindExplorer.exe
[/home/user/Downloads/LdapBlindExplorer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/user/Downloads/LdapBlindExplorer.exe or
          /home/user/Downloads/LdapBlindExplorer.exe.zip, and cannot find /home/user/Downloads/LdapBlindExplorer.exe.ZIP, period.

---

### Post by 3rdalbum on 2014-05-11
Ubuntu doesn't run Windows programs natively. There is a program for Ubuntu called Wine that can run a small number of Windows programs, you can install Wine from Ubuntu Software Center.

To run that program in Wine, open a terminal, type 'wine ' leaving a space bar at the end, and then drag the .exe file to the terminal.

---

