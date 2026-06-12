---
title: "How Do I install EasyTether?"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by iTails on 2012-03-15
Hi, I'm trying to install EasyTether on Ubuntu from my phone because I have no internet. When I open the Deb package it opens in ubuntu software center and it wont let me install it. How do I install it without having to use software center?

I also read a thread saying it works better in WINE. But as I do not have internet access, I can't install WINE. How would I go about installing that as well just incase?

---

### Post by 3rdalbum on 2012-03-15
When I turn on tethering on my Android and plug it into the computer, Ubuntu automatically knows to get its internet connection from it.

I am using Androids built in tethering function, but the Easytether website says it uses "standard APIs" so it should be the same.

Or just use the standard Tether feature from Android? It is in Wireless And Networks in the Settings program, unless your phone came from an American carrier.

---

### Post by iTails on 2012-03-15
Yeah, Im running on Sprint off of my HTC Evo 3D. I rooted it for the sole purpose of tethering. The built in tethering in CM7.1 Alpha blocks HTTPS.

---

### Post by snkiz on 2012-03-15
try putting the deb in a folder all by itself. Then open a terminal and cd into that folder. once there run the command
```
sudo dpkg -i easytether*
```

What is the output?

---

### Post by iTails on 2012-03-15
Well, I got it to install, but its just going in loops trying to connect. Is there any way I can download WINE onto my phone and install it?

---

### Post by snkiz on 2012-03-15
You don't need it please explain loops? I've used easytether for quite some time. And found lots of ways to bugger it up.

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> You don't need it please explain loops? I've used easytether for quite some time. And found lots of ways to bugger it up.

When I do

```
easytether connect
```

It wont connect, but will keep trying to connect.

---

### Post by snkiz on 2012-03-15
Two possible reasons for that
1) you don't have usb debugging turned on in your phone
2) you have an adb shell connected to your phone

Wait, can you even use adb? if you haven't set that up esytether won't work either

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> Two possible reasons for that
1) you don't have usb debugging turned on in your phone
2) you have an adb shell connected to your phone

Could you explain to me what an ADB shell is? Im kind of new to Android.

---

### Post by snkiz on 2012-03-15
what verison of ubuntu are you on what model is your phone?
you can't use easytether til you've set up adb

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> what verison of ubuntu are you on what model is your phone?
you can't use easytether til you've set up adb



Im using 11.10 and my phone is the HTC Evo 3D CDMA with CM7.1 Alpha.

---

### Post by snkiz on 2012-03-15
ok while you phone is pluged in do 
```
lsusb
``` in the terminal that will list all connected usb devices your looking for the one that says htc something

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> ok while you phone is pluged in do 
```
lsusb
``` in the terminal that will list all connected usb devices your looking for the one that says htc something

Its not showing me anything HTC in terminal. What shows up is Syntech, my mouse and High Tech Computer Corp.

---

