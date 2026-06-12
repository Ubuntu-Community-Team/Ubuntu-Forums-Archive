---
title: "Boot Repair Disc options"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by sewbiz on 2014-08-03
I am trying to install boot repair disc. I have Ubuntu 12.04.4LTS installed but need to fix Grub on my desktop.
My computer is in grub rescue mode as my boot volume disc was 100% full. I stupidly deleted files in grub.

The boot repair disc now installed shows the first colorful screen with the title Boot-Repair-Disk
at the top, now asks me for options:

lubuntu
LX Games
Lubuntu Netbook
Lubuntu Nexus 7 session
Openbox

It asks for my password but when I type it in it says it is incorrect.
Did I BURN the wrong Boot-Repair-Disk to dvd?
I burned...Boot-Repair-Disc-64bit.

Am I going about this wrong? Any help is appreciated. Speak simply to me though as I
am not tech smart.

---

### Post by sudodus on 2014-08-03
Select Lubuntu

Do not type any password (if running from CD/DVD/USB), only press the Enter key (I think).

If this does not work, please explain what happens.

---

### Post by sewbiz on 2014-08-03
I installed boot-repair disc onto a dvd.  (Burned it)

When the boot repair opens on my computer that is broken...it says "BOOT REPAIR DISC" on the
title, "upper left corner" and then it has options in a text box (the sign in section in the middle
of the screen).

Lubuntu
Password:
4other options....etc.

Why does it say "Lubuntu"not simply  "Ubuntu"?
Also...big problem....it does not recognize my password.
I am confused. Help appreciated.

---

### Post by oldfred on 2014-08-03
If it is the live installer or Boot-Repair based on the live installer, then it does not have a password.

Some Linux installs have a default password for a live installer, but Ubuntu does not.

Only after you have installed Ubuntu on your system and have created a user & password, do you have a password to boot the installed system.

Boot-Repairs own LiveCD is based on Lubuntu to allow it to fit on CD. Full Ubuntu now requires DVD or flash drive as it is too large for standard CD.

---

### Post by sewbiz on 2014-08-06
> **sudodus said:**
> Select Lubuntu

Do not type any password (if running from CD/DVD/USB), only press the Enter key (I think).

If this does not work, please explain what happens.

I tried just enter and nothing happened. 
Still think my system is a GRUB issue...I have a Full boot volume disc. ...got to chroot I THINK but
I am an idiot when it comes to these things.

---

### Post by sewbiz on 2014-08-06
> **oldfred said:**
> If it is the live installer or Boot-Repair based on the live installer, then it does not have a password.

Some Linux installs have a default password for a live installer, but Ubuntu does not.

Only after you have installed Ubuntu on your system and have created a user & password, do you have a password to boot the installed system.

Boot-Repairs own LiveCD is based on Lubuntu to allow it to fit on CD. Full Ubuntu now requires DVD or flash drive as it is too large for standard CD.

I just can't get past the screen on the boot repair disc that has you log in.

---

### Post by oldfred on 2014-08-06
I just booted my copy of Boot-Repair 64 bit based on Lubuntu.

I do get a Lubuntu@Lbuntu text for a few seconds but then it automatically goes to the screen with the background image of the sun & person leaping on right. In the middle it says scanning system and it takes a while and then comes up with the Boot-Info screen you see in the links. Auto fix or report or advanced options.

Have you tried not immediately logging in and just let it boot?

Since you have Internet can you boot 12.04 to the gui screen with icons, not just a text login?

---

### Post by yancek on 2014-08-06
The link below in the first post shows what you should see after the Boot Repair CD/DVD has booted. There is no login needed.  Go down to post five and you will see the menu  you should see immediately on booting it before you get to the GUI.   Is that what you see?

[http://ubuntuforums.org/showthread.php?t=1831869](http://ubuntuforums.org/showthread.php?t=1831869)

---

### Post by sewbiz on 2014-08-06
> **oldfred said:**
> I just booted my copy of Boot-Repair 64 bit based on Lubuntu.

I do get a Lubuntu@Lbuntu text for a few seconds but then it automatically goes to the screen with the background image of the sun & person leaping on right. In the middle it says scanning system and it takes a while and then comes up with the Boot-Info screen you see in the links. Auto fix or report or advanced options.

Have you tried not immediately logging in and just let it boot?

Since you have Internet can you boot 12.04 to the gui screen with icons, not just a text login?

No...I never let it just boot....I type in the log in screen right away. I will try this but the screen you describe
is what I get with the background image. Thanks....helpful. : )

---

