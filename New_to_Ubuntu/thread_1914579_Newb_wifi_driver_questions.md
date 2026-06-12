---
title: "Newb wifi driver questions"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by jaksmash on 2012-01-24
Bought this laptop: [http://www.microcenter.com/single_product_results.phtml?product_id=0382600](http://www.microcenter.com/single_product_results.phtml?product_id=0382600)

Fully installed Ubuntu 11.10.  It worked for a while but seemed a bit laggy.  I changed a couple of settings to have a screen saver that rotated my pictures.  I thought that I managed to get the desktop wallpaper to randomize using my pictures too.  The next time I turned it on it froze after loading the wallpaper(the 1st picture in my folder) and the pointer.  No response.  Had to hold power down for 10-15 seconds to shut off.

I have a second laptop(same kind).  Put 10.04 on a CD and replaced 11.10.  Love it.  Except it doesn't have the drivers that the Atheros AR5B12 wifi card needs.  I searched these forums and tried a few suggestions but most were miles over my head.  I did find something about loading them from the CD I installed 10.04 with.  But I can't get the CD recognized, it keeps saying the drive is not mounted.  Even though I can import mp3's.  Then I tried to reinstall 11.10 and the drive stops working before it boots.  It doesn't do this for the 10.04 CD though.

All I really want to do is extract the drivers from the memory stick I am now running 11.10 with into the 10.04 that is on my laptop.  Also, I have the driver .sys files from windows saved on a memory stick(from the other computer).  If it is easier to install these then great, but I am not sure how to turn them into .inf files.  I have the windows wireless drivers thing but I don't know where to tell it to look as it wants .inf, not .sys.

Whew.

Really green at this.

Thanks for any help.

---

### Post by anewguy on 2012-01-25
To use Windows drivers, you have to have the .inf *AND* .sys files that make up the driver.  The .inf is a text-based file that tells the system various things about the hardware and driver, and which of the actual .sys files to use.  You have to have both - and you can't make 1 from the other - 2 completely different animals.

On the Linux side, I get nothing but this post when I search Google for Linux AR5B12 .  So, please post back the output of the following:

- open a terminal window

- type:

lspci

lsusb


Copy the outputs and post back here.  In the mean time, it may be that we have to use the Windows drivers, so download them from the manufacturer keeping the following in mind:

- they *must* be Windows XP drivers only

- the driver and your Ubuntu architecture must match:  32 bit or 64 bit

You may have to unpack the driver as it may be a zip file or a self-extracting exe file.  Once you've done that you'll find the .inf and .sys files.

In this way you'll be ready for us to walk you through installing the Windows drivers if we can find no other way to get it to work.

Dave ;)

---