### Post by snkiz on 2012-03-15
from this liknk [http://forum.xda-developers.com/showthread.php?p=19446284]("http://forum.xda-developers.com/showthread.php?p=19446284")

```
gksu gedit /etc/udev/rules.d/99-android.rules
```

then put this in the file you open with gedit:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="####", SYMLINK+="android_adb", MODE="0666" GROUP="plugdev"
```

replace the # with the first 4 characters (before the ":") from the code for your phone then run in the terminal,

```
sudo service udev restart
```

thats the quick and dirty should get easytether working jist of it

---

### Post by snkiz on 2012-03-15
> **iTails said:**
> Its not showing me anything HTC in terminal. What shows up is Syntech, my mouse and High Tech Computer Corp.

High Tech Computer corp. = HTC

---

### Post by snkiz on 2012-03-15
did that help?

I am curious to know how you got cm 7 on your phone without having done this already?

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> did that help?

I am curious to know how you got cm 7 on your phone without having done this already?

I rooted my phone on a windows partition at Panera Bread lol. It didnt work. Its still doing the same thing.

---

### Post by snkiz on 2012-03-15
go over the steps again you missed something

---

### Post by snkiz on 2012-03-15
shoot my bad, you only need the 4 character part of the code for you phone I just looked at mine

---

### Post by iTails on 2012-03-15
I went over it again. Nothing has changed. I saved the page to copy/paste the config and put in my device ID

---

### Post by snkiz on 2012-03-15
see above

---

### Post by snkiz on 2012-03-15
> **iTails said:**
> I went over it again. Nothing has changed. I saved the page to copy/paste the config and put in my device ID

DO NOT COPY/PASTE quotes don't translate from the web

---

### Post by iTails on 2012-03-15
> **snkiz said:**
> DO NOT COPY/PASTE quotes don't translate from the web

OH so its all one line? *smacks head* Common sense is a blessing.

---

### Post by snkiz on 2012-03-15
> **iTails said:**
> OH so its all one line? *smacks head* Common sense is a blessing.

yes it is but I don't think that matters. The point is this " registers as something else when you copy it from web pages some times.

---

### Post by iTails on 2012-03-15
Alright, I dont think Im doing this right. Could you possibly upload a file with the config to copy/paste?

---

### Post by snkiz on 2012-03-15
> **iTails said:**
> Alright, I dont think Im doing this right. Could you possibly upload a file with the config to copy/paste?

here's mine just change the id to yours I don't have an htc. there's two lines in my file, that's because I have two phones you can ignore the second one. remove the txt extension I had to add that to upload it.

don't forget to restart udev, possibly reconnect your phone after as well.

---

### Post by PabloTempe on 2012-03-15
I gave up on EasyTether and loaded a program called: "ClockworkMod Tether." It has a Linux version which works great though you have to load it from the Terminal. If you can do that, you're good to go. ~pablo

---

### Post by snkiz on 2012-03-15
I corrected the instructions in my other post

---

### Post by snkiz on 2012-03-15
> **PabloTempe said:**
> I gave up on EasyTether and loaded a program called: "ClockworkMod Tether." It has a Linux version which works great though you have to load it from the Terminal. If you can do that, you're good to go. ~pablo

you would still need the udev rule all these programs use the adb apis

---

### Post by iTails on 2012-03-15
Now when I put in the ID, do I need to put the first or last part?

ex. 0000:0000

Because I noticed you only used one of the id's

---

### Post by snkiz on 2012-03-16
> **iTails said:**
> Now when I put in the ID, do I need to put the first or last part?

ex. 0000:0000

Because I noticed you only used one of the id's

the first (4 digit) part. afaik

---

### Post by iTails on 2012-03-16
Hmm, I still dont know why its not working. For some reason when I use standard tether it allows me to only connect to google if that helps.

---

### Post by snkiz on 2012-03-16
I'm at a loss, you builtin tether doesn't matter at all easytether spofs the phone (witch is why it works on verizion) without adb installed, witch is PITA trying to download on your phone then copy to your computer. there isn't much debugging you can do.
 I'll go through it one more time.

in a terminal:
```
lsusb
```
your looking for a line like this, only for your brand:

Bus 001 Device 016: ID 05c6:9024 Qualcomm, Inc.

take the first bit of the id. (in my case the 05c6) and open gedit as root
```
gksu gedit /etc/udev/rules.d/99-android.rules
```
in that file put this using your device id (all one line watch the quotes they don't copy well):
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="05c6", SYMLINK+="android_adb", MODE="0666" GROUP="plugdev"
```
save it, then restart udev in the terminal
```
sudo service udev restart
```
unplug your phone and plug it back in the try your easytether command.
thats it. Any more troubleshooting will require adb

Don't forget to turn on usb debugging on the phone.

---

### Post by iTails on 2012-03-16
Well, as a last ditch effort. How do I aquire ADB?

---

### Post by snkiz on 2012-03-16
> **iTails said:**
> Well, as a last ditch effort. How do I aquire ADB?

xda. that link I gave you has a full explnation just the udev rule is out of date.

---

### Post by iTails on 2012-03-16
> **snkiz said:**
> xda. that link I gave you has a full explnation just the udev rule is out of date.

Alright, thank you so much for trying to help. I'll try to get to a public wifi hotspot and try my luck with the XDA link.

---

### Post by FulciLives on 2012-03-16
I know this may seem totally off track BUT if the OP is THAT frustrated with getting EasyTether to work then may I suggest the ClockworkMod Tether app.

I was able to download this from the Android Store and get it running on Ubuntu 12.04 Beta 1 (32-Bit) without any trouble and it works a treat.

The only downside I see is that you are only unlimited for 14 days ... after that ... you need to pay $4.99 US Dollars.

I should note that my Android phone is rooted and my carrier normally blocks tethering unless you pay extra for it (yet it seems to be working A-OK right now for me).

---

### Post by snkiz on 2012-03-16
> **FulciLives said:**
> I know this may seem totally off track BUT if the OP is THAT frustrated with getting EasyTether to work then may I suggest the ClockworkMod Tether app.

I was able to download this from the Android Store and get it running on Ubuntu 12.04 Beta 1 (32-Bit) without any trouble and it works a treat.

The only downside I see is that you are only unlimited for 14 days ... after that ... you need to pay $4.99 US Dollars.

I should note that my Android phone is rooted and my carrier normally blocks tethering unless you pay extra for it (yet it seems to be working A-OK right now for me).
As I've already stated (and just confirmed by going to clockwork's website) you need functioning udev rules to make these tethering apps work. Clockwork's site even go so far as to say you need an adb environment to make it work. I'm sure the OP appreciates the help, but if you can't even be bothered to read the whole thread or do even 30 seconds of research..(yes that's how long it took me to find out about clockwork.) Then your not really helping.

for reference;
[https://play.google.com/store/apps/details?id=com.koushikdutta.tether&hl=en]("https://play.google.com/store/apps/details?id=com.koushikdutta.tether&hl=en")
and
[http://clockworkmod.com/tether/drivers]("http://clockworkmod.com/tether/drivers")

---

### Post by iTails on 2012-03-19
Just a quick bump, but Kernel 3.3 has been released. They mention something about re-adding native Android support?

[http://kernelnewbies.org/Linux_3.3](http://kernelnewbies.org/Linux_3.3)

> 1.1. Android merge

For a long time, code from the Android project has not been merged back to the Linux repositories due to disagreement between developers from both projects. Fortunately, after several years the differences are being ironed out. Various Android subsystems and features have already been merged, and more will follow in the future. This will make things easier for everybody, including the Android mod community, or Linux distributions that want to support Android programs.

Would this effect ADB or no?

---

