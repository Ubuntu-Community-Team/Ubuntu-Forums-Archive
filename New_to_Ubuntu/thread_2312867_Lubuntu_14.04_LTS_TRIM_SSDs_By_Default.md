---
title: "Lubuntu 14.04 LTS TRIM SSDs By Default ?"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by chu300 on 2016-02-07
Lubuntu 14.04 LTS TRIM SSDs By Default ? and  How to Enable TRIM ?

---

### Post by Dennis N on 2016-02-08
It is enabled by default as a cron.weekly job for Samsung and Intel SSDs. It explains in the file (below) how to run it on all SSD drives.

```
dmn@Zotac:/etc/cron.weekly$ cat fstrim
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all
```

---

### Post by mc4man on 2016-02-08
14.04.x uses a whitelist, the cron script description  is a little outdated, current list is - 
 INTEL, Samsung, OCZ, SanDisk, Patriot

After 14.04 the kernel handles thru a blacklist so only those few blacklisted are excluded. It appears the lts versions of 14.04 do not use the kernel blacklists & so remain on the whitelist even though it can exclude drives that have no issue.

---

### Post by vasa1 on 2016-02-08
> **mc4man said:**
> 14.04.x uses a whitelist, the cron script description  is a little outdated, current list is - 
 INTEL, Samsung, OCZ, SanDisk, Patriot

After 14.04 the kernel handles thru a blacklist so only those few blacklisted are excluded. **It appears the lts versions of 14.04 do not use the kernel blacklists & so remain on the whitelist even though it can exclude drives that have no issue**.
Is it possible that LTS users who have HWE (?) will have access to the blacklist? I don't have HWE and so can't provide that information.

---

### Post by Dennis N on 2016-02-08
> 14.04.x uses a whitelist, the cron script description is a little outdated, current list is -
INTEL, Samsung, OCZ, SanDisk, Patriot


Where is this whitelist located?

The output shown in post #2 comes from Xubuntu 14.04.3. Are any directions given there in the file's comments incorrect?

---

### Post by vasa1 on 2016-02-08
> **Dennis N said:**
> Where is this whitelist located?

The output shown in post #2 comes from Xubuntu 14.04.3. Are any directions given there in the file's comments incorrect?
I see exactly the same output with Lubuntu 14.04.3 LTS. The point being made maybe is that newer versions of *buntu carry the blacklist instead of a whitelist?

---

### Post by Dennis N on 2016-02-08
OK, I checked this out on my Dell laptop with a Crucial SSD. The OS is the same version as used in post 2, Xubuntu 14.04.3, but that computer has a Samsung SSD.

The same cron job is run on the Crucial system, and the fstrim file in cron.weekly is identical to post #2 which leads me to believe there is no check during install as to whether to include the job or not. 

Checking further, fstrim-all is a script that runs fstrim. fstrim-all has conditions to only check certain manufacturers. Crucial is not included. It also checks that hdparm is installed. Correct me if I'm wrong, but this is the 'whitelist' being referred to. There is no text file list you can simply append your SSD maker's name to. I assume fstrim itself won't run on a HDD and silently fail. 

Conclusion: To check my Crucial SSD, I would have to use the --no-model-check option in the cron job file. It is up to me to decide if it is OK to do so!

---

### Post by Dennis N on 2016-02-08
> **vasa1 said:**
> I see exactly the same output with Lubuntu 14.04.3 LTS. The point being made maybe is that newer versions of *buntu carry the blacklist instead of a whitelist?

The blacklist is probably just a mod of the checks in the fstrim-all script so that the conditional becomes an exclude rather than an include (no: see EDIT below). Again, there is no text file that you can simply add a manufacturer to?

The fstrim-all script is at **/sbin/fstrim-all**. fstrim itself is a binary.

EDIT: 15.10 has no fstrim-all. Only fstrim. So the 'blacklist' isn't as described above. The cron job runs **fstrim --all** instead of **fstrim-all**. The option --all seems to be to run it on "all supported file systems". If there is some SSD blacklist the user can access, where is it found?

---

### Post by mc4man on 2016-02-08
> **Dennis N said:**
> Where is this whitelist located?

The output shown in post #2 comes from Xubuntu 14.04.3. Are any directions given there in the file's comments incorrect?

For trusty this was committed - 
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/util-linux/trusty/revision/103/debian/fstrim-all](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/util-linux/trusty/revision/103/debian/fstrim-all)

The kernel commit (as of pitti post on 2014-08-20
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4222](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4222)

---

### Post by Dennis N on 2016-02-08
> **mc4man said:**
> For trusty this was committed - 
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/util-linux/trusty/revision/103/debian/fstrim-all](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/util-linux/trusty/revision/103/debian/fstrim-all)

