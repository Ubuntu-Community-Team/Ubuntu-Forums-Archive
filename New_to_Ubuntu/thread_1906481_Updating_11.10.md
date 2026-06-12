---
title: "Updating 11.10"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by NozeRyda on 2012-01-09
I have just started with Ubuntu 11.10

I've had issues during installation (on an older desktop) over the last week including after the first time I did a complete install, then updating the important security updates (there was 285) I started to receive 'crashes.'  With little time due to shift work and young family I decided to start all over again, complete re-install, so now Ubuntu is working (using it now) but I am fearful about updating and suffering time consuming crahes again.  From what little I've gathered of Ubuntu so far......

.....my questions in relation are;

1. rather than use Update Manager which just appears to only be able to do ALL updates at once, can I use another piece of software to breakdown the updates and install in smaller batches such as Synaptic package manager ?  My thinking is then if crashes commence I can 'wind back' with a smaller batch of updates to narrow down the problem to.

2. Where do I start with using Command Line ? to solve any problems, is there a link to a guide for this please? 

3. One problem I feel that caused a crash may have been when viewing Youtube, so maybe my Nvidia FX5500 graphics card?? The standard/recommended drivers are installed I noticed on installation, is updating recommended?  

_Many thanks_

---

### Post by lechien73 on 2012-01-09
Hi & welcome to the forums,

Update Manager does allow you to select just a few updates at a time, so you could do batches of updates if you wish.

There are a number of command line tutorials out there, one that gives the basics is here: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

If you specifically want troubleshooting tips, then the commands you would use depend on the nature of the problem :) For example, commands like "ps -ae" will give you a list of running processes, and "kill" followed by the process ID allows you to terminate them. This is useful for stopping troublesome processes.

"strace" is my new toy of choice for tracing what files a program opens, and what system calls it's making (it's deeply satisfying for my inner (and outer) geek ;) ).

"lsof" lists open files, and is excellent for seeing what processes are using what files, but read the man pages because the standard output is a bit long!

Finally, there are issues with the standard install of Flash, so you could try searching the forums here. There are many useful tips about how to remove and reinstall Flash with, or without, the repositories.

---

### Post by NozeRyda on 2012-01-09
Many thanks Matt.

That's great I'll read in to your suggestions further, I've got to rush to work any moment though.

Originally I did try Update Manager 'unchecking' all in the Update Manager, and just checking a few and hitting 'update,' however everything updated.  I've just looked at Update Manager again, and unchecked all, then just selected 3 items for update, but in the text under the list of items available for update it still tells me that every item is 'selected' instead of just 3?? Not sure if it's me or a glitch......

Thanks very much again.[U]

[/U]

---

### Post by lechien73 on 2012-01-09
Hmmm...I'll check that the next time there are updates available. 

When I had some repository issues last week, I unchecked the problem updates, and the rest of the updates proceeded normally. When I next went into Update Manager, just the previously unchecked updates were showing as still available.

I didn't check to see if Update Manager still said that all updates were selected, though - I'm not that observant ;)

---

### Post by grahammechanical on 2012-01-09
Hi and welcome

When we install Ubuntu we are asked if we want the system to be updated as part of the install process. This is why we are asked to confirm that the machine is connected to the Internet. If we allow the install process to update the system we get an updated operating system from the start. If we do not allow this we get a message about the need to update from the start.

Ubuntu 11.10 was released in October 2011 and for a few weeks there were frequent updates and security fixes. But by now the updates are less frequent. So, I would say that the 285 updates were to up date the slightly out of date image on the CD.

Another point, some update files are only a few bits in size. Others are a few kilo bytes in size. And some are some Mega bytes in size. The number of updates is not always so important as the size of the data to be downloaded.

A third point, some files or packages need other packages in order to work properly. If you select a certain package and allow it to be updated then the utility will also include all the other packages that are needed to work with it. This is why it seems that it will download more files than you selected. It is not necessarily downloading all 285 files, or what ever number there is.

A fourth point, some of these updates come from higher up than Ubuntu. It is called upstream. So, if the Linux developers update the kernel (the core component of the Linux OS) the Ubuntu must pass that update on to you. The same thing applies if the developers of a major program like Firefox release an updated version.

And finally (for me), if you go to System Settings in the power cog menu and load a utility called Software Sources, then under the Updates tab you can set how frequently Ubuntu checks for updates. You can even set it to never, if that is your choice.

Under the Ubuntu Software tab you can de-select the updating of certain types of software. Uncheck those four boxes and you will only get updates for security fixes.

I just had to smile when I re-read your first post just now. In one line you say that you are fearful of updating. And in another line you ask if you should update the video driver.

If Youtube caused the problem then it is not Updating that is causing the problem. You may need some special codecs for viewing content on Youtube. Open the Ubuntu Software Centre and search for codecs. If they are not already installed you might want to install

1) GStreamer ffmpeg video plug-in

2) GStreamer extra plug-ins

3) Ubuntu Restricted Extras

4) GStreamer plug-ins for aac, xvid, mpeg2, faad

Those might prevent youtube from crashing.

Regards.

---

### Post by NozeRyda on 2012-01-10
Ok both, many thanks for all that....I'll see what I can do when I've more time.  Great info. Glad I made you smile Graham. There was more than one installation attempt and more than one crash sadly, one straight after updating, and completely independently when Youtube was viewed.

  As hinted at, for me it's all about time at the moment.... Hopefully I'll get to read about terms that seem to be common with Ubuntu such as 'repositories' and I ask to try and save me that time, so thank you.  I will get around to reading a bit more on how each element is meant to work where possible.

Plenty to work on for now, very grateful, cheers.....

---

### Post by NozeRyda on 2012-01-12
found this quote elsewhere...

