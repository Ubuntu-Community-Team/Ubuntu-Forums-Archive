---
title: "Ubuntu How's Come: An Ubuntu Tutorial"
date: 2005-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by thegreedyturtle on 2005-04-25
I've just added my big ol' How's Come to the Ubuntu Wiki, and I'd really appreciate some feedback from people who are new out there. I should also mention that I've linked this post from the wiki post itself, so that people can discuss it here.

[http://www.ubuntulinux.org/wiki/UbuntuHowCome]("http://www.ubuntulinux.org/wiki/UbuntuHowCome")
Try and think: How did it help you, what parts were hard to understand and why? What could/should be added for a new user like yourself.

And old hats, I wouldn't mind some fact checking too!

Thank's, hope it helps y'all.

---

### Post by punkinside on 2005-04-28
Hey well It was perfect all the way to the install in java... it didnt work for me for some reason i couldnt get the java-package even though I added every repository there is to add...

---

### Post by DirtDawg on 2005-04-28
Okay I"m not done reading it (and wont be able to finish until tommorow due to some sweet-ass mid-terms), but I can tell you already that your bullet point, plain English style of explaining the filing system is a god-send. Every time I go looking for something I get confused. But no more! Thanks :smile:

---

### Post by mrbass on 2005-04-28
ok I read through it all.  I like how you didn't go into major detail over everything so it gave a nice overview at Ubuntu.  I liked your humor spread throughout the article..excellent writer.  

> 
But lets get back to the real potatoes here. You've seen the incredible diversity of Linux, and it's left you with that lingering question, "But which one is the best?" Well, I don't claim to know, but we can head over to  [http://distrowatch.com/](http://distrowatch.com/) and see what's on top at the moment. Hey, look at that, Ubuntu! (That's pronounced oo-BOON-to.)

I'm not going to get into why you should pick Ubuntu, that would take all day and not be too useful, but feel free to search around for comparisons. A good place to start would be [http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major), but if you do pick another distribution, you might not want to read the rest of this article. I won't say that you won't find some very useful information in it, but some of it might be different for your distro of choice, and could confuse you. 

Oh ye little humble one..hehe.

---

### Post by jobezone on 2005-04-28
Hi, in the tutorial you say when creating our user account:
" It will ask you for a full name for your new user. This information is almost totally unnecessary. " , but it is used by some applications.

 For example, gnome games store the score with the full name provided here, and there's no reason that e-mail ando other apps don't use the full name automatically (I haven't tried them, though).

Also, someone replied to your tutorial on the wiki. I haven't tried this, because the LiveCD I have is from Warty, but if this works it's very cool:

"Hi. In the "It's about the applications, Stupid!" section, about installing apps, you write: "Don't do it now silly, it won't work on the Live CD." A couple days ago, I had to re-partition my hd: I boot the Live CD and (being I a bit silly ;) installed gparted via synaptics and... wow, it worked! Go give it a try! ;)"

---

### Post by thegreedyturtle on 2005-04-29
Hey, It's Mr Bass!

Great script you got going on, simple and deadly! I usually make my own bash scripts to 'kickstart' my installations, logging everything I got installed in case I need to reinstall. ('course I'm not sure why, I think it's a habit from my XP days, where I would go into an OS install expecting to have to eventually reinstall it cuz it just got screwy...)

punkinside - I'm really not sure why you are having this problem, but I really am betting that you don't have your repositories set up right, or you have some kind of internet connection problem. If you aren't having issues finding the other packages, then it isn't a firewall or something like that,

The place I got that method from is [http://www.ubuntulinux.org/wiki/Java]("http://www.ubuntulinux.org/wiki/Java"), using method 3. The java-package is in the multiverse repository.

jobezone, I read that earlier on the comments, an' I've just now edited it a little to include that.

---

### Post by jobezone on 2005-04-30
[QUOTE=thegreedyturtle]
jobezone, I read that earlier on the comments, an' I've just now edited it a little to include that.[/QUOTE]
Nice you've add it, but it actually wasn't me who replied on the wiki, nor have I tried installing gparted with the LiveCD:), since I don't have a LiveCD of Hoary with me to try that.

It was Marco Massoli - > "not so silly, though ;) --Marco Massoli, Mon, 25 Apr 2005 23:24:29 +0100"

---

### Post by thegreedyturtle on 2005-04-30
Oop, my bad!

I don't think it was Marco either, probably someone who didn't leave a name... oh well. I've been wondering what is up with that error code...

---

### Post by GrimsbyJohn on 2005-05-04
[QUOTE=thegreedyturtle]I've just added my big ol' How's Come to the Ubuntu Wiki, and I'd really appreciate some feedback from people who are new out there. I should also mention that I've linked this post from the wiki post itself, so that people can discuss it here.
[url="http://www.ubuntulinux.org/wiki/FrontPage"]
http://www.ubuntulinux.org/wiki/FrontPage[/url]

Try and think: How did it help you, what parts were hard to understand and why? What could/should be added for a new user like yourself.

And old hats, I wouldn't mind some fact checking too!

Thank's, hope it helps y'all.[/QUOTE]

Your guide is great for me, a total linux novice.  However, I have got stuck.  Just before the section titled 'Working with programs:...' you have a paragraph that says 'Next, right click anywhere on the desktop and navigate to Scripts -> Open Scripts Folder'.  I expect I am doing something stupid, but when I right click on the desktop the menu doesn't refer to anything about scripts.  This somewhat snookers me for the rest of the tutorial, which I really want to complete.

Where am I going wrong?

By the way, I am a Windows user who is sick of windows.  I am trying to get to a stage where Ubuntu is a useful OS in my working environment and you guide is the best resource I have come across so far.  I provide more constructive fdeedback when I have completed the tutorial.

---

### Post by jobezone on 2005-05-04
Hi, I didn't write the Tutorial, but this is in fact true.
The menu wont appear until you copy a script to the hidden directory ~/.gnome2/nautilus-scripts (~ works the same as if you typed your home directory in place of it). 


*ups, corrected the directory and deleted last phrase*

---

### Post by GrimsbyJohn on 2005-05-04
[QUOTE=punkinside]Hey well It was perfect all the way to the install in java... it didnt work for me for some reason i couldnt get the java-package even though I added every repository there is to add...[/QUOTE]

I seem to have the same problem.  Did you resolve it?

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=thegreedyturtle]I
And old hats, I wouldn't mind some fact checking too!
[/QUOTE]

You did a really good job. Thanks for your contribution. This is classic:

> I am not afraid of the command line.  

One nit-pick though. You SHOULD NOT even have ANYTHING on there about the marillat repo. It breaks stuff, and everything needed out of it is in jdong's backport repo (such as codec) telling noobs to use that repo is REALLY asking for trouble and apt-get breakage.

---

### Post by thegreedyturtle on 2005-05-10
Allright, some changes:
I took out prelink, replacing it with a Gnome Baker installation, swapped out Mallirat for backports, and did a couple of little housecleaning things.

I'm pretty sure that I actually talked with John on #ubuntu and we got the nautilus scripts resolved. I updated that section to include the nautilus-scripts folder addition for people who don't have it.

'grats on the modingnation btw.

---

### Post by jobezone on 2005-05-11
Hi, I've made two different changes to your tutorial. First, was to take out my nickname in the part about installing applications on the LiveCD:)
The most important was the second, where I wrote that Stallman's purpose was to write an entire Operating System, even though only the various tools need in OS were developed by the time Linus started developing Linux. Please check the changes (in the button History I think on the top of the wiki) and change how you please . I changed it there, since you asked for it! (No, really, you asked for it at the end of the wiki:))

---

### Post by thegreedyturtle on 2005-05-17
Looks good to me - I added a mention of hurd in there as well.

 
I also deleted that subtopic, seeing as I never got any responses about it here... it's just not the place for it and I think it would confuse people.

---

### Post by dub on 2005-05-26
Linux noob here... I tried following the instructions for afraid.sh, and had problems. I copied and pasted from the web page, so shouldn't have introduced any typos.

1.Perms
 it looks like the script needs execute perms, or I get
[INDENT]
jeff@satellite:/bin$ ~/Desktop/afraid.sh
bash: /home/jeff/Desktop/afraid.sh: Permission denied[/INDENT]

So I used the GUI to change to 755. 

2. Now, I get:
[INDENT]
jeff@satellite:/bin$ ~/Desktop/afraid.sh
/bin/bash: (-): No such file or directory
[/INDENT]

Obviously, bin/bash is there.   Probably a simple glitch I don't have much experience to draw on, but it feels like some details weren't addressed.     :-? 

Thanks
Jeff

---

### Post by snoochems on 2005-08-07
Hi.  I'm a 100% total n00b to all things linux.

I've decided to try and get into it.  I'm having a hard time doing so.  I started reading this 'ubuntu how come' article, and really like it so far. 

I'm stuck though...
this part:[I]
    Tip: Remember back when you made afraid.sh? Hopefully you aren't afraid anymore, so let's rename that to Open as root, then right click the file and open it with a text editor, or just make a new file, doesn't really matter. Copy this into the new file and save it:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do 
        gnome-sudo "gnome-open $uri" &
done

      Next, right-click anywhere on the desktop and navigate to Scripts -> Open Scripts Folder. Copy your text file into this folder. Right click the desktop, and navigate Scripts -> Open as root... and... it's not there! [/I]


I can't find anything about scripts when right clicking on the desktop.  I've look everywhere.  

What am i doing wrong?

---

### Post by jobezone on 2005-08-07
> **snoochems]Hi.  I'm a 100% total n00b to all things linux.

I've decided to try and get into it.  I'm having a hard time doing so.  I started reading this 'ubuntu how come' article, and really like it so far. 

I'm stuck though...
this part:[I]
    Tip: Remember back when you made afraid.sh? Hopefully you aren't afraid anymore, so let's rename that to Open as root, then right click the file and open it with a text editor, or just make a new file, doesn't really matter. Copy this into the new file and save it:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS said:**
> 


I can't find anything about scripts when right clicking on the desktop.  I've look everywhere.  

What am i doing wrong?
 I think the directory only appears in the right click menu when you place something inside it. Just copy the text file  into 
**~/.gnome2/nautilus-scripts**

**~** is understood by bash (the program which you comunicate with in the terminal) as allways being the user's home directory, i.e., /home/username/.

---

### Post by varunus on 2005-08-07
Greedy Turtle,

This is awesome.  I think it should be stickied.

Something you might want to add, here's a guide on how to repartition your hard drive to use Ubuntu if you have windows installed.  It has pictures, something newbies will love.  (Camera pointed at screen, but still.   :) )
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

I can't take credit for these, but someone on the forums pointed me to them.  I managed to repartition myself when I installed Ubuntu, but this is great for newbies.

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=varunus]
Something you might want to add, here's a guide on how to repartition your hard drive to use Ubuntu if you have windows installed.  It has pictures, something newbies will love.  (Camera pointed at screen, but still.   :) )
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)
[/QUOTE]

