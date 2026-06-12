---
title: "new install 3 questions"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by päikese on 2008-06-14
Hi, I have just installed Hardy Heron (first time linux user) and am really impressed.
BUT
1) where can I get a copy of the install picture (brown with art nouveauish heron) for my desktop?
2) My scanner isn't easily recognised. Trust easy Connect 19200 parallel port. I have read through the xsane documentation and several links detailing how to get it recognised but after playing around with commands at the terminal I still have no scanner. Where should i post more detailed help requests for that?
3) I was using a hacked xbox headset in windows for skype using xbaudio drivers from redcloud. However xubuntu didn't even acknowledge that i had plugged the headset into a usb port let alone ask for drivers. Where best to start asking questions about this?
thanks all

ooooohh...ubuntu!

---

### Post by steveneddy on 2008-06-14
Picture is:

Go to the Desktop and right click, and choose [COLOR="Blue"]Change Desktop Background[/COLOR].

Select the wallpaper that suits your needs.

If it's not there, go to 

**System --> Administration --> Synaptic Package Manager**

In the big window on the upper right, click in the window and start typing

```
gnome-backgrounds
```

right click [COLOR="Blue"]gnome-backgrounds[/COLOR] and select [COLOR="Blue"]Mark for Installation[/COLOR].

A button at the top has a green check that says [COLOR="Blue"]Apply[/COLOR]. **Click this button**.

After install, go back to the desktop and repeat step one.

---

### Post by ibuclaw on 2008-06-14
Answer to Q1)
It is in the package named "**ubuntu-wallpapers**"
```
sudo apt-get install ubuntu-wallpapers
```
Once install, the wallpaper for Ubuntu is inside your "**/usr/share/backgrounds**" folder.
I think the image name is "**warty-final-ubuntu.png**"


Suggestion for Q3) 
With your device inserted into the USB port, can you open a terminal and post the output of this command please:
```
lsusb
```

Regards
Iain

---

### Post by steveneddy on 2008-06-14
Hmmm...the headset is a good one.

Try [here]("http://forums.xbox-scene.com/lofiversion/index.php/t387861.html") and [here]("http://www.xbox-linux.org/wiki/Main_Page") as a place to start.

:D

---

### Post by päikese on 2008-06-14
hi, I checked th desktop settings already but didn't find the right picture and it wasn't available as part of the gnome package. the picture I want is the one thats shows as hardy heron is being installed. It is basically a brown background with a large sketched picture of a heron. If anyone knows the location of that picture could they let me know. cheers

---

### Post by päikese on 2008-06-14
ok you guys are tdq.
here is the result of lsusb (I will find out what that means oneday)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:0283 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 001: ID 0000:0000  

and I think i've found the picture in ubuntu-wallpapers so ta for that.

---

### Post by ibuclaw on 2008-06-14
lsusb displays the **Vendor** and **Product** ID of all connected USB devices.

Using this information I can track down the current working state on the device.

But, as [found here.]("http://www.qbik.ch/usb/devices/showdev.php?id=3952") It seems that the device won't work with Linux yet, because
> Bluetooth is not discoverable on either end (at present).Un-Quote:


Regards
Iain

---

### Post by päikese on 2008-06-14
Thats annoying, I'm going to have to spend money on a new headset!
The bluetooth bit is weird, there's no way this is a bluetooth device in the "I know nothing about comtoopers but bluetooth aint got no wires innit" sense of the word.

Thanks for that.

Now for the stone age scanner....

After double checking your link and scratching my head this isn't the same device despite the id number being the same. My headset is an old wired headset from the origional xbox circa 2002/3 and the link describes the wireless headset adapter. Make what you will of that! I guess I'm still going shopping!

---

### Post by ibuclaw on 2008-06-14
Oh, OK then.

You're device must be deprecated then...

Perhaps a small hack into the ALSA drivers will fix it then.

Install apt-src and download the alsa-base sourcecode.
```

sudo apt-get install apt-src
mkdir -p ~/src && cd ~/src
sudo apt-src install alsa-base
sudo chown $USER:$USER alsa-driver*
cd alsa*
mousepad alsa-kernel/usb/usbquirks.h

```

Then scroll down to the bottom and insert this **before **the "**#undef USB_DEVICE_VENDOR_SPEC**" line.
```

{
        /*
         * Hack for XBox Headset
         */ 
         USB_DEVICE(0x045e, 0x0283),
         .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
                .vendor_name = "Microsoft Corp.",
                .product_name = "",
                .ifnum = QUIRK_ANY_INTERFACE,
                .type = QUIRK_COMPOSITE,
                .data = (const struct snd_usb_audio_quirk[]) {
                        {
                                .ifnum = 0,
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE
                        },
                        {
                                .ifnum = 1,
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE
                        },
                        {
                                .ifnum = -1
                        }
                }
        }
},

```
Save and quit. Then type in:
```
./configure --with-cards=usb-audio
make
sudo make install

```
Then Reboot with the device still plugged in. If Ubuntu still doesn't pick it up, try putting this in instead (replace the above source)

As a final plea of hope, you could try ./configure on its own, then make and make install. (But be sure to reinstall the alsa-base package from the repository).
```
./configure
make
sudo make install

```

If you still can't get anything.
I'm afraid there's not much else I can do.

So you'll just have to:
```
sudo aptitude reinstall alsa-base
```

Regards
Iain

---

### Post by päikese on 2008-06-15
Hi Iain,
First, thanks for your help so far, it's appreciated. I went to bed before you gave me all that stuff to do yesterday, 2 hours ahead of UK time here.
But today I have got as far as the sudo make install instruction.
All went well except for a few minor crisies. gedit wasn't installed, I needed to use sudo at the beginning of virtually everyline blah blah blah..
Anyway stupid question time..how will I know if the headset is recognised?
I have checked settings manager-sounds but it shows only my soundcard and 
MPU-401 UART which googles as a midi device.
I have also installed alsamixergui and assume that if the headset is recognised it will show up there. Is that correct?
cheers
Eric

---

### Post by ibuclaw on 2008-06-15
Yes, if the headset is recognised, it should show in the sound config app.

Although, I it was just a quick hack into the file anyway. It just assumes that the headset is just a generic usb input/output device.

I would be surprised if it worked.

And sorry about gedit (forgot you ran xubuntu).

Infact, on second thoughts. I would probably choose the later code (taking the first one down now) and compile with that (Also cleaning up the post a bit to make it more clearer).

But, as I said, it was a shot in the dark for a device that "doesn't have support yet".

Regards
Iain

---

### Post by Sef on 2008-06-15
> gedit wasn't installed, 

Xubuntu uses mousepad isntead of gedit.

---

### Post by päikese on 2008-06-17
> **Sef said:**
> Xubuntu uses mousepad isntead of gedit.

not any more it doesn't!\\:D/
Soon as the kids are in bed I will try your stuff Iain.
Thanks for getting back to me.
'tis appreciated

---

### Post by päikese on 2008-06-19
hi there Iain, I'm afraid that none of it worked. Still no headset. No worries. Thanks for trying.

---

