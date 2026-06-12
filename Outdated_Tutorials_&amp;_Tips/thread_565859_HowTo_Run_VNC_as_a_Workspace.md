---
title: "HowTo: Run VNC as a Workspace"
date: 2007-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Felson on 2007-10-02
The objective here was to run Windows XP in one of my Gnome Workspaces. In my case, I have created a vitalized copy of Winblows using Qemu. But, that isn't covered here. There are a few howtos that do a good job of explaining that.

Tested and works in:
Edgy (32 bit)
Fiesty (32 bit)
Gutsy (32bit)
Gutsy (64bit)

First we are going to need a few packages.
```

sudo aptitude install wmctrl xtightvncviewer zenity perl

```

Then we need to get a copy of vncpasswd from the TightVNC project. The default one doesn't do what we need it to.
```

wget http://www.myte.ca/files/xtightvncpasswd
sudo cp xtightvncpasswd /usr/bin
sudo chmod 755 /usr/bin/xtightvncpasswd
rm xtightvncpasswd

```
This is a 32bit binary copy extracted from an RPM from there site. If you want to make sure you have the newest one, are running a different processor, or simply don't trust binary executables from random site on the internet, you can get it from [http://www.tightvnc.com/download.html]("http://www.tightvnc.com/download.html") 
and extract it yourself. I rename it to xtightvncpasswd to fit with the tightvnc client package, and to not conflict with the one built in. (I want to know which one I am running)

Next get my handy dandy perl script.
```

wget http://www.myte.ca/files/vnc_ws
sudo cp vnc_ws /usr/local/bin
sudo chmod 755 /usr/local/bin/vnc_ws
rm vnc_ws

```

Now simply run the perl script you just downloaded, and fill in the blanks.

Now the bad news... My script isn't "perfect". there are a few know bugs, and if you find some that aren't listed here, please let me know in this thread.
1) The script is assuming that you are not going to open another copy of TightVNC before this one comes up.
2) There is a /tmp/vncpass file that contains the password to the server that you just connected too. The file is automaticly deleted after you connect, or fail to connect in 10 seconds. If someone knows it's there, and grabs it in the 10 seconds before it's deleted, and knows the host/port of your VNC Server, they can use it to connect
3) You want the target VNC server to be running the same res as you are to display nicely. If it is bigger, you get scrollbars, and if it is smaller, you get a window in the top left corner of the target workspace with no window controls. I tried using krdc instead of TightVNC, but the command line "scale" and "full screen" options don't seem to work in Gnome desktop.

---

### Post by Felson on 2007-10-26
Tested and works in:
Edgy (32 bit)
Fiesty (32 bit)
Gutsy (64bit)

---

### Post by thekman on 2007-11-01
hi guys,

I received the following error when trying to install vmware server:

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.

Please excuse my lack of linux knowledge.

Any help much appreciated.

---

### Post by Felson on 2007-11-01
Sadly I have never worked with Vmware at all. Sorry I can't help you with that. 
Not sure what version of Ubuntu you are useing, but check [this]("http://ubuntuforums.org/showthread.php?t=596189&highlight=vmware") thread  for that. It will probably be more usefull, and the guys there might have a good idea what you need. Depending on what you are trying to do, if vmware doesn't work for you, you could try qemu/kqemu or Xen instead.

---

### Post by thekman on 2007-11-01
I am running Ubuntu 7.10 64 bit

---

### Post by Felson on 2007-11-01
Ya, then the link I gave you should work for ya.

---