### Post by sewbiz on 2014-08-06
> **yancek said:**
> The link below in the first post shows what you should see after the Boot Repair CD/DVD has booted. There is no login needed.  Go down to post five and you will see the menu  you should see immediately on booting it before you get to the GUI.   Is that what you see?

[http://ubuntuforums.org/showthread.php?t=1831869](http://ubuntuforums.org/showthread.php?t=1831869)

I never get to the screen that shows the wrench and screwdriver either. I have the background image of the sun
and the figure leaping in mid air but in the middle of the screed is a text box. In the center is the title Lubuntu
then it says in a selection box with a dropdown menu "other"....then when I look to see my selection there are
none to be made but immediately the box opens futher down. I then see....login on a line by itself (as if that
is where you put your login information.....and under that to the left
Lubuntu (or you can make other selections)
Lubuntu Netbook
LX Games
Lubuntu Nexus7 session
Openbox

In the middle...on the same line is another selection box and it says 'English'.....next to it a box that says 'Cancel' and finally 'Login'

I have waited now for the duration of getting this message to you and nothing on my screen has changed.
Did I not burn the right Boot Repair disc?

Confused. Thank you for your help.

---

### Post by oldfred on 2014-08-06
Is this what you downloaded and created a live disk for?

[http://sourceforge.net/projects/boot-repair-cd/?source=recommended](http://sourceforge.net/projects/boot-repair-cd/?source=recommended)

And green button gives you this:
boot-repair-disk-64bit.iso

---

### Post by sewbiz on 2014-08-07
> **oldfred said:**
> Is this what you downloaded and created a live disk for?

[http://sourceforge.net/projects/boot-repair-cd/?source=recommended](http://sourceforge.net/projects/boot-repair-cd/?source=recommended)

And green button gives you this:
boot-repair-disk-64bit.iso

Yes, that is what I downloaded....my file in my download folder says the same name but
only 520,076 KB   not 532,6MB like the .iso file from sourceforge.net has on their page.
I am downloading again and will burn at some point tomorrow.

Son is coming home so maybe he can help me find a fix. I was hoping I would be
in the clear by now and not have to bother him on vacation. He's a geek though and
may look forward to helping mom.

Thank you for your help. I will let you know if I find a solution for the betterment of this forum,
the Linux community in general, and my very long threads.

---

### Post by sewbiz on 2014-08-07
> **oldfred said:**
> I just booted my copy of Boot-Repair 64 bit based on Lubuntu.

I do get a Lubuntu@Lbuntu text for a few seconds but then it automatically goes to the screen with the background image of the sun & person leaping on right. In the middle it says scanning system and it takes a while and then comes up with the Boot-Info screen you see in the links. Auto fix or report or advanced options.

I never get to see it even say...."scanning system"...it just sits there and does nothing.

> **oldfred said:**
> Have you tried not immediately logging in and just let it boot?

I did this and get nothing....no change...nothing happens. Something is broken...bet it has a heck of a lot to do with GRUB...but that is what this disc is suppose to fix
or should I get Grub 2 disc and install it?


> **oldfred said:**
> 
Since you have Internet can you boot 12.04 to the gui screen with icons, not just a text login?

I can get to gui screen if my live disc is in. Any time I have a live dvd in....I can do a lot of things....otherwise I only have a black text screen on my computer and it says 'grub rescue'.
I think my problem will beat any Guiness Book of Records holder, as the longest unsolved computer user's problem.

---

### Post by sewbiz on 2014-08-25
[INDENT] 					My son built my computer. After weeks and weeks of trying to figure  out why anything anyone told me of steps to take did not work, I found  out why.
My home built computer had two hard drives but the one that I thought  had the issues, was not the correct drive. Usually the A drive has all  your system
files on it and the B dirve is your back-up. Mine was reversed for some  reason. In another thread and another post, one person mentioned which  drive
my files were on but it didn't connect with me what that had to do with anything, being new and not of full understanding.

STEP ONE.......know which hard drive the files are on that you want to fix. 
Because I now have all my files restored but on my A drive and newly  installed Ubuntu 14.04-Trusty Tar, with the help of my son making sure  the
partitions on the disc were set up correctly, I am now back up and  running. I will mark this as solved and most of what all my good friends  here
suggested should have "worked" for me but did not because only my hard  drives were not set up initially in a typically set up order.

Thank you...I love being a Linux user!

THIS IS SOLVED but not finding where I am suppose to "add" that. 				[/INDENT]

---

### Post by oldfred on 2014-08-25
Glad you got it working.

---

