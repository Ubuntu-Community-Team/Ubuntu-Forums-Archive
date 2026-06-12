---
title: "[SOLVED] Regarding installed applications"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by newuserincalgary on 2008-11-20
Ok I am a novice linux user and this may be a dumb question but something is puzzling me.

One of my biggest complaints about Windows is the registry and program installation. What makes a Windows reinstall so awful is having to reinstall every single application again afterwards.

One of the reasons I thought that Linux would be better is the "everything is a file" concept. Yet is seems that applications are stored in a variety of locations... /bin, /lib, /usr, /etc....etc

So if you have to do a reinstall of the OS, as far as I can see all of these directories get wiped out along with all your installed applications leaving you in the same mess as Windows...

Is this true?  Am I missing something? Can Linux be set up so that the applications are separate from the OS. Can multiple OS's use the same applications? It appears the multiple OS's can share a single home directory if it is in a different partition from root. Can applications be handled the same way?

I am having a #%&#)*%$%$) of a time getting either Unbuntu 8.04 or 8.10 installed and working and before I go and try again, I was wondering if there might be a better way to set up my partitions to accomplish ease of reinstall and trying out other OS's

After my trouble with Ubuntu, I am thinking of trying Mephis. Any recommendations of this or other distributions that might be easier for a novice to get going on Linux with?

My basic feeling after all this is it shouldn't have to be this hard......

---

### Post by 0016 on 2008-11-20
Here is a walkthrough on setting up your /Home folder on a separate partition.  I hope this helps.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by newuserincalgary on 2008-11-20
Thanks, but I have figured out how to have a separate home directory. The question I was asking was how to have a separate "user applications" directory.

---

### Post by bobnutfield on 2008-11-20
As mentioned above, your config files are generally in your home directory.  You can create a file with your installed applications in your home directory with:

> dpkg --get-selections > installed-software

Then, after a reinstall with your previous home directory intact from having previously used a separate partition for your home directory, you COULD reinstall everything in one whack with:

> dpkg --set-selections < installed-software

> dselect

This will re-install all of your previous applications, but be aware that some of them may be obsolete or non-cooperative with a new version of Ubuntu.

---

### Post by snova on 2008-11-20
When you read "Everything is a file" I'm pretty sure they were talking about devices. It relates to how your hardware is represented to userspace, but I don't think the metaphor goes much beyond that.

It's not so much that applications are stored in a variety of places, but that different kinds of files are put in different places. Personally I agree more with the Windows and Mac way, of putting apps in their own directories, but this is how it is.

As for a "user applications" directory, I've never heard of such a thing. I don't see the point.

---

### Post by newuserincalgary on 2008-11-20
Ok then let me ask you this.

What do you do when you do a kernel update and it crashes your install and you have to reinstall the OS. Do you have to reinstall all of your applications too? That is what I am asking about.

Last year, I was working with a MAC as part of a hardware/firmware development and I had a whole bunch of applications installed and a large amount of source code that I was compiling for the target hardware. The source code and compilers were in the /usr directory and the applications were is some other directory that I don't recall now. Anyway, I had to upgrade the OS to the newest version as there was a bug in the 1394 driver of the installed OS. I put the new OS CD in and hit install, a few minutes later up it came with all of my applications intact.

This is how I thought Linux would work being another branch of Unix....maybe it does and I just don't know how....too bad MAC hardware is so expensive....

---

### Post by snova on 2008-11-20
No. You'd end up reinstalling the programs as well.

I don't know much about Mac, but it would seem that it separates your programs into two groups: system wide and user-specific. This is possible with Linux, but not through the package manager- a .deb, installed, will always put its files in one place. You can't install them locally.

It might be a useful feature, I suppose, but the only reason I can think of to do so would be if you didn't have adminstrator priviliges on the computer. Otherwise, it wouldn't be of great use.

Oh, and if you do a kernel update that crashes your computer, you just use an older kernel. They're all kept.

---

### Post by newuserincalgary on 2008-11-20
Someone else told me that....just go back and use an older kernel...you make it sound so easy....probably is if you know how...when grub comes up I only get one kernel choice and it won't boot.....please tell me how I revert to an older kernel

---

### Post by mikewhatever on 2008-11-20
> **newuserincalgary said:**
> Ok then let me ask you this.

What do you do when you do a kernel update and it crashes your install and you have to reinstall the OS. Do you have to reinstall all of your applications too? That is what I am asking about.


Why would one reinstall? When a kernel is upgraded, the older one is not deleted, so that if something is wrong with the new one, you can just reboot and use the working kernel.

---

### Post by newuserincalgary on 2008-11-20
Please tell me how.....??????

---

### Post by snova on 2008-11-20
> **newuserincalgary said:**
> Someone else told me that....just go back and use an older kernel...you make it sound so easy....probably is if you know how...when grub comes up I only get one kernel choice and it won't boot.....please tell me how I revert to an older kernel

If you only just installed, I don't know what to say. The "use an older kernel" suggestion is meant to be used for a destructive upgrade, but you only have one kernel...

Post whatever information you can in a new thread, unless you already have. I'm not much use here.

---

### Post by newuserincalgary on 2008-11-20
Here is what I have posted in another thread:

Kernal panic after installing 8.10 updates 

--------------------------------------------------------------------------------

Earlier today I ran the update manager on a working 8.10 install.

After rebooting, I got a kernal panic error message.

I have done a fair bit of online research into this problem, checking and retrying different boot menu configuration, also trying a manual grub boot...all to no avail.

The latest thread that seems to point to the problem is one that says the initrd image is not reading the ext3 file system properly and i need to change the boot partition to ext2

