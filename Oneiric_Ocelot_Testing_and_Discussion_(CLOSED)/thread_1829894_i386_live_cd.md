---
title: "i386 live cd"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-08-20
I have just downloaded 2 times the i386 build from yesterday it starts to boot on my computer,it goes through the udev screen message that oneiric is doing at the moment then just goes to a black screen and stops. i have wasted 4 dvds on this as I burnt it with brasero and k3b on 2 different burners why wont it boot into live session

---

### Post by raja.genupula on 2011-08-21
me to had this problem . still i have those two iso's in my system . what ever my interest on testing wasnt lost , so i have given a try for xubuntu aplha 2 . its working good . so i can say certainly that xubuntu alpha2 dont have any problem .

if you   wanna go with ubuntu then first run that iso with virtual box , if it is working good then go to burning .

all the best .:D

---

### Post by cariboo on 2011-08-21
Just out of curiosity, did either of you try the nomodeset option, that can be set by pressing F6 a the initial boot screen?

---

### Post by shuttleworthwannabe on 2011-08-21
> **rbrick49 said:**
> I have just downloaded 2 times the i386 build from yesterday it starts to boot on my computer,it goes through the udev screen message that oneiric is doing at the moment then just goes to a black screen and stops. i have wasted 4 dvds on this as I burnt it with brasero and k3b on 2 different burners why wont it boot into live session

Why not install it using a USB? [Look at [this]("http://ubuntuforums.org/showpost.php?p=10976640&postcount=4") post]
Also try gnomebaker to burn at slow speeds. Or windows if you have this. This happened to me a while back, so i can feel what you must be going through.

---

### Post by mc4man on 2011-08-21
Using the nomodeset option as mentioned was the only way I could get today's build to  boot up to either run or install from.
(1st time ever needing this with nvidia in any ubuntu release, dev or otherwise

---

### Post by rbrick49 on 2011-08-21
thank you folks that worked never needed it before so didnt know about that trick thanks
regards ron

---

### Post by raja.genupula on 2011-08-21
> **cariboo907 said:**
> Just out of curiosity, did either of you try the nomodeset option, that can be set by pressing F6 a the initial boot screen?


i have taken the iso from the xubuntu site . created a usb startup disk . trying to installed the both iso's of 11.10 but not worked . i have not tried any thing as you said . you must advice for the persons who are involving in testing as first time . 

thanks for your suggestion,   i am gonna try it .

---

### Post by cariboo on 2011-08-21
I've always had to use the nomodeset option with the nvidia 62XX chipsets. Two of my motherboards have 6250 graphics chipsets, although I don't use them, and I just recently got a pci 6250LE for my media center pc powered by an Intel Atom 230.

Actually because of the pci video card, the only version I could install was Natty. :)

---

### Post by jerrylamos on 2011-08-21
Let me see if I have this right.

Used to be, the kernel booted all the way in text TTY mode.  Then when the desktop came up in graphic X windows, there's a delay shifting back and forth from desktop to kernel mode example logout and login.

So part way thru boot, the kernel does a  modeset to graphics mode, unless "nomodeset" option is used. You can tell when "modeset" was issued since the screen fonts are suddenly tiny.

From a user standpoint kernel modeset has meant tons of bugs and dead boots.

These bugs are still with us.  The idea is to have Ubuntu increased market penetration, I'm not at all sure how with secrets like F6 boot.

Jerry

---

### Post by cariboo on 2011-08-21
Boot options have always been with us. They are easily discoverable, but saying that, it really shouldn't be needed for most bog standard graphics chipsets. Over the years I've only needed it when using a system with the nvidia 62XX graphics chipset. I've installed Ubuntu on many different systems, and that was the only time I've ever needed to use nomodeset/safe graphics mode.

---

### Post by rbrick49 on 2011-08-22
ati card is causing the same problem> **cariboo907 said:**
> Boot options have always been with us. They are easily discoverable, but saying that, it really shouldn't be needed for most bog standard graphics chipsets. Over the years I've only needed it when using a system with the nvidia 62XX graphics chipset. I've installed Ubuntu on many different systems, and that was the only time I've ever needed to use nomodeset/safe graphics mode.thanks for your help mate it is really appreciated by me for one looking at your post about nvidia and that pci card I wonder if my ati 6950 card is causing this problem I will remove it later and revert back to onboard graphics card and see what happens with the live cd
regards ron

---

### Post by cariboo on 2011-08-22
Just to clarify, the pci video card I was talking about is pci not pcie. I have an early Intel atom motherboard, that only has one pci slot. The onboard graphics output is vga, which only allows a resolution of 1368X700, I wanted higher resolution, so with a search I found an EVGA 6250LE pci with dvi output. With a dvi to hdmi cable I now get a resolution of 1920X1080 on my Samsung 32" HD LCD TV.

---

### Post by rbrick49 on 2011-08-22
> **cariboo907 said:**
> Just to clarify, the pci video card I was talking about is pci not pcie. I have an early Intel atom motherboard, that only has one pci slot. The onboard graphics output is vga, which only allows a resolution of 1368X700, I wanted higher resolution, so with a search I found an EVGA 6250LE pci with dvi output. With a dvi to hdmi cable I now get a resolution of 1920X1080 on my Samsung 32" HD LCD TV.are ok I understand now I still think this new card is giving me a lot of grief as to testing oneiric will revert back and see what gives

---

### Post by mc4man on 2011-08-22
At least here (w/ a 8400m laptop), the need for the nomodeset option was only for booting up the daily build of this weekend.
After install it was no longer needed

So I see it as an issue, hopefully short term, with the daily

---

### Post by cariboo on 2011-08-22
I only need nomodeset for the live CD, once the system is installed, and running either the nouvea or nvidia-current drivers, it isn't needed anymore.

---

