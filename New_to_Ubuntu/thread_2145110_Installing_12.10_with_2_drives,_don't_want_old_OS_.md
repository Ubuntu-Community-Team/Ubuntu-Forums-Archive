---
title: "Installing 12.10 with 2 drives, don't want old OS at all"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by PatheticBarrel on 2013-05-14
I was gifted an older computer from my godparents over the weekend, and am trying to get Ubuntu running properly. I don't know any real specs, but know that I have two HDD and that it is an HP. One problem I am running across is an error stating that the CRTC is not set correctly. I've tried using nomodeset, but to no avail. Am attempting install on the smaller drive instead of the larger, to see if I have the wrong boot order.

Any help in case this doesn't solve the problem would be very much apprecieted

Still giving *ERROR* failed to set mode on [CRTC:10].
This is running the install off of a USB. Will try to boot normally to see if it works, again...

Here are the two monitors I have.
[http://www.amazon.com/PL1910M-BK-19-Inch-Digital-Monitor-Speakers/dp/tech-data/B00020E4KK/ref=de_a_smtd](http://www.amazon.com/PL1910M-BK-19-Inch-Digital-Monitor-Speakers/dp/tech-data/B00020E4KK/ref=de_a_smtd)
[http://www.amazon.com/ViewSonic-VA912B-19-inch-Monitor-Black/dp/tech-data/B0009ZCTX2/ref=de_a_smtd](http://www.amazon.com/ViewSonic-VA912B-19-inch-Monitor-Black/dp/tech-data/B0009ZCTX2/ref=de_a_smtd)

The box itself is an HP Pavilion m7560n, but with an extra 400GB HDD installed.

---

### Post by grahammechanical on 2013-05-14
This is what I have found out from just a little research. CRTC = Cathod Ray Tube Controller. I know that when we install Ubuntu we do not have to set the monitor resolution, refresh rates or anything like that because Ubuntu reads the EDID (Extended Display Identification Data) that it gets from the monitor. Which often works fine for digital monitors. As you are using a CRT monitor Ubuntu cannot get any information about resolution or refresh rates from the monitor because the information does not exist in the monitor.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

nomodeset should get the live session running. What do you mean by "no avail?" You need to tell us what you see on the screen when you try to run the live session and when you try to install Ubuntu. It is my guess that you will have to set the video mode by hand - editing a configuration file.

If this computer is really that old you most likely will have other issues installing Ubuntu due to the low specification of the hardware. I really hate to say this as I support Ubuntu but you may need to try another Linux distribution (not the powerful distributions not the lesser know Linux distros), especially one that requires you to set the monitor resolution as part of the installation Process.

You need to know the specfications of the monitor. Horizontal frequency range, Vertical frequency range, Resolution (such as 800x600), video mode (such as 5f), and colour depth (256 colors). That sort of thing. Run the monitor at the wrong settings and there is a high risk of damaging the monitor.

Regards.

---

### Post by PatheticBarrel on 2013-05-14
By no avail, I mean that I'm getting the same issue. When I boot USB, then install, everything works as I expect, until the system restarts and it tries to boot again, in which I get the CRTC error. When trying to boot normally, without the USB, the screen is black with a flashing _ in the corner. I do not believe that either monitor I have is a CRT, but I'll double check that. Should I perhaps try hooking my TV up to check if the install itself worked?

---

### Post by PatheticBarrel on 2013-05-14
Ok, haven't tried my TV idea yet, but I am still getting the same issues. Have found that if I get the CRTC error when booting the USB, hitting Enter then Esc lets me continue, so I'm going to attempt that when I get the message when it boots after install.

---