The kernel commit (as of pitti post on 2014-08-20
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4222](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4222)


Fine. I understand the first, but the kernel commit link is Greek to me, an ordinary user. 
So the 'whitelist' for 14.04 that is mentioned exists as I described in post #7?

You also mention a 'blacklist' in releases after 14.04 in the same post. I would like to see this SSD blacklist and what is on it. Where can I find it? I looked in 15.10 without success. The **fstrim-all** script is gone in 15.10 so nothing to see there anymore.

Just to add, the actual script in 14.04.3 is the updated whitelist version, but the comment in the cron job file was not updated to reflect this.

---

### Post by mc4man on 2016-02-08
> **Dennis N said:**
> Fine. I understand the first, but the kernel commit link is Greek to me, an ordinary user. 
So the 'whitelist' for 14.04 that is mentioned exists as I described in post #7?

You also mention a 'blacklist' in releases after 14.04 in the same post. I would like to see this SSD blacklist and what is on it. Where can I find it? I looked in 15.10 without success. The **fstrim-all** script is gone in 15.10 so nothing to see there anymore.

As I understand it the kernel is blacklisting, the linked commit seems clear in that regard

Here I have a crucial 200mx which I'm sure is fine (shipped fw MU02, upgraded to MU03 after I installed it), I'm not inclined to run fstrim on it. If on 16.04 it runs weekly fine, otherwise I'll just leave the drive alone.

