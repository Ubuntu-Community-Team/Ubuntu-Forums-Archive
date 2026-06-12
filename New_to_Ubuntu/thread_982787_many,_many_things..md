---
title: "many, many things."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Adamant on 2008-11-15
OMG i installed linux a couple weeks ago, since xp bsod'd me like 4 times today i finally said ,<snip> you windows - made ubuntu my primary, uninstalled my windows and everything i wouldnt use.

im on ubuntu 8.4.

after making it the primary, i didnt like the look so i dl'd a new theme etc, now .. everything is odd to me

i have no understanding of 'terminal' - i consider it near a cmd of windows except i dont know all of the functions/commands - which is pretty much terrible...

so.
in firefox on the top/sides my text often gets cut in half by the borders.
also in firefox i have major text problems. some text comes up as characters that resemble something in chinese - in more than firefox too. i've installed all the updates i could from the system prompt.
I've got a logitech g15 + logitech mx revolution that i have no idea how to configure to this
I need to go to HOST to find my windows files because apparently during the installation of ubuntu it has a 15gb partition that i can only use, how can i expand this to my entire hd? (500gb)

Even though it says im on 1440x900 resolution i have viewing problems.( much bigger than usual )


eh... thats it for now lol, sorry if its a bit much...


SPECS: i only know the 'general' specs, is there a program that i can use for this? would be ... equivalent of "everest" for windows ...
"general specs" 3ghz dual core, 3gb ram, radeon x1650, dvdrw 500gb 3gb/s sata,,,

edit: even after this half of my text shows up as widgets.

---

### Post by Adamant on 2008-11-15
nobody...?

---

### Post by nhasian on 2008-11-15
Hello Adamant,

first take a breath and relax.  Linux is quite different from windows, but if you give it a chance i think you will like it :)

Everyone here is very helpful.  lets try to tackle your problems one at a time.  First i should say dont be scared of the command prompt (also known as a shell or terminal).  you will use it frequently.  You can start a terminal by going to Applications/Accessories/Terminal.  To see what kind of hardware is in your computer, you can type in the terminal:

```
lshw
```

its quite detailed, so dont worry if you dont understand everything.

As for your garbled text, what is your default language in Ubuntu?  Go to System/Administration/Language Support.  Mine is set to English (United States) for example.

Also in firefox in the menu bar, check View/Character Encoding.  Mine is set to Western ISO 8859-1.

For your disk space, yes you can expand your filesystem with gparted, but you must do it when booting from the liveCD.  Make sure you've backed up any files first.

---

### Post by Adamant on 2008-11-15
yep tried those to see correctly, to no avail .. i could post a screeny of what i'm seeing if you want -

also backing up 400gb is going to be a b*tch. 
and from the lshw -
32 bit, 3041mb ram, pentium D 3.0ghz, x1650 pro video card,500gb sata WD Caviar

---

### Post by swoody on 2008-11-15
Well, I'd like to say welcome to Ubuntu! And welcome to the forums! I'm sorry I can't really help you out with your problems, but I wanted to mention a couple things. This forum is a family-friendly place, and it's common for moderators to be upset by cursing, even if it is censored like that. Also, the Ubuntu forums are an amazing place, with LOTS of knowledge and knowledgable people, but you may have to wait longer than 15 mins to get a response :) so don't worry if it takes a little while for someone to answer it. If you'd like to get help in a quicker, real-time way, you can check out the Ubuntu IRC chat on FreeNode (#ubuntu). Again, I'm sorry I couldn't be more helpful, but welcome to the forums!! :D

---

### Post by Adamant on 2008-11-15
sorry about the... 'profanity' thanks for the advice... this could take a while.

---

### Post by nhasian on 2008-11-15
yes if you can take a screenshot that might help troubleshoot your problem.  You can just press the printscreen button to save an image.  pretty easy :)

also just out of curiosity, why did you ditch windows?  wanted to see if there are any common issues you had with the other OS as well...

---

### Post by nhasian on 2008-11-15
sorry for the double post but i just realized you had an ATI card.  perhaps getting the latest driver will resolve your issues?  take a look at:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by swoody on 2008-11-15
> **Adamant said:**
> sorry about the... 'profanity' thanks for the advice... this could take a while.

It's ok, I just figured I'd give you a heads-up before a moderator does :D And like the other guys said, just take a deep breath and don't worry too much about having bugs in your system. Just keep in mind this is Linux, not Windows, so you CAN actually solve all your problems, and get everything working but like you said - it might take a little time and a little work ;)

---

### Post by LordTakyon on 2008-11-15
Afraid I cannot help either, but stick with Ubuntu, I did.

It is very strange moving from Windows to Ubuntu at first, so much to learn LOL, but persevere with it and it will be worth it.

I had quite a few issues to fix, but doing this over the past fortnight has actually taught me a fair bit.  I am no whizz by any means, but I also have not booted Vista for around 10 days now.

The next release will become the only OS on this machine, I will be wiping the HDD before hand, and I have high expectations.

---

### Post by PierreDeKat on 2008-11-15
> **Adamant said:**
> I've got a logitech g15 + logitech mx revolution that i have no idea how to configure to this
Since you're on 8.04, you're in luck. You can [install Btnx]("http://ubuntuforums.org/showthread.php?t=455656") and configure your mouse to do just about anything.

Unfortunately, 8.10 breaks Btnx, and there's going to be precious little support for multibutton mice for awhile, unless the Ubuntu developers add support for configuring "unusual" input devices in Jaunty or until a few real whizzbang hackers start developing some usable fdi files that the rest of us can adapt.

> I need to go to HOST to find my windows files because apparently during the installation of ubuntu it has a 15gb partition that i can only use, how can i expand this to my entire hd? (500gb)
This sounds like a job for [gparted]("http://gparted.sourceforge.net/").

---

### Post by Skripka on 2008-11-15
Regarding the G15 keyboard-it is a great tool.


For getting most of the functionality out of it, there is this:
[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

Know THAT-in the Intrepid Ibex repos all the packages listed on that page are already made into debian packages for click to install (no messing around compiling things)....In Hardy Heron, MOST of them are already compliled (I remember that g15stats is not--BUT, you can grab it off the Ibex repos with your internet browser, and it should run fine in Hardy).

---

