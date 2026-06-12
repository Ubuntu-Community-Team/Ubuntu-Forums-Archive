---
title: "Samsung TV LE32N73BD/Shuttle SN68PTG6/Geforce 7050 Display problems"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Elijah2104 on 2008-08-22
Hello, I'm definitely in the category of absolute beginner to Linux.  I have bought a new [Shuttle SN68PTG6]("http://global.shuttle.com/product_detail_spec.jsp?PI787") barebones system.  The system includes an integrated NVidia Geforce 7050pv graphics card.

Using an HDMI cable I have connected it to my [Samsung LE32N73BDX]("http://www.dabs.com/productview.aspx?quicklinx=48dm") TV. The TV is capable of a resolution of 1360x768.

My problem is that the proprietary drivers will only allow a resolution up to 1280x720.  The non-proprietary ones only go to 800x600.  In addition to the display not looking very good it also disappears off the edges.

I've tried downloading a new [driver]("http://www.nvidia.co.uk/object/linux_display_amd64_173.14.12_uk.html") but I don't know how to install it.  I tried the suggested command in the terminal window and it told me it couldn't open the file.

This goes for every firefox plugin I've wanted to install as well, I just don't know how to do it!

Is anybody able to assist me?  Bearing in mind I'm so new to Linux I will need very clear and step by step instructions.  Words of one syllable may be necessary :)

Thanks in advance.

---

### Post by michaelwc on 2008-08-22
Hi,

Have you installed the 32 or 64bit OS?  If 32, try this page:
[http://www.nvidia.co.uk/object/linux_display_ia32_173.14.12_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.12_uk.html)

This downloads a package which you call from terminal as before.

You may wish to RTFM about x-config or use the nVidia config tool also available.

MWC

---

### Post by Elijah2104 on 2008-08-22
> **michaelwc said:**
> Hi,

Have you installed the 32 or 64bit OS?  If 32, try this page:
[http://www.nvidia.co.uk/object/linux_display_ia32_173.14.12_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_173.14.12_uk.html)

This downloads a package which you call from terminal as before.

You may wish to RTFM about x-config or use the nVidia config tool also available.

MWC

It's the 64bit version so I guess trying that one would be pointless?

Thanks for the pointer on what to look for in TFM :)  Part of the problem is not knowing what I don't know :confused:

---

### Post by Elijah2104 on 2008-08-26
> **Elijah2104 said:**
> It's the 64bit version so I guess trying that one would be pointless?

Thanks for the pointer on what to look for in TFM :)  Part of the problem is not knowing what I don't know :confused:

Ok, so I've downloaded a driver from NVidia.  I tried to run it in the terminal (and the fail safe terminal) by typing:

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

This executes it but fails with a message that the x-server is still running and it needs to be shutdown.  After some digging I found [this]("http://ubuntuforums.org/showthread.php?t=304325") thread which shows how to shut down the x server except all I get is a blank screen.  No prompt, nothing.  I've tried running the command from the terminal and tried the Ctrl+Alt+F1 and still all I get is a blank screen.

I really am at a total loss here! :confused:

---

