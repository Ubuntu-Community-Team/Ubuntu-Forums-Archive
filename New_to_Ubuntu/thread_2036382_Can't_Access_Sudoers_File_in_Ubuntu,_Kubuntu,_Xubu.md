---
title: "Can't Access Sudoers File in Ubuntu, Kubuntu, Xubuntu"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by gdawg on 2012-08-01
I managed to somehow mess-up /etc/sudoers file and now I am unable to access it. I added 2 users to the file using 'sudo visudo' command and apparently messed something up. Here are the results of attempts to access file:```
 jane@gdawg-Inspiron-530s:~$ sudo visudo
sudo: >>> /etc/sudoers: syntax error near line 9 <<<
sudo: >>> /etc/sudoers: syntax error near line 9 <<<
sudo: parse error in /etc/sudoers near line 9
sudo: no valid sudoers sources found, quitting...
sudo: unable to initialise policy plug-in
 
```I recently installed Ubuntu Remix. All help is welcome.

Linux gdawg-Inspiron-530s 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by drs305 on 2012-08-01
Take a look at *psychocat's* page on fixing sudo:
[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by NikTh on 2012-08-01
Hi , 

please open a terminal and run 
```
pkexec gedit /etc/sudoers 
```copy-paste below code inside (DELETE everything else , if any) 
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults    env_reset
 # Host alias specification
 # User alias specification
 # Cmnd alias specification
 # User privilege specification
root    ALL=(ALL) ALL
 # Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d
 # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```save the file , and tell me if your problem fixed. 

Thanks

---

### Post by gdawg on 2012-08-01
Thanks for the replies. Tried both suggestions and neither worked. Psychocat's method had me boot into recovery mode, select "drop to root shell prompt", enter "mount -o rw, remount /" and response is "mount: special device remount does not exist".
NikTh's method produced this result:```
 jane@gdawg-Inspiron-530s:~$ pkexec gedit /etc/sudoers
Cannot open display: 
Run '/usr/bin/gedit --help' to see a full list of available command line options.

** (gedit:2533): WARNING **: Command line `dbus-launch --autolaunch=89df75f973f485e2fea070210000000c --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
 
```I don't know what else to try. Thanks again.

---

### Post by steeldriver on 2012-08-01
try psychocat's method again, you mistyped the mount command - there should be no space after the comma between the options rw,remount

```
mount -o **rw,remount** / 
```(with the space there it treats 'remount' as a block special device not a second option)

---

### Post by gdawg on 2012-08-02
Thank you steeldriver. It's finally fixed. I had to deviate some from psychocat's instructions. My situation fit "Case 2" of repair instructions but it wouldn't work with any sudo command so I entered "visudo" at root prompt and then used NikTh's "/etc/sudoers" sample file to correct the file.
Thanks to all for your excellent help.

Regards,

Glen

---

### Post by NikTh on 2012-08-02
Hi , 
glad you solved . 

For future knowledge (maybe): If I understood correctly you applied command I gave you from recovery mode. Gedit its a graphical application and cannot be applied with no Desktop environment. It was my mistake I didn't mention that. 
You should apply the command from your Desktop environment (nor Recovery mode or Console) 
or else you should be run nano instead . 
```
pkexec nano /etc/sudoers
``` 

Thanks

---

### Post by dhirendra2212 on 2013-05-16
Thanks Nikth,

Your file worked.

Dear fellas, If you cant open the sudoers file then just make a newfile in home dir and then sudo paste it in /etc with name sudoers.

---

