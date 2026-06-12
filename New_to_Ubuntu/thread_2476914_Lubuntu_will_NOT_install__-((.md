---
title: "Lubuntu will NOT install  :-(("
date: 2022-07-11
forum: New to Ubuntu
---

### Post by az64x on 2022-07-11
Trying to install Lubuntu 22.04 LTS on a fairly recent Samsung Laptop. 500 gig hd and 5 gig ram

 

 Using DVD created from Lubuntu download which did not work. Then tried using Rufus to put it on 16 gig USB.  It did not work.

 

 It does NOT bring up the blue screen to select Lubuntu.
 

 With both DVD and USB it brings up a black screen that says GNU Grub version 2.06
 

 That is the end.
 

 **HELP**

---

### Post by sudodus on 2022-07-11
Is it failing, when you try to boot from the DVD and from the USB pendrive? Or did you manage to install, and the installed system fails to boot?

Did you check with sha256sum, that the downloaded iso file is good (that the download process worked correctly)?

If failing from DVD and USB: What happens when you select Try Lubuntu? Nothing, or do you hear some noise? Is something written to the screen (for example an underline character)?

What kind of graphics chip/card is there? nvidia, radeon or intel graphics? If not intel, please try recovery mode (or manually using the boot option **[FONT=Courier New]nomodeset[/FONT]**).

---

### Post by guiverc on 2022-07-11
How far did you get following [the manual]("https://manual.lubuntu.me/stable/1/Installing_lubuntu.html")?

Did the checksum verify correctly?

DVD media is not, and hasn't been to be used for install media for Ubuntu (*and flavors like Lubuntu*) for some time, yes it's still possible, but due to timeout issues (*optical media is very slow, some DVD drives slower than others*) which result in timeout issues & error messages that are hard to interpret for non-technical users. You may find some more details in this [Lubuntu thread]("https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246"), but I'd avoid using DVD or optical media unless you had to, and expect an install to take an hour.. and 10-15 mins of black screen during boot is not unexpected which leads many to think it's not booted, when its just a matter of great patience is required.  There is a tracked bug that may result in it a little better for Ubuntu 22.04.1 (*including Lubuntu of course*) when that releases in August 2022.

Blue screen?   On some boxes it's blue, on others the `grub` appears only as a black background & white text.  Some boxes show a blue themed grub, others don't - the firmware on the box determines that.

If by *blue screen* you mean the desktop, did you try the ***safe graphics*** option listed in the manual in [installation 1.3]("https://manual.lubuntu.me/stable/1/1.3/installation.html") and do note you still should be patient. Certain boxes can take time to boot *live* media due to *bugs in the firmware itself* either because you've not applied the fixes, or the OEM/seller of the board never provided *firmware fixes*.  These *firmware bugs* don't stop booting, but can result in 6-11 minutes of black screen where the *boot* just pauses with nothing displayed.  This may not be your issue (*it impacts only a small number of brand/model boxes*) but you maybe impacted by this, esp. if you already tried the *nomodeset* (*safe graphics*) option & verified your media.

If my media fails to boot on one box; I tend to eject it, then boot on another box & confirm the media on that other box. The reason I do this is the most common failure in my experience is the write of ISO to installation-media (*USB thumb-drive*) as the thumb-drive media is cheap & made to be cheap (*a consumable item*). About 5-8% of writes fail in my experience using Sandisk branded drives; with higher failure rates for other brands. Ubuntu 22.04 LTS (*which includes Lubuntu 22.04 LTS*) will self-verify the boot media, but it needs to boot first; so I'm using another box to perform this check; which will prove the media is valid & I have a box specific issue.  I'll suggest you use another box to confirm you write work.


I'll provide a link to a askubuntu question which has some of my thoughts - [https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/](https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/) ; not as much for my most-upvoted answer, but my other answer which wasn't upvoted as it contains some detail I use to confirm a boot was successful. The actual messages tend to vary slightly by release, and for 22.04 I'd scan using `sudo journalctl` and look for all the `**casper-md5check**`, especially the last line which report 

"**Check finished: no errors found**".

If this completes & you see this on another box; it looks like your media is valid. I'd often boot on a third box & confirm there too, then I'd know it's an issue related to the box you want to use, be it graphics, timeouts (*esp. where optical media is used*), or *firmware *(*unlikely but an issue with 20.10->22.04 and some boxes*).

If it's *firmware* issues, patience is just need to boot the *live* media, as once installed the issue won't occur - the bug only applies to external media booted *live*, with the bug existing on a chip on some motherboards (*fixed by firmware upgrades*).


*Unlikely your issue, but I rarely use a `samsung 700t1c-p10aat (i5-3317u, 4gb, 3rd gen.core.intel.graphics.4000)` in QA-testing as I find that device a royal pain to boot external/live media.. That's done intentionally (by Samsung firmware) so it's harder to replace the OS the box came with... I gather this isn't your issue, but your mention of Samsung just made me cringe.*

---

### Post by poorguy on 2022-07-12
> **guiverc said:**
> How far did you get following [the manual]("https://manual.lubuntu.me/stable/1/Installing_lubuntu.html")?
DVD media is not, and hasn't been to be used for install media for Ubuntu (*and flavors like Lubuntu*) for some time, yes it's still possible, but due to timeout issues (*optical media is very slow, some DVD drives slower than others*) which result in timeout issues & error messages that are hard to interpret for non-technical users. You may find some more details in this [Lubuntu thread]("https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246"), but I'd avoid using DVD or optical media unless you had to, and expect an install to take an hour.. and 10-15 mins of black screen during boot is not unexpected which leads many to think it's not booted, when its just a matter of great patience is required.  There is a tracked bug that may result in it a little better for Ubuntu 22.04.1 (*including Lubuntu of course*) when that releases in August 2022.

For some of us DVD may be the only choice we have for installation as not all computers boot from usb created media.

I also had a long wait with installing from a DVD and then just walked away and then returned in forty five minutes or so to a Ubuntu display.

It would have been nice to have known from the start that it was going to take some time to load the (3.4GB) installation files as I believed they are compressed but may be wrong about that.

Anyway learn by doing and that Ubuntu 22.04 and Ubuntu 22.04 flavors are going to take quite a while to install on old or low powered hardware and I speak from my own experience.

Once installed Ubuntu 22.04 and Ubuntu 22.04 flavors work okay however depending on the hardware used your mileage may vary.
I had to use a tool I haven't had to use since the installation of Windows 10** "Patience".** :lolflag:

---

