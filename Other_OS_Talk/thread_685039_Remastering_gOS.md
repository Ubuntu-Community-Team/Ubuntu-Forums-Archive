---
title: "Remastering gOS"
date: 2008-02-01
forum: Other OS Talk
---

### Post by amrishodiq on 2008-02-01
Is there anyone ever succeed remastering gOS and will show us how to do it? Since the distro's size is approximately 530 MByte only, I wan't to put some additional software. So I need to remaster it to match my taste.

Is remastersys or reconstructor will work?

---

### Post by smartboyathome on 2008-02-01
Remastersys should work for this. Reconstructor is iffy in my opinion, since it did not always add the stuff I told it to.

---

### Post by chris4585 on 2008-02-07
remastersys should do what you want just fine

---

### Post by darthchaosofrspw on 2008-02-19
> **amrishodiq said:**
> Is there anyone ever succeed remastering gOS and will show us how to do it? Since the distro's size is approximately 530 MByte only, I wan't to put some additional software. So I need to remaster it to match my taste.

Is remastersys or reconstructor will work?

I successfully remastered gOS using Remastersys 2.0.2. This remastersys is found at [http://linuxmint.com/repository/pool/daryna/r/remastersys/remastersys_2.0-2_all.deb](http://linuxmint.com/repository/pool/daryna/r/remastersys/remastersys_2.0-2_all.deb)

Trouble is, you have to use **sudo remastersys backup**. If you try to use **sudo remastersys dist**, it will produce an ISO which will not boot correctly.

If you want to download my customized gOS, visit my blog entry. It has download links. It's being hosted on RapidShare for now. You can download it and seed it as a torrent if you wish.

[http://darthchaosofrspw.wordpress.com/2008/02/17/announcing-gos-rocket-linux-20-ultimate-edition/](http://darthchaosofrspw.wordpress.com/2008/02/17/announcing-gos-rocket-linux-20-ultimate-edition/)

Visit the website to see how I customized it.

---

### Post by david0810 on 2008-02-21
Thanks for the link...  I've been looking for something like this with no luck...  Thanks for the find!

-----------------------------------------------
[SIZE="1"][review]("http://www.penis-review.com") [sizegenetics]("http://www.penis-review.com/devices/sizegenetics.html")  [prosolution]("http://www.penis-review.com/pills/prosolution.html")  [sizepro]("http://www.penis-review.com/pills/sizepro.html")[/SIZE]

---

### Post by darthchaosofrspw on 2008-02-21
> **david0810 said:**
> Thanks for the link...  I've been looking for something like this with no luck...  Thanks for the find!

-----------------------------------------------
[SIZE="1"][review]("http://www.penis-review.com") [sizegenetics]("http://www.penis-review.com/devices/sizegenetics.html")  [prosolution]("http://www.penis-review.com/pills/prosolution.html")  [sizepro]("http://www.penis-review.com/pills/sizepro.html")[/SIZE]

I'm planning on doing another version of gOS Ultimate that has Firefox uninstalled and has Opera as default browser. Is there any way I can change the web apps (Facebook, Blogger, Google apps, etc.) to where they use Opera upon installation (using Remastersys)? You can right-click on an icon such as Gmail in the iTask NG dock and change the executable from "firefox http://mail.google.com" to "opera http://mail.google.com", but what I want to do is have it that way as soon as the OS is installed.

If that's impossible, then I'll just leave Firefox on and uninstall Opera. For the new version, I'm replacing xine-ui with totem-xine and upgrading GIMP from 2.4.2 to 2.4.4.

---

### Post by igknighted on 2008-02-21
> **darthchaosofrspw said:**
> I'm planning on doing another version of gOS Ultimate that has Firefox uninstalled and has Opera as default browser. Is there any way I can change the web apps (Facebook, Blogger, Google apps, etc.) to where they use Opera upon installation (using Remastersys)? You can right-click on an icon such as Gmail in the iTask NG dock and change the executable from "firefox http://mail.google.com" to "opera http://mail.google.com", but what I want to do is have it that way as soon as the OS is installed.

If that's impossible, then I'll just leave Firefox on and uninstall Opera. For the new version, I'm replacing xine-ui with totem-xine and upgrading GIMP from 2.4.2 to 2.4.4.

Google apps don't really run on opera (or they run in reduced-functionality mode), so I wouldn't advise that.  It's too bad cause Opera is indeed a much better browser :-/

---

### Post by RAV TUX on 2008-02-22
> **igknighted said:**
> Google apps don't really run on opera (or they run in reduced-functionality mode), so I wouldn't advise that.  It's too bad cause Opera is indeed a much better browser :-/Google Documents run perfectly in Opera.

---

### Post by darthchaosofrspw on 2008-02-23
> **igknighted said:**
> Google apps don't really run on opera (or they run in reduced-functionality mode), so I wouldn't advise that.  It's too bad cause Opera is indeed a much better browser :-/

I've had no problems running the Google apps on Opera......as long as I edit the launcher in the dock from something like "firefox http://mail.google.com" to "opera http://www.google.com".

And yes, I also think Opera is a much better browser. I never did like how if you tried to uninstall Firefox it would want to uninstall ubuntu-desktop.

---

### Post by ryan.overton on 2008-02-26
anyone have a link to the gOS Ultimate iso or torrent?

---

### Post by igknighted on 2008-02-26
> **darthchaosofrspw said:**
> I've had no problems running the Google apps on Opera......as long as I edit the launcher in the dock from something like "firefox http://mail.google.com" to "opera http://www.google.com".

And yes, I also think Opera is a much better browser. I never did like how if you tried to uninstall Firefox it would want to uninstall ubuntu-desktop.

I've always had problems with the chat feature in opera (in gmail).  Not to mention it usually yells at me for using an "unsupported browser".  Konqueror is worse though (although I haven't tried the webkit-based version from KDE4).

Why does it matter about the ubuntu-desktop package?  That's just a convenience package to pull in the standard ubuntu packages if you install from the minimal/server disk, or want to switch from X/Kubuntu.  Having the metapackage isn't important though, as it doesn't actually do anything.  The real problem with removing firefox from ubuntu is the host of other applications that are built on gecko/xulrunner that get removed or break because ubuntu doesn't split between the browser and the engine (as many argue they should).

---

### Post by iamclueless on 2008-04-05
> **ryan.overton said:**
> anyone have a link to the gOS Ultimate iso or torrent?

+1

not sure how to use the rar files due to no longer having windows on this box

thanks

---

### Post by iamclueless on 2008-04-05
> **iamclueless said:**
> +1

not sure how to use the rar files due to no longer having windows on this box

thanks

should add that im after the "finalized"/latest version

---

