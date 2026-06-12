---
title: "USB not seen"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Southmin on 2012-12-16
I cannot seem to make Ubuntu see a USB memory stick. All the other devices are shown. It sees my USB wireless network device fine.
Can anyone tell me how I can store files onto a USB memory please?

---

### Post by ty74 on 2012-12-16
Have you tried all the slots on your computer. It could be that the slot doesn't work. You could also try moving all the stuff off the flash drive and see if it works then.

---

### Post by DuckHook on 2012-12-16
with the stick inserted, do:

```
lsusb
```Please post results back to this thread between the [CODE][\CODE] markers, but changing \ to /.

Also, please provide following info:

1. Have you tried different sticks? If so, is problem universal or just one in particular?
2. Size of stick, make and model.
3. Brief description of computer (cpu, RAM, etc)
4. What flavour and version of OS are you using?

---

### Post by Southmin on 2012-12-17
It's an Acer computer. 5 years old with AMD Sempron processor and 2G RAM.
My wireless network adaptor works in every USB socket and 2 different memory sticks are not seen in any USB socket.
It's Ubuntu 12.10 32 bit downloaded and installed very recently.

---

### Post by squakie on 2012-12-17
Please post the output the DuckHook requested - it's really fruitless for us to give any advice until we see that.  It could be (but doubt) a udev problem, it could be a permissions problem, it could be all kinds of things.

So, with one of the flash drives plugged in, please do the following in a terminal and post back the results:

lsusb

sudo lsusb (in case it's some sort of permissions problem)


How were the flash drives formatted and in what format?

---

### Post by audiomick on 2012-12-17
> **squakie said:**
> 
So, with one of the flash drives plugged in, please do the following in a terminal and post back the results:

lsusb

sudo lsusb (in case it's some sort of permissions problem)

do both. As far as I know, if it is a permission problem ( which would be the udev that has been mentioned, I think) the stick will not show up in the listing without sudo, and will with sudo.

---

### Post by Southmin on 2012-12-17
Thanks for the replies, I'll get on to that in a day or two (rather busy at the moment) and let you know what results.

---

### Post by squakie on 2012-12-18
> **audiomick said:**
> do both. As far as I know, if it is a permission problem ( which would be the udev that has been mentioned, I think) the stick will not show up in the listing without sudo, and will with sudo.

That's right.  This used to happen a few releases ago and you had to put udev rules in for specific devices or "classes" of devices and change the permissions to include other than root.  And you're right again - that's why I requested the sudo version as well. ;)

---

### Post by Southmin on 2012-12-20
I don't know if this makes any difference, but on reading my original message I may have unintentionally misled you, for which I apologise.
When I click on "Go" then "Computer" the USB device is seen (although the smaller 128M one of them shows up as a hard drive) but I cannot access them or write to them. They both have files on them in FAT32.
The computer tells me that it has no application in which to open them.

---

### Post by audiomick on 2012-12-20
Ah, that is a different kettle of fish altogether. ;)

What I would try, although it is all thrashing around in the dark:

Look at it with gparted (or the hardware utility) at see what that says about it. Might give you a clue about irregularities on the file system or something.

Can you, by the way, access these USB devices from another machine? Is it likely that the device itself has a problem, or can you say for sure that they are only not accessible on this one machine?

Do you use the USB sticks with windows machines? If they are used exclusivly with Linux machines, you might want to think about re-formatting them to a Linux file system. That will allow, for instance, applying Linux permissions to the files on there.

---

### Post by honeybear on 2012-12-20
> **Southmin said:**
> I cannot seem to make Ubuntu see a USB memory stick. All the other devices are shown. It sees my USB wireless network device fine.
Can anyone tell me how I can store files onto a USB memory please?

try these is you see it:

plug and unplug it.

```
dmesg

```
```
/sbin/fdisk -l
```
```
lsusb
```
```
/sbin/blkid 
```

post what you see we can help we are not n00bs :)

---

### Post by Southmin on 2012-12-20
I know that the files on them are readable on other machines, in fact I added a few jpegs to the smaller one only yesterday.

---

### Post by fdrake on 2012-12-20
```
sudo apt-get install parted
sudo parted -l
```
post output pleasee

---

### Post by Southmin on 2012-12-30
Very strange! After an update the USB problem appears to have resolved itself. I'll just keep an eye on whether or not this is a permanent state of affairs. Thanks people, for your offers of help.

---

