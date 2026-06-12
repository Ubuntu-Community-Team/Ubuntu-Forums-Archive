---
title: "How to create ISO images from your HD CD DVD"
date: 2004-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Sniffer on 2004-11-29
This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

To make an ISO from files on your hard drive, create a directory which holds the files you want. Then use the mkisofs command.

mkisofs -o /tmp/cd.iso /tmp/directory/

This results in a file called cd.iso in folder /tmp which contains all the files and directories in /tmp/directory/.

For more info, see the man pages for mkisofs, losetup, and dd, or see the CD-Writing-HOWTO at [http://www.tldp.org](http://www.tldp.org).

Hope it helps
Sniff.

Ubuntu Freak :mrgreen:

---

### Post by pklntkj334 on 2005-04-15
hi,

but as i see it just creates a image from hd/cd...  

to make it more fun,  how could we make it a bootable/reinstall cd/dvd???  

I mean, if we could create a cd.iso from our hd, that could be very nice if we could restore it.

Considering a hard disk crash, what are the best ways to do that ( restore from cd.iso)??

---

### Post by kuleali on 2005-04-16
nice, guide

---

### Post by Maddy on 2005-05-16
[QUOTE=Sniffer]This is very helpfull to backup you cd and dvd into iso images:

dd if=/dev/dvd of=dvd.iso # for dvd
[/QUOTE]


can I use this command to make an iso of an double layer dvd too ?

---

### Post by Sniffer on 2005-05-16
Never tried...but it should work, i presume.

---

### Post by Maddy on 2005-05-18
[QUOTE=Sniffer]Never tried...but it should work, i presume.[/QUOTE]

Well I tried to make an iso of my suse 9.3 dvd, this is a dual layer dvd so it contains 8.1Gbyte, If i use dd to make an iso I get about 3.9Gbyte in the iso.

---

### Post by Sniffer on 2005-05-18
Maybe it can help you out.

> Since I always make a back-up copy of my original SuSE dvd's, I looked around if it can be done with the new dual layer dvd as well. And I found an easy and excellent way to do it over at linux-club.de.
All kudos goto "crazyrolf", I just translated his German how-to into English and added a comment or two.

Here it goes:
I found a nice manual how to make a back-up of your SUSE 9.2 DVD that includes only the 32bit version and fits on a single layer dvd. This how to will create an ISO that can be burned to a regular DVD.
This is only intented to be used with legal copies of SuSE 9.2

Some explanations.
Everything will be done in a root shell
# ... is a prompt
Everything to the right of the prompt is an order that has to be executed.
Lines without prompt are just messages that are created during the executions of the orders

Lets start:
First mount the original DVD (if you created an ISO from the original DVD then you must extract that into a folder) with (or similar, that depends on your system)

# mount /cdrom
Now you need to create a new directory on your harddrive (it will take about 4GB). I called mine "/suse92". Lets get to work ( I will not explain the single commands, just use them in the order they are posted but change it for your dvd drive or the folder in case you already extracted the entire dvd):

# mkdir /suse92
# cd /cdrom
# cp -p * /suse92
cp: Verzeichnis ?boot? ausgelassen
cp: Verzeichnis ?docu? ausgelassen
cp: Verzeichnis ?dosutils? ausgelassen
cp: Verzeichnis ?media.1? ausgelassen
cp: Verzeichnis ?suse? ausgelassen
# cp -a boot /suse92
# cp -a docu /suse92
# cp -a dosutils /suse92
# cp -a media.1 /suse92
# mkdir /suse92/suse
# cp -a suse/i586 /suse92/suse
# cp -a suse/i686 /suse92/suse
# cp -a suse/noarch /suse92/suse
# cp -a suse/setup /suse92/suse
# cd /suse92/suse
# mkdir x86_64
# chmod +w *

Now it is time to get rid of the stuff we don't need:

# cd /suse92/suse/i586
# ls aspell-[a-z]*|grep -v -- -de-|grep -v -- -en-|grep -v devel|xargs rm
# ls OpenOffice_org-[a-z]*|egrep -v "(gnome)|(kde)|(Quick)|(-de-)|(-en-)"|xargs rm
# cd /suse92/suse/noarch
# ls ispell-*|grep -v german|xargs rm
# ls yast2-trans-*|egrep -v "(-en)|(-de)"|xargs rm
# ls susetour-[a-z]*|grep -v de|grep -v en|xargs rm
# ls susehelp_[a-z]*|grep -v de|grep -v en|xargs rm
# ls suselinux-adminguide*|egrep -v "(_de)|(_en)"|xargs rm
# ls suselinux-userguide*|egrep -v "(_de)|(_en)"|xargs rm
# ls myspell-*|egrep -v "(german)|(american)|(british)"|xargs rm
# ls k*-i18n*|egrep -v -- "-(de)|(en)"|xargs rm


This last chapter is only valid for the German and English language installation. If you need a different language then you have to make the proper changes.

We are done with the data and it is time to create the ISO

# cd /suse92

ISO Image creation : the next lines are one entire command, that needs to go in one line

# mkisofs -o SuSE_9_2.iso -b boot/loader/isolinux.bin -no-emul-boot -boot-info-table -joliet-long -publisher SuSE -r -V SuSE_9_2 -graft-points /suse92

Done
Burn the DVD and enjoy your back-up.

This is only intented to be used with legal copies of SuSE 9.2

---

### Post by bzaume on 2005-07-30
hi,
it works perfectly to create iso images from cd-rom ; but do you know how to create an iso image of an audio cd ?
thanks

---

### Post by kahping on 2005-10-12
[QUOTE=bzaume]hi,
it works perfectly to create iso images from cd-rom ; but do you know how to create an iso image of an audio cd ?
thanks[/QUOTE]

*bump*

i'm interested in learning this, too.

kahping

---

### Post by Nwallins on 2006-02-14
.

---

### Post by engla on 2006-02-14
If you right-click on a cd on the nautilus desktop and select "Copy CD" you can choose to make an .iso. I had to install the tool cdrdao, though (w/ synaptic)

---

### Post by lf82 on 2006-03-05
[QUOTE=bzaume]hi,
it works perfectly to create iso images from cd-rom ; but do you know how to create an iso image of an audio cd ?
thanks[/QUOTE]
It works the same way,  only you'll have music instead of files.

Tried and tested.

---

### Post by cosmolee on 2006-04-04
Hmmm, doesn't work for me for *audio* CDs - data OK, but not audio:

# dd if=/dev/hda of=/tmp/dd.iso
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 1.707692 seconds (0 bytes/sec)
#

---

### Post by Rasymas on 2006-04-07
I don't understand the guide posted in the beggining of page 1. The hell -o means?.. I have a DVD movie on my desktop, so what should I type in order to make it the ISO file? 

Thanks in advance ;)

