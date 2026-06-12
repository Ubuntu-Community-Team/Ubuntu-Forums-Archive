---
title: "New to Linux, MANY Questions (Simple)"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by ralphygarfield on 2008-05-24
Just installed Linux yesterday in a dual-boot environment with XP. So far the experience has been very positive, although I'm a little worried after reading some negative things about Linux. I'm hoping that I'll love Linux and that eventually (maybe in 2-3 months) I can ditch Windows for good, as I'm very annoyed with it. 

I got Ubunutu 8.04. I mainly use my computer for Internet browsing, watching videos (in all sorts of formats), burning DVDs, making movies, etc. I'm not a gamer at all, although there is one Windows 95 game I may want to get working. 

I am on an Acer Aspire 5630 with 1.5GB RAM. 

So I have many starters questions to ask:

- What do I have to do/install to get my built-in webcam working (I'm on a laptop)?

- What are some of the most important commands I should know? What do I need to put in the command prompt to make a recovery disk?

- Will making a a recovery disk made under a dual-boot system still work if I want to install Linux as my only OS?

- How do I change my appearances to make Linux more asthetically pleasing to the eye? I want gummy windows and etc.

- How do I view thumbnails when I'm choosing a file to send, or choosing a desktop background? It makes it much easier if you can see all the pictures at once.

- Why do my two desktop-workspaces just because of seemingly-random mouse movements?

- What are the settings I need to make to get my mic working for voice-recorder? My mic is built-in and it's not working on Linux.

- What do I need to use to send files to different places? Is there something like "Send To" or "Explorer"?

To anyone who can help: Thank you so much!

---

### Post by Inxsible on 2008-05-24
1) open a terminal and type in ```
lsusb
``` and post it back here. This will let us know what kind of camera you have.

2) You can learn the basic linux commands from [LinuxCommands]("http://www.linuxcommands.org")

3) For recovery, you can use partimage or the built-in "dd" command to create a bit by bit copy of your ubuntu installation.

4)Yes it will work even if you only have Linux as your only OS.

5) You can add themes/wallpapers etc from [Gnome Look]("http://www.gnome-look.org"). I am not sure what gummy windows are tho. You can also have eye candy by enabling desktop effects under System>>Preferences>>Appearances>>Visual Effects tab

6) nautilus should automatically show you thumbnails. At least I think it does.

7) I am not sure what you mean here

 8 ) You can always copy and paste. nautilus does have a send to bluetooth(if your comp has bluetooth). But I am not sure if there is another apps that do something like this.

---

### Post by daberger on 2008-05-24
to enable desktop effects, preferences, desktop effects i believe. im not at a linux station rite now

---

### Post by ralphygarfield on 2008-05-24
My Cam:

Bus 005 Device 002: ID 046d:09b0 Logitech, Inc.

---

### Post by ralphygarfield on 2008-05-24
.......

...

So you're telling me that there's no casual way to send files to and from places in Linux? 

....

---

### Post by Inxsible on 2008-05-24
> **ralphygarfield said:**
> .......

...

So you're telling me that there's no casual way to send files to and from places in Linux? 

....No. I am saying that I don't know if there is a way. But there could be.

also, you will not be able to copy anywhere but your home drive unless you use root privs. Remember Linux is not Windows. :)

---

### Post by ivze on 2008-05-24
- How do I view thumbnails when I'm choosing a file to send, or choosing a desktop background? It makes it much easier if you can see all the pictures at once.

"Explorer" is called Nautilus here. By default, it tries to show tumbnails for everything drawable, at least, for me. For folders, this can be changed: (menu)View->two bottom entries or Ctrl+1 and Ctrl+2.

- What are some of the most important commands I should know? What do I need to put in the command prompt to make a recovery disk?

To tell the truth, never heard about recovery disks for ubuntu. If something goes really wrong, you can boot from a Live CD, copy the whole /home/<yourname> folder and reinstall the whole from scratch.
You can also use backup-ers to be able to make a roll-back in case of some faults. Look for "Simple Backup" suite, it is installable via Add/Remove.

The most importank command :) . Well, don't execute "sudo rm -rf /", it nukes the whole system and thus may be used as a joke by some impolite users. 

- How do I change my appearances to make Linux more asthetically pleasing to the eye? I want gummy windows and etc.

See System->Parameters->Appearance. Some effects may not be available, if your graphic card don't have good drivers for Linux.

About Microphone and Camera:
If something don't work out-of-the-box, it's generally pain to make work, because if it had been easy, the Ubuntu team would have included it. You lspci output might be helpful, however: it reveals the chip names of your devices, some people from this forum might help you run the devices, if it's possible.

Have good luck!!

---

### Post by ralphygarfield on 2008-05-24
Thanks everyone, but I am very confused.

