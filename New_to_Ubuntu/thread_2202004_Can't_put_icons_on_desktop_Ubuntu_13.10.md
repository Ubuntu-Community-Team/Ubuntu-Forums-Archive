---
title: "Can't put icons on desktop Ubuntu 13.10"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by dennis-tonevi on 2014-01-26
Hi

Not really an absolute beginner, but haven't used UNIX since the 1970's. Frankly I was glad when they brought out DOS and happier still when they brought out Windows. But I figured UNIX must be better now, so why not give it another try?

Details, I7 Ivy Bridge laptop with 8 gb RAM Windows 8.1 running Ubuntu 13.10 in Virtualbox VM with 1 gb RAM.

Two frustrating initial problems, one is I can't get app icons onto my desktop. I read other forum discussions on this and there was one theory that you can enter "sudo cp /usr/share/applications/firefox.desktop ./Desktop/firefox.desktop", for example. Well, that does put the icon on the desktop, but when I try to run the app it won't, giving a message to the effect that it is an unknown launcher. Then there is another theory that you can navigate to the folder containing the app and right click on it and press "make link". The problem with that theory is that the "make link" is greyed out and doesn't work. Further research indicates this may be because I don't own the folder. Well who does own it? I'm the only user. Has it been stolen, and if so, how can I get it back?

Oh, the second issue is the scroll wheel on my Microsoft mouse doesn't work in Ubuntu.

any help appreciated

:confused:

---

### Post by RadicaX on 2014-01-27
What version of Ubuntu? I mean like Kubuntu or Ubuntu. I believe with the Unity Desktop (normal Ubuntu) you can only have shortcuts to the apps to the side window. I highly doubt it has been "Stolen" especially if you are the only account. The command above indeed puts it in desktop... but go to your file manager, you will find "Desktop" there. If you had something like Xubuntu, it should let you make shortcuts with ease.

---

### Post by squakie on 2014-01-27
I've been through this myself.  The untrusted launcher message was fixed by right-clicking on the icon on the desktop, then properties and changing permissions to make executable.  Also, you don't need sudo to copy files from /usr/shae/applications - and doing so might make the resulting file owned by root instead of you.  To check this, right-click on the icon on the desktop, then properties and then check the ownership under permissions.  If the owner is root, you will need to change this via a terminal window:

ctrl/alt/F1 - then log in with your normal userid and password (the password isn't echoed)

cd Desktop

ls -al  => you will be able to see your particular desktop file, such as firefox.desktop.

now change the ownership:

sudo chown <your userid> firefox.desktop

now change the group:

sudo chgrp <your userid> firefox.desktop

If the file doesn't show as executable, you can do that now also:

chmod +x firefox.desktop

Hope that helps.

EDIT:  BTW - you get the permissions error when trying to create the link because the folder is owned by the system (root), not you.  You shouldn't need the links anyway - just do as I mentioned.  I didn't figure this out - I had to rely on others to get me going on this, so I'm just trying to pay it forward.

---

### Post by DuckHook on 2014-01-27
You are basically asking for a crash-course in Linux (which is different enough from UNIX that you are setting yourself up for disappointment assuming they are the same). Linux is about 10,000 times as powerful (and complex) as DOS, so please don't set yourself up with unrealistic expectations.

In your case, I highly highly recommend the following sites:

"Linux is not Windows" intro:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It is the furthest thing from my intent to discourage you, but the number one fallacy of new users from Windows is coming into Linux thinking that any of its distributions is just a free version of Windows, complete with all of the bad old Windows habits, quirks and paradigms. Linux will be unfamiliar to you, use completely different desktop paradigms and have an appreciable learning curve. It is also far more secure, but the price of that security is complexity, more details and persnickety things like file ownerships and permissions. You must decide if you are okay with this. Only if you are do I recommend that you forge ahead.

If you are still reading, then:

Unity (Ubuntu's default desktop environment) is not designed to throw a million icons onto the desktop. Rather, it is designed to attach your most frequently used apps to the launcher (bar on left), and the occasional apps to be launched from the dash. You invoke the dash in applications mode with <Super>+<a> then type in the name of the app. The dash will return matching selections after the first two or three letters. Some people hate this layout, in which case, I would recommend that you install Kubuntu, Xubuntu, or Lubuntu instead.

However, if you simply must have desktop icons for your apps, then the process is just a tad more complicated. Instructions [here]("http://ubuntuforums.org/showthread.php?t=2181761").

The best option for you would be to install 12.04 instead of 13.10. 12.04 is a long term release with old functionality intact (i.e. desktop icons can be created by drag-copying them from /usr/share/applications to desktop). Also, because it is LTS, it is supported and updated until 2017 whereas 13.10 is supported only until June of this year. Once more, just because 13.10 is newer does not mean that it is "better", especially for new users. Actually, it is designed more for Linux enthusiasts who must have the bleeding edge stuff whereas 12.04 is designed for new users and those who need a stable and secure long-term environment.

---

### Post by dennis-tonevi on 2014-01-27
Thanks for all the replies

RadicaX - it's standard Ubuntu from the Ubuntu site
squakie, thanks for the useful info, it may come in handy
DuckHook, thanks, will try the 12.04, it sounds more appropriate for my needs

---

### Post by RadicaX on 2014-01-27
A lot of people are in for a bit of a shock when they first start trying out some of the Linux Distros out there to see how different they are. I hope you find one that suits you, Kubuntu has a Gui that is a little more akin to the Windows Gui. Xubuntu is a bit different, (the task bar on top when you first use it, but it is easy to put short cuts on the desktop.) but it life is about to end with 14.04 coming out soon. (just 12.04 I mean, the other Ubuntus are different in this regard.) 

If your problem is fixed, be sure to mark the thread solved, and if you just want to try Ubuntu without doing a new liveCD,

```
sudo apt-get update
```

```
sudo apt-get install xubuntu-desktop
``` 

Then reboot the computer, and you should see a thing called "Session" by the log-in stuff, change it to XFCE and you will be in XFCE. Back up any important data first of course. 

And you can change the code if you want to try Kubuntu to sudo apt-get install kubuntu-desktop. And at sessions looking for KDE.

---

### Post by deadflowr on 2014-01-27
Quick note:
  You shouldn't need to use sudo to copy into your home folder.
Only when copying into a system folder.
So instead of
```
sudo cp /usr/share/applications/thingyiwant.desktop /home/me/Desktop/
```
just use
```
cp /usr/share/applications/thingyiwant.desktop /home/me/Desktop
```
if you don't have to run as root, then don't.

---

