---
title: "Adobe Flash Player"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by arno48 on 2012-04-30
Adobe Flash Player plugin is available in Ubuntu Software Center.
 Do you think it useful to download it?
 In the affirmative, why it was not delivered with Ubuntu 12.04 ?
 Are there other important softwares to be added?
 Thanks

---

### Post by Curtis6767 on 2012-04-30
The version in the Software Center is .233.

The previous version .228 was giving a lot of people problems.

If you're not having problems with your current version, then I would guess you would not have problems with the update. Unfortunately there's only one way to find out.

Check your version here: [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

I did not nor am I currently having any problems with Flash.

---

### Post by arno48 on 2012-04-30
Thank you Curtis. 

There is something I do not understand.
 		I checked at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and they answered that
 I have already installed the version Adobe Flash Player 11.2.202.233 while if I check at my Ubuntu Software Center   Adobe Flash is not marked as already installed.

---

### Post by genterminl on 2012-05-15
The problem seems to be that some recent versions of the flash plugin have been compiled with a setting that uses instructions (sse2) that are not present on some CPUs (such as may AMD Athlon XP).  I haven't yet found a solution that works consistantly, but you can check various other threads for suggestions.

---

### Post by SeijiSensei on 2012-05-15
> **arno48 said:**
> Adobe Flash Player plugin is available in Ubuntu Software Center.
 Do you think it useful to download it?
 In the affirmative, why it was not delivered with Ubuntu 12.04 ?
 Are there other important softwares to be added?
 Thanks

You should always choose to install the packages in the repositories since they have been tested and known to work.  In addition, those packages will be updated automatically when necessary.

Flash plugin is not shipped with Ubuntu because it's proprietary.  Only entirely free software is distributed with Ubuntu releases.  All proprietary software is accessible only via the "partner" repository, as Flash and Skype are, or by installing the version of restricted-extras for your flavor of Ubuntu.

---