I need more detailed instructions as I am not good with computers and I am new to Linux. IE, if you tell me to get a program, I need directions about HOW and WHERE to DL it from, and how to use it.

I have no idea about how to use Nautilus or where to find it.

I still have no idea about how to transfer files to other places on the computer, or my external hard drive.

I hope someone can help... but as of right now, I'm doubting Linux. I mean, I have a webcam built in... how can Linux be good if you can't even have every part of your computer functioning?

---

### Post by m_ad on 2008-05-24
everything will function correctly after you configure it. don't expect everything to work 100% right after your install.

like someone above said, nautilus is your "windows explorer." when you click on places->home folder (or any other place) nautilus loads.

as for transfering files, I never thought it was a difficult task. can't you just copy/paste, or drag and drop?

---

### Post by crashcoredump on 2008-05-24
> I hope someone can help... but as of right now, I'm doubting Linux. I mean, I have a webcam built in... how can Linux be good if you can't even have every part of your computer functioning?


Hmmmmmmmmm,
Ok not be be a downer here man, but the idea of the forum is a support community where we all can trade information and assist one another. It seems like you need someone to convince you to use *nix or just do it for you. The very nature of Linux is that many things do require some configuration and there is great satisfaction in getting those things working. True, just about everything works but there will be some work you will need to do also.

Buy a book, look on the internet and then most importantly have an open mind when things take a little effort and thought to make operate the way you would like.


Good luck

---

### Post by Dan_Dranath999 on 2008-05-24
> **ralphygarfield said:**
> 
I still have no idea about how to transfer files to other places on the computer, or my external hard drive.

Just drag n'drop. (like in the Mac)

> **ralphygarfield said:**
> I hope someone can help... but as of right now, I'm doubting Linux. I mean, I have a webcam built in... how can Linux be good if you can't even have every part of your computer functioning?

That's the biggest problem of Linux, i think: Hardware support (but it's not their responsability). It's a problem that might be solved as Hardware developers realize that there are an important number of people using other Operative systems than the old Window$, and that if they don't WANT TO make drivers for their products, at least their source code should help the community build the drivers and software we need. 

