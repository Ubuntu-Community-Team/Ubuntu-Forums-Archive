---
title: "Driver question"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by phunqe on 2008-07-25
Hi,

I'm about to install Ubuntu onto a HTPC that I'm building.
Even if I use linux on a daily basis, the last time I installed an X system was like 10 years ago (which needless to say required both patience and a sturdy blood pressure to get all the latest gfx cards to work).

In any case, I have bought an Asus P5E-VM SE Card with the Intel G35 chipset (X3500 graphics). My question is here how the drivers for the motherboard will work when I install the latest Ubuntu version. From what I can read, the chipset and other components are supported, but what about the versions of the drivers? How do I make sure I always have the latest versions installed?
As I said, back in the days I did everything manually, so I'm wondering what I need to do if I install Ubuntu. Does it offer automatic updates (i.e through the package manager) of these drivers or do I still have to download drivers manually etc.
I'm aware of that you can manage most updates through package managers, but since driver updates (as opposed to software updates) tend to be a different beast I thought I'd ask.

Thanks in advance.

Cheers.

---

### Post by Bachstelze on 2008-07-25
> **phunqe said:**
> 

As I said, back in the days I did everything manually, so I'm wondering what I need to do if I install Ubuntu. Does it offer automatic updates (i.e through the package manager) of these drivers

No. When you'll install Ubuntu, you will get the driver version that ships with it, and it won't get updated until the next Ubuntu release (unless a major bug or securiy flaw is discovered).

It does not matter much, however, since driver updates are much less important nowadays than they were ten years ago. You can just stick with the driver shipped with your Ubuntu version, and you will be just fine.

---

### Post by bobnutfield on 2008-07-25
Hello,

If you have confirmed that your video chipset is supported, then you can feel comfortable it will be supported with both open source and proprietory drivers.  Once you have installed Ubuntu, you will be able to find proprietory drivers for your card with the operating system itself.  While it does not come with Ubuntu (for legal reasons, closed source drivers are not included with Ubuntu), you can go to System>HardwareDrivers and you will be offered the opportunity to install these drivers.

There is also a GUI based application called EnvyNG which will identify and install the correct driver for your video setup.    Also, updates will be provided through the normal automatic update process in Ubuntu once the drivers are installed.  When updates are available, you are notified via an icon on the desktop panel.

Hope this helps

Bob

---

### Post by Bachstelze on 2008-07-25
> **bobnutfield said:**
> Hello,

If you have confirmed that your video chipset is supported, then you can feel comfortable it will be supported with both open source and proprietory drivers.  Once you have installed Ubuntu, you will be able to find proprietory drivers for your card with the operating system itself.  While it does not come with Ubuntu (for legal reasons, closed source drivers are not included with Ubuntu), you can go to System>HardwareDrivers and you will be offered the opportunity to install these drivers.

There is also a GUI based application called EnvyNG which will identify and install the correct driver for your video setup.    Also, updates will be provided through the normal automatic update process in Ubuntu once the drivers are installed.  When updates are available, you are notified via an icon on the desktop panel.

Hope this helps

Bob

Please. He's saying he has an Intel chipset. There is no need for proprietary drivers, or Envy, or whatever! Envy is only for nvidia or ATi card, for Heaven's sake, can you read?

Please refrain from posting when you don't know what you're talking about.

---

### Post by phunqe on 2008-07-25
Alright, cheers.

Reason I want to make sure I use the latest drivers is because I want to make sure everything is optimized for HD playback (even if not HW accelerated, making sure latest OpenGL is used etc).

Thanks.

EDIT: If I find newer drivers I'll just fiddle with them manually then :)

---

### Post by Bachstelze on 2008-07-25
> **phunqe said:**
> Reason I want to make sure I use the latest drivers is because I want to make sure everything is optimized for HD playback (even if not HW accelerated, making sure latest OpenGL is used etc).

With one release every six months, your drivers will never be more than six months late. You really shouldn't worry about that.

---

### Post by phunqe on 2008-07-25
Yeah I probably won't, just that I know from previous experience that I tend to be a bit anal about drivers ;)

But as you said, I'll probably be fine. I'll try running everything before I start to fiddle with anything manually in any case.

---

### Post by bobnutfield on 2008-07-25
Please. He's saying he has an Intel chipset. There is no need for proprietary drivers, or Envy, or whatever! Envy is only for nvidia or ATi card, for Heaven's sake, can you read?

Please refrain from posting when you don't know what you're talking about.


OK, I did not look up the chipset before replying, and for that I apologize if I gave incorrect information.  However, I am thankful for my own attitude and desire to attempt to help.  Your response to seems to reveal a really uptight attitude and certainly bad for the spirit of Ubuntu in trying to help newcomers, especially for FORUM STAFF.  As far as not knowing what I am talking about, your sour attitude is not going to deter me from trying help if I can, even if I may get it wrong on occassion.  Of course, if you are in fact the ALL-KNOWING LINUX GURU, then my comments are not with-standing.  If you youself are not correct 100% of the time, please keep comments like that to yourself.

Bob

---

### Post by tjajab on 2008-07-25
I, too, got confused by the rude tone of the Forum staff member entry. Let's call it of as a bad day mistake, or maybe a hacked account.

As you said, we all makes mistakes.

However, my respond to the original question would be just to try it out, and if, which hopefully will be the case, everything runs as it should, then do not worry about drivers. Otherwise, check the forum for specific questions about your chipsets.

Best regards,
Andreas

---

### Post by phunqe on 2008-07-25
So my first ever thread here managed to turn into a bbq :P

---

### Post by bobnutfield on 2008-07-25
> **phunqe said:**
> So my first ever thread here managed to turn into a bbq :P

No, this type of exchange is not the usual fare.  I did give the wrong information for your video chipset and I am sorry I did not look it up first before posting.  You WILL get a tremendous amount of help here, and most of us want to do just that, HELP.  But, as you have seen, sometimes someone will post too quickly to give you the complete information you need, so SELF-STUDY is your best tool.  It was for me, and when I got really stuck, I always found the people here very helpful.

If you stick with it, I am sure you will be very glad you chose Linux and Ubuntu.

Bob

---

