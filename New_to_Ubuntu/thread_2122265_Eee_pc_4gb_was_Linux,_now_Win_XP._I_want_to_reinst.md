---
title: "Eee pc 4gb was Linux, now Win XP. I want to reinstall Linux but no option to boot fro"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Markup 001 on 2013-03-04
Greetings to all on the forum!
My name is Mark, I have joined with you hoping to get some help or advice with a problem I have with an 
Asus eee pc 4gb
Original OS was Linux
Current OS Windows XP

My problem is this.
As I say the machine came with Linux installed from new and I have the original restore disc that came with it (The disc is entitled Linux Recovery DVD Rev.1.5 English version) at some stage a previous owner of the computer has installed Windows XP and there is no sign of the original Linux.

I downloaded the Blackberry desktop manager application so that my daughter could use her blackberry mobile as a modem for connecting to the internet. Unfortunately the BBerry manager would not install as it only works with the service pack 3 of windows XP, when I tried to update to this, I found that the eee pc did not have enough memory to accommodate the XP sp3 update. I went through the computer removing programs & deleting everything that I felt I safely could in order to free up some memory but it’s still not enough. I have tried hitting f9 at startup to see if I could access the recovery or restore but nothing happens – it feels as though I am running a stripped out version of Windows XP if such a thing exists.

I really can’t see how the eee pc 4gb machine could accommodate Windows XP as there is virtually nothing installed on the machine, no documents, images or music etc and there is still only something like 100MB of space on the hard drive.

So now I want to take the machine back to its factory state of having Linux as its OS. This is something I have been meaning to look at as an option on my own current machine for some time now so the timing at least is right.

I have purchased an external DVD drive that is working fine but when I try to run the Linux recovery disc the computer will not boot from it. I have used the option of f2 to access the BIOS to set the optical drive as my preferred one to boot from but there is no option to set it. I looked out for the Boot Booster in the BIOS too, but it is not there.

I am at a loss now as to how to proceed and wonder if anyone here can guide me in getting the machine to accept the DVD as bootable. I am not great with computers but I can easily understand any instructions I am given.
If you could take the time, and need me to take a picture of any stage of any process I have tried or anything like that, I will get onto it immediately.
Any guidance will be greatly appreciated...
Thanks,
Mark

---

### Post by coldraven on 2013-03-04
I have the eee pc 900 which has a 4GB system drive and  16GB user drive.
I put Xubuntu on it and it almost fills the 4GB. I needed to remove all the archived packages, there is an option in Synaptic that does this..
Settings>Preferences>Files 

As for the BIOS ASFAIR there are two windows that change the boot order and you need to look again.
You probably need to to switch off the Boot Boost while installing.
I updated the BIOS and the fan runs much quieter.

Edit: If you only have 4GB then maybe Puppy Linux would be better

---

### Post by Impavidus on 2013-03-04
Just found the [specs]("http://www.cnet.com/laptops/asus-eee-pc-4g/4507-3121_7-32466960.html") of that machine:
CPU: Intel Celeron M 353 / 630.0 MHz
RAM: 512MB
Storage: 4GB SSD

Unless is has been modified somehow you'll have a hard time installing Ubuntu on that machine, which was already low-spec when introduced in 2007. Win XP, being old by now, is a quite light system for today's standards. That memory is insufficient to run the full ubuntu (latest version at least, six years ago it would have worked), but Lubuntu may be OK. Also, that SSD memory is too small for Ubuntu. A bare-bone version of Linux (edit: indeed, Puppy may work) should just fit. You can also try installing on a USB drive.

The recovery cd you have may be just a recovery cd, not a complete installation cd. You'd have to download a new installation cd and burn it to a usb drive, then figure out how to boot from it. Besides, I've got no idea for what Linux version that recovery cd was, but it's probably outdated.

---

### Post by Markup 001 on 2013-03-04
Hi there coldraven

Thanks for the tip re Puppy Linux, I am not familiar with it but its name suggests a smaller system which is just what I am looking for as I only have 4gb. So I will go now to read up on it and see if there is a download I can access somewhere - Thank You!