Anyway, remember that Linux(the several flavors of Linux) is just another Operative system. NOT a Windows replacement or Clone.
(Have you used a Mac recently? it is not like windows at all, either, and some people get used to it, some people don't)

---

### Post by TJCIB on 2008-05-24
You bring up a lot of very good questions.  I have been using Linux since December and my recommendation to you is this:

Search for each question individually.  Most of your answers are out there already.

If you can't find an answer, start a thread with one specific question, you will have better luck getting it answered.

There are a number of tutorials and explanations.  If you don't know what Nautilus is, google and and find out.  I did that with nautilus, sudo, lots of commands, and about 30 programs and protocols....not to mention scripts.

In the 6 months I've been using Linux I have been able to set up a 15-computer network with file-sharing, printer-sharing, login sharing, caching of updates to prevent multiple downloads of the same thing, written several very useful scripts for automating actions....

All of this came with no knowledge of Linux, very little computer experience, and just some free time reading pages on the internet.  Its all out there.

Good luck.  Welcome to Linux, its fun.

---

### Post by TJCIB on 2008-05-24
With that said, here is my help...

1. I'm still not good at getting hardware to work.  Google searches usually treat me well, next step: search forums.

2. the best way to learn commands is to look up everything you do.  When someone says "sudo mount blah blah blah" I looked up what sudo means, then mount, then blah blah blah.  If you type in "man mount" into the terminal, it gives you the manual for the mount function.  That works for every command (pretty much).  Check out this site:
[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)

3. Recovery disk should work.  I've never had to use one.  I have gotten my system how I like it, then made my own CD so I can reinstall it exactly how it was if i mess it up.  Using disk images works well too.

4. gnome look and gnome art are good places to find themes and stuff. You can also got to System>Preference>Appearance and it has options for you.

5. I was wondering the Thumbnail thing myself, i'll get back to you on that, I know its possible, but I'm not on a Linux box right now.

6. You're statement doesn't make sense.  But the easiest way to switch between workspaces is ctrl+alt+arrow

7. Same response as for webcam.

8. You can send files one of two ways, using the file manager, called Nautilus.  Or using the terminal.  The file manager works just like windows in that you can drag and drop most files.  Some folders are protected to keep the system safe.  You will need to give yourself permission to move those files.

If you want to move/copy files in the terminal, your commands are "cp" and "mv" among others.  "mkdir" makes a folder, and a bunch others.  Check out some basic command tutorials and that will help.

Good luck, again.

---

### Post by friendofpugs on 2008-05-24
I think you'd do really well getting the book Ubuntu for non-geeks by Rickford Grant. It's a great introduction to Ubuntu Linux for someone who's clueless about what's what. I read it myself and heartily recommend it. That being said, with a little more work you can find answers to all your problems on the 'Net, but it takes longer.

---

### Post by ralphygarfield on 2008-05-24
I some how think that I would not do well in getting my answers from a book, but I might check it out. The book sounds interesting, but I came here for my answers since the Linux help button pointed me towards it. I hope you're not telling me that this isn't the place I can find support and that I have to go somewhere else...

And to what the other guy said: I'm not trying to get anybody to convince me of anything. But truth being said, if I can't get all of my hardware to function properly, I will not use Linux. 

When people say to me "you have to tweak a bunch of stuff to get it working," I don't know what that means. Using the terminal is not for me. I would find such commands hard to learn, and I wouldn't be able to memorize all of them. I'm not going to look up an answer on how to use the terminal every time I want to do something. The terminal is something I'll only use VERY, VERY rarely. I don't mind using it to get hardware set up, but I need guidance and direct instructions. 

I just really hope that I don't have to keep explaining myself and engage in debates... I came here for tech. 

And to elaborate on the workspace problem I mentioned: I am serious. Sometimes I'll just move my mouse, and the workspace (screen) will switch to the next one. At least, that's what it appears to me.

Please let me know about my Cam...

---

### Post by Aearenda on 2008-05-24
For me, research is vital to successful Linux use. With Windows, you decide where you want to go, and get on the train that takes you there. If you see somewhere nice along the way, that's tough - the train doesn't stop, and it can only go where there are tracks. With Linux, you drive your car, stop where you like, stray off the road, and you need to read the mapbook from time to time.

Here are my answers to your original questions, hopefully with helpful stuff added.

> - What do I have to do/install to get my built-in webcam working (I'm on a laptop)?
Bus 005 Device 002: ID 046d:09b0 Logitech, Inc
Your Logitech camera is likely already working - [http://www.fsf.org/resources/hw/cameras](http://www.fsf.org/resources/hw/cameras) and [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) suggest it is supported. However, you still need to run the right software to access it, such as "Ekiga Softphone" on the Applications->Internet menu. Sadly, this program will not get you working with MSN or Skype. To use Skype, you will need to add the software - see [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)


> - What are some of the most important commands I should know? What do I need to put in the command prompt to make a recovery disk?
There is no single way to make a recovery disk. The Linux ethos says 'you have choices' and the price you pay for this freedom is the need to do a bit of research. There are built in tools such as rsync that will copy your installation to a safe place on another partition or over the network. There is a free bootable CD called 'Clonezilla' that will make partition image copies for you, akin to Ghost for Windows. However, rsync and similar tools will make a perfectly good backup - it is much easier to use this kind of tool with Linux than with Windows, since there is no registry and all the files can be copied while in use (though you should stop things like database services if you use them). I suggest you search for sites that have how-to material for taking backups on Ubuntu, such as:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html](http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html)

[http://www.ubuntu-unleashed.com/2007/08/howto-clone-ubuntu-to-different.html](http://www.ubuntu-unleashed.com/2007/08/howto-clone-ubuntu-to-different.html) is about cloning your system.

As for lists of commands, I suggest [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/) as a starter.

> - Will making a a recovery disk made under a dual-boot system still work if I want to install Linux as my only OS?
Making a backup as I have suggested will still work. If you remove partitions, there may be minor adjustments to make after restoration. However, unlike with Windows, it is straightforward to do this. Don't rush in and do it yet.

> - How do I change my appearances to make Linux more asthetically pleasing to the eye? I want gummy windows and etc.
As ivze has already said. If you have an older machine, the 3D effects may not be possible (like Aero on Vista).

> - How do I view thumbnails when I'm choosing a file to send, or choosing a desktop background? It makes it much easier if you can see all the pictures at once.
Others have named 'nautilus' as the equivalent of Windows Explorer. They are right, but need to say: this is what starts if you go to the 'Places' menu and choose a location to view. 
Nautilus will preview photos and graphics - check the preferences under the 'edit' menu for when to do it. However, when selecting a file to add as a background, the file picker only previews the currently selected file, on the right of the file list. Some apps have a checkbox that turns previews on.

> - Why do my two desktop-workspaces just because of seemingly-random mouse movements?
Not sure quite what you are describing here. It may be that you do have 'visual effects' turned on, as this can do mouse desktop switching. My system does not have enough video memory for this to work, and Ubuntu doesn't switch desktop workspaces with the mouse for me unless the pointer is over the workspace pager, in which case the mouse wheel switches desktops. 
Try turning Visual Effects off in System->Preferences->Appearance to see if this is what is happening for you.
You can also reduce the number of desktop workspaces to 1 to avoid it, by right-clicking on the workspace pager and choosing 'preferences' - but then your system will be more like Windows :-(


> - What are the settings I need to make to get my mic working for voice-recorder? My mic is built-in and it's not working on Linux.
Try experimenting with the mixer settings for 'mic' and 'capture' - this is very dependent on your particular hardware. To get into the mixer settings, right-click on the volume-control (loudspeaker) icon on the panel, and choose 'Open Volume Control'.

> - What do I need to use to send files to different places? Is there something like "Send To" or "Explorer"?
There is a 'send to' menu in Nautilus, which offers to send by email on my system. However, it is often simpler to reverse your way of doing things - open the email program and add an attachment to a new email from there.
To copy from one place to another in the file system, including to flash drives and the like, you can use copy and paste inside Nautilus.
To copy to other network file servers, you use Nautilus again, using the 'Network Servers' shortcut on the left panel, or using 'Network' in the 'Go' menu. Then copy and move just like with Windows Explorer.


Please be persistent, there is a steep learning-curve at first with Linux, but it does get easier in time.

Other useful links:
[http://doc.ubuntu.com/ubuntu/switching/](http://doc.ubuntu.com/ubuntu/switching/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

---

### Post by Aearenda on 2008-05-24
By the way, if you are serious about > if I can't get all of my hardware to function properly, I will not use Linux then you should know that some hardware doesn't work in Linux because the hardware manufacturers don't want it to or don't care if it doesn't. Some of them simply refuse to tell the Linux developers how to make their hardware work, and the developers have to guess. Some of them change their hardware chipsets internally without changing the box. I'm amazed how well it all works, frankly!

---

### Post by ralphygarfield on 2008-05-24
My webcam DOES work with that Ekiga Softphone thing, but that seems to only be for phone calls and the like. 

I need to use my webcam for making videos of myself for presentations and etc.

What do I need to DL?

---

### Post by Aearenda on 2008-05-24
I have never made a movie using a webcam, so I'll leave it to others to respond. If it were a digital video camera, kino would be a good place to start - you can install it from "add/remove..." or Synaptic.

Note that it is relatively unusual to download a program from just anywhere onto Ubuntu. This is quite unlike Windows, and much safer. Most useful programs are available through "add/remove", with the added benefit that they are signed and virus-free. They come from a variety of trusted sources called "repositories", and of course they are free. You can start "Add/remove..." or Synaptic and search inside them for keywords.

EDIT: by the way, you may get more response from others if you start a new single-topic thread titled something like "How do I make a movie using a webcam?"

---

### Post by Raccoon1400 on 2008-05-24
> **ralphygarfield said:**
> 
I have no idea about how to use Nautilus or where to find it.


It is the default file manager in GNOME

It manages the desktop. The desktop would not show up if nautilus was not running. If you open a folder to browse files, you are using nautilus. If you open one of the locations in  the places menu, you are using nautilus.

---

### Post by furoido on 2008-05-24
Some advice from another newbie...don't ask questions on too many different topics in one post!! Break it down into several specific topics/posts - you'll get a lot more (and clearer/more useful) answers!

Also, don't be afraid to just experiment with your pc on your own! I am a complete pc-idiot like yourself and somehow I've managed to resolve many of my problems, even though I haven't a clue how! I know Linux is a bit scary for us newbies, but I'm finding its actually much easier than it initially looks once you start getting the hang of both how it works and how to use the forum/internet to get the relevant info. (and it is out there, never worry).

---

### Post by Raccoon1400 on 2008-05-24
> **furoido said:**
> Some advice from another newbie...don't ask questions on too many different topics in one post!! Break it down into several specific topics/posts - you'll get a lot more (and clearer/more useful) answers!

Also, don't be afraid to just experiment with your pc on your own! I am a complete pc-idiot like yourself and somehow I've managed to resolve many of my problems, even though I haven't a clue how! I know Linux is a bit scary for us newbies, but I'm finding its actually much easier than it initially looks once you start getting the hang of both how it works and how to use the forum/internet to get the relevant info. (and it is out there, never worry).

Yeah, when you get to know it, you can do much more with it than with windows.

---

### Post by ralphygarfield on 2008-05-24
I apologize. I just didn't want to spam the forum with a bunch of my posts, but maybe I'll have to.

Although, quite a few of my questions have been answered, so thanks for that.

---

### Post by saratchandra on 2008-05-25
Install "cheese" from synaptic package manager(found in system -> Administration) for using your webcam. Then go to Applications -> Graphics -> Cheese for taking vids and pics from your webcam.

---

### Post by daberger on 2008-05-25
ralphy dont give up on linux. if u think uve had it bad take a look at som of my old posts. i gaurantee that after u get the hand of it u will love it

---

