---
title: "mtp://[usb:002,009]/  What is this?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-05-13
Hi Guys,

SO I thought I'd give 14.04 a spin and most of it works for me.
One frustrating thing though is trying to sync my Sony Walkman Digital Media Player.
I listen to a couple of podcasts before I go to sleep at night.
I have been using a script I wrote to download the latest episodes using the gpodder client and then to sync them with the Walkman.
Well as of 14.04 the command gpo sync no longer works with my Walkman.
SO I thought I'd just have the script copy the mp3s to the correct folder on the Walkman.
I did ctrl+L in nautilus and found the address of the Walkman was:
```

mtp://[usb:002,006]/

``` 
That worked until the next time I plugged in the mp3 player then the address was
```

mtp://[usb:002,007]/
```
In fact every time I plug it in the usb number increases by 1.

Why is this?
Is there anything I can do about it?
Is there a way to copy files via a script to a drive that seems to change it's address every time it is plugged in?

---

### Post by squakie on 2014-05-14
The USB "address" is always subject to change - and why for such things as USB disks, etc., using the UUID is the recommended way since it is unique to the device.

So, a couple of questions:

(1) currently you can access the device if you get the address set?

(2) with the device plugged in, try this in a command line:  sudo blkid <press enter>    .  It will show the UUID's for any disk-type device on the system.  Can you see your device?

(3) check /media/<your userid here> - is the device mounted there?

---

### Post by GrouchyGaijin on 2014-05-14
> **squakie said:**
> The USB "address" is always subject to change - and why for such things as USB disks, etc., using the UUID is the recommended way since it is unique to the device.

So, a couple of questions:

(1) currently you can access the device if you get the address set?

(2) with the device plugged in, try this in a command line:  sudo blkid <press enter>    .  It will show the UUID's for any disk-type device on the system.  Can you see your device?

(3) check /media/<your userid here> - is the device mounted there?

Thank you for the reply.
1. Yes 
2. I get:
```
/dev/sda1: UUID="10bd6c4f-e111-44df-9bf5-dc6a158d44b3" TYPE="ext4" 
/dev/sda5: UUID="e807c351-7667-4dda-ae6f-54242257fff4" TYPE="swap" 
/dev/sdb1: LABEL="Elements" UUID="12B0DF25B0DF0DDB" TYPE="ntfs"
```

It does not seem that any of these are the Walkman.
3.  The only device mounted in media is my external hard drive.

The Walkman does show up in the list

---

### Post by squakie on 2014-05-14
Right-click on the Walkman icon in the file manager and select properties - it should show the path to the file system/device.  Paste back here what that is.

It may be that a udev rule will need to be created for that USB manufacturer/product id to mount it at a specific location whenever it is plugged in so that the path will always be known to your script.

---

### Post by GrouchyGaijin on 2014-05-14
Right clicking doesn't show the path, but hovering does.  At the moment the path seems to be:
```
mtp://[usb:002,006]/
```

---

### Post by squakie on 2014-05-14
May take me a little bit, but I'll work on a udev rule for you and see if it helps or not.

---

### Post by GrouchyGaijin on 2014-05-14
Thank you!
I really do appreciate the help.
What does mtp mean?
It seems there are two options of syncing a device with gPodder: mtp and file system based.  Unfortunatly neither is working in Ubuntu 14.04
In 14.04 this Walkman now comes up with Storage Media as the Walkman's root directory.  I do not remember anything called Storage Media in 12.04.
I'm also attaching a screen shot showing the Walkman open - I need to put the files in the Music directory.

---

