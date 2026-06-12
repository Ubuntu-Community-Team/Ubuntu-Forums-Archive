---
title: "[SOLVED] widescreen kaput?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by peaceforall on 2008-07-27
Hello,  I installed a Hanns-G 19" momitor and accidentally see to display size to 1600x... Now I can't see or access my menu bar in order to change it back to 1440x900.  I can acces the command line however. Can you help?

---

### Post by mgranet on 2008-07-27
> **peaceforall said:**
> Hello,  I installed a Hanns-G 19" momitor and accidentally see to display size to 1600x... Now I can't see or access my menu bar in order to change it back to 1440x900.  I can acces the command line however. Can you help?

Edit your /etc/X11/xorg.conf file to reflect the new resolution.

---

### Post by eightmillion on 2008-07-27
Press Alt-F2 and a run dialog should open. Enter:
> gnome-display-properties

---

### Post by peaceforall on 2008-07-27
My alt keys do not work and what do I write and where once I'm in xorg.conf?

---

### Post by eightmillion on 2008-07-27
If you have a terminal open, you can just use 'gnome-display-properties' and fix it from the GUI. Otherwise find this section in xorg.conf:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection


```
Change your Modes lines to, Modes            "1440x900"

---

### Post by peaceforall on 2008-07-27
Here is what mine says:

Section "Monitor"
        Identifier     "Configured Monitor"
End Section

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor
        Device          "Configured Video Device"
End Section

```````````````````
That is what it says with no "Modes" line.  How should I proceed?

---

### Post by eightmillion on 2008-07-27
First make a copy of you xorg.conf with:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
Then change your screen section to:
```

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor
        Device "Configured Video Device"
        SubSection "Display"
                Modes           "1400x900"
        EndSubSection
End Section

```

---

### Post by peaceforall on 2008-07-27
Eight Million thank you for your help.  So far I have been able to at least see part of my desktop. I was able to get the Alt-F2 option to work and changed the resolution to 1400x. However when I rebooted "now" using my login/password that I have always used ubu won't let me login to my system. This is a brand new phenom and this has never happened before. Any ideas about how to proceed so I can login at 1400x?

---

### Post by eightmillion on 2008-07-27
Nothing we changed here would affect that. Is your caps lock key on maybe?

---

### Post by peaceforall on 2008-07-27
I double-checked on my caps lock is off.  Would you say I'm dead in the water at this point and will need to do a reinstall that will cause a loss of some of my data/pictures in the process?

---

### Post by eightmillion on 2008-07-27
I wouldn't give up yet. If you can log in with the root recovery console you can use the command:
> passwd username
and change your password. You'll have to replace 'username' with your actual username.

---

### Post by peaceforall on 2008-07-27
I logged in as root and was able successfully change my password.  At reboot no go however, it still won't let me log in?

---

### Post by markbuntu on 2008-07-27
Can you login in gnome safe mode?

---

### Post by eightmillion on 2008-07-27
Log into the recovery console again and run this command:
> dpkg-reconfigure -phigh xserver-xorg
It will ask you a bunch of questions. Answer them as best you can. If you don't know the answer just go with the default. Once it's finished, try logging in again.

---

### Post by peaceforall on 2008-07-27
I think we are getting warm. I did as you said and got this error message 'xserver.xorg' not installed.

---

### Post by eightmillion on 2008-07-27
Well that is strange. Do this command and try logging in again
> apt-get install xserver-xorg

---

### Post by peaceforall on 2008-07-27
Did what you said. It installed, did the phigh again exactly as noted above, and got the same error as noted above?

---

### Post by eightmillion on 2008-07-27
Are you making sure that you're typing xserver**-**xorg and not xserver**.**xorg?

---

### Post by peaceforall on 2008-07-27
Excellent!  I was able to log in.  My mistake, typing the . and not the -. Thank you so much for you help today.  It's been awhile since I've been on this forum. How to I show that this problem was solved and closed.

---

### Post by eightmillion on 2008-07-27
Good. I was racking my brain trying to figure out why it would tell you that xorg wasn't installed. :lolflag:

---

### Post by eightmillion on 2008-07-27
> How to I show that this problem was solved and closed.

I think it's under Thread Tools at the top.

---

### Post by peaceforall on 2008-07-27
Got it. Solved by the best Tech Support in the World....

---