Is this true? Has anyone else had a working 8.10 install stop working in this fashion...please help...i am at the point of reinstalling everything....seems extreme to have to do this after a simple upgrade

I found another thread that shows how to update initrd but it doesn't work from the live CD....any ideas on how to do this?



So far, I have installed 8.10 from the live CD onto a brand new system, no other Linux OS's....as I said it ran until I ran update manager now it won't boot....I next tried installing 8.04 into another partition, thinking that it would be more stable....it did not install properly and won't run at all...

The only working kernel that I had was the 8.10 kernel that now boots into kernel panic....



Sorry, I see what you are saying...that you can't help me...ok well thanks anyway....i have posted several threads about my challenges....so far no one has offered to help

---

### Post by paultag on 2008-11-20
so, newuserincalgary.

Each folder may or may not reside on a separate partition. You have the option of separating nothing ( all of the OS on one partition ) to moving one out ( i.e. /home or /boot ) or all of your folders ( /usr, /home/. /bin, etc )

If you would like to "save" applications, save the binary paths, and any deps for it. Parting out just /usr would be OK, but you would loose /lib, /etc ( and so on )

You need to decide how much you really want to save. My suggestion is learn a bit more about linux before attempting to do something like that.

-----

also, r.e. your OS now:

I would suggest a wipe. It sounds pretty Fubar. Don't worry, I have reinstalled my OS too many times to count. It builds character



Cheers,
Tag

---

### Post by newuserincalgary on 2008-11-20
Ok, I am just about to do that.....

I am going to wipe out both root partitions and start over....

I am also going to set them up as ext2 as ext3 seems to be an issue for some....

The only question is, should I try and 8.04 running before installing 8.10 or just go for the 8.10 install again???

Recommendations please...

---

### Post by paultag on 2008-11-20
> **newuserincalgary said:**
> Ok, I am just about to do that.....

I am going to wipe out both root partitions and start over....

I am also going to set them up as ext2 as ext3 seems to be an issue for some....

The only question is, should I try and 8.04 running before installing 8.10 or just go for the 8.10 install again???

Recommendations please...

Try 8.10, and if it fails, please file the relevant bug reports. If its broken, then we should rightfully fix it.

Cheers,
Tag

---

### Post by Paqman on 2008-11-20
> **newuserincalgary said:**
> 
I am also going to set them up as ext2 as ext3 seems to be an issue for some....


Ext3 is fine, very stable.

In fact, the next version of Ubuntu due out in April 09 may upgrade us to ext4, which is now considered stable enough to use.

---

### Post by paultag on 2008-11-20
not that this is very relevant, but ext4 is actually a transient FS, btrfs will eventually replace that, if memory serves me.

Good luck OP,

Cheers,
Tag

---

### Post by egalvan on 2008-11-20
> **mikewhatever said:**
> Why would one reinstall? When a kernel is upgraded, the older one is not deleted, so that if something is wrong with the new one, you can just reboot and use the working kernel.

One would re-install when the current installation is messed up so bad that it is easier to erase and start over.

See post #13 for an example.

When one is "experimenting" with an OS, sometimes one does "bad things".

Using 'rm' badly, installing 'experimental' packages, playing with 'alein' packages...

you should get the picture.

My in-home file server is stable. I installed 8.04, and haven't touched it since (security up-dates ONLY)

My "play" machine has been wiped and re-done so many times I have lost count. I play and experiment with this machine, I install packages with abandon... it is very un-stable.

There IS a place for re-installs, especially for us newbies.

---

### Post by jimreynold2nd on 2008-11-20
OK I wanna say something....

1) Reinstalling Ubuntu = reinstall all softwares.
    Yea, too bad. But not as bad as with Windows, since Ubuntu has a wonderful package manager, all you need to do is 'sudo apt-get install what-ever-softwares-you-want' and then wait. Familiarize yourself with APT and synaptic, you'll feel Windoze's add/remove program is like a joke.

2) If your /home directory is intact, all the settings stored there are not lost (that includes startups, compiz settings, themes...). Assuming the software is well-written and put settings in there (most FOSS software does, dw).

3) About using old kernel, at the GrUB menu you can edit the menu item to select the kernel you want by pressing 'e' at the item then edit the kernel line. Or you can also drop to GrUB shell by pressing 'c' and from there you can boot virtually anything, even from your usb stick (you can't do this with ntlrd :cool:). I would recommend reading [this]("http://www.dedoimedo.com/computers/grub.html") for menu.lst editing or [this]("http://www.troubleshooters.com/linux/grub/grub.htm") to work with GrUB cli.
    Yea, I know it's a steep learning curve but once you master it, you'll never wanna use anything else (with an exception of GrUB2, maybe)

---

### Post by mikewhatever on 2008-11-20
> **newuserincalgary said:**
> Please tell me how.....??????

I usually just reboot, select the old kernel from Grub's menu and press enter to boot.

> **egalvan said:**
> One would re-install when the current installation is messed up so bad that it is easier to erase and start over.

See post #13 for an example.

When one is "experimenting" with an OS, sometimes one does "bad things".

Using 'rm' badly, installing 'experimental' packages, playing with 'alein' packages...

you should get the picture.

My in-home file server is stable. I installed 8.04, and haven't touched it since (security up-dates ONLY)

My "play" machine has been wiped and re-done so many times I have lost count. I play and experiment with this machine, I install packages with abandon... it is very un-stable.

There IS a place for re-installs, especially for us newbies.

Clever.:evil: You may want to re-read the part of the OP's post I replied to.

---

### Post by newuserincalgary on 2008-11-27
Thanks for all the help and suggestions. I have reinstalled and now have installed a second version of 8.10 where I can do experimental things while maintaining a stable install....it has been a steep learning curve but all is good now....

---