---

### Post by Sarteck on 2006-07-23
For some reason, this doesn't seem to wish to work for me.  D:  It makes an image file, but it's generally only about 25 KB, as it gets an Input/Ouput error.

In case it was a permissions error, I tried doing this "sudo"ed, with similar results.

```
sudo dd if=/dev/cdrom of=/home/sarteck/FFIX1.iso
dd: reading `/dev/cdrom': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.224965 seconds, 109 kB/s
```

{Yeah, trying to make ISOs of my PSX games for backups, heh.}

---

### Post by CodeNosher on 2007-04-15
I get the same problem.  I've tried to make an iso of a game.  It makes an ISO with like 1.5 MB.  When I mount it, it shows all the files that were on the CD, even the correct size, but the data is missing.

What's up with that?

---

### Post by Moosetek13 on 2007-06-01
Try ISO Master:
[http://littlesvr.ca/isomaster/](http://littlesvr.ca/isomaster/)

---

### Post by redester on 2007-06-13
Thanks Sniffer,

Copied, printed, saved and remembered where I saved it.

:D

---

### Post by cpoint on 2007-09-18
> **Sniffer said:**
> This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi


Ubuntu Freak :mrgreen:

I have tried this and had no success.  I've also tried isomaster, Gnome CD master, and "cat /dev/hdc > /mount/location/image.iso."  No luck.  My output from the above code is similar to that of two other people who posted here.  Has anyone had success with this stuff?  I'm guessing I have a simple change to make somewhere but I'm not sure where to start.  Thanks in advance; here's the output when I run the above command:

$ dd if=/dev/cdrom of=Taj.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.008087 seconds, 0.0 kB/s
$

So I tried /dev/hda, because that's how I normally refer to my CD drive.  Same output:

$ dd if=/dev/hda of=Taj.iso
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.003242 seconds, 0.0 kB/s
$

NOTE: I have no trouble creating .iso images from DATA CDs; I'm having all of my trouble creating .iso images out of my audio CDs.  Any suggestions?  Thank you!

---

### Post by cpoint on 2007-09-24
Hey all - 

No one has any suggestions about this?  I've tried all of the options in this thread on two different computers and I'm still getting no results (or results like the ones posted in my last post, above.)

If anyone can let me know how to archive audio CDs, I'd very much appreciate it.

Thanks!

---

### Post by dutch_gecko on 2007-12-07
Sounds to me like there might be some copy protection involved, stopping the CDs from being ripped. The same probably applies to the game disks as well.

---

### Post by smartboyathome on 2007-12-07
cpoint, have you tried [remastersys]("http://klikit.pbwiki.com/Remastersys")? It basically does what this howto does, but is more convenient.

---

### Post by tenchu77491 on 2007-12-24
p$ dd if=/dev/cdrom of=/home/MYNAME/Desktop/cd.iso
dd: reading `/dev/cdrom': Input/output error
32+0 records in
32+0 records out
16384 bytes (16 kB) copied, 5.33848 seconds, 3.1 kB/s

