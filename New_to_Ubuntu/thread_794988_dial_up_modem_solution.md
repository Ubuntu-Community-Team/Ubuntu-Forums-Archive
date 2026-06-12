---
title: "dial up modem solution"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by paulgill on 2008-05-15
i tried 20 odd linux programs but was unable to connect to net using a dial up modem. i also tried 5 different modems. ubuntu kubuntu and edubuntu were among those programs that i tried. i know nothing much about linux, even when i could download linux drivers for zoltrix hsf micromodem with pctel phantom chipset from their site, i had no idea how to install them. 

finally after strugling with linux for a while, i tried puppy 2.17 and it works right out of the box with zoltrix micromodem with pctel phantom chipset, flawlessly. neither i knew how, nor i needed to install any drivers for it'

puppy 4.0 and puppy 2.17.1 support many more modems anyone in my situation can use one of these puppy programs to get on the net using dial up modems.

i wonder why there is only one program out there for millions upon millions who have excess only to dial up network.

---

### Post by ZabiGG on 2008-05-15
I'm no expert, but there's this HOW-to ;)

It's a bit dated, but it might help.

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Cheers
:)

---

### Post by Jawihan on 2008-06-20
Hello,
I am a newbie. After losing my Windows xp operating system a week ago, I decided to try Ubuntu 8.04. I have now spent a week trying to get modem recognition. Complete frustration!!!!. I downloaded and ran ScanModem: 1st. with USR winModem---appears to not be supported (not sure though, due to technical talk which I don't understand). 2nd. swapped modem with PCtel HSP MicroModem 56, ran ScanModem again(maybe supported this time). Tried the above link to set up modem and the further I read into that the more complicated it seems to get. It talks about using different "kernels" etc.!!!!. Now, I realize that I am severely lacking in the technical aspect of working on computers, I have used the Windows operating systems for many years, but never have I had any difficulty in something so basic as getting a modem to work. I need help please to set up internet access via dialup modem. Currently, I have to borrow a friend's computer to use the internet.
Thanks (not sure if this request for help should be posted here)
James

---

### Post by wpshooter on 2008-06-20
Have you tried calling your local resident Linux expert at the ISP that you have your dial-up account thru ?

That is what I am going to be doing for my sister's Ubuntu computer shortly.  The ISP assured me that they could get Ubuntu to work and connect using her dial-up modem.

Good luck.

---

### Post by phidia on 2008-06-20
More people have moved to broadband so dial up doesn't receive as much focus as it once did. That doesn't help those who still use narrowband though. 
I used dial up for years with linux and found that external serial modems are your best bet. Most usb modems are winmodems too so they're not worth the bother. The issue with these controlerless modems is that they were designed to work with the windows OS. That is it was a cost saving move to let windows take over some of the hardware function. Many winmodems can be made to work but it takes work and time plus if you update the linux distro you're using it could effect the modem driver.
Having said all that the ubuntu community docs (wiki) have a [modem howto]("https://help.ubuntu.com/community/DialupModemHowto"). 
Try that and while it may go over somethings you've already tried-what's useful about the ubuntu howto is that it's all in one place so you can go back to it rather then hunting all around. Hope that's helpful.

---

### Post by Jawihan on 2008-06-20
Thanks for the speedy responses. My ISP offers no assistance with Linux setups. I have visited the "forum how to set up modem" section and I don't understand such things as changing kernals etc. A lot of the other commands mentioned are beyond my scope of understanding. I also searched online retailers here for an external serial modem compatable to Linux systems eg. Tiger Direct.ca. Several modems shown do not indicate Linux use.
Thank you for your time
James

---

### Post by phidia on 2008-06-20
I have no affliation with this seller but they have an external modem listed [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002") which some reviewers claim is recognized with ubuntu. I also have no experiance with the brand Trendnet, but it might be worth looking at.

---

### Post by hopelessone on 2008-06-20
You should know not all modems are "true" modems..there are WinModems...in which half the modem components are missing..and the proprietary system does all the work so some might not work in linux at all..

---

### Post by editrix on 2008-06-21
Just a note regarding the kernel issue:

The easiest way to understand that (but please don't take this as a precise answer!) is to think of how, when people went from Win98 to XP, a lot of their hardware no longer worked. Same for XP to Vista. The kernel is the "core" of Linux, but some hardwre drivers are not built into it--like hardware drivers that existed in Win98 weren't in XP.

But the good news is, unlike Windows, if it ever existed in Linux, you can get it back--although the pain of learning how to may not be worth it.

---

