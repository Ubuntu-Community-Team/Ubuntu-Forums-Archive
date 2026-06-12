---
title: "Need help installing XMMS from through terminal"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-09-29
I d/l the XMMS tar.bz file.  Extracted to desktop.  

I opened the terminal typed:

cd Desktop
 cd xmms...
  ./configure


now what?  

thanks

ps- is there an easier way to do this?  Synaptic doesn't have XMMS packages so I had to d/l the tar.bz file from the website.

---

### Post by WWSmith36 on 2008-09-29
Please read and follow this installation guide
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

### Post by Drakkor on 2008-09-29
I thought xmms was dead, anyway you could just use audacious,it's in the repos :D

---

### Post by ubunt2guy on 2008-09-29
> **Drakkor said:**
> I thought xmms was dead, anyway you could just use audacious,it's in the repos :D

oh sweet.  I'll do that.  Is it stable??

---

### Post by bobpur on 2008-09-29
You must be using Ubuntu 8.04 or another distro derived from it. 

I liked XMMS too, but it's not included any more for some reason. If, like me, you want to listen to tunes on Streamtuner/ripper it's not gonna happen without XMMS the default player. 

Unless you know how to change the default player. So, here goes:
1). applications > Sound & Video > Streamtuner > Edit > Preferences 
2). In the "Preferences" dialog box "Applications" should be highlighted. 
3). In the "Actions" box in the first and third line delete both instances of "xmms %q" (Use slide bar to bring them into view.)
4). Next replace with your desired player (Amarok, Audacious, etc.)
NOTE: NO capital letters. DO NOT forget "%q" (These errors are both showstoppers)
Example: "amarok %q" or  "audacious %q" 
ALSO: NO quotation marks. 

I don't know if it's my machines or not, but move the highlighted line off of what you just changed. If you don't it will revert back to "xmms %q." I don't know what it is, but if you don't move the highlighted line to another line besides the ones you just worked on it'll change back to what it was before.

That's it! Back out and enjoy!

---

### Post by Drakkor on 2008-09-29
Hmmmmm......... mine was working fine , but now not so much, you could use rhythmbox comes with hardy,or amarok or vlc,which are in the repos.

---

### Post by Drakkor on 2008-09-29
Just fixed my audacious, I guess after the upgrade it didn't work, did a little research and changed "PulseAudio" output plug-in to "Alsa" output plug-in,and now it works fine ! :D

---

### Post by markbuntu on 2008-09-29
No need to build xmms, it is available as debs:

i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

---

### Post by Drakkor on 2008-09-29
Hmmmm......... it looks just like audacious to me,lol :)

---