### Post by pfeiffep on 2014-05-14
[COLOR=#000000]@GrouchyGaijin, [/COLOR]I'm interested in learning and have no solutions to your music dilemna, but I can offer this ...> [COLOR=#000000]What does mtp mean?[/COLOR]

Media Transfer Protocol

Hopefully @[COLOR=#000000]squakie will have some 'real solutions' for you[/COLOR]

---

### Post by squakie on 2014-05-14
I'm going to see if I can get some tonight late tonight to work on the rule.  To do so, I need the USb "id" for the device - it is in a xxxx:yyyy format and can be seen by plugging the device in and doing lsusb from a terminal.  You should see your device.  Copy the line for your device and post it back here.  BTW - the "xxxx" portion is called the manufacturer id and the "yyyy" is called the product id.  They uniquely identify a USB device.  I need that to write the rule.

---

### Post by GrouchyGaijin on 2014-05-15
This is what I see when I run lusb:
```

Bus 002 Device 007: ID 054c:0385 Sony Corp. Walkman NWZ-E436F

```

---

### Post by squakie on 2014-05-16
Having a hard time with the rule-thing since I don't have your device.  Basically, we want to create an alias device when the device is recognized, so you can then always mount from that device.  I don't know if this will work or not.

Would you mind trying the following:

sudo gedit /lib/udev/rules.d/98-wlakman-nwz-e436f.rules  to create a new file and put these in it:
# 
#  set symlink for Walkman NWZ-E436F
#

SUBSYSTEM=="usb", ATTR{idVendor}=="054c", ATTR{idProduct}=="0385", SYMLINK+="nwz-e436f"

Then save the file and close the editor.

Before we go any further, plug the device in and see if a new device of /dev/nwz-e436f is now visible. 

If so, you should be able to sudo mount /dev/hwz-e436f <you mount options - like file system type> <your mount point - example: /home/<your userid>/hwz-e436f>.

If it does mount, and if you are able to access it, then you can add the mount to the fstab.  That way 2 things will happen automatically:  when the device is plugged in it will be at /dev/nwz-e436f which would get mounted to some mount point - available for your process.

You could take it a step further and add RUN+="<your script path name here>" to the end of the rule statement, then change your script to look at your mount point - for example: /home/<your userid>/hwz-e436f>.

But, a step at a time.  Try the rule - then plug in the device and see if /dev/hwz-e436f shows.  You can try the rest if you want.

Sorry I have to do it this way but without your device it's pretty hard for me to try to test this.

---

### Post by GrouchyGaijin on 2014-05-16
Well I think you are on the right track!
I can see it in /dev/
but get this error message when trying to mount it:
```

$ sudo mount /dev/hwz-e436f
mount: can't find /dev/hwz-e436f in /etc/fstab or /etc/mtab



```

---

### Post by squakie on 2014-05-16
Well, lets try this in a terminal window:

cd ~
mkdir dwetest
sudo mount -t msdos /dev/hwz-e436c /home/<your user id here>/dwetest 

*IF the mount works, try:

cd dwetest
ls

The syntax of mount is basically  mount -t <file system type> device <folder to mount to>

---

### Post by GrouchyGaijin on 2014-05-16
Rats
```

mount: special device /dev/hwz-e436c does not exist

```

---

### Post by squakie on 2014-05-16
Hummmmm.....we may be beyond what I can do right now.  I'll do some reading on the net and hopefully in the mean time someone with more knowledge might post.

Sorry!

---

### Post by GrouchyGaijin on 2014-05-16
Thanks man!  I sincerely do appreciate the effort!

---

### Post by squakie on 2014-05-16
Hey - just noticed - I had a typo in the mount.  Try:

sudo mount -t msdos /dev/hwz-e436f /home/<your user id here>/dwetest 

I had e436c instead of e436f the first time.

---

### Post by GrouchyGaijin on 2014-05-16
Unfortunately I still get:
```

mount: special device /dev/hwz-e436f does not exist

```

---

### Post by GrouchyGaijin on 2014-05-16
Well I found a **DIRTY** solution that does not work nearly as well as the old gpo sync command used to.
Basically it involves using mtp-tools.
See the article **[[COLOR=#ff0000]here[/COLOR]]("http://lucky13linux.wordpress.com/2009/07/29/a-sync-script-for-mtp-device/")** for a detailed how to - like I said it works, kind of.
I keep getting an error that causes no files to be copied from the source directory if there is a file in the source directory that has already been sent to the device.
That could just be a result of the super basic way I am moving the files.
```

mtp-sendfile ~/gpodder-downloads/Podcast1/*.mp3 121

```

The 121 is the name of the destination directory on the device in mtp-tool speak.
To get that number you first have to run:
```
mtp-folders | grep -i <directory name>
```
but you only need to do that once, since mtp-tools uses the device ID the number used for the directory doesn't seem to change.

I'm not going to mark this as solved in the hope that someone much smarter than I will come along with a better solution.

---

### Post by squakie on 2014-05-16
Geez - that is kind of a pain!  A lot of us are having problems getting USB devices of varying sorts to mount - my camera included.  There is a bug report filed so I sure hope they figure it out soon.  Just making the change from 13.10 to 14.04 screwed me up!

Sorry I can't be of more help - we're just beyond my knowledge at this point.

---

### Post by Luke M on 2014-05-16
Maybe jmptfs or mtpfs will do what you want?

---

### Post by GrouchyGaijin on 2014-05-17
Problem solved!

All (sarcasm there) it took was to launch an xfce session instead of the default Unity.

See the attached screenshot - my Sony Walkman is once again behaving like a file based system :popcorn:

As a bonus, most of the other slight annoyances I had experienced seem to have vanished as well.[ATTACH=CONFIG]253238[/ATTACH]

---

