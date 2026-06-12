---
title: "Do not install 16 if using Radeon card"
date: 2016-08-15
forum: Recurring Discussions
---

### Post by realpariah2 on 2016-08-15
I can't believe this! I should have known though. I go to upgrade from 14lts to 16lts right. Well good ol Ubuntu made an arbitrary decision to just entirely throw out fglrx support (they'll give some reason which only makes half sense about security or performance I'm sure). 

Well it's really hard to dig up the info but Ubuntu has gone with the experimental amdgpu driver (like brand new drivers don't have issues).

My issue with this is you could have built some sort of backward compatibility to enable a huge number of video cards which can now no longer use Ubuntu.

My bigger issue, if you call something lts to me that means a long time not until we feel like it. At the absolute least your upgrade script should check for basic compatibility of hardware and warn someone before they lose an entire OS install (you try downgrading it'll never work).

You wonder why you're having trouble breaking Microsoft's strangle hold on the residential market you're gonna have to think more about your end users wants and needs and less about your and your vendor wants and whims.

---

### Post by wildmanne39 on 2016-08-15
*Thread moved to **Recurring Discussions**.*

For the record they are working on the driver you need it should be ready soon hopefully.

I am using 16.04 with the same card and it is working good but I have not tried to enable desktop affects or anything like that.

---

### Post by QIII on 2016-08-15
> **realpariah2 said:**
> Ubuntu made an arbitrary decision to just entirely throw out fglrx support ...

No, actually.  Ubuntu is an operating system and makes no decisions.  But Canonical, the distributor of Ubuntu, made no such choice either.

Short version:  AMD did not want to make fglrx compatible with the version of X Server used by 16.04 because they are working on their new generation of open source driver -- which the open source community has been asking for for years.  That driver, AMDGPU, is the basis for the proprietary driver, AMDGPU Pro.  Notice what I just said:  AMD's new driver will be based  on an open source driver.

Unfortunately, that driver will not work with some older hardware that does not support newer technology.  So AMD is also improving the open source Radeon driver.  There is even the possibility that they will come out with a version of fglrx that will work going forward.

Nice article [here]("http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1").

I am using AMDGPU right now, and its performance is *better* than fglrx.  Of course, I also have a card that supports AMDGPU.  But I tested the current version of Radeon on another machine with an older card not supported by AMDGPU and it worked very well.  AMDGPU is not experimental.  It's here.  AMDGPU Pro is still under development.

So, let's not jump to conclusions and spread FUD, OK?  Does this suck right now?  Absolutely -- if you don't have a card that will run with AMDGPU.  Will it always be thus?  No.  This is a temporary situation because AMD is busting a hump getting what the open source community has been demanding:  a truly capable open source driver.

By the way, "we" aren't trying to break Microsoft's strangle hold.  Neither are any of the distributors of Linux desktop distributions.  "We" are users just like you. 

Well, except for the fact that we don't drive-by Windows forums and spread FUD.

---

