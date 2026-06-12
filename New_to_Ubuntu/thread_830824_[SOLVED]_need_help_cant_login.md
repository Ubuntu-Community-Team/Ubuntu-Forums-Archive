---
title: "[SOLVED] need help cant login"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Bob1nz on 2008-06-16
Hi I have been using ubuntu 8.04 for a week or 2 and I was mucking around with the sound driver trying to install a new one to see if i could get better sound control options but now I cant get past the login screen and get this message:

/ect/gdm/xsession: beginning session setup...
Setting IM through im-switch for locale=en_NZ
Start IM through /ect/x11/xinit/xinput.d/all_ALL linked to /ect/x11/xinit/xinput.d/default.
/usr/bin/seahorse-agent:error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory


Also the little drum sound isnt there when the login screen appears
Any help would be greatly appreciated

---

### Post by drs305 on 2008-06-16
First, did you hand-type the generated messages? There are references to "/**ect**/gdm/xsession" when it should be "/**etc**..." 

Perhaps you can start in recovery mode. If so and you can get to a terminal or synaptic, reinstall 'libasound2'. 
```
sudo aptitude update && sudo aptitude install libasound2
```

---

### Post by Bob1nz on 2008-06-16
hey thanks for the reply yes it was hand typed sorry about that mistake
i managed to login to the terminal in failsafe mode and did as you said regarding reinstalling libasound2 but Im still getting the same message

---

### Post by drs305 on 2008-06-16
You don't seem to be getting much assistance. The only things I can think of trying are:
1. Reconfigure gdm
```
sudo dpkg-reconfigure gdm
```

2. Try to reconfigure xorg to see if it resets something:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3.  Take a look at /etc/x11/xinit/xinput.d/all_ALL link and default (same contents).  Mine has nothing of note in it so if you have any lines that might be suspect you could try commenting them out. Here is what the relevant lines of mine looks like (uncommented lines only):
```

XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
GTK_IM_MODULE=
QT_IM_MODULE=
DEPENDS=

```

Sorry I can't help with a definitive answer, but at least this bumps your thread...

---

### Post by Bob1nz on 2008-06-16
thanks for your help so far I followed all your steps but still cant login to any gui. My all_ALL and default files were both the same as yours. Was wondering if the default-xim file has anything to do with my problem? 

Heres the lines that look important in default-xim:

XIM=none
XIM_PROGRAM=
XIM_ARGS=
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS=

Not sure if it has anything to do with it at all im just shooting at the wind 

Thanks again

---

### Post by drs305 on 2008-06-16
My default.xim looks the same as yours.

Do you have libasound.so.2 in /usr/lib/ and /usr/lib32/  (I do.)
```
sudo find / -iname libasound.so.2
```

---

### Post by Bob1nz on 2008-06-16
libasound.so.2 is in my lib32 folder but not in my lib folder are they both the same on yours? if so is it just a matter of copy and paste? its also not in my lib64 folder either? Im not sure if this makes a difference or not i am using the 64bit version of hardy

---

### Post by drs305 on 2008-06-16
> **Bob1nz said:**
> libasound.so.2 is in my lib32 folder but not in my lib folder are they both the same on yours? if so is it just a matter of copy and paste? its also not in my lib64 folder either? Im not sure if this makes a difference or not i am using the 64bit version of hardy

In my /usr/lib, /usr/lib32 and/usr /lib64 I have a link libasound.so.2 which in each case links to the libasound.so.2.0.0 in each folder. So I have 1 each libaound.so.2 (link) and libasound.so.2.0.0 in each of the three lib folders.

---

### Post by Bob1nz on 2008-06-17
ok so i made a mistake before those files are in lib64
what iv done is copied the libasound.so.2 and the libasound.so.2.0.0 files from the lib32 folder into the lib folder then rebooted and got a new error message same as the first one at the top of this thread except the last line said this:

/usr/bin/seahorse-agent:error while loading shared libraries: libasound.so.2:wrong ELF class: ELFCLASS32

so i did a bit of a google on elfclass32 and semi-figured that it needed a 64bit version of the file(just guessing here). So i booted the live cd again and found the files from the lib64 folder and copied them to the lib folder replacing the ones id put in earlier.
however i still got the same ELFCLASS32 message and cant go any further.
so close yet so far...
off to see if i can find any more info from google

---

### Post by Bob1nz on 2008-06-18
iv given up on trying to fix this and have gone for a fresh install i had all my files backed up with all my themes i wantd so its not a major i would hav liked to have repaired itbut maybe next time

---