What is the problem? Makes a 16kb little .iso =(

---

### Post by petersk on 2008-01-07
In order to help diagnose your problem, can you also show the results of you "umount"ing your drive?
Kurt

---

### Post by Antarctica on 2008-01-16
> **Sniffer said:**
> This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

To make an ISO from files on your hard drive, create a directory which holds the files you want. Then use the mkisofs command.

mkisofs -o /tmp/cd.iso /tmp/directory/

This results in a file called cd.iso in folder /tmp which contains all the files and directories in /tmp/directory/.

For more info, see the man pages for mkisofs, losetup, and dd, or see the CD-Writing-HOWTO at [http://www.tldp.org](http://www.tldp.org).

Hope it helps
Sniff.

Ubuntu Freak :mrgreen:
Hey, why don't you all just go to Places, Computer, right click on the CD/DVD drive, go to "Copy Disc" and copy to a file instead of a CD or DVD?  I did it and it's much easier than memorizing some terminal commands.

---

### Post by mdurham on 2008-02-04
> **Sniffer said:**
> This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

:

<edit>

---

### Post by Dark-Penguin on 2008-02-04
> **mdurham said:**
> This does NOT make an iso file, it's just an image, which is different from an iso.

Cheers, Mike

I have a Dell Latitude Laptop C840 with an nvidia card in it. I was interested in anyone out there that had done a ISO of their machine that one can download. I've tried a bunch of guides to get the driver loaded and nothing seems to work. I've loaded the driver and the edid.nin file but screen is still messed up.

I pulled a couple of Ubuntu ISO's off of a torrent download and they seem to be using the NV driver. Using the NV driver and they got the 3d graphics to work but for me that works but no go on the beryl or compiz (cube stuff)......

---

### Post by Fred Doolie on 2008-02-14
[QUOTE=Sniffer;25568]This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

Or......

Right-click on the icon for the CD
Choose "Copy Disc"
Change the destination to "Image File"

---

### Post by mdurham on 2008-02-14
> **Fred Doolie said:**
> [QUOTE=Sniffer;25568]This is very helpfull to backup you cd and dvd into iso images:

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi


<edit>
This is correct.
Cheers, MIke

---

### Post by kevinlam on 2008-02-20
> **mdurham said:**
> [QUOTE=Fred Doolie;4332081]

This is NOT correct. Just calling something ".iso" DOES NOT make it an iso format file.
Cheers, MIke

hmm while that's true but its says here 
[http://www.tldp.org./HOWTO/CD-Writing-HOWTO-4.html#ss4.7](http://www.tldp.org./HOWTO/CD-Writing-HOWTO-4.html#ss4.7)

Second case: you don't have a separate CD-ROM drive. In this case you have to use the CD-writer to read out the CD-ROM first:

    dd if=/dev/scd0 of=cdimage

This command reads the content of the CD-ROM from the device /dev/scd0 and writes it into the file "cdimage". The contents of this file are equivalent to what mkisofs produces, so you can proceed as described earlier in this document (which is to take the file cdimage as input for cdrecord). If you want to see a progress-meter and other fancy stuff, then you can also use Jörg Schillings sdd. 

btw adding options conv=noerror,sync to dd might help with error prone cdroms that have read errors if i am not wrong

---

### Post by mdurham on 2008-02-20
> **kevinlam said:**
> [QUOTE=mdurham;4332594]

hmm while that's true but its says here 
[http://www.tldp.org./HOWTO/CD-Writing-HOWTO-4.html#ss4.7](http://www.tldp.org./HOWTO/CD-Writing-HOWTO-4.html#ss4.7)

Second case: you don't have a separate CD-ROM drive. In this case you have to use the CD-writer to read out the CD-ROM first:

    dd if=/dev/scd0 of=cdimage

This command reads the content of the CD-ROM from the device /dev/scd0 and writes it into the file "cdimage". The contents of this file are equivalent to what mkisofs produces, so you can proceed as described earlier in this document (which is to take the file cdimage as input for cdrecord). If you want to see a progress-meter and other fancy stuff, then you can also use Jörg Schillings sdd. 

btw adding options conv=noerror,sync to dd might help with error prone cdroms that have read errors if i am not wrong

Yes kevinlam you are quite right, I'm sorry that I misled whoever might have read my post. I've just made a dd image and an iso image of the same CD and the images are indeed exactly the same. My mistaken belief came from trying to do what was suggested in the first place. ie, writing a dd image as an iso, and it didn't work for me, I got the error message "input file is not an iso". Ever since I believed this to be the case. Mistakenly alas.
Sorry about that.
Cheers, Mike

---

### Post by merlinDwizzard on 2008-02-20
I used remastersys to make a live disro of my system. there are two ways to use it. 1) make a complete reinstallable back up disc or 2) make a redistributable disc that excludes your home directory. pretty slick. i can put the distro in a machine at school and run advanced desktop effects from a live disc.

---

### Post by BassKozz on 2008-03-04
Confirmed working for CD Backup :D
Awesome thread... Thanks for the help everyone :guitar:

---

### Post by SloYerRoll on 2008-03-06
OK. I've seen some really good stuff in here. But I got lost on a few things. 

[LIST=1]
[*]Ubuntu automatically mounts cd/DVD's when they are loaded. The OP said you can easily unmount it through terminal. I'm not scared of terminal, but don't understand the file hierarchy of nix systems yet. So, how do i determine the path to my cd/dvd drive? I assume when I type in unmount and bash doesn't recognize the command is because I'm not in the correct place to unmount. Correct? (BTW: I Googled all over hte place and searched for it in these forums and found nothing, so it's not THAT common:))
[*]I tried the right click>copy CD method. I have a pretty fast DVD drive and it took over 20 minutes to burn 1/4 of a DVD, Is there any way to optimize this or check to see if everything is OK?
[*]What happens w/ double layer DVD's that have a larger size than 4.7GB? I read about this in the thread, but I didn't see a clear explanation for this
[/LIST]

