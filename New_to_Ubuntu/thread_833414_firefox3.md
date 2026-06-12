---
title: "firefox3"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by wfsswmr7285 on 2008-06-18
just upgraded from 7.10 to 8.04 last night and am using the default firefox 3b5. how do you upgrade to the stable release? I tried checking synaptics, but they don't have the new version yet.

---

### Post by philinux on 2008-06-18
> **wfsswmr7285 said:**
> just upgraded from 7.10 to 8.04 last night and am using the default firefox 3b5. how do you upgrade to the stable release? I tried checking synaptics, but they don't have the new version yet.

It will appear in an update in a few days. There's nothing wrong with version you're running.

You should have the Release Candidate at the moment

---

### Post by robert.cooper on 2008-06-18
actually, you can get a bunch of updates now if you add the medibuntu repository:
sudo apt-get install gui-apt-key
apps>system Tools
add the key for medibuntu
0C5A2783
and add the url in synaptic>settings>repositories>thirdparty
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free
reload and mark updates.. good luck!

i imagine that a bunch of other repositories are updated as well, i happened to add the medibuntu one as instructed for dvd playback capability thread (am still in want of solution :/ )

---

### Post by Exsecrabilus on 2008-06-18
> **philinux said:**
> It will appear in an update in a few days. There's nothing wrong with version you're running.

You should have the Release Candidate at the moment
In a few days? I upgraded to the final release 30 minutes after it was released at [http://mozilla.com/](http://mozilla.com/) !

---

### Post by Sef on 2008-06-18
> In a few days? I upgraded to the final release 30 minutes after it was released.... 

A few days is ok.  Not everyone desires to compile.  It is not the easiest thing to do.  A few days wait and it will be installed with absolutely no hassle.

---

### Post by Exsecrabilus on 2008-06-19
> **Sef said:**
> A few days is ok.  Not everyone desires to compile.  It is not the easiest thing to do.  A few days wait and it will be installed with absolutely no hassle.
I didn't compile. I updated via **Update Manager** through *hardy-updates*.

---

### Post by MemoryDump on 2008-06-19
> **Exsecrabilus said:**
> I didn't compile. I updated via **Update Manager** through *hardy-updates*.

odd that it hasn't showed up for me yet :(

---

### Post by Doby on 2008-06-19
is there going to be a release for gutsy or should I upgrade to hardy?

---

### Post by Exsecrabilus on 2008-06-19
> **Doby said:**
> is there going to be a release for gutsy or should I upgrade to hardy?
There's probably not going to be, but IDK.

The way Ubuntu works with releases is it doesn't update packages if a new whole number version comes out.

For example:

A package is at version 4.8.5.
A new version called 4.8.5.1 will make it into the repos, because it is only a security update.
But let's say a new version 5.0.0 is released. This package update will be held off until the next release of Ubuntu, to prevent bugs, and to encourage users to upgrade.

---

### Post by Joeb454 on 2008-06-19
Actually you might find that Firefox 3 will make it into gutsy-backports :)

---

### Post by Tom--d on 2008-06-19
I got the Firefox 3 update around 10mins after it was released! 

I was using the Uk servers and I live in the UK. Maybe thats it. 
It was in the Hardy updates. (recommended)

---

### Post by Exsecrabilus on 2008-06-19
> **Tom--d said:**
> I got the Firefox 3 update around 10mins after it was released! 

I was using the Uk servers and I live in the UK. Maybe thats it. 
It was in the Hardy updates. (recommended)
I was using the official server and got it like 30 minutes after its release. :3

---

### Post by NilsE on 2008-06-19
Could one of you who are on the final release post the Gecko date from help/about. 

Just curious to see what the final Gecko date is and if it really indicates the final release.

---

### Post by philinux on 2008-06-19
Here's mine

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008061017 Firefox/3.0

---

### Post by Exsecrabilus on 2008-06-19
> **philinux said:**
> Here's mine

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008061017 Firefox/3.0
Wait, one thing is different.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0

Yours says 2008061017, but mine says 2008061015.

Maybe it's because of the fact that Ubuntu had this update in proposed to test for bugs before releasing on the same day Mozilla did.

---

### Post by NilsE on 2008-06-19
> **philinux said:**
> Here's mine

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008061017 Firefox/3.0
Mine is 2008061015.  I wonder what the difference between 15 and 17 is. The first part seems clear.  

On Windows the Gecko on mine is 2008052906

---

### Post by Exsecrabilus on 2008-06-19
> **NilsE said:**
> Mine is 2008061015.  I wonder what the difference between 15 and 17 is. The first part seems clear.  

On Windows the Gecko on mine is 2008052906
I know right? Mine says 15 too. Maybe because it was released on June 15th? IDK.

---

### Post by NilsE on 2008-06-19
> **Exsecrabilus said:**
> I know right? Mine says 15 too. Maybe because it was released on June 15th? IDK.
Not sure.  I went back into Synaptic and the history shows the last update I installed for FF was on 6/10. That is why I am confused as to how this can be the final.  My guess is that the last RC is actually the final and no changes or new package was needed.

---

