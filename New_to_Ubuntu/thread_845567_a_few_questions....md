---
title: "a few questions..."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Omega234 on 2008-06-30
So... I just installed Ubuntu Server 8.04 (completely text - no graphical interface whatsoever).  I wanted a bit of help with a few things...

Firstly, is there a way to change the default login text?  Right now, it just says
"Ubuntu 8.04 omega234 ttyX
omega234 login: _"
And I was wondering if there's a text file or something to modify that?  I don't need to modify .bashrc - when I log in it says stuff, but I want it to say things *before* I log in, so is there any way to do that?

Secondly, regarding flash drives - how can I mount one?  I know about the mount command, but my flash drive is currently formatted for UNIX (I used it on my Mac), but I'm not sure how to mount that.  If I just do something like "mount /dev/sdb /media/usb/", it complains about "mount: you must specify the filesystem type"... I know this involves the "-t" switch, but what would I put right after that?  Or is there maybe a better way to do this?

Another thing I was wondering about - is there a way to set up my server as a mail server?  It's essentially pointless to do, I know - it's just me and my family within my network - but I'd kind of like to play around with it to learn more about Linux and mail and stuff.  Any ideas?

One last thing: configuring the prompt.  I've changed my default prompt to be almost how I want it, except one thing: I want a trailing slash on the end of the current working directory.  I've added in a "/" to where it should belong, but one thing bothers me: the root directory.  It's a bit odd to see "//" as the current working directory, so how would I go about fixing that?

Thanks for all info.

Oh, P.S. - I'm not scared of playing with settings at all.  It's just a small project I'm having fun with for now, and I also have root enabled.  Lastly, if there's anything anyone thinks maybe I should try (for whatever reason), go ahead and tell me - I don't have a whole lot of ideas of what to do with this server, so any sort of customization or programs or whatever would be cool.

Thanks again!

---

### Post by sayakb on 2008-06-30
```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

---

### Post by Omega234 on 2008-06-30
Hmm...
I try that, and it still says "mount: you must specify the filesystem type"... if I look in [FONT="Courier New"]/dev/[/FONT] for anything with "sdb", I get this:
```
/dev/ $ ls | grep sdb
sdb
sdb1
sdb2
sdb3
sdb4
```
So... does that mean that there's more than one partition on the drive?  If so, that's odd, because I should only have one partition on the drive...

Thanks for the quick response, though!

---

### Post by stoneybroke on 2008-06-30
If you use this sudo tasksel you will be able to install a mail server as well as any desktop you wish if you are thinking of creating a website to use with the server using LAMP then try TYPO3 at [www.typo3.org](www.typo3.org) or [www.typo3.net](www.typo3.net) it is free to download but it takes a lot of time to learn fully but there are loads of documents and video to help you.

Enjoy

---

### Post by deejaypip on 2008-06-30
To change the login screen text:

system -> administration -> login window

You should get a menu that has a bunch of tabs.

Click on 'local.'

At the very bottom of the menu, you can choose between the default message and a custom one. 

I will tell you this, though: this doesn't work if you have installed a fancy login theme from gnome-look or something.

---

### Post by Omega234 on 2008-06-30
@stoneybroke:
Hey, thanks!  I already had it set up as a LAMP server, but I didn't know about TYPO3 - I'll have to download that and try it out.

@deejaypip:
Oh, thanks, but it's Ubuntu Server, so there's no graphical interface - all text based.  Thanks though - I'll have to remember that if I ever decide to get a regular Ubuntu desktop.  I guess I forgot to mention the text-only thing in the first post... I'll have to fix that...

---

### Post by jordanmthomas on 2008-06-30
The file you're looking for is /etc/issue

---

### Post by Omega234 on 2008-06-30
Oh, thanks!  That's exactly what I wanted for that.

You wouldn't happen to know if there's a way to change the "omega234 login:" bit that comes under that, would you?

---

### Post by jordanmthomas on 2008-06-30
You can change your hostname but it would still just be "hostname login:"

It'd be possible to recompile login if you *really* wanted it changed.  A quick look at its binary shows it's just a string in there and would probably be defined at compile-time by some header file
```
%s login:
```

I dunno

---

