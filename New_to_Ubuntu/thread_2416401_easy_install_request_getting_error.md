---
title: "easy_install request getting error"
date: 2019-04-09
forum: New to Ubuntu
---

### Post by pratap73 on 2019-04-09
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 13] Permission denied: '/usr/local/lib/python3.6/dist-packages/test-easy-install-9996.write-test'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python3.6/dist-packages/

Perhaps your account does not have write access to this directory?  If the
installation directory is a system-owned directory, you may need to sign in
as the administrator or "root" account.  If you do not have administrative
access to this machine, you may wish to choose a different installation
directory, preferably one that is listed in your PYTHONPATH environment
variable.

For information on other options, you may wish to consult the
documentation at:

  [https://setuptools.readthedocs.io/en/latest/easy_install.html](https://setuptools.readthedocs.io/en/latest/easy_install.html)

Please make the appropriate changes for your system and try again.

---

### Post by huff2 on 2019-04-09
*sudo -i*

then run your command.

The issue is that you are running the command as a "normal" user. You need to tell the computer that you are not a normal user, you are in fact the boss of the show, the administrator. This is why you must use *sudo* before installing or upgrading and are then prompted for your password. ie *sudo apt-get upgrade*. 

From the pages of the manual (I got their by typing *man sudo* in the terminal):

sudo allows a permitted user to execute a command as the superuser or
     another user, as specified by the security policy.  The invoking user's
     real (not effective) user ID is used to determine the user name with
     which to query the security policy.

**DID YOU SEE THIS!!:** This is from the webpage that was in the output of your terminal:

[B][COLOR=#ff0000]Warning[/COLOR]
[/B]
**Easy Install is deprecated. Do not use it. Instead use pip. If you think you need Easy Install, please reach out to the PyPA team (a ticket to pip or setuptools is fine), describing your use-case.**

---

### Post by pratap73 on 2019-04-10
sudo -i
[sudo] password for user: 
root@user-HP-Pavilion-g4-Notebook-PC:~# easy_install requests
easy_install: command not found

---

### Post by huff2 on 2019-04-11
Did you read my whole post? Easy_install will not work. Are you just trying to install the latest Python version? Use APT. 

Simply: sudo apt-get install python3.6

---

