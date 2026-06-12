---
title: "Problem with videos online"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ramunenke on 2008-08-19
There seems to be a problem when I try to watch any video online, even youtube videos. I've tried using both my firefox browser and my opera browser, turning off and on my adblock extension but no dice. I should also mention that this started yesterday after I installed the virtual box through the synaptic package manager and it started messing with my other applications. I have removed virtualbox and most of my applications have returned to normal. My browsers are the only apps that seem to be suffering now.

---

### Post by Sorivenul on 2008-08-19
First question is have you ever had video (I'm assuming flash) working in your browser?
Second, do you have either the nonfree flash plugin or gnash installed?

---

### Post by ramunenke on 2008-08-19
to answer your first question yes it has worked before. To answer your second (i think) I don't download updates from websites, I just use the update manager which was one of the programs negatively affected when I had virtualbox installed

---

### Post by Sorivenul on 2008-08-19
Okay.  If they were working before in your browser go into Firefox and type:
about:plugins

into the address bar.  If you see Flash/GNASH listed, I'm rather at a loss.  If both are listed, uninstalling one usually does the trick.  If neither is listed, pick one to install.

I've had issues with VirtualBox myself, however they've never affected anything other than VirtualBox itself.

---

### Post by ramunenke on 2008-08-19
shockwave flash is present and enabled but I can't find gnash.

---

### Post by ramunenke on 2008-08-19
Maybe it would help if I explained it better. When the page loads, the video loads like normal and it runs normally for 1-4 seconds and then the timer goes back to zero and the video load bar resets. Then the video shows its load emblem and gives up after a while. Could it be a virus?

---

### Post by Sorivenul on 2008-08-19
Virus is doubtful.  I actually have a similar issue when watching, that the video will play for a while, then stop and reset.  I'll try removing "Shockwave Flash" and installing GNASH.  It may be a bug in the proprietary Flash release.  GNASH is in the repos:
sudo apt-get install gnash

However, having both installed will give you more headaches.

---

### Post by le singe on 2008-08-19
> **ramunenke said:**
> Maybe it would help if I explained it better. When the page loads, the video loads like normal and it runs normally for 1-4 seconds and then the timer goes back to zero and the video load bar resets. Then the video shows its load emblem and gives up after a while. Could it be a virus?

Hey that sounds a bit like what was happening with me, but in my case the video would work fine if I hadn't played any other audio before.  If I had played an mp3 or something, videos on youtube would stop on me after two seconds.

Look at this post I made:
[http://ubuntuforums.org/showthread.php?t=882576](http://ubuntuforums.org/showthread.php?t=882576)

Does this problem describe any trouble you're having?  I followed parts A and B of the guide that Vivaldi linked ([http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)) and all my audio trouble ceased.

Maybe this will help.

---

### Post by ramunenke on 2008-08-19
this has always been a burning question of mine. I'm not much for programming, so where do I go to use the sudo commands

---

### Post by le singe on 2008-08-19
I just typed in all those commands, sudo and others, into the terminal, which is located under Applications>Accessories.

Be warned this How-To makes changes to your pulseaudio setup.  But in my case pulseaudio wasn't working correctly to begin with, so I was open to changing things around.  I think at the end of the guide he gives the commands for how to undo everything.

Anybody know, pulseaudio.... what is it, exactly?  Is it the default sound driver/set of libraries Ubuntu uses?

and ramunenke, are you having the problems I described in my post?

---

### Post by ramunenke on 2008-08-19
no, I closed amarok and then looked up a random video on youtube. I got one second of McBain and Homer Simpson (?) and then it reset. I think you and I have different issues.

---

