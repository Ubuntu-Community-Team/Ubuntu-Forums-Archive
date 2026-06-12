---
title: "Ubuntu 7.10 crashed bad, I can't get it to load"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by discmaster on 2008-05-22
Ok, long story short. I wasn't using the pc for anything too labor intensive today, just playing music, surfing, whatnot. I was visiting my local car club websites, clicking on pics, and the pc froze, locked up completely. I could do nothing to get it to respond, so I had to press reset.


After that, the pc will not boot. See the following pic for all the info. A whole bunch of "bash' stuff I don't understand.

Help!

[[IMG]http://img394.imageshack.us/img394/2889/errorcf8.jpg[/IMG]](http://imageshack.us)

---

### Post by Sinkingships7 on 2008-05-22
type
```
fsck
```
into that spot after it says 'root@tr'.

press 'y' every time it asks you to. when it's done, type 
```
reboot
```

then everything should work fine.

---

### Post by tamoneya on 2008-05-22
```
fsck /dev/sda2
```

---

### Post by discmaster on 2008-05-22
I did all that & I am back to the desktop, everything seems okay.

My question is, what happened???

---

### Post by tamoneya on 2008-05-22
probably shut down improperly or something and caused some filesystem corruption.  Have you had a power outage or something recently.

---

### Post by Sinkingships7 on 2008-05-22
Going off of what tamoneya said, it's because your computer was improperly shut down when you had to restart it.

When everything seems to freeze, instead of restarting, try using the ctrl+alt+backspace combo. That kills the X environment (the GUI) and bring you back to the log on screen. Then you should just log in again and everything should be fine.

If that fails, then I have another trick up my sleeve for you.

Built into the Linux kernel is a little key combo that will save you when you get a really bad lockup like that.

Simply hold 

alt + printscreen + R + E + I + S + U + B

R gives back control of the keyboard
E sends all processes but init the term signal
I sends all processes but init the kill signal
S issues a sync
U mounts all filesystem to to prevent a fsck at reboot
B reboots the system

---

### Post by discmaster on 2008-05-22
> Going off of what tamoneya said, it's because your computer was improperly shut down when you had to restart it.

When everything seems to freeze, instead of restarting, try using the ctrl+alt+backspace combo. That kills the X environment (the GUI) and bring you back to the log on screen. Then you should just log in again and everything should be fine.

If that fails, then I have another trick up my sleeve for you.

Built into the Linux kernel is a little key combo that will save you when you get a really bad lockup like that.

Simply hold

alt + printscreen + R + E + I + S + U + B

R gives back control of the keyboard
S issues a sync
E sends all processes but init the term signal
I sends all processes but init the kill signal
U mounts all filesystem to to prevent a fsck at reboot
B reboots the systemVery nice! I will print that info out for future reference.

The pc has been a bit unstable for the last week or so. When I boot in the mornings, I sometimes would get a "file system" files were damaged or something like that.

It would then go thru a process in which it "fixed" things & then all was well. Don't know, is it time to reinstall the OS?

---

### Post by Sinkingships7 on 2008-05-22
> **discmaster said:**
> Very nice! I will print that info out for future reference.

The pc has been a bit unstable for the last week or so. When I boot in the mornings, I sometimes would get a "file system" files were damaged or something like that.

It would then go thru a process in which it "fixed" things & then all was well. Don't know, is it time to reinstall the OS?

Perhaps my blog will be of interest to you. I strongly recommend you check it out:

[www.christopherstechcorner.blogspot.com](www.christopherstechcorner.blogspot.com)

---

### Post by discmaster on 2008-05-23
I'm still having the situation where Ubuntu is giving me trouble loading. This morning when I booted the pc, it got to the "Ubuntu" screen with the progress bar that fills up & it kinda just stays their forever, at about a 1/2 filled progress bar.

I pressed the reset button, pc restarted as normal, took me to the username/password screen just fine. Should I just reinstall the OS, or I guess at this point, upgrade to the latest release.

I suppose that would cure my problems, yes?

---

### Post by Sunfist on 2008-05-23
To be honest it sounds more like a hardware issue than an Ubuntu issue, have you checked your HD lately?

---

### Post by Sinkingships7 on 2008-05-23
> **discmaster said:**
> I'm still having the situation where Ubuntu is giving me trouble loading. This morning when I booted the pc, it got to the "Ubuntu" screen with the progress bar that fills up & it kinda just stays their forever, at about a 1/2 filled progress bar.

I pressed the reset button, pc restarted as normal, took me to the username/password screen just fine. Should I just reinstall the OS, or I guess at this point, upgrade to the latest release.

I suppose that would cure my problems, yes?

As per my last post, if you do reinstall Ubuntu (which I do recommend), you should do a minimal install. I always had multiple problems with the standard install CD's. My blog will guide you through it, if you choose to take that route. It's quite easy, and you can always PM me if you get stuck.

---

### Post by discmaster on 2008-05-23
> To be honest it sounds more like a hardware issue than an Ubuntu issue, have you checked your HD lately?How do I check it? This is a fairly new sata drive, maybe 6 mo. old.
> As per my last post, if you do reinstall Ubuntu (which I do recommend), you should do a minimal install. I always had multiple problems with the standard install CD's. My blog will guide you through it, if you choose to take that route. It's quite easy, and you can always PM me if you get stuckI will probably go that route the weekend. As with everybody else, I do have a lot of data on here that I should backup, so I need to work on that first.

---

### Post by discmaster on 2008-05-23
Hey there, Sinkingships7,

I believe I may have major probs. of some kind here. My pc froze again, just now. I can't find the mouse pointer...I tried all of those key combos that you listed, & the pc will not respond at all.

What do you think?

---

### Post by Sinkingships7 on 2008-05-23
Be sure you're holding down the alt and printscreen keys at the same time. Keep pressing, then press the R key. You may have to wait a few seconds. Doing it multiple times won't hurt, either. Then press E, which should bring you to a black background with a blinking white cursor type thing.

Don't worry, It's safe to say that I'll be right here refreshing the page for hours on end. We'll get this sorted.

---

### Post by discmaster on 2008-05-23
Did that. I tell ya, it's locked up good, it will not respond. It is stuck on a webpage & nothing will budge it.

---

### Post by Sinkingships7 on 2008-05-23
Go ahead and hard reboot. Everything should be fine, even if you do have to go through the disk check again.

After that, get what you need backed up, and let's get your new install going. Then we can test for similar problems. If these problems keep occurring, and the alt+sysrq+reisub combo doesn't work, then you might be facing a bad hardware problem. But before we deem your hardware rotten, let's see what we can do.

---

### Post by discmaster on 2008-05-23
Rebooting now. I will work on the backups. Don't worry about checking this thread anymore tonight, as I must bow out to get some sleep for work tomorrow.

But please stay tuned over the next few days, I may need your assistance again! Bad thing is, I know how to troubleshoot in windows, but I don't know my way around Linux enough to fix it, especially troubleshooting for a hardware problem.

**EDIT** - I was just thinking; would a log file show us anything, give us a clue as to what is going on?

---

### Post by Damiox on 2008-05-23
> **discmaster said:**
> I'm still having the situation where Ubuntu is giving me trouble loading. This morning when I booted the pc, it got to the "Ubuntu" screen with the progress bar that fills up & it kinda just stays their forever, at about a 1/2 filled progress bar.

I pressed the reset button, pc restarted as normal, took me to the username/password screen just fine. Should I just reinstall the OS, or I guess at this point, upgrade to the latest release.

I suppose that would cure my problems, yes?

hey ...i had that same problem when installig ubuntu....i had 2 ext3 formated hard drives and one ntfs ...i had to unplug the ntfs and try again..and it worked....there is either something wrong with your hard drive/IDE ribbon cable(if you have to plug and unplug it alot it will break internally)...u need to run your live cd and check the extension type on your hard drive....these other guys will know how to do that better ...im mainly a hardware guy.....


oh i didnt realize it was sata...u need to be verbose when loading so u can see what its locking up on.....

---

### Post by discmaster on 2008-05-25
I am reinstalling/upgrade to 8.04, as per **Sinkingships7 blog**. I am at the partitioning section. Here is what I have;

SATA Drive 250 GB - 

#1 primary - 50 gb
#2 primary - 16 gb ext3  / (root)
#5 logical - 2.2 gb swap
#6 logical - 182 gb storage ext3 

Look good?

Also, I don't know what file system to select for #1. I am planning on using it simply for storage, just as #6. Should I select ext3 for #1 during the partitioning? If I do that, the option that it gives me is "ext3 journaling file system".

Is that right, because it doesn't say that under the #6 partition. #6 is full of data from the past year, so I am not touching that one.

Thanks in advance!
:popcorn:

---

### Post by Sinkingships7 on 2008-05-25
Yes, if #1 is going to be used for storage (and you don't plan on accessing it from a windows partition), then ext3 is the choice you want.

---

### Post by discmaster on 2008-05-25
lol, well I left it blank for now & forged on ahead with the install. I can fix that after it is completed, I guess. I am running "sudo aptitude install metacity" from your blog instructions right now, & I am at a point where I got a screen that says "Configuring uswsusp" informing me that the swap file is inactive?

At the end it says, "Continue without a valid swap space?" Yes/No. I assume I want to select "No" so that the swap file will be active? I want to do this part right - I am so close, I don't want to goof things up!

---

### Post by Sinkingships7 on 2008-05-25
Yes. Select 'NO'. Go back and check your swap partition. Remember that it needs to be set to be used as swap.

---

### Post by discmaster on 2008-05-25
> Yes. Select 'NO'. Go back and check your swap partition. Remember that it needs to be set to be used as swap.I remember from the previous partition screen, that it was set as swap. I am sure of it.

At any rate, while I was waiting for your reply, I guess my pc got tired of waiting, because the screen went blank & then continued with the install on its' own. I am now at the "sudo aptitude install gnome-terminal" step.

Should I continue with it at this point?

---

### Post by Sinkingships7 on 2008-05-25
Now I must go watch a movie with my fiance. I'm watching it on this computer, so I'll try to keep an eye open for another post from you. Just be sure to read and re-read my guide to make sure you have everything right.

EDIT: Also, I could be wrong, but I believe that your swap needs to be at the end of your partition table...

---

### Post by discmaster on 2008-05-26
Okay, here is where I am at; All is installed, I have run "sudo aptitude install ubuntu-desktop". I am now having a couple of issues. A couple of recurring errors I receive when trying to install any programs, weather thru synaptic or otherwise.

[[IMG]http://img55.imageshack.us/img55/7435/errorkx8.png[/IMG]](http://imageshack.us)

[[IMG]http://img402.imageshack.us/img402/9638/2nderroram7.png[/IMG]](http://imageshack.us)


[SIZE="2"]Also, when I boot, there are two entries for Ubuntu 8.04 that are the same. Actually, one has a "16" at the end, & one has a "17". What is up with that?[/SIZE]

[[IMG]http://img402.imageshack.us/img402/8255/bootscreenxh2.jpg[/IMG]](http://imageshack.us)

---

### Post by Sinkingships7 on 2008-05-26
I can't read the first two pictures, as they're too small. The third one indicates that you have two different versions of the linux kernel to boot from. Why you have both, I can't be sure. Unless you never formatted your other install. In any case, one kernel may work better for you than the other, so go ahead and try both out to see if your problems persist.

My recommendation is that you uninstall ubuntu-desktop. I'm not sure if this will work, but you can try with
```
sudo aptitude remove ubuntu-desktop
```
I know that using apt-get doesn't work, because ubuntu-desktop is a metapackage and not software itself, but I think that aptitude will uninstall everything for you. The reason I suggest this is because I never just installed the whole ubuntu-desktop, and I imagine that installing so many things at once is why you're having these issues.

The first thing you should have done is install the update-manager, update-notifier, and the drivers for your graphics card. It's my fault for not suggesting it, so I apologize. See if you can roll things back, and if it ends up being more trouble than it's worth, reinstall and start from the beginning.

No, Ubuntu is not known to be the most stable version of Linux. From what I've heard, a lot of the Red Hat systems are pretty stable. You may want to try Fedora if we can't get Ubuntu to work for you.

---

### Post by discmaster on 2008-05-26
I will uninstall the desktop first, see how that works out. If no good, I will boot into the other install & see if it works any better for me. If it does, how can I get rid of the other one? I guess that install should work better, as ubuntu desktop should not be on it yet, I guess.

I have no clue how two versions of the same thing can be on here, as I never worked with 8.04 until just now. :confused:

EDIT - That error is a "Postfix" error. When I just uninstalled desktop, I saw that error in the term. window as well.

---

### Post by discmaster on 2008-05-26
Uninstalled desktop; I can't tell any difference in the OS. Shouldn't a lot of the programs have been removed?

EDIT - Just installed a pgm. thru synaptic. Here is the error message that I always end up with. Any ideas?

[[IMG]http://img501.imageshack.us/img501/4950/postfixmessagetg4.png[/IMG]](http://imageshack.us)

---

### Post by Sinkingships7 on 2008-05-26
It seems like that would mean that something went wrong with the installation of the program... does the program work fine?

I'm thinking a reinstall of the OS.

---

### Post by discmaster on 2008-05-26
> I'm thinking a reinstall of the OS. Already ahead of you on that one! :D Yeah, I decided to  reinstall, re-partitioned w/swap at the end. (it was in the middle last time)

Back up & running, so far all looks good. Only one entry for the ubuntu OS (plus win xp on the other HD)

Thank you very much for your help, I sure appreciate it.

Regards, discmaster :)

---

### Post by Sinkingships7 on 2008-05-26
> **discmaster said:**
> Already ahead of you on that one! :D Yeah, I decided to  reinstall, re-partitioned w/swap at the end. (it was in the middle last time)

Back up & running, so far all looks good. Only one entry for the ubuntu OS (plus win xp on the other HD)

Thank you very much for your help, I sure appreciate it.

Regards, discmaster :)

Awesome! Plus, we both learned something. I only guessed that your swap partition had to be at the end, and now we know for sure! 

DO NOT hesitate to PM me here if you need ANY assistance. It's been nice working with you! :)

---

