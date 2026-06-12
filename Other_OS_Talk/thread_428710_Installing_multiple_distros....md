---
title: "Installing multiple distros..."
date: 2007-04-30
forum: Other OS Talk
---

### Post by ThinkBuntu on 2007-04-30
To date, every Linux distro I've used has been a clean install largely because I don't know another way. I have an 80GB HD in my laptop with Linux, and I'd like to be able to test other distros while keeping around my current distro and personal files. I'll be using the GRUB bootloader because I'm more familiar with it, and because Ubuntu uses it. The only distro I've used heavily with LILO is Zenwalk.

So, is there a guide out there for this? A specific way to partition my drive? Any help is appreciated...I'll be installing Ubuntu as my main (most likely) and try out other distros as they're released. I really enjoy Zenwalk, but I'm very busy right now, and need my laptop to "just work," so I may be on a ZW hiatus until the 4.6 final or 5.0 snapshot comes out.

---

### Post by ceelo on 2007-04-30
You could use only some of your free space to install Ubuntu, then install another OS in the remaining space. This would allow you to mount your Ubuntu partition from the other distro and access all your stuff. If you create an extended drive (I think Ubuntu does this by default) you can then break that up into several logical drives with a distro on each one. I'e attached a shot of how my system is currently partitioned. I have 2 distros installed on hda5 and 6. If I wanted to put another, I'd just resize one (most likely hda6 because it's larger) and install in the free space. I use the GParted LiveCD to do all my partitioning.

---

### Post by DJiNN on 2007-05-01
Whilst it's a great idea to have multiple partitions (I do it on ALL of my machines) you have to be careful , because often, if you have K/X/Ubuntu already installed & decide to play around with "Resizing" partitions, Ubuntu (Or GRUB) will complain by possibly NOT booting anymore...... which is not good. :)

Just a warning, because i have had it happen to me on many occassions. It's much better to make a few partitions ready for say 2 or 3 distros, of optimal size, and then leave them that size, whatever distros you start to try. Even then there's a good chance that one of the distros won't boot when you install another distro. 

Just FYI. :)

Above all..... have fun. 

DJiNN

---

### Post by adromidon on 2007-05-01
Will Ubuntu's Grub detect other distros with the Other Os option or what ever it is at boot

---

### Post by DJiNN on 2007-05-02
> **adromidon said:**
> Will Ubuntu's Grub detect other distros with the Other Os option or what ever it is at boot

It should detect pretty much everything without any extra options at boot etc.  :)

Always has for me anyway, whatever OS's i've had installed (& i've had plenty).

DJiNN

---

### Post by adromidon on 2007-05-02
what does ubuntu look for when searching for other distros? Do i need to install a boot loader in the boot partition of every distro partition to make it detect them?

So far the only one i have working is Ubuntu

---

### Post by igknighted on 2007-05-02
> **adromidon said:**
> what does ubuntu look for when searching for other distros? Do i need to install a boot loader in the boot partition of every distro partition to make it detect them?

So far the only one i have working is Ubuntu

Nope, You just need to enter all the information about where the kernel and initrd are for each distro into the /boot/grub/menu.lst file of whatever distro's grub you are using (any should work fine).  Here is mine for a reference:

```

default=2
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
# hiddenmenu

title         Fedora (2.6.21-1.3116.fc7)
root        (hd0,2)
kernel     /boot/vmlinuz-2.6.21-1.3116.fc7 ro root=LABEL=/ noapic rhgb quiet
initrd        /boot/initrd-2.6.21-1.3116.fc7.img

title      Fedora (2.6.20-1.3104.fc7)
root     (hd0,2)
kernel  /boot/vmlinuz-2.6.20-1.3104.fc7 ro root=LABEL=/ noapic rhgb quiet
initrd    /boot/initrd-2.6.20-1.3104.fc7.img

title SAM Linux
root            (hd0,1)
kernel          (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/sda2 rhgb noapic
initrd          (hd0,0)/boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro quiet splash noapic
initrd          (hd0,0)/boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro single
initrd          (hd0,0)/boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          (hd0,0)/boot/memtest86+.bin
quiet

```

Note a few things:  Fedora uses labels instead of UUID's commonly used by Ubuntu.  Also, I changed my UUIDs from Ubuntu to block devices (/dev/sdaX notation).  Also, note that Grub uses a zero index (meaning it starts counting HD's and partitions from zero, not one).  Finally, My SAM Linux entry looks weird because it is... I am booting a kernel off the Ubuntu partition due to some hardware issues with the Mandriva 2007 based kernel.

