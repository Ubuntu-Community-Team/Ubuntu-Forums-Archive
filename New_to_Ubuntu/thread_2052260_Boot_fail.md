---
title: "Boot fail"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by Frank Blood on 2012-09-02
i burned the files i donwloaded from the ubuntu site for 12.04 onto a cd: iso and iso.PART, windows installer.
went to the BIOS and booted from cd but windows just keeps booting like normal. WTF?
what am i doing wrong?

---

### Post by Petro Dawg on 2012-09-02
You may have to download EasyBCD in windows and set up the boot loader for Linux.  

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

Just download the non-commercial free version from their site.

That's how I did it anyways.

EDIT:
Ooops, I think I understood you wrong.  You mean the LiveCD doesn't load the linux installation when you boot from the CD drive don't you?  My previous advice was given thinking that you already installed Ubuntu but it wasn't booting.

It's possible your ISO image is bad, or the burn didn't go well.  Try downloading again and reburning and see if it still does it.

---

### Post by critin on 2012-09-02
> **Frank Blood said:**
> i burned the files i donwloaded from the ubuntu site for 12.04 onto a cd: iso and iso.PART, windows installer.
went to the BIOS and booted from cd but windows just keeps booting like normal. WTF?
what am i doing wrong?

> **[COLOR=Red]iso and iso.PART, windows installer.[/COLOR]**What is this exactly?  Are you using Wubi as the windows installer?  Did you copy the files as data?  Or burn them as an ISO?  I don't know what is meant by the statement in red.

Sorry.  Could the [COLOR=Red]"iso.PART" [/COLOR]be the md5 used to check the accuracy of the iso download?  If so, don't burn that--just burn the iso image--burn as slowly as you can.  If you are using Wubi, it will install the iso itself by running, not booting.

Just in case it is Wubi:  here is the Wubi thread.  If not, just ignore it.

  [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by NikTh on 2012-09-03
> **Frank Blood said:**
> i burned the files i donwloaded from the ubuntu site for 12.04 onto a cd: iso and iso.PART, windows installer.
went to the BIOS and booted from cd but windows just keeps booting like normal. WTF?
what am i doing wrong?

Hello 

If you have 2 files .iso and iso.PART , then the download NOT COMPLETED. The iso.PART file is a temporary file that shows that the main .iso file is downloaded at current time. When the download completes , the iso.PART file must Disappear. 

First , remove the files you downloaded earlier . .iso and .iso.PART . 

Try to download the .iso again , from here : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Wait until the download complete. NO .iso.PART file must be present. 

Then burn the .iso again , at **lowest speed**. (it is important cuz you copy data)

Thanks.

---

### Post by Wim Sturkenboom on 2012-09-03
I agree with NikTh

Further, before burning, verify the MD5sum; this would have straight away told you that your download was corrupted ;)
Google for md5sum in combination with your current OS (e.g. [windows md5sum](http://www.google.co.za/search?q=windows+md5sum&btnG=Search&hl=en&site=)) to download a tool for this; there are plenty.

You can find the md5sums at [http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/) ; follow the link for the version that you've downloaded and click the file MD5SUMS
For 12.04.1, [http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/12.04.1/MD5SUMS](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/12.04.1/MD5SUMS).

---

