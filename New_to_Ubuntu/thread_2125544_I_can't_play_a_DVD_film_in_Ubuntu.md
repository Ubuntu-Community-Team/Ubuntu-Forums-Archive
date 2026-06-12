---
title: "I can't play a DVD film in Ubuntu"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by viriatovigo on 2013-03-14
Good morning/afternoon/evening to every one.

Still I am an absolute beginner thought I did manage by now to use Ubuntu "*nearly*" as fluently as Windows (I have nothing anymore that smells Microsoft in my PC, enough was enough) but still remain some..."gaps"...

When I input a DVD film into the drive nothing happens. I do open VLC or Movie Player I can't see in the menu any command to play the DVD in the drive.

Actually, I have not a clue about how to see at once all the drives in my computer (CD-rom drive, C:/, etc.).

How can I play the DVD in the drive with Ubuntu and how to see all the details of my PC with Ubuntu?

With thanks in advance for your kindess and apologizing for my stupidity,

viriatovigo
(Tino)

---

### Post by SuperFreak on 2013-03-14
You may have to enable Restricted Extras in Software Center (see screenshot). You should if you have these be able to open VLC or Totem and watch a DVD. It is possible to set one of these as the default player and it will open automatically when you put a DVD in (I think it is in Preferred Software (not sure as I use Cinnamon DE -in mine it is in Menu/Preferences/Details/Default Applications))

---

### Post by Kopkins on 2013-03-14
If the above post doesn't work, try running this:```
sudo /usr/share/doc/libdvdread4/install-css.sh
```****Kopkins

---

### Post by JRV on 2013-03-14
ubuntu-restricted-extras provides a lot of codecs for playing many audio/video files.
It is something you will want, but it does not play encrypted DVDs.

You need libdvdcss2 and w64codecs/w32codecs.

This link explains how to install them:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by SuperFreak on 2013-03-14
I believe the Restricted Extras does in fact provide for playing back DVDs (see attachment)


edit: JVR you are right as  libdvdcss2 is not installed with restricted extras. But I don't seem to have it on my computer and am able to watch DVDs

---

### Post by viriatovigo on 2013-03-14
Ta SuperFreak, Kopkins and JRV

What JRV said was right, installing Restricted Extras doesn't play the DVD.

I did all what all of you said and the solo improvement after I did what JRV said, is that now the CD drive flashes for some time but still the CD doesn't play at all, not with VCL, not with Movie Player.

And still remains that I don't know how to see the drives in my PC as I used to do in Windows, so I can not explore the contents of the CD.

---

### Post by viriatovigo on 2013-03-14
Right... Patience is not one of my virtues... So I did resolve this issue in my way.

I did borrow a laptop with Windows from a neighbour, I did put the DVD on the laptop (that did play straightaway), I did plug a USB flash memory stick, I did copy the DVD files in the USB stick, I did put the stick in my PC and copy the DVD files into Home>Videos>The Interpreter, I did open VLC and chose to play from the file and did play.

End of the problem. I knew that Linux is not customer friendly and never was intended to, but this is just riciculous...

Anyway, problem resolved.

All the best to everyone.

viriatovigo

---

### Post by SuperFreak on 2013-03-14
I have had no problems playing DVDs or CDs in Ubuntu. was this a home made disc?

---

### Post by Kopkins on 2013-03-14
In nautilus, the defualt file manager, you should be able to see the disk listed near the top right under the devices. You can open nautilus by pressing the windows key, typing files, then pressing enter.

First, lets find out what drive your disk is in.
Enter the following in the terminal, but make sure you have the disk inserted.
```
df
```

The output on my computer has several lines like this
```

/dev/sr0          509952   509952         0 100% /media/ARCH_201302