Thanks for all your help. It's been a little bit of a bumpy road converting over to Ubuntu. I'm still very happy I did it though!

Best,

---

### Post by dexter23 on 2008-07-07
k3b -> burn CD/DVD -> make image only (or sth like that) :)

---

### Post by Sniffer on 2008-07-22
This was one of my 1st threads in ubuntu community...still here :)

I would like to recommend ACETONEISO, a great utility to deal with images.

Try it, really AWESOME.

Regards
Sniff

---

### Post by greginedmonton on 2008-08-13
Be sure to check out this link as this may be why your dd command is coming up with errors.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by starcannon on 2008-09-06
Guide worked perfectly for me, created a back up copy of my CD, thanks very much. Wish they allowed a "Thank You" in this forum.

---

### Post by tealio on 2008-12-13
if you want to learn more about the *dd* command, check out [_this page_]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/").

It gives a ton of other really useful uses for the *dd* command, including imaging a hard drive, etc...

---

### Post by sanemanmad on 2009-01-19
Hi, 

I do not see anyone else mentioning this either, so here is another quick-n-dirty way of creating an .iso of any CD/DVD:

Example: I wanted to install WinXP 64bit onto a VM in VirtualBox... through the CLI, remotely (Reason I resorted to this method). So I had the Windows XP install CD inserted into the server and performed the following commands in order.

