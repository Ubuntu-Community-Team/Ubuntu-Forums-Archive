---
title: "hardware drivers"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by deezdrama on 2012-10-17
Just installed ubuntu on my old acer aspire 5515 laptop for testdriving my first shackel free OS.

sofar so good....looks promising, but running really reaally sluggish compared to windows, its a fresh install and assuming i need drivers.

I go to system settings>hardware>addition driver..... it does a search then says "no proprietary drivers are in use on this system"

any ideas on where to go from here?

On windows I would just get on the net and DL my drivers, is it the same process here or....??

thanks

---

### Post by Sylos on 2012-10-17
Hello there and welcome to the party!

Most hardware drivers are contained in the Linux kernel as modules, so the downloading of such things is not usually required (some hardware is an exception to this rule of thumb).

Can you give some specs info regarding the hardware and what things you may want to install drivers for?

Cheers

---

### Post by deezdrama on 2012-10-17
hmmm.... the systems running really laggy, even typing it takes a second or two for the characters to show up, same laggyness opening folders or anything.

Figured i was in need of a graphics driver since it acts like how windows does on a fresh install with no graphics driver, but guess not :confused:

also no sound

---

### Post by philinux on 2012-10-17
> **deezdrama said:**
> hmmm.... the systems running really laggy, even typing it takes a second or two for the characters to show up, same laggyness opening folders or anything.

Figured i was in need of a graphics driver since it acts like how windows does on a fresh install with no graphics driver, but guess not :confused:

also no sound

Can you post the full system specs and the version of ubuntu you installed.

Also is this a full install to internal hard disk? Or is it a Wubi install in windows or other?

---

### Post by Sylos on 2012-10-17
Well we cant be sure of what (if any) drivers or optimization that you may need without knowing what the hardware specs are. If you have old hardware then it could just be a general struggle to run up to date desktop environements etc. There is normally a way of speeding up (changing DE etc) but its best to rule out a bug or other issue first.

Post up some specs and we will see what can be done.

As for the sound (annoyingly) its normally just default that it starts up with the sound muted. Try unmuting it from your sound icon and if that doesnt work open up a terminal and type "alsamixer" and see if anything needs unmuting/turning up from there. If in doubt post a screenshot.

Cheers

---

### Post by Jimmyfj on 2012-10-17
Seems like you made the classic error of installing the latest release of Ubuntu. If you install Ubuntu on an old computer you need a system that's just as old. Ubuntu 12.04 wont run perfectly on a ten year old hardware.

If at all possible you need to get hold on some older versions of Ubuntu.

---

### Post by Mark Phelps on 2012-10-17
According to my Google search, that laptop is using an ATI X1200 video chipset -- and ATI dropped Linux driver support for that chipset years ago.  

Ubuntu installed the default Radeon drivers for that chipset -- which are the best available now.

---

### Post by Mopar1973Man on 2012-10-17
> **Jimmyfj said:**
> Seems like you made the classic error of installing the latest release of Ubuntu. If you install Ubuntu on an old computer you need a system that's just as old. Ubuntu 12.04 wont run perfectly on a ten year old hardware.

If at all possible you need to get hold on some older versions of Ubuntu.

Being I'm also in the this boat could you supply links to said older version of Ubuntu? (Please?)

---

### Post by philinux on 2012-10-17
> **Mopar1973Man said:**
> Being I'm also in the this boat could you supply links to said older version of Ubuntu? (Please?)

Please start a new thread stating your problem and your system specs. Thanks.

---

### Post by Mark Phelps on 2012-10-17
> **Mopar1973Man said:**
> Being I'm also in the this boat could you supply links to said older version of Ubuntu? (Please?)

If you have the same ATI video chipset as the original poster, there is really nothing useful you can do.  ATI (now AMD) dropped Linux driver support for that chipset back when Ubuntu 9.04 came out -- three years ago!  That Ubuntu version has expired and has not been supported for some time.

---

