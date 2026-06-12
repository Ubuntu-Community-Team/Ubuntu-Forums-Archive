---
title: "Virtualbox WinXP virus/spyware?"
date: 2008-08-11
forum: Other OS Talk
---

### Post by ncosens on 2008-08-11
I have a bit of a dilemma.

A couple nights ago I finally got Virtualbox running on Ubuntu 8.04 with WinXP Pro as the guest OS.  I had to use the closed source version as the OSE wasn't working.  Got the sound working and a couple other things.  Then I installed Reason 3.0 which was the whole point of using VirtualBox so I wouldn't have to boot to my other hdd to use it.  So far so good.

Then out of nowhere this warning pops up when trying to browse the files in Explorer.

[[IMG]http://img526.imageshack.us/img526/4567/criticalwarningmd9.th.jpg[/IMG]](http://img526.imageshack.us/my.php?image=criticalwarningmd9.jpg)

If I select no: IE opens then attempts to close as part of the 'no' button script but crashes.  It tried to load a web page at this url:

[[IMG]http://img152.imageshack.us/img152/1264/selectnoresulturlcj6.th.jpg[/IMG]](http://img152.imageshack.us/my.php?image=selectnoresulturlcj6.jpg)

I opened the page in Firefox from Ubuntu and it gave me a very colorful and fictionally looking WinXP My Computer window with a scanner progress bar and wanted to download some software which is the same as if I press the yes button:

[[IMG]http://img59.imageshack.us/img59/4884/selectyesresultlf9.th.jpg[/IMG]](http://img59.imageshack.us/my.php?image=selectyesresultlf9.jpg)

I have not downloaded this software because I believe it is some form of malware since it is not coming directly from Microsoft's servers.

I have scanned the virtual hard drive with both Avira AntiVir free fully updated, and Lavasoft Ad-Aware free fully updated.  Only cookies were found and a few warnings about critical system files that couldn't be opened.  And yes I did the most thorough and resource intensive scans I could.

Also when I try to use IE it often takes me to a page that I didn't type in the address bar.  Have a look.  It's Google's home page in the address bar but the page is definitely not google.com

[[IMG]http://img182.imageshack.us/img182/8462/aboutblankinfectionmw1.th.jpg[/IMG]](http://img182.imageshack.us/my.php?image=aboutblankinfectionmw1.jpg)

Once this happens it usually takes awhile to close out the circuit of dialog boxes and windows and web pages it opens trying to entice me to download the program.

It may be possible that this is caused by the proverbial "malicious software" that Microsoft keeps wanting to remove via their updates.  I don't know. Never had this problem before.  If anyone has seen this or has heard of something like this, please let me know how you resolved it.  I'm running WinXP Pro SP1a inside VirtualBox on Ubuntu 8.04

---

### Post by sonofusion82 on 2008-08-11
yes, even as virtual machine, windows are still vulnerable as long as it is connect to the net and not well updated.

the good news is that you can easily wipe that virtual guess OS and reinstall it. no problem.. just a virtual machine.

---

### Post by molom on 2008-08-11
A VM is an equivalent in many ways to a normal OS installation on a PC. It is as vulnerable as Windows installed on your PC. VM's aren't like WINE clients. Therefore its best to have an anti-virus/spyware/malware on the VM or not let it connect to the Internet.

---

### Post by lisati on 2008-08-11
One thing to watch with popups is the behaviour of the pointer over different parts of the popup. Some are graphics that fake a dialog box but are really a image with links to something of a dubious nature.

---

### Post by zmjjmz on 2008-08-11
Why are you using Internet Explorer?

---

