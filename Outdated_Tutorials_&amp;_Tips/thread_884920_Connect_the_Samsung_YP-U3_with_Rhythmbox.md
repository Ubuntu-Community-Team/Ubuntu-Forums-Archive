---
title: "Connect the Samsung YP-U3 with Rhythmbox"
date: 2008-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Martje_001 on 2008-08-09
Today I bought a Samsung YP-U3. When I came home I found out it has no drag & drop support with Ubuntu (nor with Windows). After searching on google the only solution was to install gnomad2, to transfer my music.

After some research I found out that gnomead2 uses the [MTP](http://en.wikipedia.org/wiki/Media_Transfer_Protocol) protocol. Now, the happy news, Rhythmbox support MTP also! I'll show you how:
[SIZE="4"]
**Step 1:**[/SIZE]
Start Rhythmbox

[SIZE="4"]**Step 2:**[/SIZE]
[IMG]http://82.93.77.136/mbastiaan/forums/YP_U3-1.png[/IMG]
Go to Edit --> Plugins.

[SIZE="4"]**Step 3:**[/SIZE]
[IMG]http://82.93.77.136/mbastiaan/forums/YP_U3-2.png[/IMG]
Enable the plugin 'Portable Players - MTP'

[SIZE="4"]**Step 4:**[/SIZE]
[IMG]http://82.93.77.136/mbastiaan/forums/YP_U3-4.png[/IMG]
Go to Applications --> Accessoires to start a terminal. There type:
```
gksudo gedit /etc/udev/rules.d/libmtp.rules
```
.

You now should see a window (an empty document). Add these lines to it:
```
#Samsung YP-U3
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="666"

```
and save it. Close the terminal.

[SIZE="4"]**Step 5:**[/SIZE]
[IMG]http://82.93.77.136/mbastiaan/forums/YP_U3-3.png[/IMG]
Drag & Drop your music to the new detected device!

---

### Post by be4truth on 2008-08-10
Hi, thx for this post but where is the Devices tab? I can't find it.

---

### Post by Martje_001 on 2008-08-10
Hmm, maybe you need to do this first (I think I forgot to mention this):

Go to a terminal and typ:
```
gksudo gedit /etc/udev/rules.d/libmtp.rules
```
and add these lines:
```
#Samsung YP-U3
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="666"

```
Save it, close the terminal, and now the devices tab, along with your Samsung, should be visible in Rhytmbox.

---

### Post by Martje_001 on 2008-08-10
Ow, and you should have the package 'libmtp' installed.

---

### Post by be4truth on 2008-08-10
> **Martje_001 said:**
> Hmm, maybe you need to do this first (I think I forgot to mention this):

Go to a terminal and typ:
```
gksudo gedit /etc/udev/rules.d/libmtp.rules
```
and add these lines:
```
#Samsung YP-U3
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="666"

```
Save it, close the terminal, and now the devices tab, along with your Samsung, should be visible in Rhytmbox.

Nope, didn't work. libmtp7 is installed. I am on Hardy 32bit. The U3 shows only in the places menu as 'U3'.

---

### Post by Martje_001 on 2008-08-11
Does [gnomad2]("http://ubuntuforums.org/attachment.php?attachmentid=59537&d=1202880735") work?

If not, what's the ouput when running it in a terminal?

---

