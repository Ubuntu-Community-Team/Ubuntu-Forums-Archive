---
title: "How do you RIP a DVD in 8.04LTS???"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by lentomies on 2008-10-30
Hi Everybody,

I have a home video that was burned to a DVD but now I want to rip it to another file format like wmv or avi maybe divix.

But I don't know if Ubuntu 8.04 is capable of this. If it is what software can I get to do this and from where.

Thanks for the potential info.

---

### Post by aeiah on 2008-10-30
there are several. i like acidrip. you'll need the codecs installed first. what you cant play, you cant encode to. you probably wont be able to encode to wmv but who in their right mind would want to is beyond me.

---

### Post by northern lights on 2008-10-30
Check out [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu").

These should provide all necessary fixes.

---

### Post by clancymf on 2008-10-30
I normally use k9copy and output the burn directly to a blank disc in the second drive.

Also, I heard that Handbrake is coming, or has come out with a GUI.  That should be worth looking into.

---

### Post by forger on 2008-10-30
for ogg/theora instead of avi, I use thoggen, doesn't get easier than that :)

Install it:
```
sudo apt-get install thoggen ubuntu-restricted-extras
```

And head to Applications > Sound & Video > Thoggen DVD Ripper

---

### Post by Circus-Killer on 2008-10-30
> **clancymf said:**
> I normally use k9copy and output the burn directly to a blank disc in the second drive.

Also, I heard that Handbrake is coming, or has come out with a GUI.  That should be worth looking into.

+1 for k9copy

definately my first and only choice.

---

### Post by fatphilthethird on 2008-10-30
> **clancymf said:**
> I normally use k9copy and output the burn directly to a blank disc in the second drive.

Also, I heard that Handbrake is coming, or has come out with a GUI.  That should be worth looking into.

I love handbrake, best thing I've found for ripping my DVDs so I can watch them on my PSP. 

Used this guide to install the main program and the gui:

[http://andrewalliance.wordpress.com/2008/08/29/handbrake-with-gui-ubuntu-linux-how-to/](http://andrewalliance.wordpress.com/2008/08/29/handbrake-with-gui-ubuntu-linux-how-to/)

---

### Post by ace007 on 2008-10-30
dvdrip is available in the repositories and is easy to use.  I have neved had a problem with it.  

Just create a project, select the chapter to rip, rip it, then select the output format you want and adjust the settings, transcode and then you're done.  I do recall that the divx setting was buggy though just use xvid. By default you can select which file format (container) to use (.avi,.mpg,.ogg) and then set what bitrate or size you want in order to set the quality and file size.
dvdrip is my suggestion.

GUI Guide and explanation of each setting.
[http://www.exit1.org/dvdrip/doc/gui.cipp](http://www.exit1.org/dvdrip/doc/gui.cipp)

---

