---
title: "Screen Resolution Problem"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Febri Ichsan on 2012-07-05
Greetings.

Well since this is my first time using ubuntu, I face so many problems just trying to get used to it.
But the main problem is about screen resolution problem.
When I start an apps, like hedgehog wars, my screen seems to be not big enough for the apps, I can't see the bottom screen at all (i dunno whether it is  'cancel', 'apply', or 'okay' button.
This problem occurs in some apps too.

Sorry for my bad English.
Thanks.

---

### Post by QIII on 2012-07-05
Can you give us some information about your system hardware, drivers you are using, etc?

---

### Post by Febri Ichsan on 2012-07-05
I'm using Asus Eee PC P1015B with AMD Radeon 6310 HD Graphic.
I download the driver automatically using 'additional drivers menu' in system setting.
Should I deactivate my additional driver?

---

### Post by codingman on 2012-07-05
AMD has a big record for these sorts of failures, so therefore this is not a surprise to me. Disable the extra drivers and manually install them from the AMD website.

---

### Post by QIII on 2012-07-05
AMD has no worse a record than NVIDIA  for this sort of thing.

The driver from the repo IS a driver from AMD.  Installing from AMDs website is more difficult and entirely unnecessary in Ubuntu.

---

### Post by QIII on 2012-07-05
@Febri Ichsan

What have you done to attempt to adjust your resolution?

Which driver did you install?  The basic one or the -updates version?

---

### Post by codingman on 2012-07-05
> **QIII said:**
> AMD has no worse a record than NVIDIA  for this sort of thing.

The driver from the repo IS a driver from AMD.  Installing from AMDs website is more difficult and entirely unnecessary in Ubuntu.

Doing it from the AMD site is worth a shot. nVidia has had a better record in drivers in general than AMD. An HP Envy with high spec AMD graphics proves more graphically faulty than an HP with a high spec nVidia.

---

### Post by Febri Ichsan on 2012-07-05
lemme check amd site.
well actually there are two choices when I check additional driver. a post-release and bla bla bla.
here's the screenshot

should i deactivate it and check amd site for drivers?

---

### Post by QIII on 2012-07-05
> **codingman said:**
> Doing it from the AMD site is worth a shot. nVidia has had a better record in drivers in general than AMD. An HP Envy with high spec AMD graphics proves more graphically faulty than an HP with a high spec nVidia.

That bit of FUD dies hard.  The differences are marginal, with each OEM's card doing some things better than the other's.

Both NVIDIA and AMD/ATI make good products and I use both.

One computer OEM's particular model is not a large enough experimental population to draw conclusions from.  Furthermore, integrated graphics are much more affected by the design and function of the motherboard.

That may be a factor here.

AMD/ATI botched the launch of the HD 7xxx series and the Linux driver did not work.  NVIDIA, for their part, recently produced an updated driver that borked many systems, sending users scurrying to downgrade to the previous version.  If you look through the forums, you will find a lot of people having problems with NVIDIA, too.

Both make good products.  Neither makes perfect products.

---

### Post by QIII on 2012-07-05
@Febri Ichsan

The -updates version causes problems for some users, as does installation using the graphical Additional Drivers method.  There is no need to go the more difficult route of installing the driver from source from the AMD/ATI site.  The driver in the repo IS AN OFFICIAL AMD/ATi driver.

See the ATI driver wiki in my signature.

Find the section entitled "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)".

---

### Post by NikTh on 2012-07-05
@[Febri Ichsan]("http://ubuntuforums.org/member.php?u=1694440") why you installed restricted (additional) drivers ? had any problem (or problems) with open source (radeon) that are pre-installed in Ubuntu ?

---

### Post by Febri Ichsan on 2012-07-05
If that's the case, should I deactivate my driver first before I use ur methods using repositories?
well for your information, my Ubuntu is quite laggy compared to my friend's netbook even though he has a lower spec with intel gma graphics.

---

### Post by Febri Ichsan on 2012-07-05
@NikTh:
how do I check whether it is pre-installed or not?
well, since i'm such a noob in ubuntu, the first thing comes in my mind when I use ubuntu is updating and installing every possible driver and package without even checkin whether it is pre-installed or not.

---

### Post by NikTh on 2012-07-06
> **Febri Ichsan said:**
> @NikTh:
how do I check whether it is pre-installed or not?
well, since i'm such a noob in ubuntu, the first thing comes in my mind when I use ubuntu is updating and installing every possible driver and package without even checkin whether it is pre-installed or not.

Yes you have right. I don't blame you .. no.. no... this notification.. "additional drivers available..." its confusing for new users . 

Ubuntu comes with open source drivers available.. pre-installed. Radeon for Ati and nouveau for Nvidia . (intel has only open source drivers for linux.. no additional no restricted) .. so..
..if open source driver works correct there is no need to entangle with additional drivers installation..

I suggest you to purge (deactivate) any additional driver you installed , for graphics 
and see how your system works. If its ok , then leave it with open source.. 
if you see lag or graphics performance is poor then you can activate again restricted (additional) drivers.

---

