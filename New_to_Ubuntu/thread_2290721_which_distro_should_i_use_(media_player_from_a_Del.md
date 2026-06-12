---
title: "which distro should i use? (media player from a Dell GX240 + GeForce FX 5700 LE)"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by rene7 on 2015-08-14
hello ubuntu users!

i hope you guys can help me out.

i have an old Dell desktop (GX 240) with a replaced graphics card (GeForce FX 5700 LE)
it's a P4 1.6GHz or something (close enough to not matter i think) with some 512MB RAM
i was hoping to turn this into a sort of media player to play movies n stuff from an external harddrive.
i have tried Ubuntu, Lubuntu n think i even tried Xubuntu, all with various releases (12 through 15)
best results i got sofar was a very (very!) choppy video experience with Lubuntu 14.4 (screen size also wasn't exactly right)
i tried Kodibuntu and a minimal install according to a guide i found on the forums, but after install these didn't boot to any desktop or console or anything.

next idea was OpenELEC, but while reading the differences between their mainstream and their "legacy" releases i noticed the FX 5700 LE isn't mentioned  in either list of supported graphics cards.
maybe this thing is older than i thought, but i think this card should still be quick enough to function in the capacity of media player, but i just need to find the right distro.

so, here's to you, the ubuntu community, what would you suggest?

---

### Post by MartyBuntu on 2015-08-14
That system will absolutely choke on most modern codec formats for anything beyond standard definition.

---

### Post by papibe on 2015-08-14
Hi rene7.

The system as it is can't work as an HD HTPC, and I'm not even sure if with the following upgrades the CPU will be able to handle it anyway, but ...

There may be a chance if you upgrade your GPU (assuming that the current GPU is a PCIe card). You can go as low as an Nvidia 210, 410 or 610 (about $30-$40). All of them handle video acceleration with the Nvidia proprietary driver.

Another upgrades that might help:
[LIST]
[*]Replace your hard drive for a SSD. Again assuming your motherboard has SATA ports.
[*]Install more RAM. Another 512MB should do it.
[/LIST]
If I were you, I'd star with the GPU and see how it handle HD movies.

Regarding a distro. I personally would go with Ubuntu minimal install, and then install all necessary packages to set it up as an very slim HTPC. 

However, it should be a lot easier to do this:
[LIST]
[*]Install light desktop environment: example Lubuntu 14.04+
[*]Install the nvidia proprietary driver.
[*]Install Kodi from the repositories.
[*]Set up kodi as autostart/autologin application so when you boot, go directly to Kodi.
[*]
[/LIST]
Just a thought.
Regards.

---

### Post by MartyBuntu on 2015-08-14
With the money required to get that machine capable of running as an HTPC, you're better off spending your money on a cheap Android based media appliance like Roku or Pivos.

---

### Post by mörgæs on 2015-08-15
I agree with the posters above. It's old stuff and you can't expect too much. Did you use closed-source graphics drivers? 

Did you monitor system load using for example Gkrellm?

---

### Post by Yellow Pasque on 2015-08-15
> There may be a chance if you upgrade your GPU (assuming that the current GPU is a PCIe card)
It's not. The Geforce FX 5700LE is an AGP card. The GeForce 5 series was mostly AGP and the few models using PCI-e were named "PCX" instead of "FX" to avoid confusion.

Maybe a RadeonHD 4000 series would allow HD video playback through VDPAU. Maybe not...
Unfortunately, RadeonHD 4000 series cards using AGP seem to carry a price premium. Also, I've seen lots of complaints about trying to use these RadeonHD AGP cards on Linux.

---