---

### Post by DJiNN on 2007-05-02
> **igknighted said:**
> 
```

title SAM Linux
root            (hd0,1)
kernel          (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/sda2 rhgb noapic
initrd          (hd0,0)/boot/initrd.img-2.6.20-15-generic
quiet

```

Hi igknighted, nice post..... :)

I notice that you're using SAM Linux....? What do you think of it? It's based on Mandriva isn't it?  I'd be very interested to hear your opinions & what you think are the pros & cons, if you have the time to jot them down?

[quote]Note a few things:  Fedora uses labels instead of UUID's commonly used by Ubuntu.  Also, I changed my UUIDs from Ubuntu to block devices (/dev/sdaX notation).  Also, note that Grub uses a zero index (meaning it starts counting HD's and partitions from zero, not one).  Finally, My SAM Linux entry looks weird because it is... I am booting a kernel off the Ubuntu partition due to some hardware issues with the Mandriva 2007 based kernel.

Interesting....... i didn't know that you could dispense with the UUID's and substitute the designated drive instead?  What are the UUID's for then? I never noticed them in Edgy, then when Feisty came along there they were, and (so it would seem anyway) causing a certain amount of trouble with my system..... i've never had so many "Drive" related problems..... :)

Anyway, thanks in advance for the "Heads up" & look forward to hearing from you.

Cheers.........

DJiNN

---

### Post by igknighted on 2007-05-02
> **DJiNN said:**
> [quote=igknighted;2579922]
```

title SAM Linux
root            (hd0,1)
kernel          (hd0,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/sda2 rhgb noapic
initrd          (hd0,0)/boot/initrd.img-2.6.20-15-generic
quiet

```

Hi igknighted, nice post..... :)

I notice that you're using SAM Linux....? What do you think of it? It's based on Mandriva isn't it?  I'd be very interested to hear your opinions & what you think are the pros & cons, if you have the time to jot them down?



Interesting....... i didn't know that you could dispense with the UUID's and substitute the designated drive instead?  What are the UUID's for then? I never noticed them in Edgy, then when Feisty came along there they were, and (so it would seem anyway) causing a certain amount of trouble with my system..... i've never had so many "Drive" related problems..... :)

Anyway, thanks in advance for the "Heads up" & look forward to hearing from you.

Cheers.........

DJiNN

I would be more than happy to, although I'll warn you I am a little biased since I am on the development team :)