I was going to ask to add this as well.

---

### Post by jc87 on 2005-09-08
By the way the backport repositories in your tutorial are out of date  (there are new ones).

And excellent tutorial , it hellped me a lot with ubuntu (especially sudo and su parts , i´m thinking in translating it for my language ).

Keep up the good work.

---

### Post by TwiceOver on 2005-09-12
I really enjoyed reading this tutorial however I have run into the same problem as the others with not being able to see the scripts menu when right-clicking.  I manually copied over the file from the desktop to the nautilus-scripts folder, unfortunately that didn't solve the problem.

Anyone know how to fix this?

---

### Post by vayu on 2005-09-14
Great article.  It really filled some holes in my understanding.  Thanks for spending the time!

---

### Post by tseliot on 2005-09-14
Great guide, I've got to study it. Thanks

---

### Post by JurB on 2005-09-18
[QUOTE=TwiceOver]I really enjoyed reading this tutorial however I have run into the same problem as the others with not being able to see the scripts menu when right-clicking.  I manually copied over the file from the desktop to the nautilus-scripts folder, unfortunately that didn't solve the problem.

Anyone know how to fix this?[/QUOTE]

Right-click the "open as root" file --> Properties
Permissions Tab --> add execute for owner
Close window

Right click on desktop..... Voila! \\:D/

---

### Post by yeswings on 2006-04-19
I just installed (oo boon to) on my old compaq It would not accept any windows OP I had tried everything. To my amazement (oo boon to) loaded with no problems at all. Now I just need to get some tutorials and get started. I would also appreciate a resource page with links to any help with dual boot and compatability programs for other OS's. Any other programs available would be nice.
Aloha 
[email]yeswings@excite.com[/email]

---

