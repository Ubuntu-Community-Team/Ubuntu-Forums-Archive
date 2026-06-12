---
title: "live dvd XUbuntu"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by jimpierce7 on 2013-05-19
I must be missing it, I can't find where/how to run XUbuntu from the DVD. I don't even see an install option. I got the KUbuntu DVD ok.

---

### Post by jimpierce7 on 2013-05-19
I have downloaded twice from a mirror site. Should I just get a bittorrent  downloader?

---

### Post by mastablasta on 2013-05-19
yes you must be "misisng it".
assuming tou plan to go with DVD:
1. download the iso
2. burn the .iso to DVD
3. reboot the maschine and open the boot order menu or access the BIOS. select to boot from DVD in BIOS.
4, once it boots select try it to boot into Xubuntu

what was your procedure? and where (at what step) the do you fail?

---

### Post by sudodus on 2013-05-19
> **jimpierce7 said:**
> I must be missing it, I can't find where/how to run XUbuntu from the DVD. I don't even see an install option. I got the KUbuntu DVD ok.

Xubuntu is Ubuntu with the XFCE desktop environment

Kubuntu  is Ubuntu with the KDE desktop environment

They reside on different iso files. You will not find Xubuntu on the Kubuntu iso file or CD/DVD/USB install drive. Or was it a typing error? Do you have a Xubuntu DVD?

---

### Post by pqwoerituytrueiwoq on 2013-05-19
[http://cdimage.ubuntu.com/xubuntu/releases/raring/release/](http://cdimage.ubuntu.com/xubuntu/releases/raring/release/)
i just use the torrent, no chance of bad download that way
if you are on windows burn it using infrarecorder (burn disk image)

---

### Post by jimpierce7 on 2013-05-19
I download from a mirror server? As I don't have software currently for bittorrent. I burn the DVD, then restart. On the Kubunto the icon was there as well as a program to install to make sure it starts on reboot.
On a separate disc is the Xubuntu, and I can't find any of that. I was thinking I hadn't looked far enough as one of the 'read me' files says there should be something there.

---

### Post by sudodus on 2013-05-19
- Did you 'burn from the iso file' or did you make a data DVD with the iso file 'copied' onto it for Xubuntu?

- Do you remember or can you check if it is made from a 'desktop iso file' or an 'alternate iso file'? (The alternate iso file installs in text mode, which is good for computers with low RAM. The final result is Xubuntu with graphical desktop interface anyway.)

- What happens when you try to boot from the Xubuntu DVD?

- What does the Xubuntu DVD look like, when inserted into a running computer? What files can you see?

---

### Post by jimpierce7 on 2013-05-19
I get 9 folders. 
.disk
boot
casper
dista
install
isolinux
pics
pool
preseed

and a md5sum twxt document and README disc defines file.

---

### Post by jimpierce7 on 2013-05-19
in Install I read the doc about the sbm. It won't run. It opens on the note pad is all. It doesn't install.

---

### Post by jimpierce7 on 2013-05-19
I used a torrent download and the same thing. I'm trying the 12.04 this time. Tried Ubuntu but it was going to take 8 hours to download. That's an over nighter.

---

### Post by jimpierce7 on 2013-05-20
this is what the read ne in install says.............

About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.

---

### Post by sudodus on 2013-05-20
> **jimpierce7 said:**
> I get 9 folders. 
.disk
boot
casper
dista
install
isolinux
pics
pool
preseed

and a md5sum twxt document and README disc defines file.
This looks OK :-)

Did I get it right, that the Kubuntu DVD boots, but not the Xubuntu DVD?

---

### Post by jimpierce7 on 2013-05-20
yes, that is right. Do I have to remove the Kubuntu first? And I can't get the bin file to do anything. I'm going to bed. 5 gets here quick. I have Ubuntu downloading now. It still has 8 hours to go. Not much upload speed I'm guessing?

---

### Post by sudodus on 2013-05-20
I have not used SBM. Have you tried the standard Xubuntu desktop iso file or Xubuntu alternate iso file for the version 12.04.2? Not a DVD, but one of the official CD image iso files. I tried the Xubuntu desktop iso yesterday, and it worked as it should :-)

---

### Post by sudodus on 2013-05-20
> **jimpierce7 said:**
> yes, that is right. Do I have to remove the Kubuntu first? And I can't get the bin file to do anything. I'm going to bed. 5 gets here quick. I have Ubuntu downloading now. It still has 8 hours to go. Not much upload speed I'm guessing?

I suggest that the next thing you write about is the computer. If you describe it, you will get better advice about what to install and how to install it.

If you have an old computer you need an Ubuntu flavour with a light desktop environment. Otherwise you can run any flavour. ***You*** choose between speed and eye-candy.

- Lubuntu is lightest.
- Xubuntu is light.
- Ubuntu and Kubuntu are heavy but have more eye-candy.

If you have low RAM (512 MB or less), you need the alternate iso, otherwise the desktop iso is better.

So please specify

- computer hardware specs, at least cpu, ram and graphics chip/card.

- what operating system(s) you have and what you want (for example dual boot)

-o-

Have you installed Kubuntu? How is it running? Or are you only running it live from the DVD?

If you need to remove Kubuntu depends on what you have on your internal hard disk and how much free space there is.

Please mount all partitions that can be mounted (use the file browser to mount the partitions on the internal drive), run the following commands and post the output in a reply (from Kubuntu, if that is the only linux system that is working)

```
sudo fdisk -lu
```
```
sudo parted -l
```
```
df
```

---

