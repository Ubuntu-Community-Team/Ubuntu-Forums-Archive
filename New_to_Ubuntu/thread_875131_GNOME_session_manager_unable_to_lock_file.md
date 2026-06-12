---
title: "GNOME session manager unable to lock file"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by swaj38812 on 2008-07-30
So somehow as if by magic Ubuntu will not boot anymore. It goes to the log in screen and lets me log in then gives me this error

The GNOME session manager was unable to lock file '/home/justin/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwriteable, you could try loggin in via the failsafe session and ensuring that it is.

Well I tried loggin in under the failsafe and it gives me the same error but it will let me log into the failsafe terminal but have no idea what to do from there.

I also tried running the recovery mode and that got me nowhere.

I am sure it is something I did and right when I was really starting to enjoy linux PLEASE help.

---

### Post by Troll_the_Great on 2008-07-30
I think I saw a thread exactly like yours and the answer was to delete that file ICEAutorithy (but I'm not sure so DON"T do anything yet, till I find the thread or somebody more experienced then me gives you an answer).

---

### Post by t0p on 2008-07-30
> **swaj38812 said:**
> 
The GNOME session manager was unable to lock file '/home/justin/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwriteable, you could try loggin in via the failsafe session and ensuring that it is.

Well I tried loggin in under the failsafe and it gives me the same error but it will let me log into the failsafe terminal but have no idea what to do from there.


Try this: log in into failsafe session, and change the permissions on /home/justin/.ICEauthority to make it writeable. As to whom it should be writeable for - your user, root - I don't know.  You'll have to experiment.

---

### Post by swaj38812 on 2008-07-31
I just dont know how to make it writeable once I log into the fail safe terminal.

---

### Post by Potatoj316 on 2008-07-31
to make files writable use chmod
```
chmod a+w /path/to/file
```
this will make it writable for everyone, which may not be what you want to make it writable for only you change the a+w to u+w or for group change to o+w

---

### Post by silkstone on 2008-07-31
The permissions for that file should be read and write for the owner (justin) only.

---

### Post by swaj38812 on 2008-07-31
I logged in to the fail safe terminal typed it in and it did nothing so I restarted and it is still giving me the same error on log in. It says it cant lock the file?? I am really shot out on this one!

---

### Post by silkstone on 2008-07-31
Try this...

Open the failsafe terminal and edit the file **/etc/gdm/Xsession**. Add the following lines right under the **PROGNAME = Xsession line** :

ICEAUTHORITY="tmp/ICEauthority-${root}"
export ICEAUTHORITY

Normally to edit the file you would use gksudo gedit /path to file

I guess this won't work as you can't get into the GUI, so try sudo nano /path to file

---