```
That line is my dvd drive. /dev/sr0 is my drive.

Like mine, you should have the 100% used and it will most likely be in /media/NAMEofDISK

If you can't figure out what disk drive is yours post the info back here.

Now try opening the disk from VLC. Open VLC, then go to the menu > media > open disk...
Or press ctrl + D while in vlc.

There will be a window that opens. There will also be a box for Disc device. Try putting your drive in there. So for me it would be /dev/sr0. Or try choosing from the dropdown.

Good luck,

Kopkins

---

### Post by Kopkins on 2013-03-14
> **viriatovigo said:**
> Right... Patience is not one of my virtues... So I did resolve this issue in my way.

I did borrow a laptop with Windows from a neighbour, I did put the DVD on the laptop (that did play straightaway), I did plug a USB flash memory stick, I did copy the DVD files in the USB stick, I did put the stick in my PC and copy the DVD files into Home>Videos>The Interpreter, I did open VLC and chose to play from the file and did play.

End of the problem. I knew that Linux is not customer friendly and never was intended to, but this is just riciculous...

Anyway, problem resolved.

All the best to everyone.

viriatovigo

It's not that linux as that much less user friendly than windows. If you ever install windows onto a computer that has no operating system you'll find it's much easier to install linux and make it work. When windows comes preconfigured on a computer everthing is already set to work so it seems a lot easier. In linux or Ubuntu here, you have to install the software that lets you play dvd's. Once you have that you have to tell the program how to find the dvd. Like I described above. 

Best of luck with Ubuntu and Linux.

Kopkins

---

### Post by coolman98 on 2013-03-14
right click on one of the video files on the dvd and click open with then vlc media player

---

### Post by viriatovigo on 2013-03-14
[SIZE=3][FONT=arial]Ta SuperFreack

Not, is not a home made. Is from a videoshop from Eire. The DVD label seems to me authentic with the censorship stamp on it in gaelich "Oifig scrúdóir na scannán" what in gaelich means "Film censor'soffice".[/FONT][/SIZE]

---

### Post by viriatovigo on 2013-03-14
Ta coolman98

As I said, I don't know how to explore the CD drive like in Windows.

---

### Post by viriatovigo on 2013-03-14
Ta Kopkins.

This what it says:

  	 	 	 	   tino@user-fdf42c16fb:~$ df 
 Filesystem        1K-blocks        	Used       		Available    	Use%    		Mounted on 

 /dev/sda1            75902048   	22538280  	49508104      	32%     		/ 

 udev                          499824             	4            499820           	1%      		/dev 

 tmpfs                       202844           	808            		202036            	1%     		/run 

 none                            5120         0                  		5120               		0%     		/run/lock 

 none             507108         	388             		506720           	1%     		/run/shm

---

### Post by viriatovigo on 2013-03-14
Sorry... Also I did  menu > media > open disk... and chose /dev/sda1 as per response on the terminal and says that can  not be opened    ???????????

---

### Post by 3rdalbum on 2013-03-14
You need to install libdvdcss2. Several people have told you how - please re-read the replies carefully. Someone gave you one command to do it. Restricted Extras is not enough.

You can't play DVDs by opening the individual files.

---

### Post by Kopkins on 2013-03-14
> **viriatovigo said:**
> Sorry... Also I did  menu > media > open disk... and chose /dev/sda1 as per response on the terminal and says that can  not be opened    ???????????

Was your DVD in the drive when you tried? The drive won't come up unless there is a dvd in it. /dev/sda is your hard drive. /dev/sda1 is partition on your drive.

Try this, go to System Settings > Details > Default Applications and change video to VLC. Then go to Details > Removable media and change DVD video to VLC. 

Then run this in terminal ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then take your DVD out and put it back, VLC should open and play it.

Kopkins

---

### Post by viriatovigo on 2013-03-15
Thank you 3rdalbum for your wise advise.

Following your advise of "please re-read carefully" you will notice from my responses to JRV and Kopkins that following the advise of JRV I did install libdvdcss2 and following the advise of Kopkins I did install libdvdread4 **with not avail whatsoever**.

Perhaps my English is not good and I gave the wrong impression in my answers. If you wish I can write them in the other 6 European languages that I do speak + catala, euzkera and gaelich.

Kind regards.

Tino

---

### Post by MoebusNet on 2013-03-15
Have a look at:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It has sorted all of my audio, video and DVD issues for years.

---

### Post by viriatovigo on 2013-03-15
Ta Kopkins.

Yes, the DVD where in the drive. Thank you for confirm to me that sda is my HD and sda1 is the partition. I wasn't sure about that but I am now, thank you. But as you can see it doesn't identify the CD drive at all... ?????

Because I hate Micrsoft, last night I did uninstall anything that smell Microsoft from my laptop too and I did install AppleMac 10.8  Mountain Lion. When I put any DVD in Apple they play straightaway, so the problem is only with Linux. By the way, even the audio CDs doesn't play straightaway in Linux, I need to follow a lot instructions from the media players to get it playing. Again that doesn't happen in Apple and didn't happen in Windows.

I must be doing somethig wrong but I don't know what and it is driving me crazy. Or I find what I am doing wrong or I change my name to Sue...

Afer luch I'll try your last tip and I'll let you know.

See you later.

Tino

---

### Post by Kopkins on 2013-03-15
post back the output of ```
dmesg | grep DVD
```

Kopkins

---

### Post by viriatovigo on 2013-03-15
Kopkins!

It doesn't play yet but now somethig new do happens after I did what you told me.

When I put in the drive any DVD, opens VLC but it doens' play, just shows a black screen and in the top left says the name of the film and - VLC.

Kind regards.

Tino

---

### Post by viriatovigo on 2013-03-15
tino@user-fdf42c16fb:~$ dmesg | grep DVD
[    1.364500] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB02, max UDMA/66
[    1.381847] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB02 PQ: 0 ANSI: 5

---

### Post by viriatovigo on 2013-03-15
Ta MoebustNet

I am now dealing with the advise from Kopkins; after that I'll perform what is in your link and I'll be back to you with the results.

Kind regards.

Tino

---

### Post by Kopkins on 2013-03-15
> **viriatovigo said:**
> Kopkins!

It doesn't play yet but now somethig new do happens after I did what you told me.

When I put in the drive any DVD, opens VLC but it doens' play, just shows a black screen and in the top left says the name of the film and - VLC.

Kind regards.

Tino

You are so close! I was at that point once a year ago, I just can't remember what I did to get it working.

try ```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly  
```

Then try your dvd. Fingers crossed!

Kopkins

---

### Post by JRV on 2013-03-15
I edited my post to say:

ubuntu-restricted-extras provides a lot of codecs for playing many audio/video files.
It is something you will want, but it does not play **encrypted** DVDs.

---

### Post by viriatovigo on 2013-03-15
Hi Kopkins.

Nop! Still doesn't play but there is another improvement this time. 

Now the disc drive shows up in the Launcher that it didn't before. When I do explore the disc, it shows icons for each track. When I do click on the tracks VLC plays **only** the sound but not the image and the sound is like if where cut off every 5 seconds.

Good! Sooner or later you are going to remember how you did resolve the issue. I am not all the time in the Forum because since the stroke I can not move very much and I am working from home as interpreter through Skype and translator online, so I do spend most of the time working, but I check the Forum 3 or 4 times per day every day to learn slowly slowly how to use Ubuntu. I am not new on Linux since about 10+ years ago or so I was using Red Hat but I gave up (my mistake...) because I did find it out of my capacity at that time (I've been on computers since 1975 with an IBM 360 30 Mainframe as COBOL programmer but "that" was in the Dark Ages... I think that now I am too much too old to cope with these new "tosters").

So, as soon as you remember, please, give me shout. 

Also, What about what says JRV that may be encrypted? How can be found that? He says that if encrypted it would't work as easy as that...

See you when I see you again.

Kind regards

Tino

---

### Post by viriatovigo on 2013-03-15
Ta JRV.

You did say that in first place. But, How to know then? And, What can be done about if that is the issue? Why doesn't happen with Apple and didn't happen with Windows?

Kind regards.

Tino

---

### Post by arpanaut on 2013-03-15
> Why doesn't happen witth Apple and didn't happen with Windows?
Programs that come with those operating systems have the ability to play encrypted DVD's 
That the vendors(and through them, you) PAY $$$ for. 
Thus Ubuntu being a free distribution they cannot distribute those propitiatory bits.
These are legal and monetary issues.

---

### Post by viriatovigo on 2013-03-15
Ta arpanaut.

Right... I got it... It makes sense to me.

Oh, well! I'll keep watching them in the laptop with Apple then. It is not going to be the end of the World, anyway...

In any case, thank you very much because it tells me that I was not doing anything wrong, just being naive.

However... I did upgrade to 12.10 few hours ago and now I can see the details of my PC and I get the Disks icon in the Launchpad where I can explore the DVD and... copy the contents in a folder within Documents. The copy shows track by track and now, by clicking on them, they play. The solo thing is that I need to open every track to see the full film but it works (errrr... after some arrangementes...). Now... How can I merge all the tracks in order so I can see the full film at once without having to open every track one by one? I know how to do it in Windows but I have not a clue how to do it in Linux.

All the best.

Tino

---

### Post by viriatovigo on 2013-03-15
It is OK arpanaut... I did find the solution:

[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

### Post by arpanaut on 2013-03-15
While what i posted earlier is true, you should be able to get dvd's to play through the tips in this thread.
And now that you have upgraded and your disc's are visible things may be better now take a look here and see if you have all this installed.
[https://help.ubuntu.com/12.10/ubuntu-help/video-dvd-restricted.html](https://help.ubuntu.com/12.10/ubuntu-help/video-dvd-restricted.html)

If so inclined you could buy this software to just get 'er done...
[https://apps.ubuntu.com/cat/applications/fluendo-dvd/](https://apps.ubuntu.com/cat/applications/fluendo-dvd/)

Hope this helps, I was just pointing out why it seems to work so seamlessly on other OS.
It can be done on Ubuntu and Linux.

---

### Post by viriatovigo on 2013-03-16
Ta MoebusNet

Too many things to do just to play a film. I think that Linux is too much for my expertice. After upgrading to 12.10 I am having a mountain of problems (and I can see in the Forum that I am not the only one with problems after upgrading to 12.10). It is hapening to me the same that did happen with Red Hat and in the end I gave up.  

I believe that I should stick to Apple Mountain Lion (and Apple now is too OpenSource) because I have not the intelligence level required by Linux, I am afraid...

Thank you anyway for your willingness to help.

Al the best.

Tino

---

### Post by Rukiri on 2013-03-17
> **Kopkins said:**
> If the above post doesn't work, try running this:```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Kopkins