```
mount /media/cdrom0
cat > /dev/scd0 > whatever.iso

```
Note that you will not see a progress bar during this time as I was not too concerned with status, after all I just performed the command```
ls -l 
```on that server and watched the size grow.

---

### Post by GIRI MURALI on 2010-05-15
Using APT-GET,Synaptic we can create ISO on CD or DVD of installed pakages in your computer
Here is the step by step procedure

First install APTonCD on your system
then system > administration >APtonCD
you will se APTonCD window then select creat button
now select the packages you need to install and click on BURN button
Now you can see installation properties under type of medium you can select CD or DVD as your wish
now click applay button
after creating ISO image you can see a dialog box saying image ready  if you want to create ISO image now you can click yes and after putting CD/DVD click on write button

here is a good tutorial
[http://www.beubuntu.co.cc/2009/12/using-apt-getsynaptic-we-can-create-iso.html](http://www.beubuntu.co.cc/2009/12/using-apt-getsynaptic-we-can-create-iso.html)

---

### Post by areskz on 2010-07-13
You can simply type one command in terminal to get an iso:

```
cat /dev/scd0 > /home/username/test.iso
```

thanks [shamanstears]("http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/")

---

### Post by dagdeniz on 2010-08-23
> **areskz said:**
> You can simply type one command in terminal to get an iso:

```
cat /dev/scd0 > /home/username/test.iso
```thanks [shamanstears]("http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/")

> **sanemanmad said:**
> 

```
mount /media/cdrom0
cat > /dev/scd0 > whatever.iso

```Note that you will not see a progress bar during this time as I was not too concerned with status, after all I just performed the command```
ls -l 
```on that server and watched the size grow.

Those who'll take this method, just keep in mind that it will not work with a bootable cd/dvd.

---

### Post by nerdybrunette on 2010-12-03
> **pklntkj334 said:**
> hi,
 
but as i see it just creates a image from hd/cd... 
 
to make it more fun, how could we make it a bootable/reinstall cd/dvd??? 
 
I mean, if we could create a cd.iso from our hd, that could be very nice if we could restore it.
 
Considering a hard disk crash, what are the best ways to do that ( restore from cd.iso)??
 
 
Does anybody have a solution for this that doesn't involve using a 3rd party program?

---

### Post by cosmolee on 2010-12-03
As someone previously mentioned, try Remastersys:

[http://klikit.pbworks.com/w/page/7315119/Remastersys](http://klikit.pbworks.com/w/page/7315119/Remastersys)

It *is* third party software, though it's free....

HTH,
Cosmo

---

### Post by nerdybrunette on 2011-01-14
Thanks for the input, I ended up using Ghost 4 Linux ([G4L]("http://sourceforge.net/projects/g4l/")).

---