### Post by mastablasta on 2013-05-20
> **jimpierce7 said:**
>  Do I have to remove the Kubuntu first? 


wait! what?

do you have Kubutnu installed on computer? and you want to install xubutnu to it now? just open muon software center and search for xubuntu desktop. click install logout and select xubuntu desktop on login.

---

### Post by jimpierce7 on 2013-05-20
I have a Dell Inspiron 530s that runs Vista. 3g ram. I figured out my problem downloading Ubuntu, downloading straight to Roxxio instead of a folder. BIG difference in download time. Kubuntu is only running on the DVD, but the DVD helper in downloaded.

I'm going to see if Ubuntu works and if it does, I'm going to just run it along side Vista for the time being.

---

### Post by houseworkshy on 2013-05-20
"If you have low RAM (512 MB or less), you need the alternate iso, otherwise the desktop iso is better." from sudodus.

That's  a bit strange though I haven't given a recent Xubuntu a spin recently.   I've just tried Xfce sitting on Debian Wheezy live ( which is the  latest stable one )  a spin on a single core 512 machine and it was fast  using very little of the resources available, only around 28 % of  available RAM ( though it may be counting the 128 in the card too ) and  that was live with the file system sitting in there. If Ubuntu is based on Debian and Xfce is the same in both what uses the extra RAM?

It was a test proir  to putting it on someones machine for them.  Also tried out video,  gimp, office, flash and various other bits  and it was still nippy.    I'd taken several distos round to choose from, mostly light ones like  bodhi and antiX and the Wheezy was just a "be nice if it can".   Oddly  the officially light ones made the fans do vacume cleaner impressions  and the cd/dvd drive grind, could be something peculiar to do with that  particular machines compatability (they'd all worked fine on mine ), we  didn't persevere as it sounded damaging.   Will be buying a new dvd/cd  before installing anyway despite Debian not having had  that effect,   it's probably due as that drive installed Ubuntu 8.04 when it was fresh  and it wasn't new even then.  Think the machine dates from when XP was Microsofts latest.
Bit of an aside there.  The pertinant bit is that if you want Xfce and Xubuntu won't then Debian Wheezy might.

---

### Post by sudodus on 2013-05-20
> **houseworkshy said:**
> "If you have low RAM (512 MB or less), you need the alternate iso, otherwise the desktop iso is better." from sudodus.

That's  a bit strange though I haven't given a recent Xubuntu a spin recently.   I've just tried Xfce sitting on Debian Wheezy live ( which is the  latest stable one )  a spin on a single core 512 machine and it was fast  using very little of the resources available, only around 28 % of  available RAM ( though it may be counting the 128 in the card too ) and  that was live with the file system sitting in there. If Ubuntu is based on Debian and Xfce is the same in both what uses the extra RAM?

It was a test proir  to putting it on someones machine for them.  Also tried out video,  gimp, office, flash and various other bits  and it was still nippy.    I'd taken several distos round to choose from, mostly light ones like  bodhi and antiX and the Wheezy was just a "be nice if it can".   Oddly  the officially light ones made the fans do vacume cleaner impressions  and the cd/dvd drive grind, could be something peculiar to do with that  particular machines compatability (they'd all worked fine on mine ), we  didn't persevere as it sounded damaging.   Will be buying a new dvd/cd  before installing anyway despite Debian not having had  that effect,   it's probably due as that drive installed Ubuntu 8.04 when it was fresh  and it wasn't new even then.  Think the machine dates from when XP was Microsofts latest.
Bit of an aside there.  The pertinant bit is that if you want Xfce and Xubuntu won't then Debian Wheezy might.

It is the installer of the Ubuntu desktop iso, that need that amount of RAM. The alternate installer needs less, and gives you the same system (in this case Xubuntu). After installation Xubuntu runs with less RAM.

But Debian with XFCE needs less RAM than Xubuntu (and probably has a leaner installer too). I think the Ubuntu kernel needs more ram than the debian one, and I think more services are running in Ubuntu based flavours. I think Xubuntu offers a better user experience without adding packages and tweaking (at the cost of using more RAM).

---

### Post by houseworkshy on 2013-05-20
Thanks for the info Sudodus.   I was guessing it was something like that, the  live version includes some none free stuff like codecs whist the main  one doesn't, the graphic installer is similar to Ubuntus' several years  ago ( the 7's and 8's ) ;  text with a few drop down menues but no slide  show.  I've actually put Wheezy into my machine twice now using the  standard iso; on one drive with a root account and on the other drive  leaving the root password blank so that it disabled the root account and  installed sudo instead.  Still playing with it, only put it/them in last night, just feeling round it but so far very nice.  Really like the  multi-architecture feature and it has some things which I'd only  associated with Ubuntu like app-armour.

Xubuntu won't really need  much in the way of tweeking and just adding a meta package like  "ubuntu-restricted-extras" will sort most of it out.  So yes it may be  easier.    As Ubuntu is already in just, as said above,  install Xfce.   
Then reboot and at login use the dropdown menu to choose to use it.   You'll probably find a few duplicated menu entries as you will now have  both UI's installed, don't worry about that yet. Test that all works as  you like, if it does then it is a matter of removing KDE.  It's not  quite so simple as just uninstalling it if you want to remove all of it,  but not hard,  so search the forums again for that if it's what you  choose to do.  As an aside if KDE works okish  ( and it's a beauty of a  UI IMHO if you have the RAM for it, can easily configure it into  practically anything, there's a light version too called razor-qt which  ain't bad ) then Xfce will run very fast indeed.

---