I downloaded the restricted drivers, well the program caption kept blinking and poping up with errors, basically just copied/pasted what you said into the terminal and bam... I'm watching a movie. 

So, why doesn't this work by default?  DVDs are from the 90s, codecs/free codecs should already exist...

---

### Post by viriatovigo on 2013-03-17
Hi Rukiri.

The answers is in the previous arpanet post. People is running a business for profit not for charity. If everybody can jamp the encryptions nobody would buy a new item, it wiill download it from the net and the business will end going bankrupted.

Linux is free for a good reason, we do not pay a dime for anything and Linux t is second to none; if Linux set to play DVD without restrictions, it must pay its part of the royalties and, then, could not be free.

I don't think that to stop of being an OpenSource just because someone want to play DVDs in his/her PC is total nonsense. You always can **buy** an apps that you can find in the Sofware Centre. They are pretty cheap, most of the times at ridiculous price. You could call the Software Centre the Linus' Ebuy.

Well... It is my personal opinion what means nothing, of course, anyway.

Kind regards.

Tino

---

### Post by Kopkins on 2013-03-19
> **Rukiri said:**
> I downloaded the restricted drivers, well the  program caption kept blinking and poping up with errors, basically just  copied/pasted what you said into the terminal and bam... I'm watching a  movie. 

