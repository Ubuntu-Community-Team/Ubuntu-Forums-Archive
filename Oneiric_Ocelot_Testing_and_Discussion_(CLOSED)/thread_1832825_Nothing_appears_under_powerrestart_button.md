---
title: "Nothing appears under power/restart button ?"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-08-25
Is broken for everyone? That quit button on top right of panel?

---

### Post by jerrylamos on 2011-08-25
> **rajeev1204 said:**
> Is broken for everyone? That quit button on top right of panel?

Busted for days and days on my fastest pc.  I update most days, no help.

I made a shutdown now exec, wait for an appropriate time, then turn off the terminal strip.  Oneiric does shut off the hard drive so I listen for that.  I forget the launchpad bug number.

The power button still works on this notebook but reboot is missing so I made an exec.

I think Ubuntu thought we'd be happy to go through "logout" and a bunch of other keystrokes to reboot.  They didn't remove the command line yet...

Jerry

---

### Post by rajeev1204 on 2011-08-25
> **jerrylamos said:**
> Busted for days and days on my fastest pc.  I update most days, no help.

I made a shutdown now exec, wait for an appropriate time, then turn off the terminal strip.  Oneiric does shut off the hard drive so I listen for that.  I forget the launchpad bug number.

The power button still works on this notebook but reboot is missing so I made an exec.

I think Ubuntu thought we'd be happy to go through "logout" and a bunch of other keystrokes to reboot.  They didn't remove the command line yet...

Jerry

Iam on a desktop.Right now i do a ctl-alt-del which strangely asks me if i would like to log out.Does not show any other buttons.Then it drops me to the greeter screen from where i used to use restart but that seems to have disappeared too last few days.So i do a hard reboot from my PC power button.

---

### Post by cariboo on 2011-08-25
> **jerrylamos said:**
> Busted for days and days on my fastest pc.  I update most days, no help.

I made a shutdown now exec, wait for an appropriate time, then turn off the terminal strip.  Oneiric does shut off the hard drive so I listen for that.  I forget the launchpad bug number.

The power button still works on this notebook but reboot is missing so I made an exec.

I think Ubuntu thought we'd be happy to go through "logout" and a bunch of other keystrokes to reboot.  They didn't remove the command line yet...

Jerry

All you have to do is select shutdown from the menu, and a window pops up with the choice to Restart, Cancel and Shutdown, if you aren't seeing the 3 choices, your installation is broken.

---

### Post by jerrylamos on 2011-08-25
> **cariboo907 said:**
> All you have to do is select shutdown from the menu, and a window pops up with the choice to Restart, Cancel and Shutdown, if you aren't seeing the 3 choices, your installation is broken.

It's not the installation that's broken, it's Oneiric.  There's an Oneiric bug that crashes the "Indicator".  I forget the launchpad bug #'s can find if anyone cares.

Oh, well, we'll see what the next updates do.

On this notebook, selecting the power indicator gets me about 12 choices with one grey'd out.  On the other pc I get nothing.  Command line still works.

On a third pc selecting shutdown I do get a restart option.  Why didn't they leave that on the first dropdown menu?  More keystrokes for what advantage?

Oh, yes, in testing mode, I reboot a lot.

Jerry

---

### Post by cariboo on 2011-08-25
> **jerrylamos said:**
> It's not the installation that's broken, it's Oneiric....

Oh, well, we'll see what the next updates do.

On this notebook, selecting the power indicator gets me about 12 choices with one grey'd out.  On the other pc I get nothing.  Command line still works.

On a third pc selecting shutdown I do get a restart option.  Why didn't they leave that on the first dropdown menu?  More keystrokes for what advantage?

Oh, yes, in testing mode, I reboot a lot.

Jerry

I'm not going to argue with you, but I and many others have exactly what I suggested, so I would say your installation is broken. All three systems  I have running Oneiric shutdown and restart work properly.

---

### Post by meborc on 2011-08-26
> **cariboo907 said:**
> I'm not going to argue with you, but I and many others have exactly what I suggested, so I would say your installation is broken. All three systems  I have running Oneiric shutdown and restart work properly.

I can confirm... besides the annoying white box in the indicator area everything else is fine. I can click on the power icon and select all the options I wish.

netbook aspire one (all intel) with all latest daily updates

---

### Post by rajeev1204 on 2011-08-26
Maybe it does not affect notebooks?

---

### Post by rajeev1204 on 2011-08-26
@cariboo

