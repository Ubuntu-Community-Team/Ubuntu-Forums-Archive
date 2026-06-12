---
title: "New Installation of 12.10 (Desktop 64) won't boot"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by sag on 2012-11-03
Hi All,
I've just installed 12.10 on my laptop (Compaq Presario CQ57) from My USB stick. It booted OK after installing, though it was slower than I expected (taking about a minute or so), and appeared to work well.
I set the desktop background etc, and then tried to set up Ubuntu One, which appeared to hang on the synchronising screen (I left it for at least 10 minutes), I closed that down and ran the update manager, there were 50 ish updates indicated, and that completed sucessfully, I was asked to reboot which I did. The computer comes up into the Ubunto purple screnn (no text), gives the little drum beat, and just sits there with a completely blank purple screen.
My instinct is to just do a fresh re-install, but that is a bit of a cop-out as I'd like to get to know Ubuntu warts and all!
Thanks for any comments/help
sag

---

### Post by pqwoerituytrueiwoq on 2012-11-03
boot using nomodeset in the kernel boot line
then install the lastest driver (google amd driver ubuntu)

---

### Post by sag on 2012-11-03
Hi Pqwoerituytrueiwoq,
Thanks for your rapid response, but unfortunately I have no idea how to do what you suggested!
My level of expertise is way down there!
sag

---

### Post by newb85 on 2012-11-03
Good instructions for booting nomodeset are at [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132").  Scroll down to the heading "How to temporarily set kernel boot options on an installed OS (not wubi)".  (I assume from the fact you installed from a USB that you didn't install from within Windows...)

With any luck, that will allow your system to come up once.  Then, you can open Additional Drivers or Hardware Drivers (depending on your release) and install the drivers for your GPU.

---

### Post by sag on 2012-11-03
Hi Newb85,
Thanks, worked a treat eventually!! 12.10 is up and running now!
sag

---

