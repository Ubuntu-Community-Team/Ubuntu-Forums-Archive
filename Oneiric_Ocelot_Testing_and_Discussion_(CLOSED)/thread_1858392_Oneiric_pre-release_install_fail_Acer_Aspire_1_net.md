---
title: "Oneiric pre-release install fail Acer Aspire 1 netbook"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-10-12
This netbook runs Lynx, Meerkat, Narwhal, earlier Ocelot O.K. with usual bug experience.

Daily build 20111011 pre-release image will not install.  Install gets up to "Choose a picture", or "take a picture" with the built in camera, then install refuses to go on.  Install did work on my tower which doesn't have a built in camera and this "Choose a picture" window didn't come up.

Note this is a typical netbook with 1024 x 600 screen and the "Choose a picture" window falls off the bottom of the screen.

The window will not scroll so I can't see what's at the bottom.  I suspect a Continue is way down there at the bottom, but there's no way to reach it.

Enter doesn't work, can't proceed.  Nothing the mouse will do will go on.

Tried to enter this install bug on the pre-release page but the i386 image is lined out.

I did do a launchpad bug #872622.

Note, booting from USB stick, the old zeitgeist bug is back.  I entered bug #872495.  

Jerry

---

### Post by lucazade on 2011-10-12
Have you tried to move window with Alt+left click+move it? 
If you pick the window from the middle you can reach the end of it.

---

### Post by jerrylamos on 2011-10-12
> **lucazade said:**
> Have you tried to move window with Alt+left click+move it? 
If you pick the window from the middle you can reach the end of it.

Thanks, lucazade, that worked.

Now install totally screwed up the grub boot loader.  Some "error" it wouldn't define,, launchpad bug#872845.

After several tries and a couple hours later, finally got it to use grub off a USB hard drive, then selecting Ocelot on the main hard drive.  A few tries later Ocelot said grub installed O.K.  Now to try it...

Update: Didn't boot.  Several go-arounds with grub update & install from USB hard drive and with Meerkat on a separate partition, finally limped up.  Ocelot grub update & install finally worked.  Not for the faint of heart even at this late stage...

Isn't this fun.

Jerry

---

### Post by erichouse98 on 2011-10-12
When will the ISOs be released? On the 13th 12:01AM UTC/GMT +2 time? I cant wait!!!

---

### Post by jerrylamos on 2011-10-12
> **erichouse98 said:**
> When will the ISOs be released? On the 13th 12:01AM UTC/GMT +2 time? I cant wait!!!
Usually the CD Daily Build a day or two before the release is nearly identical, so using that .iso plus a minor update will get you there.  

Jerry

---

### Post by jerrylamos on 2011-10-13
> **jerrylamos said:**
> Usually the CD Daily Build a day or two before the release is nearly identical, so using that .iso plus a minor update will get you there.  

Jerry

Example, install I did with the Oct 11 image had no update/upgrades to do today the 13th.  I'll check the MD5SUMS when the final release came out.

Note I had a bad time with the install.  Well after install was under way the window "Choose a picture" showed up.  On this netbook "Continue" is off the bottom of the screen.  I couldn't continue.

By that time the partition was clobbered with a partial install, and more importantly grub was all screwed up.

Took me several hours with a USB hard drive and with a Meerkat partition before I could get the hard drive to boot at all.

Then on the forums someone said put the mouse cursor on the middle of the troublesom window, hold down Alt and push left mouse button, move the screen to where Continue is accessible.  That worked.

I don't think troublesome windows like "Choose a picture" should come up at all while install is in progress, or at least let install complete with the #$%^& window un-answered.  Yes someone has entered a launchpad bug on the problem of mandatory install windows falling off the bottom of a netbook screen.

Jerry

---

