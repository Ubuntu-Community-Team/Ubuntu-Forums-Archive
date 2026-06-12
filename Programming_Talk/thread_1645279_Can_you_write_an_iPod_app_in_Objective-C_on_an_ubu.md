---
title: "Can you write an iPod app in Objective-C on an ubuntu machine or do you need a Mac?"
date: 2010-12-14
forum: Programming Talk
---

### Post by tc101 on 2010-12-14
Can you write an iPod app in Objective-C on an ubuntu machine or do you need a Mac?

If it can be done in ubuntu, any pointers to documentation would be great.

---

### Post by r-senior on 2010-12-14
You can write in Objective-C on Ubuntu but it's not Objective-C 2.0 as used by the iOS devices. You also need the Xcode IDE for deploying signed code to a device and the device simulator for testing. Unless you are talking jailbroken devices, iOS development is pretty much dependent on a Mac with OS X.

This link has some alternate ideas:

[http://www.taranfx.com/how-to-develop-iphone-apps-on-windows](http://www.taranfx.com/how-to-develop-iphone-apps-on-windows)

---

### Post by nvteighen on 2010-12-14
Ugh... even if we had Objective-C 2.0 on GNU/Linux, we'd still lack a decent OpenStep implementation that also had Apple Cocoa extensions. GNUStep and SideStep just don't do the job (The FSF has set GNUStep as one of its highest priority projects... if you're interested and have the skills, there is a place where you can help a lot).

---

### Post by tc101 on 2010-12-14
> GNUStep and SideStep just don't do the job (The FSF has set GNUStep as one of its highest priority projects... if you're interested and have the skills, there is a place where you can help a lot). 

Thanks for the info.  Unfortunately I don't have the skills to help tackle something like this.

---

### Post by akand074 on 2010-12-14
Well if your determined to write an app, write an Android app ;) That is supported in Ubuntu more than any other OS. Haha, just felt the need to throw that out there.

---

