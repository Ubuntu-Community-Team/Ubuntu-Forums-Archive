---
title: "Installation of VLC 1.2.0 at Linaro distribution"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by gtamorim on 2012-02-14
Hello guys -

I know it may sound a ridiculous newbie question - well, it is indeed - but I have been struggling with this for the last two weeks with no success.

I'm using Linaro 12.01 installed on a iMX53 board.

I added the PPA for the nightlies builds (ppa:videolan/master-daily) but I can't get it to update my current version of VLC. No matter what I do, I only get "The Luggage" version 1.1.12. I'm current running a application that needs a newer version - at least the 1.2.0 which is not released yet, but I need to test it.

I've also tried the git version with no luck.

Does anyone have any hints?

---

### Post by cavh on 2012-02-14
Are you sure the PPA contains the version you need?

---

### Post by spcwingo on 2012-02-14
I think the reason you're not able to install is your architecture is not included in the PPA (You're using an ARM based system, correct?).

---

### Post by gtamorim on 2012-02-14
I'm sure the PPA contains the version I need. In fact, I was able to install the VLC 1.2.0 using a "normal" Ubuntu distribution (sorry for the newbie terms). I followed this FAQ ([http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)) which is quite well explained. I tried that after having problems with the Linaro. So right now I don't if I should go for a brand new Linaro installation and try to to reinstall or if it's another issue.

The problem is whenever I try to update or upgrade the version of the VLC package it won't go to 1.2.0. 

Yes, I'm using the iMX53 ([http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=IMX53QSB](http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=IMX53QSB)) which it does have an ARM architecture.  Is there any workaround in case that's the case?

---

### Post by spcwingo on 2012-02-14
> **gtamorim said:**
> Is there any workaround in case that's the case?

You'll probably have to grab the code and build it yourself as all of the PPAs that I have ever seen include only x86 and/or x86-64 binaries.

---