SAM Linux is very much like an Xfce version of PCLInuxOS (Slightly more different than Xubuntu->Ubuntu).  It is very new-user friendly.  Comes with the ability to play some media (mp3 included, not DVD or WMA I think), although I am currently writing a gui script to install DVD and WMA playback ability to SAM, it should be available in the next release.  It uses all the Mandriva DrakConf tools, which can configure everything from Samba to Beryl easily.  Overall, the speed is fast.  Not quite what you are getting from Zenwalk I am sure, but still quite quick.  Oh, and while it is rpm based (it uses the PCLOS repo's mostly), it uses apt and synaptic, so it should be familiar.  Visit [www.sam.hipsurfer.com](www.sam.hipsurfer.com) for more info, or you might catch some people at #sam-linux on IRC (freenode), but its usually quiet there, just me or a couple others if we're around.

As for the UUIDs, it is your option.  The advantage UUIDs give is that if you have a removable drive (usb/firewire etc) it has a constant address in the fstab, while the block device could fluctuate.  If you like to change distro's and reformat drives, UUIDs will change, so you should use block devices.  Fedora uses labels which (if you use them properly) can have the advantages of both, but require you to set the label the same each time you format a drive.  This of course could be done in Ubuntu or any other distro if you like.

Hope this helps, PM me or drop by the sam linux forum if you want more info.

---

### Post by DJiNN on 2007-05-02
> **igknighted said:**
> [quote=DJiNN;2580637]

I would be more than happy to, although I'll warn you I am a little biased since I am on the development team :)

That's OK.  I don't mind some Bias at all.... 

> SAM Linux is very much like an Xfce version of PCLInuxOS (Slightly more different than Xubuntu->Ubuntu).  That's great, because my fave WM is XFCE.... that's part of the reason why i love Xubuntu so much & use it on 3 machines here   (The 64 bit version is now on my laptop & running really well.)

The only time i tried PCLOS was about 2 years ago, version 0.9 something or other, and although there were a few issues, it was (At the time) one of the only distros that i could install on my friends ACER laptop, that would detect the WiFi card and everything else straight off the bat! Ubuntu didn't have a chance at the time!  

The only thing i didn't like about PCLOS was KDE! :)

> It is very new-user friendly.  Comes with the ability to play some media (mp3 included, not DVD or WMA I think), although I am currently writing a gui script to install DVD and WMA playback ability to SAM, it should be available in the next release.  It uses all the Mandriva DrakConf tools, which can configure everything from Samba to Beryl easily.  I've heard (& seen) some good things about Mandriva. I've just downloaded the MCNLive CD (Have you seen it?) which is Mandriva based and it's pretty good. Quite fast, very stable & entirely useable.   Samba has always been a right pain in the neck to set up hasn't it? So anything that makes it newbie friendly is good by me. I would LOVE to get my dad into Linux instead of Windows. 

Well, all i can say is i HAVE to try SAM Linux then.  Which is why i'm downloading it right now. :D

> Overall, the speed is fast.  Not quite what you are getting from Zenwalk I am sure, but still quite quick.  Oh, and while it is rpm based (it uses the PCLOS repo's mostly), it uses apt and synaptic, so it should be familiar.Zenwalk is fast for sure, and quite a slick package, but it has it's share of faults or problems, and as they say.... "Speed isn't everything!" 

>  Visit [www.sam.hipsurfer.com]("http://www.sam.hipsurfer.com") for more info, or you might catch some people at #sam-linux on IRC (freenode), but its usually quiet there, just me or a couple others if we're around.OK, that'll be kool. I'll have a look at the CD once it's down & burned and head on over for a chat. The IRC name is ZenDJiNN if you happen to see me hanging around.   

The SAM website looks really great by the way, and in my favourite colour as well!! 

> As for the UUIDs, it is your option.  The advantage UUIDs give is that if you have a removable drive (usb/firewire etc) it has a constant address in the fstab, while the block device could fluctuate.  If you like to change distro's and reformat drives, UUIDs will change, so you should use block devices.  I am "Always" adding or changing distros (Apart from Xubuntu which is my main OS of choice for everyday Netstuff etc) and i'm often having problems (Especially after i have changed a distro for another) with my main OS not booting up after the change for instance.... which is really annoying because i'm having to install again & again!!   And it's not as if i'm changing the size of the partitions either, because i'm not..... i'm just taking one Distro OFF & then putting another ON to try it out.... & "BAM!"..... Ubuntu (Or Xubuntu) goes down and can't find the /home folder & i'm stuffed again! 

Do you think if i use the block devices as you say that this will help my problem? I'd like to think so, and i never had this problem a year ago when running breezy or edgy etc etc. Only since Feisty....... i think.  Well, recently anyway. 

> This of course could be done in Ubuntu or any other distro if you like.So, if i'm hearing you correctly, all i have to do is scrap the UUID's & go back to the old(ish) way of doing things, but using the new "sda" instead of the old "hda" kind of thing? (Or have i got it all wrong?) :D

> Hope this helps, PM me or drop by the sam linux forum if you want more info.I will pop into the SAM forums i think. Thanks for the help, it's much appreciated & i look forward to a little more chatting over at SAM's!  Oh, and BTW, i would really like to know a bit more about how you are running your Apache server (Edgy) that you're hosting your website on, and what it entails etc.

Soooo many questions.......!! :)

DJiNN

---

### Post by davin on 2007-05-03
GRUB can detect many operating system i used it with free bsd and suse on same hardidsk.

---

### Post by VCSkier on 2007-05-06
Is there an effective way to make use of a separate boot partition?  I'd like to be able to remove or reinstall either of my two installed distributions, and not effect the booting of the other.  Can I achieve that easily by using a separate boot partition?

Basically, I'm wondering how you all have your multi-distro hdd's partitioned.  Which setup is most effective?

---

### Post by igknighted on 2007-05-06
> **VCSkier said:**
> Is there an effective way to make use of a separate boot partition?  I'd like to be able to remove or reinstall either of my two installed distributions, and not effect the booting of the other.  Can I achieve that easily by using a separate boot partition?

Basically, I'm wondering how you all have your multi-distro hdd's partitioned.  Which setup is most effective?

I usually pick a distro and each time I do an install I choose not to install a bootloader.  Then I add the new distro to my existing bootloader to get everything working.  Some distro's *cough*Ubuntu*cough* don't like to let you not install a bootloader, so you have to install it and then fix it later.  A separate /boot is a great idea, if I was more foresighted during partitioning I probably would have done that.

---

### Post by phidia on 2007-05-06
Maybe someone already said this but you can also install grub to the root partition, for those other installs, and then use the chainloader +1 command in the grub installed to the mbr to pass off to the grub for the particular distro. I like that method because then I get the distros boot up screen.

---

### Post by VCSkier on 2007-05-08
I just stumbled across [Gag, the Graphical Boot Manager]("http://gag.sourceforge.net/") and it seems like the ideal solution.  If I understand it correctly, I just install each distribution like normal, install grub to the "SuperBlock of the root partition" ($ grub-install /dev/sdaX), and then install GAG to the MBR.  This way, the grub installation on each partition only needs to handle the distribution that it came with, and if I remove one of the distributions, I should still be able to boot to the other, right?

And when I install a distribution, worst case senario, it overwrites the MBR, and then I just have to reinstall GAG, no big deal, right?

Am I missing something?  Thanks?

---

### Post by igknighted on 2007-05-08
> **VCSkier said:**
> I just stumbled across [Gag, the Graphical Boot Manager]("http://gag.sourceforge.net/") and it seems like the ideal solution.  If I understand it correctly, I just install each distribution like normal, install grub to the "SuperBlock of the root partition" ($ grub-install /dev/sdaX), and then install GAG to the MBR.  This way, the grub installation on each partition only needs to handle the distribution that it came with, and if I remove one of the distributions, I should still be able to boot to the other, right?

And when I install a distribution, worst case senario, it overwrites the MBR, and then I just have to reinstall GAG, no big deal, right?

Am I missing something?  Thanks?

There is no need to use GAG for this, just use grub.  Point a chainloader entry at each partition and then install grubs for each distro as mentioned above.  I typically just add a new GRUB entry each time I change.  Another option would be to symlink the kernel you use for each to the same spot then no grub updates would be needed, just type "ln -s /boot/vmlinux-kernel-version /vmlinuz" and symlink the initrd as well, then point grub to /vmlinuz in each partition and make the symlink each time you change distros.

There are lots of options, just pick the one that suits you best.

---