[https://bugs.launchpad.net/indicator-session/+bug/834718](https://bugs.launchpad.net/indicator-session/+bug/834718)

---

### Post by dino99 on 2011-08-26
my config is worst: logged as gnome-classic, the top right menu icons are lost, have had to reinstall the old icons by right clicking.

---

### Post by Sycron on 2011-08-26
> **rajeev1204 said:**
> Is broken for everyone? That quit button on top right of panel?
My power button looks like this since alpha 3.

---

### Post by rajeev1204 on 2011-08-26
> **Sycron said:**
> My power button looks like this since alpha 3.

Exactly.

---

### Post by jerrylamos on 2011-08-26
On topic, I've three pc's with current updated Oneiric Ocelot.  One of them has nothing under the top right power switch icon.  

This is the pc that gets launchpad bug #824243 something about an indicator-service-session crash.  Nothing from development on that one that I've seen.

The other two have about a dozen options, none of them restart.  You have to go through shutdown to get to restart makes no sense to me to add an extra drop down menu and extra step.

Jerry

---

### Post by rajeev1204 on 2011-08-27
[https://bugs.launchpad.net/indicator-session/+bug/834718](https://bugs.launchpad.net/indicator-session/+bug/834718)

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243)

---

### Post by ricsi-pontaz on 2011-08-28
There is a patch for this bug: 

[(https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)"][https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)]("[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)

But I don't know how to try this. Any suggestion?

---

### Post by lidex on 2011-08-28
> **ricsi-pontaz said:**
> There is a patch for this bug: 

[(https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)"][https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)]("[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)

But I don't know how to try this. Any suggestion?

Apparently this is over my head as well. I'm guessing you have to patch udev source. Do you have dvb/tv card installed?

---

### Post by rajeev1204 on 2011-08-29
> **lidex said:**
> Apparently this is over my head as well. I'm guessing you have to patch udev source. Do you have dvb/tv card installed?

I have a tv card installed.How is that related ?

---

### Post by medeshago on 2011-08-29
> **rajeev1204 said:**
> I have a tv card installed.How is that related ?

It says right in comment 19 of bug 824243: "The problem, in my case, is that g_udev_client_query_by_subsystem (mgr->client, video4linux_subsystem)[1] is returning devices that are not video devices (webcams). I have a PCTV board instaled in my system, and this method is returning (wrongly) /dev/radio0 as a video4linux device.

The crash is happening in udev_mgr_handle_webcam, because both 'vendor' and 'product' are null (again, because the device is not a webcam).

The attached patch solves the crash in my system.

[1] this call is in udev_mgr_new method, in udev-mgr.c"

And that's the same problem that I'm having.

---

### Post by lidex on 2011-08-29
> **rajeev1204 said:**
> I have a tv card installed.How is that related ?

You can check to see that's the problem by powering down, removing card, and powering up again. If that does work please comment on the bug tracker.

---

### Post by mc4man on 2011-08-29
> **ricsi-pontaz said:**
> There is a patch for this bug: 

[(https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)"][https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)]("[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/824243/comments/19)

But I don't know how to try this. Any suggestion?
Pretty simple - 
Install build deps of indicator-session
apt-get source indicator-session
Apply the patch
Build a new indicator-session package and install with gdebi or dpkg

---

### Post by lidex on 2011-08-29
> **mc4man said:**
> Pretty simple - 
Install build deps of indicator-session
apt-get source indicator-session
Apply the patch
Build a new indicator-session package and install with gdebi or dpkg

I think what (s)he's asking is how to apply the patch.

---

### Post by jerrylamos on 2011-08-29
Daily Build .iso 32 bit as of 28 August the drop down menu under the power switch applet is working.  Most of the time....

Jerry

---

### Post by mc4man on 2011-08-29
> **lidex said:**
> I think what (s)he's asking is how to apply the patch.
Many ways, 1 ex.,  using as of today's current source, using 1 terminal, start to finish
```
sudo apt-get build-dep indicator-session && \
sudo apt-get install patch fakeroot

```
```
mkdir is_build && cd is_build
```
```
apt-get source indicator-session && cd indicator-session-0.3.3.2
```
Now either grab the patch from Lp and place in the is_build folder or use gedit and C&P below  
```
 gedit ../bug824243.patch
```
Copy & Paste this into gedit, save, close gedit
```
--- src/udev-mgr.c	2011-08-25 18:42:14 +0000
+++ src/udev-mgr.c	2011-08-28 18:12:58 +0000
@@ -226,6 +226,10 @@
   
   vendor = g_udev_device_get_property (device, "ID_VENDOR_ID");
   product = g_udev_device_get_property (device, "ID_MODEL_ID");
+
+  if (!vendor || !product) {
+    return;
+  }
   
   if (action == REMOVE){
     if (g_hash_table_lookup (self->webcams_present, product) == NULL){

```
Then in same terminal (at the ~/is_build/indicator-session-0.3.3.2$ prompt
```

patch -p0 < ../bug824243.patch
```
```
dpkg-buildpackage -rfakeroot -D -us -uc
```

---

### Post by lidex on 2011-08-29
> **mc4man said:**
> Many ways, 1 ex.,  using as of today's current source, using 1 terminal, start to finish...<snip>   


Wow. Wasn't expecting that. Big fan of your work.

---

### Post by jon4248 on 2011-08-30
> **mc4man said:**
> Many ways, 1 ex.,  using as of today's current source, using 1 terminal, start to finish
```
sudo apt-get build-dep indicator-session && \
sudo apt-get install patch fakeroot

``````
mkdir is_build && cd is_build
``````
apt-get source indicator-session && cd indicator-session-0.3.3.2
```Now either grab the patch from Lp and place in the is_build folder or use gedit and C&P below  
```
 gedit ../bug824243.patch
```Copy & Paste this into gedit, save, close gedit
```
--- src/udev-mgr.c    2011-08-25 18:42:14 +0000
+++ src/udev-mgr.c    2011-08-28 18:12:58 +0000
@@ -226,6 +226,10 @@
   
   vendor = g_udev_device_get_property (device, "ID_VENDOR_ID");
   product = g_udev_device_get_property (device, "ID_MODEL_ID");
+
+  if (!vendor || !product) {
+    return;
+  }
   
   if (action == REMOVE){
     if (g_hash_table_lookup (self->webcams_present, product) == NULL){

```Then in same terminal (at the ~/is_build/indicator-session-0.3.3.2$ prompt
```

patch -p0 < ../bug824243.patch
``````
dpkg-buildpackage -rfakeroot -D -us -uc
```
Nice ex., worked good for me. Thanks.

---

### Post by mc4man on 2011-08-30
Just to note - this should be fixed in the next indicator-session upgrade

---

