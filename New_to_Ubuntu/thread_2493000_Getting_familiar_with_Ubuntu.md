---
title: "Getting familiar with Ubuntu"
date: 2023-11-29
forum: New to Ubuntu
---

### Post by airraid2010 on 2023-11-29
Hello,

I have worked as tier 1 help desk over a decade and I am now preparing for transition to system administration role.
I installed Ubuntu Server on a legacy laptop and deployed as a web server for the internal self-service portal.
With very little expertise, I have hard time to configure things with it but it's been very fun learning new things.
I hope I can continue to learn a lot from this great community and interact with you all.

Thanks ;)

---

### Post by MAFoElffen on 2023-11-29
Welcome to Ubuntu. Sounds like you are taking a deep dive. 

The [Ubuntu Server Guide]("https://ubuntu.com/server/docs") is a good reference.

[The Linux Command Handbook]("https://www.freecodecamp.org/news/the-linux-commands-handbook/") will give you a head start on learning Command Line. 

Things online are a good reference, as long as you keep an eye on the dates they were written. Being you have worked i a support role, you know that things in technology can change fast. Try to ensure things you try are what is the current way to do something.

Setup another computer with a Desktop that use as a management console, so you can ssh and scp to your new server. That way you can open a browser and read, cut and paste between things while you are learning. You do not have to be a masochist. I started out on a tty terminal many years ago on Unix, then graduated to a graphics terminal with XServer... Day and night difference. Later I managed everything fro a desktop. 

Most times, I am at a single computer, managing many others from it.

---

### Post by airraid2010 on 2023-11-30
I really appreciate such great references.
I will definitely take a look at those.

Yes. I've ssh-ed and sftp-ed to the laptop deployed as the web server via from Windows 10 command prompt of the computer I was assigned to use to manage things.

---

### Post by TheFu on 2023-11-30
win10 isn't a great client to use ssh/scp/sftp/rsync/sshfs or the 50 other ssh-based tools admins use daily.  Just setting up ssh-keys so all these connections only prompt for credentials once per login is harder on MS-Windows, whereas it is 2 easy commands on Linux workstations.

I avoid working directly on server consoles.  Too painful.  Almost as bad as using MS-Windows. ;)
But from a Linux workstation with a GUI and a few xterms, I can make a server sing.

Right now, I have 15 windows open in this workspace.  8 of those are xterms and most are connected to other systems. Only a few are local to the machine I'm actually using.  "The network is the computer" applies and has since at least the mid-1990s.  My web browser runs on a different system than the one I happen to be sitting behind, for example. Same for email.  I'm actually running 2 different browsers. Both are constrained inside a firejail container for my protection. One of those browsers can't write to any storage. That's one of the constraints.  When it is closed, any temporary files are gone, gone, gone, never to be seen again.

---

### Post by airraid2010 on 2023-12-05
Thanks for the detailed recommendation.
I think it is definitely a worth to try my own.
I have relied on Command Prompt to ssh and sftp to the server I configured but yes I have kinda felt there are some limitations I can't really tell.
I hope I can share my experience with you later.

---

### Post by TheFu on 2023-12-05
The MS-Windows command prompt is very limiting though it might appear to be similar to Unix terminal programs.

If you watch a few videos of people using Linux terminals, starting with beginner level, but then transitioning to experts who don't care about the terminal, but just getting things done, you'll see how different a beginner is to how an expert uses the exact same program.   When I'm showing how to do things at my LUG, I'll share the full workspace with multiple terminals so people can see me use different terminals efficiently. They barely see me type anything because I select/paste between windows seamlessly and use tab-completion like a champ.  It is hard to explain in text, but really easy to see at work.  

Look up tab-completion in bash - that's one of the most important things you can learn today. Master it.   It prevents mistakes and makes typing more than a few characters at a time unnecessary.  Tab-completion is part of the shell program, usually bash. It isn't tied to the terminal program.  However, if you have to use MS-Windows as your workstation, check out putty for terminal use.  It has a good select/paste capability.  Notice, I didn't say copy/paste, but select/paste.  If you are doing more than selecting before pasting, that's extra work and unnecessary.  When people are trying to teach Linux, you'll often see them use a popup menu, select "copy", then use the same popup menu somewhere else, select "paste".  This is for noobs and the hard way.

---

### Post by SeijiSensei on 2023-12-06
If you want to talk to a Linux server from Windows, you should install [**PuTTY**]("https://www.putty.org/"). Then you can initiate SSH sessions with the server.

---

### Post by TheFu on 2023-12-06
+1 for PuTTY when on MS-Windows.  I suspect there might be other alternatives, finally, but for the last 20 yrs or so, Putty was what everyone really used. It has some non-standard aspects, but the functionality we expect from ssh clients is all there.

---

