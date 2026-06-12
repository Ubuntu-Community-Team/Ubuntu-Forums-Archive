---
title: "Help booting from USB"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by delicious3141 on 2012-11-08
Hi guys,

My computer went haywire and refused to start up. I really thought it was ruined but my friend suggested booting from USB with Linux (Ubuntu) as a way to potentially get in and retrive files I thought I'd lost.

I downloaded the installer from pendrivelinux.com and managed to boot up off the USB from the BIOS. I was excited to see Ubuntu seemed to have actually loaded! But now I have what I assume is the default Ubuntu desktop and it's asking for login username and password. I never had a username and password on my XP before the crash and i don't know how to get past this screen. It's frustrating because I would be ridiculously stoked if I were able to save some of these files.

Thanks in advance for your help.

---

### Post by newb85 on 2012-11-08
What release of Ubuntu are you using?  (The release is indicated by numbers like 12.04 or 8.10.)  To my knowledge, none of the current releases ask for that information in a live session.

I know that in old releases, when that happened, leaving them blank was the way to go.  However, not all of the old releases have NTFS support built-in, which you will probably need to retrieve your files.

Edit: perhaps you're using a variant, like Lubuntu, Xubuntu, or Kubuntu?

---

### Post by delicious3141 on 2012-11-08
Hi, thanks for replying.