With regards to my BIOS though, I do not have Boot Boost as an option and can see no way of switching it on or off. (on the boot tab of the BIOS there is only one option and it relates to the operating system being either "enabled" or "finished" Also I have no option, no matter where I look in the BIOS of changing the boot order so that my machine will boot directly from my dvd to wipe Windows XP from the machine and install Linux.

Can you tell me whether you know of a command prompt that I could use to have the machine boot from disc at startup or something like that that. 
I copied the files from the disc to a usb stick and tried booting from that but same thing again, it would not boot.

When you say you [COLOR=#000000]have the eee pc 900 which has a 4GB system drive and 16GB user drive, do you mean you have upgraded a standard 4gb machine to get the extra capacity? I have no knowledge of either the eee pc or of Linux so please excuse me if my questions appear simplistic or not very intelligent to you but would be very interested to learn that this is possible?

Thanks for getting back friend.[/COLOR]

---

### Post by Markup 001 on 2013-03-04
> **Impavidus said:**
> Just found the [specs]("http://www.cnet.com/laptops/asus-eee-pc-4g/4507-3121_7-32466960.html") of that machine:

Yes, thats the one. Thanks for taking the time to help me out Impavidus . Your comment regarding Puppy Linux is something that another member suggested as a possibility so I am going to read up on it and get it downloaded onto my USB. What would be a fair price, Is it expensive and are there places I should avoid when going for the download? Please excuse what may appear to be simplistic questions but today will be my first toe in the water regarding Linux and I am totally green - but very keen.

> **Impavidus said:**
> The recovery cd you have may be just a recovery cd, not a complete installation cd. You'd have to download a new installation cd and burn it to a usb drive, then figure out how to boot from it. Besides, I've got no idea for what Linux version that recovery cd was, but it's probably outdated.

Yes good point, I had no idea it could be as old as 2007 so it (the disc I have) is, in all likelihood, outdated. there are .glz, .bld, .dat, .gz, .bin .cfg, .c32 files contained on the disc inside a couple of folders (boot & isolinux) but there is no .exe file for me to start the process manually. I really need to gain the knowledge to be able to force the machine (possibly through a command prompt) to boot from the disc (or a usb stick as I have copied the disc files to one) at startup so that I can determine what disc it is and then if it is an installation disc, whether it can be brought up to date with updates before I consider the expense of Puppy Linux or something similar.

Thanks a lot again for taking the time friend.

---

### Post by Impavidus on 2013-03-04
For puppy try here: [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

Most linuces are free, so you won't have to spend a lot of money (just on the usb drive). And don't expect a lot of .exe files. They don't work on linux.

Creating a bootable usb drive is a bit more complicated than just copying a .iso file onto it.

---

### Post by Markup 001 on 2013-03-04
Again, your helpful input is really appreciated Impavidus!

My .exe boob shows that my knowledge of IT is strictly limited to Windows, but I am quite good with taking instruction, written or otherwise so am looking forward to getting my head around this. In fact I'm looking forward to getting to know Linux a great deal now as the little bit of reading I have done tonight leads me to believe it is a much more attractive proposition to Windows for many uses.

I have just cleaned off a fresh USB drive that I can use, so here goes with my visit to puppylinux.org.

Much appreciated friend!

---

### Post by Markup 001 on 2013-03-04
Hmmm, that was very helpful of the 3 mobile network. I use my iphone as a modem and pay for unlimited internet. However, some 80 MB and 8 minutes into a 108 MB download they decided it was taking too long and stopped it - how frustrating after I had put the night aside to try to get my head around a new set up.

So what unlimited is supposed to mean I am not sure. I will find a wired connection somewhere tomorrow, download again and let you know how I got on with my first steps into Linux. 

I feel really confident now that I have found your forum!

---

### Post by mlloyd on 2013-03-04
> **Impavidus said:**
> Just found the [specs]("http://www.cnet.com/laptops/asus-eee-pc-4g/4507-3121_7-32466960.html") of that machine:
CPU: Intel Celeron M 353 / 630.0 MHz
RAM: 512MB
Storage: 4GB SSD

Unless is has been modified somehow you'll have a hard time installing Ubuntu on that machine, which was already low-spec when introduced in 2007. Win XP, being old by now, is a quite light system for today's standards. That memory is insufficient to run the full ubuntu (latest version at least, six years ago it would have worked), but Lubuntu may be OK. Also, that SSD memory is too small for Ubuntu. A bare-bone version of Linux (edit: indeed, Puppy may work) should just fit. You can also try installing on a USB drive.

The recovery cd you have may be just a recovery cd, not a complete installation cd. You'd have to download a new installation cd and burn it to a usb drive, then figure out how to boot from it. Besides, I've got no idea for what Linux version that recovery cd was, but it's probably outdated.

I have a PC like that, and I unstalled Lubuntu (no Unity). The 4GB SSD was still too small so I put it on the larger SSD (which is upgraded to 32GB). It was installed from a USB flash drive.

BTW, the 4GB SSD currently has no partitions on it. I'm not sure what would happen if I tried to create any.

---

### Post by coldraven on 2013-03-05
You cannot just copy an install disc to a USB stick and make it bootable.
To do that you can use Unetbootin which will work on Mac, Linux or Windows.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Installing Puppy Linux might be a little daunting so for the moment just try to create a bootable USB drive and get it to boot up.
Then you will see how Puppy looks and we can assist you if you want to make it a permanent install.

---

### Post by s1wood on 2013-03-05
I use an eee PC 1000, my first linux computer, and it took me a long time to work out that there was a 16Gb  drive waiting to be used. I now have Lubuntu 12.04 on it with the /usr directory sharing the 16GB drive with the /home directory which seems to work pretty well. 

On mine, when you go into the BIOS and select boot, the 'select boot' option doesn't show up a USB or SD card unless you first go into the item below which allows you alter the order of HDDs - can't be more specific since I am using the machine at the moment!
If you put whatever you want to boot from a first hdd then it should show up in the 'select boot' list. In my experience I have to do this every time I want to boot from a card or USB, it reverts to the standard setting.

Some of that may apply to your machine -if not, sorry if I've confused you further!

Susan

---

### Post by JLeon85 on 2013-03-05
I have an ancient Aspire One with the same problem. I put a persistent USB of Knoppix on it, and it runs like new.

---

### Post by Markup 001 on 2013-03-05
> **coldraven said:**
> You cannot just copy an install disc to a USB stick and make it bootable.
To do that you can use Unetbootin which will work on Mac, Linux or Windows.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) 

Yes I understand this now coldraven, I am getting there slowly. I'm having quite a bit of trial and erring at the moment because the eee pc is not connected to the internet and I am using a laptop running windows vista for downloads etc. After reading your help for the first time I went to UNetbootin and downloaded the windows version but needed to download the Linux version. I will then practise on getting the machine to boot from the USB and move on from there.

> **coldraven said:**
>  Installing Puppy Linux might be a little daunting so for the moment just try to create a bootable USB drive and get it to boot up.
Then you will see how Puppy looks and we can assist you if you want to make it a permanent install.

I am certain that I will want to make it permanent and am really keen, even now as I type, to get cracking on learning how. But I appreciate your taking time out to point me in the right direction so much that I just wanted to check back with you to say thanks!

---

### Post by Markup 001 on 2013-03-05
Not confused at all, thank you Susan, you've just given me more to go at when the time comes around for me to be thinking about capacity. I've been staring pretty dumbly at the bios "as is", so am looking forward to finding out whether the additional options you can call on will apply in my case too.

Thank you,
Mark

---

### Post by Markup 001 on 2013-03-05
> **JLeon85 said:**
> I have an ancient Aspire One with the same problem. I put a persistent USB of Knoppix on it, and it runs like new.

Thanks jleon85, I have made a note somewhere to read up on Knoppix and look forward to learning more about it once I am installed with Linux of some version and up and running.

Cheers my friend.

---

### Post by 3rdalbum on 2013-03-05
Wait, if your computer currently runs Windows, then you need the Windows version of Unetbootin.

---

### Post by drawkcab on 2013-03-06
Ok, I'm an owner of a 900a and I've had 32948203950602934 versions of linux installed on it.

1.  Upgrade your drive.  4gb is extremely limiting.  You can do one of two things.  First, upgrade the ssd to a larger drive.  Mine is 16gb.  If that's prohibitively expensive these days you can run a Linux OS from a larger sd card and ignore the ssd.  Install from the USB live session to the sd card and set your eeepc to boot from the sd card.

2.  The other option is to run something small.  Puppy based on Ubuntu is one choice.  Another would be Lubuntu or Bodhi.  There are probably some smallish Debian-based distros too that I'm forgetting.

In summary, look to upgrade the memory capacity of your eeepc and/or run a lighter version of linux.

That should be functional machine for the indefinite future if you set it up right.

---

### Post by mastablasta on 2013-03-06
> **drawkcab said:**
> 2. The other option is to run something small. Puppy based on Ubuntu is one choice. Another would be Lubuntu or Bodhi. There are probably some smallish Debian-based distros too that I'm forgetting.
.

antiX for example: 

> The **[COLOR=#000000]installer[/COLOR]** needs minimum 2.2GB hard disk **[COLOR=#000000]size[/COLOR]**.

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)


might be easier to install than puppy.


Slitaz is also super mini linux worth to look at.

some list of distributions for older computers.
[http://distrowatch.com/search.php?ostype=All&category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?ostype=All&category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active)

---

### Post by Paqman on 2013-03-06
> **Markup 001 said:**
> 
As I say the machine came with Linux installed from new and I have the original restore disc that came with it

This is probably a distro called Xandros. It's not particularly good, which is the reason the early Eee PCs with Linux weren't that popular and it got swiftly replaced with Windows XP.

You'll definitely want to try something like Puppy, although there is a security caveat with Puppy in that it runs as root the whole time (much like Windows XP would make the first user an admin). There used to be special distros for the 4GB Eee PCs like [EasyPeasy]("http://www.geteasypeasy.com/") and [Eeebuntu]("http://www.auroraos.org/?page=eeebuntu").

However, the problem is that since it was only the first gen Eee's that were stuck with the 4GB SSD there's not been any demand for special <4GB distros for a while, and those ones are now somewhat out-of-date and unsupported. Recent builds of Ubuntu would probably struggle to get onto a 4GB drive. Technically you could use anything based on Ubuntu 10.04 (such as EasyPeasy 1.6) or Ubuntu Netbook Remix, but support for these ends this April.

---

### Post by Markup 001 on 2013-03-06
Thanks a million times over for all of your input friends, 3rdalbum, **drawkcab, **mastablasta & Paqman. I can't read enough of your comments and take every one of them as encouragement and inspiration!!
I had a look at antix and as you pointed out 2.2gb is an awful lot of what I have available at this present time so for now I am thinking Puppy Linux is the way to go.

Right...

I am now officially a Linux user - albeit a very slow one as the more I learn, the more I come to realise just how little I know, and need to know.

I managed to get the download and installation of Linux onto my eee pc, via a laptop with an internet connection, to work for me with guidance from people on the forum here. 
Using a command line, I have established that I am using this version of Linux...well I will type here what I see on the eee pc screen.


/home/user> uname -a
 
Linux asus-1470923030 2.6.21.4-eeepc #2 Mon Oct 1512.49.37 EDT 2007 1686 GNU/Linux
 
/home/user> cat /proc/version
Linux asus-1470923030 2.6.21.4-eeepc(root01386-desktop.build.ottawa.xandros.ca) (gcc version 4.1.2 20061115 (prerelease) (debian 4.1.1-21)) #2 MON OCT 15 12;49;37 EDT 2007

I have downloaded an .iso file of Puppy Linux (pup-431.iso) to my bootable USB and am considering overwriting (if that is the correct term) my existing version of Linux with it because no matter how many times I try, I cannot establish an internet connection on the eee pc, either wireless or wired.
I am totally familiar with the setting up of connections etc so I’m fairly certain that the error is not with me but with the machine, or more specifically the Linux version I have installed because it was fine when running windows XP.

Can anyone advise me on whether installing puppy linux at this stage is a little ambitious please and whether, after looking at my stats above, I am choosing the correct upgrade or not? I am very patient and don’t mind doing one or more installations in between if I will get the most suitable and stable installation in the end.
 
I have read up on the internet connection issue I am experiencing and find that it was a serious gripe with eee users a few years ago, so I am not overly concerned with that as I hope a proper upgrade will sort it out for me.
 
Thanks again for your generosity friends.

---

### Post by Markup 001 on 2013-03-06
> **s1wood said:**
> 

On mine, when you go into the BIOS and select boot, the 'select boot' option doesn't show up a USB or SD card unless you first go into the item below which allows you alter the order of HDDs...

Susan

As I was so unfamiliar with what a BIOS even was Susan, your post really helped me and since then I managed to enable boot from my USB and installed Linux - Thank you it really helped.

---

### Post by drawkcab on 2013-03-07
I would recommend the version of Puppy Linux based on Ubuntu 12.04:

[http://distrowatch.com/?newsid=07515](http://distrowatch.com/?newsid=07515)

My only issue with puppy is that it is pretty sparse.  Yeah, it has an extremely small footprint but I think most folks would be happier with, say, lubuntu...especially if you're a neophyte transitioning from winxp.

Don't hesitate to nuke your current linux install.  First, Xandros is awful and should never have been installed in the first place.  Almost any modern distro properly sized will work much better.  As you're learning about Linux it's good to be experimental.

I haven't hung out here in a long time but this forum used to be a go-to spot for eeepc users.  It's not as active as it used to be but some searching might help you learn:

[http://forum.eeeuser.com/index.php?/forum/4-eee-pc-linux/](http://forum.eeeuser.com/index.php?/forum/4-eee-pc-linux/)

---

### Post by s1wood on 2013-03-07
Get rid of the Xandros. I gave up on it when I found it wasn't updating  firefox automatically and I was being warned my version was obsolete.

I have Puppy installed on a 2GB SD card for occasional use and it works well.

Susan

---

### Post by Markup 001 on 2013-03-07
I have installed the puppy Linux and found it to be great fun just messing around for a couple of hours - so ,much more navigable than the xandros version I have permanently installed on my machine. I want to completely replace the xandros version I have on the maqchine with the puppy version I have on my USB so that when I log off and remove the usb then log back on again it will load the puppy and not the xandros as it is doing now. Do I have to be online to do this or can I do it from the machine as it is?

Thanks friends, I am getting there but I am making myself a little dizzy with the speed I am moving at ha...

---