So, why doesn't this work by default?  DVDs are from the 90s, codecs/free codecs should already exist...


Depending on your locale, installing that software via the command I posted is illegal. Installing it by default would limit the distribution possibilities of Ubuntu.

That command installs the ability to play encrypted DVD's, so my guess is that it's a legal issue. Copyright's last a long time, so even the 90s are protected.

---

### Post by Rrory on 2013-04-11
Hi just want to say, I'm no tecchie expert. But I read this thread, installed the Ubuntu Restricted software, and also libdvdread4 command at the Terminal. It worked perfectly and now I can watch my movie. Thanks for the excellent help!
rory

---

### Post by JohnnyC44 on 2013-05-10
Thanks. Had the same problem. Downloaded the restricted extras, but did not realize I also had to run an install. Anyway, I'm good to go now.

---

### Post by nsync on 2013-05-10
i think the only answer to that is do update ubuntu weekly.. or always check for updates..

---

### Post by trovador on 2013-05-22
> **Kopkins said:**
> In nautilus, the defualt file manager, you should be able to see the disk listed near the top right under the devices. You can open nautilus by pressing the windows key, typing files, then pressing enter.

First, lets find out what drive your disk is in.
Enter the following in the terminal, but make sure you have the disk inserted.
```
df
```

The output on my computer has several lines like this
```

/dev/sr0          509952   509952         0 100% /media/ARCH_201302


```
That line is my dvd drive. /dev/sr0 is my drive.

Like mine, you should have the 100% used and it will most likely be in /media/NAMEofDISK

If you can't figure out what disk drive is yours post the info back here.

Now try opening the disk from VLC. Open VLC, then go to the menu > media > open disk...
Or press ctrl + D while in vlc.

There will be a window that opens. There will also be a box for Disc device. Try putting your drive in there. So for me it would be /dev/sr0. Or try choosing from the dropdown.

Good luck,

Kopkins

Hi, I've the same problem ,better with encrypted dvd, but when I try to play by VLC nothing happen after a while VLC is closing without any message
This is the dvd
/dev/sr0          7660760 7660760         0 100% /media/PLS0EIW1
Is there anything else that I can do ?
Thank you

---

