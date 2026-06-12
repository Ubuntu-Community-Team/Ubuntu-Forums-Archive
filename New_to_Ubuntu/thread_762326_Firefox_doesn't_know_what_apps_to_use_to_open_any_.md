---
title: "Firefox doesn't know what apps to use to open any type of downloaded files"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by hanzj on 2008-04-22
Please take a look at the attached screenshot files:

It says:> This link needs to be opened with an application. Send to
How come Firefox has this problem? Firefox won't even know how to open the folder containing the file.



I'm on Xubuntu 8.04 Beta and using Firefox 3 Beta 5.

---

### Post by Kingsley on 2008-04-22
I guess you don't have a default image viewer set. 

What I would do is look in /usr/bin/ for an image viewer and check the box that says "Remember my choice for file links."

---

### Post by hanzj on 2008-04-22
Kingsley,
It's not just for jpg files. It is for ALL types of files. PDF, DOC, MOV, MP3, etc. ALL filetypes.

---

### Post by hanzj on 2008-04-22
By the way, outside of firefox, there are default file-viewers for the different file-types. The problem seems to be with firefox not "listening" to the computer.

---

### Post by rklk on 2008-05-02
I got exactly the same problem but on Ubuntu 8.04. Firefox won't remember my choice - the options page is always empty and always was.

Similar threads:
[http://ubuntuforums.org/showthread.php?t=774393](http://ubuntuforums.org/showthread.php?t=774393)
[http://ubuntuforums.org/showthread.php?t=775864](http://ubuntuforums.org/showthread.php?t=775864)
[http://ubuntuforums.org/showthread.php?t=772805](http://ubuntuforums.org/showthread.php?t=772805)

---

### Post by hanzj on 2008-05-02
Bug report is at [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220504](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220504). Please check that out. It helped me.

---

### Post by rklk on 2008-05-11
OK, I just couldn't stand it anymore. I have solved this problem by installing **firefox-gnome-support** as it has been suggested here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798). Now everything seems to work fine.

---

### Post by inportb on 2008-05-11
> **rklk said:**
> OK, I just couldn't stand it anymore. I have solved this problem by installing **firefox-gnome-support** as it has been suggested here [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798). Now everything seems to work fine.

That seems to be the way to go. I only wish there were a firefox-kde-support package...

That trick with thunar... I tried it with dolphin and it didn't work. I shall try with konqueror and see what happens. Basically, thunar is acting as a proxy.

EDIT: Yeah, it works... sorta. If it's a format that Konqueror can open or embed, Konqueror displays it; if not, Konqueror launches the suitable app, but Konqueror itself stays open.

---

### Post by LukeT123 on 2009-05-22
I came across this thread in trying to fix a similar problem in Kubuntu.  The solution I found may not apply at all, but I'll drop the info here in case it does.  

I couldn't even 'open containing folder' from the downloads window in Firefox 3.0.10 on Kubuntu 9.04 - AMD 64 - 'Jaunty Jackalope' until I told Firefox where to find Dolphin (the file manager).  I was able to fix this on my system using the method described at the following url.  [http://kubuntuforums.net/forums/index.php?topic=3098337.15](http://kubuntuforums.net/forums/index.php?topic=3098337.15)

  Essentially, when I tried to 'open containing folder' and it asked me to choose an application, I chose my file manager, Dolphin, and selected the remember my choice option.  This allowed me to open folders from the download tab.  As to it not 'remembering' your choice as mentioned by rklk, I'm not sure if he means he's done this and it still forgets or if he means something else.  Hope this helps.  If not, sorry to get your hopes up.

---

### Post by isaidi on 2009-09-14
I get the same thing with Firefox under Mythbuntu 9.04. It is annoying. I will try Firefox-Gnome-Support and see what happens.

was this bug not fixed in latest release ?

---

### Post by MountainX on 2012-03-12
> **isaidi said:**
> I get the same thing with Firefox under Mythbuntu 9.04. It is annoying. I will try Firefox-Gnome-Support and see what happens.

was this bug not fixed in latest release ?

This sounds like the bug I'm having in Kubuntu 12.04 beta 1... **three years** later! #-o

---

### Post by Fincer on 2012-05-02
It seems that LukeT123 has found a solution to this annoying problem for Kubuntu. However, the link he provided doesn't work anymore.

I'm using Kubuntu 12.04 LTS. Firefox is asking a default program to open a file, no matter whether it's the question of a RAR, PDF, AVI or whatever file. Firefox is not even able to understand to use file manager (dolphin) when trying to open "containing folder". Firefox doesn't know what program to use to open a folder. Come on!

Furthermore, I have set default programs for all file types in OS settings. OS is recognizing all programs and file types with no problems.

Firefox is the only program that doesn't really understand to use my default application configurations. The problem is occurred with all newest Firefox releases since last autumn at least.

What should I configure to get rid of this problem with Kubuntu? Does anyone know a real and exact solution? How to tell Firefox about my default apps that it should use for downloaded files?

---

### Post by pqwoerituytrueiwoq on 2012-05-02
edit-> preferences -> applications

---

### Post by Fincer on 2012-05-02
Thanks for your answer, pqwoerituytrueiwoq

However, Firefox doesn't even recognize all system programs. For example, Libreoffice is recognized but Okular is not. Firefox suggests *soffice* to open Word documents but nothing to open PDFs in applications submenu you pointed at. 

It simply reads *default* instead of *Okular* or even any other application there. In other words, Firefox is not able to see any programs which could possibly open PDFs.

However, Libreoffice is found: instead of dummy text *default (*as with PDF documents^), Firefox can even suggest *soffice.*

So, how do I tell Firefox to use Okular to open PDF documents? How do I tell Firefox that a program called Okular exists in my system and should be used to open PDFs?

---

### Post by nucleuskore on 2012-06-14
I am having the same issue with my Kubuntu install :(

---