It is Ubunto 12.10 and not one of the variations (or at least the file was ubuntu-12.10-desktop-i386.iso and it's saying Ubunto on the desktop background behind this login request.

I tried blank and blank just now and that didn't work.

---

### Post by delicious3141 on 2012-11-09
Can anybody help? $10 via paypal to anybody with a solution which leads to me getting my file back!

---

### Post by blade4 on 2012-11-09
If its Ubuntu 12.10 , there should be an option for accessing guest account ( just scroll down on the login screen ) . This account is not password protected and you should be able to access it .

---

### Post by delicious3141 on 2012-11-09
I posted this in beginners but it got mostly ignored. I'll paypal $10 to anybody who can give me instructinos which lead to me retriving my files.

----------------

"Hi guys,

My computer went haywire and refused to start up. I really thought it was ruined but my friend suggested booting from USB with Linux (Ubuntu) as a way to potentially get in and retrive files I thought I'd lost.

I downloaded the installer from pendrivelinux.com (Ubuntu 12.10) and managed to boot up off the USB from the BIOS. I was excited to see Ubuntu seemed to have actually loaded! But now I have what I assume is the default Ubuntu desktop and it's asking for login username and password. I never had a username and password on my XP before the crash and i don't know how to get past this screen. It's frustrating because I would be ridiculously stoked if I were able to save some of these files.

Thanks in advance for your help."

Additional: I have tried blank and blank for the password as suggesed in other thread but no luck.

---

### Post by The Cog on 2012-11-09
The live CD doesn't normally ask for a username and password as you log in. However, certain operations need admin rights and will ask for a password, for which you just press Enter. As it happens, the username is **ubuntu** but I don't think you should need to know that for what you want to do.

Can you tell us which version if Ubuntu you are using, and describe the desktop you see? This might help us work out what's going on.

---

### Post by delicious3141 on 2012-11-09
Logging in with Ubuntu username and no pass got me in. Thank you! Unfortunately it looks like my hard drive is messed up because as soon as it got in the screen started flickering maniacally and crashed. I'm pretty sure something majorly bad has happened to the HD or some other internal component caues that fits with the whole system refusing to start in windows even in safe mode.

Thanks.

---

### Post by lisati on 2012-11-09
Threads merged.
Please do not start multiple threads for the same problem, it dilutes the community's ability to help. Please also keep in mind that we have people reading this forum who have a wide range of tolerance for "naughty" words, so try to avoid language that could trip our word filter.

---

### Post by varunendra on 2012-11-09
> **delicious3141 said:**
> Logging in with Ubuntu username and no pass got me in. Thank you! Unfortunately it looks like my hard drive is messed up because as soon as it got in the screen started flickering maniacally and crashed.
Can you post a screenshot of that 'flickering'? It may be a video driver issue. Since you are booting from a live usb, it has nothing to do with the condition of files on the hard disk.

Also, it shouldn't ask you for a password, as others have already said. So maybe either the downloaded iso is corrupt, or there could be some error while creating the live usb. While the 'flickering' could be due to driver incompatibility, an error in the iso or the live usb may also cause this. Accordingly, you should check the integrity of the downloaded iso : [How to md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")

When the usb starts to boot, pressing any key should bring up 'Advance' menu. There should be an option to "Test the disc for errors". Use that to verify disk contents. In the same menu, pressing F6 should present you a pop-up menu. Look for 'nomodeset' option in it > select it by highlighting and pressing 'spacebar' > Esc > Enter to boot. That should take care of driver incompatibility issue.

Some other options :
[Slax]("http://www.slax.org") (200MB iso, ridiculously easy to create live usb)
[Unetbootin]("http://unetbootin.sourceforge.net") (a good alternate to the universal usb installer)

---

### Post by delicious3141 on 2012-11-09
> **lisati said:**
> Threads merged.
Please do not start multiple threads for the same problem, it dilutes the community's ability to help. Please also keep in mind that we have people reading this forum who have a wide range of tolerance for "naughty" words, so try to avoid language that could trip our word filter.

Sorry about that. I did wait 12 hours without any replies before I tried again in a different forum. I use my computer for business so have been quite stressed about this and jumping the gun somewhat. My apologies.

---

### Post by C.S.Cameron on 2012-11-09
If you are having problems with the installer from PendriveLinux, try Unetbootin or better yet Startup Disk Creator from the Live USB.

I have also had problems with a Live install asking for passwords, I figure it is due to a corrupt iso.

Has your hard drive been making a clicking sound?

---

### Post by varunendra on 2012-11-09
> **C.S.Cameron said:**
> try Unetbootin or better yet **Startup Disk Creator** from the Live USB.
A big +1 to Startup disk creator also. Just be aware you'll need a separate usb card/drive and the downloaded iso if you are running the live session from usb rather than cd.

For alternates and possible driver issues, see my previous post.

---

### Post by crushkittykitty on 2012-11-10
on my site the first page walks you threw the live install on usb then just mount the hard drive and pull what you need assuming your hard drive is still in working order . unetbootin also has other fixes for hard drives. Donate the 10 to ubuntu.
this isnt window usually advise is free :popcorn:
[http://ubuntutheotheros.webs.com/](http://ubuntutheotheros.webs.com/)

---

### Post by Bartender on 2012-11-10
Depending on your level of ability, and whether or not you've got another PC laying around, it might be far easier to physically remove the HDD from the one that won't start and slave it to another PC.

If I read it right, the sick unit is XP?  That means the HDD is very likely to be PATA.  You know, the big, wide ribbon cable for data rather than the skinny SATA cable.  SATA's been around for about 10 years, so it could be either.

If it's a SATA drive, and you can get your hands on a [dock]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817153066&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA"), it'd be simple to access the data from another PC.  

If it's PATA, then probably easier to open up another older PC and slave it to the motherboard.

If you just want a LiveCD environment, I'd suggest Knoppix rather than the full-blown Ubuntu LiveCD.  Knoppix is designed for exactly what you describe.

If the PC freaks out when you access the HDD via a LiveCD (screen flickering, crashes) then I'd suggest getting the HDD out of that rig and plugging it into some other rig.  You could have a failing power supply or motherboard or etc. that's going to keep messing with you as long as you're trying to use the sick PC.  If it's an old XP PC, you probably want to take the side case off and look for [bad capacitors]("http://en.wikipedia.org/wiki/Capacitor_plague") anyway.

---

