---
title: "Booting Blind. Can't see dual boot options: Xubuntu and Vista"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by LearnAlways on 2012-04-19
I just installed Xubuntu on this box. I set it up to dual-boot with my already-installed Vista. The problem is that I cannot see an option to choose my OS at startup. Xubuntu loads automatically every time. 

I think this is a display problem. For an unusual portion of time during startup my monitor says something like "signal out of range. configure it to display at 1920 x 1080 at 60Hz". It seems that my monitor cannot understand the boot manager program's display configuration. Presumably, the boot manager is waiting all this time for me to make a choice I cannot see, and then loads Xubuntu by default after that set period of time.

My monitor is an HP 2159m. I have almost no linux knowledge and I know absolutely nothing about the boot manager (including its name). I'd appreciate any help you folks would give me. Even if it's just telling me what the default keystrokes are to load each OS.

---

### Post by Mark Phelps on 2012-04-19
Suggest you download and install GRUB-Customizer in Ubuntu (link below).

That will give you the ability to change the screen resolution you see on boot (among other things)

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer")

---

### Post by dzponce11 on 2012-04-19
If you're sure that you can't access Windows Vista, try reinstalling it, then get Wubi(Windows Ubuntu Installer) and run Xubuntu alongside windows.

Wubi Link: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by LearnAlways on 2012-04-20
> **Mark Phelps said:**
> Suggest you download and install GRUB-Customizer in Ubuntu (link below).

That will give you the ability to change the screen resolution you see on boot (among other things)

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer")

Thank you for this, but I'm having issues.

I did my best to follow the steps in the link you provided but I failed to install the program. I added the repository (I think), but I cannot find the Grub Customizer program in the search.

Would you give me some advice about how to install it?

Also, I read some things about editing Grub's configuration file, but I'm hesitant to do that because I would not know what I'm doing. The configuration file says something like "if you change something run 'update grub' ". I have no idea what "update grub" is nor how to run it. Does "update grub" simply tell Grub that it's config file has been altered and that it should use the altered version? Do you have any ideas/suggestions as to using the grub config file to remedy my display issue?

dzponce11,

I'll read-up on that program. It might prove helpful if I choose to do a reinstall of windows (although I hope it won't come to that). Thanks man.

---

### Post by LearnAlways on 2012-04-20
Update:

I installed Grub Customizer using the command line. I followed the instructions at 

[http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/](http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/)

Using the program, I was able to configure Grub to display at 1280x1024 (I think that was what I chose), and this enabled me to view the Grub boot menu and see all of my options. Thanks, Mark Phelps, for telling me about the Grub Customizer. My problem is solved.

I would still like to know why I couldn't get it to show up in the Ubuntu Software Center. Hopefully I didn't enter the wrong information for the repository and get something malicious - probably a ridiculous concern, but I have no idea how this stuff works.

And I am still curious about how to properly edit Grub's configuration file. Some of the instructional material I've seen may be a bit above my head at this time.  So if anyone would care to educate me on these two matters, that'd be cool. As my name implies, I like to learn.

In any case, I am happy that my boot problem is solved. Thanks again Mark.

---

### Post by Bartender on 2012-04-20
Do you have access to a plain old CRT monitor?  Hook that up and you should be able to see the info that's not being displayed...

---

### Post by oldfred on 2012-04-20
Before grub customizer drs305 posted many guides on editing and understanding grub2. Look in his signature if you want to learn the 'hard' way to do things. After you do it, it really is not so hard, but requires a few command line edits.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by LearnAlways on 2012-05-02
Thank you both for your responses and I am sorry for this delay. I figured no one else was going to reply so I didn't check the thread for a while. I just remembered another thread I started and then I figured that maybe I should check this one too. 

Bartender,

My problem is solved, but your CRT idea seems pretty good. Maybe it will help someone else with problems like this.

oldfred,

I am going to check those links out and maybe I'll learn a thing or two. Also, per the suggestion in your signature, I am going to mark this thread as solved.

Again, thanks to both of you for the information.

---