[COLOR="RoyalBlue"]*"There are two types of linux user, those who like a stable open source OS they can get their work done on, and those who like the cutting edge (buggy) releases and can get their hands dirty. Well ok, most are probably a blend of each"*[/COLOR]

   So I'm thinking of changing distro.  I do not have time to learn to get my hands dirty and I guess don't really wish to right now..... I just need to get my work done, listen to tunes, view and lightly edit some images and view some videos and the odd bit of Office type work, no time for buggy related tinkering..... it's stability I need, recommendations for which Distro appreciated please? Slackware? Pinguy? Mint? Debian? ...and which version is most stable? 

and/or do I go for an LTS version ?

cheers

---

### Post by NozeRyda on 2012-01-13
Uninstalled 11.10 due to another crash.
Issue now before I can install another Distro is getting recognition of my formatted hard drive,which now shows as unpartitioned but also unallocated/unrecognised and linux won't install with the infamous input/output error. So it's square one again need to overcome this before a new distro can go in. Gparted or Disk Utility say error each time I try and format drive to whichever standard now. It appears totally blank no used data on it, any resolution advice please?

---

### Post by NozeRyda on 2012-01-13
Still overly keen for help on the last...... ;-)

---

### Post by Rex Bouwense on 2012-01-13
You mentioned that the desk top is an older model.  What are the specs?  The reason why I ask is that it may not be able to properly run Ubuntu with Unity.  
You might consider a lighter OS, such as Lubuntu or Mint with LXDE, or even Bodi Linux.  
In any event, you cannot to do anything to the hard drive while it is mounted.  
If you have a bootable CD of the OS you are interested in and boot from it you can try the OS without actually installing to see if all of your hardware will work with it. You will also get an idea if you are going to like it.
Any OS that hasn't just been released will have a list of updates.  That just brings it up to date.  Don't be afraid of updates.

---

### Post by NozeRyda on 2012-01-13
Hey, many thanks.   It runs on a K8VMX motherboard, with AMD64 3200+ processor, Nvidia FX5500 card and 1gb RAM (ddr2 I think).

I've both run 11.10 from cd and installed (the latter is where I experienced crashes)... I've got Xubuntu, Lubuntu and Mint 9 on cd but with the hdd issue I can't install...input/output error on what scans show to be a healthy drive.

You said about 'mounted' hdd so how do I unmount (if that's what I need to do) if Gparted and Disk/drive Utility programs show an error each time I try to format please?

---

### Post by Rex Bouwense on 2012-01-13
I believe if you boot from one of the CDs the hard drive will not be mounted.  Also, if you install, the hard drive will be formatted as part of the installation process.  So unless you really want to format before you install...

---

### Post by NozeRyda on 2012-01-13
I do know what you mean I believe...... but the input/output error during installation, at point of choosing timezone, prevent insallation and from what i've understood so far it may be something to do with the installer thinking there is some data still on the drive somewhere which is why I was looking to do one clean format. Am a bit lost now I guess.

---

### Post by NozeRyda on 2012-01-13
Ohh, stand by.....a Distro now appears to have started to install correct, gone past time-zone selection, no error report there or after next option about keyboard..... crossing fingers!

---

### Post by NozeRyda on 2012-01-13
Hmmm seems to be hanging at about a third installed.... :-(

---

### Post by NozeRyda on 2012-01-13
Nope.  'Failed to mount at / on Ext4' sadly. Will have to keep trying....

---

### Post by NozeRyda on 2012-01-14
> **NozeRyda said:**
> I do know what you mean I believe...... but the input/output error during installation, at point of choosing timezone, prevent insallation and from what i've understood so far it may be something to do with the installer thinking there is some data still on the drive somewhere which is why I was looking to do one clean format. Am a bit lost now I guess.

I need to revisit this point,is this potential data presence a possibility and is there any guide to preparing hdd for fresh install please?

---

### Post by NozeRyda on 2012-01-15
How can I fix this please? Gparted won't perform any action on the drive...from live CD.

---

### Post by NozeRyda on 2012-01-16
Absolutely cannot resolve, as per last 2 posts. Using 4 different Distros from CD give different results on status of my HDD when using gparted or Disk Utility, one will show an empty unallocated disk, another will show 3 partitions (2 at 1gb each, other is remainder of free space)or the HDD is just not seen by gparted, neither will format now. Neither distro will install either via auto process option or via creating own partitions. Sometimes its the 'input/output' error others it just hangs at a third of the auto partition creating (for ext4) stage. There must be a way?

---

### Post by NozeRyda on 2012-01-18
Head ----> Wall.... Bangin it! Callin time I think.....

---

### Post by NozeRyda on 2012-01-19
Using 'partedmagic' on an 80gb hdd to format entire drive to ext4, it's getting towards 2hours of waiting for this to complete now. Anyone know whether it should have completed ages ago on a hdd that barely had data on anyway, please?

---

### Post by dFlyer on 2012-01-19
> **NozeRyda said:**
> Using 'partedmagic' on an 80gb hdd to format entire drive to ext4, it's getting towards 2hours of waiting for this to complete now. Anyone know whether it should have completed ages ago on a hdd that barely had data on anyway, please?

Way too long.

---

### Post by NozeRyda on 2012-01-19
Ahh ok, so it's got hung up for some reason.... Oh when will this work? Many thanks to you....

---

### Post by NozeRyda on 2012-01-19
The time is now..... FINALLY..... I have Lubuntu installed, after getting my hard drive to an unpartitioned, unallocated state and suddenly recalling something I read recently about some people with the 'input/output' error pulling cables out of their hdd's and replacing I've just done the same and suddenly Lubuntuhas run right through easy as pie!

many thanks to each who replied and helped stimulate my next move to try and resolve this.

Magic. ;-)

---