(- the current cron.weekly script in 16.04 is - 
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true

As far as my 14.04.3 install on that ssd, again don't care, maybe if it's volume is mounted the trim will run on it from 16.04. If not doesn't matter (to me

---

### Post by yoshii on 2016-02-08
Where does ext4 lay in all of this?  I thought that trim was implemented at the filesystem/hardware level with ext4?  I don't know much about this, I'm just curious.

---

### Post by Dennis N on 2016-02-08
> **mc4man said:**
> As I understand it the kernel is blacklisting, the linked commit seems clear in that regard

Here I have a crucial 200mx which I'm sure is fine (shipped fw MU02, upgraded to MU03 after I installed it), I'm not inclined to run fstrim on it. If on 16.04 it runs weekly fine, otherwise I'll just leave the drive alone.

(- the current cron.weekly script in 16.04 is - 
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true

As far as my 14.04.3 install on that ssd, again don't care, maybe if it's volume is mounted the trim will run on it from 16.04. If not doesn't matter (to me

> As I understand it the kernel is blacklisting, the linked commit seems clear in that regard

So is there no way to see the blacklisted items on the new releases? Some command? By the way, I think in terms of the common meaning of 'list' - a number of items written consecutively, like my shopping list - in plain text. 

The Crucial only runs 14.04, so no trimming for it unless I use the --no-model-check option (or run it manually). And no trimming has ever been done. Maybe that's the right decision since it is not among the favored few in 14.04. Not trimmed, It has nevertheless been doing fine so far with no noticeable decrease in performance (installed in Oct 2014). If it would be checked on 15.10 I wouldn't know unless the kernel's blacklist were readable. That is why I ask.

---

### Post by bab1 on 2016-02-08
> **Dennis N said:**
> So is there no way to see the blacklisted items on the new releases? Some command? By the way, I think in terms of the common meaning of 'list' - a number of items written consecutively, like my shopping list - in plain text. 

The Crucial only runs 14.04, so no trimming for it unless I use the --no-model-check option (or run it manually). And no trimming has ever been done. Maybe that's the right decision since it is not among the favored few in 14.04. Not trimmed, It has nevertheless been doing fine so far with no noticeable decrease in performance (installed in Oct 2014). If it would be checked on 15.10 I wouldn't know unless the kernel's blacklist were readable. That is why I ask.

You can use fstrim as a cron job quite easily.  See [**here**]("http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html") especially the part about "Using a daily cron job - recommended".

---

### Post by mc4man on 2016-02-08
> **Dennis N said:**
> So is there no way to see the blacklisted items on the new releases? Some command? By the way, I think in terms of the common meaning of 'list' - a number of items written consecutively, like my shopping list - in plain text. 

The Crucial only runs 14.04, so no trimming for it unless I use the --no-model-check option (or run it manually). And no trimming has ever been done. Maybe that's the right decision since it is not among the favored few in 14.04. Not trimmed, It has nevertheless been doing fine so far with no noticeable decrease in performance (installed in Oct 2014). If it would be checked on 15.10 I wouldn't know unless the kernel's blacklist were readable. That is why I ask.
I guess you could ck. the kernel source or try some of the dmesg or hdparm commands floating about that bug report. What model crucial do you have?
(- you could get a full report with something like this, replacing red with what /dev/sdx your drive is. - 

sudo hdparm -I /dev/sd[COLOR="#FF0000"]b[/COLOR]

My ssd experience has mainly been with ext. usb3 ssd's which can't use fstrim & I've noticed no slowdown over an  extended time &  use(running 3 or 4 Os's, ect.). I just replaced the internal hdd with the crucial ssd I mentioned & am absolutely not going to worry about trim, for me don't think it'll matter much. If it happens to get 'trimmed' fine, if not also fine.

---

### Post by Dennis N on 2016-02-08
> **from bab1:** You can use fstrim as a cron job quite easily. See here especially the part about "Using a daily cron job - recommended". 

Yes. A user created cron job what what I was thinking when using the word "manually". Poor choice of words on my part.

 
> **from mc4man:** I just replaced the internal hdd with the crucial ssd I mentioned & am absolutely not going to worry about trim, for me don't think it'll matter much. If it happens to get 'trimmed' fine, if not also fine. 

I am with you on that. I installed it in Oct 2014, and notice no slowdowns at all. I am pleased with the performance. I didn't know the USB connected ones can't use trim. I learned something new there.

My  model is Crucial MX100 256 gB - I've been investigating a bit, and Crucial says it uses "active garbage collection" independent of the OS to maintain a "high level of performance over time". It also supports trim, but a look at their forums finds comments/answers that it is not needed because of the a.g.c.

My decision: I am leaving it as is for now with no trim job.

[http://forum.crucial.com/t5/Crucial-SSDs/TRIM-and-SSD-performance-why-is-it-important/ta-p/100276](http://forum.crucial.com/t5/Crucial-SSDs/TRIM-and-SSD-performance-why-is-it-important/ta-p/100276)

Product Flyer documents trim support:
[https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/ssd/crucial-mx100-ssd-product-flyer-en.pdf](https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/ssd/crucial-mx100-ssd-product-flyer-en.pdf)

---

### Post by mc4man on 2016-02-08
> **Dennis N said:**
> Yes. A user created cron job what what I was thinking when using the word "manually". Poor choice of words on my part.

 
 

I am with you on that. I installed it in Oct 2014, and notice no slowdowns at all. I am pleased with the performance. I didn't know the USB connected ones can't use trim. I learned something new there.

My  model is Crucial MX100 256 gB - I've been investigating a bit, and Crucial says it uses "active garbage collection" independent of the OS to maintain a "high level of performance over time". It also supports trim, but a look at their forums finds comments/answers that it is not needed because of the a.g.c.

My decision: I am leaving it as is for now with no trim job.

[http://forum.crucial.com/t5/Crucial-SSDs/TRIM-and-SSD-performance-why-is-it-important/ta-p/100276](http://forum.crucial.com/t5/Crucial-SSDs/TRIM-and-SSD-performance-why-is-it-important/ta-p/100276)

Product Flyer documents trim support:
[https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/ssd/crucial-mx100-ssd-product-flyer-en.pdf](https://www.crucial.com/wcsstore/CrucialSAS/pdf/product-flyer/ssd/crucial-mx100-ssd-product-flyer-en.pdf)
That drive was one of the ones[ blacklisted]("https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4231")/not whitelisted but I believe only for the orig. firmware MUO1. With the firmware update to MUO2 it should be good - 
"Corrected error handling NCQ Trim Commands "
[http://www.crucial.com/usa/en/support-ssd-firmware](http://www.crucial.com/usa/en/support-ssd-firmware)

(- it's pretty simple to upgrade crucial firmware if on MUO1 or you could just leave well enough alone...

---

### Post by Dennis N on 2016-02-08
> That drive was one of the ones blacklisted/not whitelisted...

Mine would have the original firmware, since I bought it well before the update release. I downloaded the upgrade ISO. Looks easy enough with the bootable media. 

Thanks for the heads-up.

---

### Post by mc4man on 2016-02-08
> **Dennis N said:**
> Mine would have the original firmware, since I bought it well before the update release. I downloaded the upgrade ISO. Looks easy enough with the bootable media. 

Thanks for the heads-up.
The hardest part I had yesterday updated my mx200 was making the boot device from that iso. unetbootin made a usb from it but didn't do anything. I had some blank dvd's so made one with brasero ("Burn image" option
Seeing as though the iso is quite small it only took several sec. to burn but brasero took a long time to finalize the dvd, maybe because it was a dvd vs. a cd.??

Then just booted to that dvd & it was pretty much automatic.

---

