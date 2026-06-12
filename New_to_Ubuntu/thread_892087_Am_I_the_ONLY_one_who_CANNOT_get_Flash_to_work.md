---
title: "Am I the ONLY one who CANNOT get Flash to work??"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by radi0j0hn on 2008-08-16
I've really enjoyed Ubuntu, it does everything I need EXCEPT I can't watch a video on CNN, Youtube, etc.

Can someone PLEASE --in careful numbered steps without assuming I know a lot about sudo apt-get, etc.--explain how to install whatever is needed to play the darn files.  I've got Java and (supposedly) Flash installed.

But please, if you are going to help, really lay it out in a step-by-step fashion beginning at square one, not three!

Thanks in advance!    John

---

### Post by andysking on 2008-08-16
you should be able to get a flash player on synaptic. Or a plugin for firefox.

---

### Post by dje on 2008-08-16
ok open a terminal and type (applications >> accessories >> terminal) and run this pressing enter after typing/pasting the command:
```
sudo apt-get install flashplugin-nonfree
```
enter your password when/if prompted (it will not appear as though it is being registered but it is, just enter your password and hit enter). let it run through that entering the letter y and then pressing enter again if prompted to confirm the install

alternatively open up add/remove and search for:
> flashplugin
and mark Macromedia Flash plugin for installation

hope that helps
dje

---

### Post by jmd9qs on 2008-08-16
you aren't the only one... flash doesn't seem to work on hardy and i can't find a fix, either. i use shockwave flash as a plugin for firefox, and it works (most of the time) for videos but as far as flash animation, i am at a loss myself.

---

### Post by niyonk on 2008-08-16
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

this link will give you step-by-step procedures.
remove all flash plugins you already installed and read from the link i posted :)

Cheers!

---

### Post by nicedude on 2008-08-16
Re: Am I the ONLY one who CANNOT get Flash to work?? I guess so as I can watch flash videos just fine as well as download them. Sorry but thats the question you asked.

---

### Post by TJCIB on 2008-08-16
Follow this guide.  It has worked on 20+ installations for me every time...

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

sorry, should be this one...newer version:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
(this is linked in the first page i said)

---

### Post by pparks1 on 2008-08-16
I maintain a comprehensive Ubuntu setup guide on another forum and here are my steps

[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)
Choose Download .tar.gz for Linux. Choose Save file when asked
Open a terminal
cd Desktop
gunzip *.gz
tar -xvf *.tar
cd install_flash_player_9_linux/
sudo ./flashplayer-installer
when asked for browser install point, enter /usr/lib/firefox-3.0b5 (or whatever your browser may be)

Hope that helps.

---

### Post by ptn107 on 2008-08-16
```
sudo apt-get install swfdec-mozilla
```

---

### Post by vikramaditya on 2008-08-16
If it's any help, both java & flash were buggy as hell when I used FF after installing hardy.  Then I d/l'ed & installed the *real* Opera (from their site) & it's been smooth sailing ever since.

---

### Post by aysiu on 2008-08-16
> **radi0j0hn said:**
> I've really enjoyed Ubuntu, it does everything I need EXCEPT I can't watch a video on CNN, Youtube, etc.

Can someone PLEASE --in careful numbered steps without assuming I know a lot about sudo apt-get, etc.--explain how to install whatever is needed to play the darn files.  I've got Java and (supposedly) Flash installed.

But please, if you are going to help, really lay it out in a step-by-step fashion beginning at square one, not three!

Thanks in advance!    John
Unlike most other guides that will plop you to the terminal immediately, this will guide you step by step with screenshots and not assume anything:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by pparks1 on 2008-08-17
What's wrong with the terminal?  It allows for the cutting and pasting of instructions.   It's hard to type something in wrong or do the wrong step when you cut and paste.   That's why I try to do absolutely everything at the terminal.

---

### Post by aysiu on 2008-08-17
> **pparks1 said:**
> What's wrong with the terminal?  It allows for the cutting and pasting of instructions.   It's hard to type something in wrong or do the wrong step when you cut and paste.   That's why I try to do absolutely everything at the terminal.
This is what the OP said: > Can someone PLEASE --in careful numbered steps without assuming I know a lot about sudo apt-get, etc. I hope that answers your question.

---

### Post by pparks1 on 2008-08-17
> **aysiu said:**
> This is what the OP said:  I hope that answers your question.

I tried to provide a short concise set of steps which don't require any knowledge of apt and other utilities.

This is the guide that I put together for another forum. [http://itcertforum.com/forum/showthread.php?t=205](http://itcertforum.com/forum/showthread.php?t=205).   Most members there have had absolutely no experience whatsoever with Linux and many downloaded it after chatting with me.  Many used this guide and successfully were able to get their systems up and operational.   And it's almost exclusively a command line setup guide.   

Just because it's at the command line, doesn't necessarily mean it's complicated.  Maybe by posting my guide link, it will provide him with the information that he needs.

---

### Post by Crafty Kisses on 2008-08-17
Flash works perfect on every box with Linux that I've had, try Gnash.

---

### Post by Cope57 on 2008-08-17
```
sudo aptitude update && sudo aptitude install swfdec-mozilla swfdec-gnome swfdec-mozilla
```
**Y**/n to any additional dependencies.

But then again, it should work since they are in the Ubuntu [[COLOR="Red"]universe[/COLOR]] repositories.

I do not have Adobe flash installed, and I am able to view flash movies / animations on YouTube, and other places using swfdec.

---

### Post by LaRoza on 2008-08-17
I use Flash 10 beta 2 with Opera 9.51 all the time.

The simplest way to install Flash is to download the tarball (.tar.gz) extract, and run the install script (it just moves the flash plugin to the appropriate directory). I install to ~/.mozilla/plugins (opera looks there for plugins)

---

### Post by Loaded.len on 2008-08-17
"sudo apt-get install ubuntu-restricted extras" worked for me (on several machines) or if you prefer GUI over CLI...

Click Applications
Click Add/Remove
Select All Available Applications in the "Show:" dropdown
Search for "restricted"
Select ubuntu-restricted extras and Apply.

Come to think of it, I DID have some problems on one particular machine... a Blue and White G3 PPC. Never did get it figured out on that bad boy, the PPC architecture just doesn't jive with anything flash related running on Linux.

---

### Post by t0p on 2008-08-17
Looks like it! ;)

If you want some more instructions to follow: check **ajgreeny's** advice [here]("http://ubuntuforums.org/showthread.php?t=891976").  Works for me anyway.

---

