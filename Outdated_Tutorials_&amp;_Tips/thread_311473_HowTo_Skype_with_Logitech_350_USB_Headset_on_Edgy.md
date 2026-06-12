---
title: "HowTo: Skype with Logitech 350 USB Headset on Edgy"
date: 2006-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by NobodySpecial on 2006-12-02
Many thanks to the devs for all their hard work, because now Skype and the Logitech 350 USB Headset work *great* on Edgy!

First be sure ALSA is working right.  If you are having problems, check out [Gandalf's thread.]("http://www.ubuntuforums.org/showthread.php?t=32063")

At this point I recommend you plug your headset into a USB and reboot if you haven't already, as it will be easier to do this from a cold boot.

Next, see what usb devices are detected:
```
lsusb
```
You might see one or more listings for Logitech such as:
> Bus 002 Device 002: ID 046d:c223 Logitech, Inc.
Check which sound cards are recognized:
```
cat /proc/asound/cards
```
Here is what mine shows:
> 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xdf00, irq 74
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:02.0-8.2, full speed
So card 0 is my Audigy and card 1 is my 350 headset.

Check which sound devices are recognized:
```
cat /proc/asound/devices
```
Here is part of what mine shows:
> 17: [ 1- 0]: digital audio playback
18: [ 1- 0]: digital audio capture
19: [ 1]   : control
So my headset is recognized as soundcard device 1-0 (yours may be different).
Now the part of the puzzle to make this work (thanks to [Josh Goodwin]("http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/2006/05/06/logitech-usb-desktop-microphone-in-linux")):
```
gedit ~/.asoundrc
```
and enter the following:
```
pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:1,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}
```
Note the line above: capture.pcm "hw:1,0"
 You can change it to 2,0 or whatever your system recognizeds your headset is as per the command output above.

Next adjust headset sound levels with this command:
```
alsamixer -c 1
```
Turn speaker and mic up appropriately and press "m" to unmute if neeed.
Note that the "-c 1" in the above command is the same soundcard device found with the "cat /proc/asound/cards" command.  Change to "-c 2" or whatever required.

Test the sound by playing a song with your favorite media player.  Both XMMS and Beep Media Player have a sub-menu for "Device settings" then "Audio device" and you can choose "Logitech USB Headset".  If you cannot hear music, then go to your main menu at System -> Preferences -> Sound and change settings as needed until you can hear.

To test recording, use Applications -> Sound & Video -> Sound Recorder.  Try to record something then play it back.  If you cannot pick up anything, again go to your main menu at System -> Preferences -> Sound and change settings as needed until it works.

Now that we have out headset working, we can install Skype.  Gone are the days of drudging up obscure QT libraries and running "hijacker" programs.  Simply:
```
sudo gedit /etc/apt/sources.list
```
Then add this line:
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
Then do the following:
```
sudo apt-get update
sudo apt-get install skype
```
Run via Applications -> Internet -> Skype

Under Skype, be sure to select Tools -> Options -> Sound Devices and choose "Logitech USB Headset" where appropriate.

---

### Post by amonsul on 2006-12-19
it doesnt work for me. I have a Logitech USB HEADset and microphoe doesnt work.

this is my output in the terminal

> amonsul@amonsul:~$ lsusb
Bus 006 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 046d:0a02 Logitech, Inc. 
Bus 004 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
amonsul@amonsul:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 66
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.1-2, full speed
amonsul@amonsul:~$ cat /proc/asound/devices
  2:        : timer
  3: [ 1- 0]: digital audio playback
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control
  6: [ 0- 1]: digital audio playback
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control
amonsul@amonsul:~$ 




When i configure "gedit ~/.asoundrc" nothing happens. I reboot the computer and i have the same issue.

I think USB HEadset are generally unsupported in Ubuntu.... :(

---

### Post by scrooge_74 on 2006-12-19
i once had to help someone configure a usb headphone in XP and it took me about 30 minutes to get it working and still I was not to convince of the result.  So from all the editing you are doing I feel this is one think XP users can't easily throw at Linux users.

---

### Post by fbarsoba on 2006-12-20
Hi,

I have Ubuntu 6.10 edgy and the headset logitech 350 works almost fine... I plug it, and it is detected correctly.. I only have to change the option in skype, in tools/sound devices.. However, the volume control does not seem to work. I can mute the microphone pressing the button, but cannot increase or decrease the volume.. Any idea?

---

### Post by NobodySpecial on 2006-12-21
amonsul - the output you posted looks fine.  Did you cut and paste as instructed?  What do you mean "nothing happens"?  Can you play music in XMMS?  Can you record sound in Sound Recorder?  Can you do the test call in Skype?

fbarsoba - I haven't found a way to adjust the sound either.  If anybody reading this has found a way, please post in the forum.

---

### Post by styracosaurus on 2007-01-07
Has anyone had any experience with the 250 model?

---

### Post by ratondeau on 2007-01-10
Hello,

I followed this guide too but cannot persuade skype to work.

Ifollowed the guide of gandalf earlier end everything went fine. 

Then I did the following:

```
cat /proc/asound/cards
```
```

c 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xd5003000, irq 225
 1 [U0x6980x2003   ]: USB-Audio - USB Device 0x698:0x2003
                      USB Device 0x698:0x2003 at usb-0000:00:02.1-1.1, full speed
 2 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:02.1-1.4, full speed
 3 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
at /proc/asound/cards

```

so it is card 2

edit .asounrc in homedir  and change line to card 2:
```
gedit .asoundrc
```
```

pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:2,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}

```

saved und typed

```
alsamixer
```
to get this output:
```
 Card: NVidia CK804                                                           &#9474;
&#9474; Chip: Realtek ALC850 rev 0                                                   &#9474;
&#9474; View:  Playback  Capture [All]                                               &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;    Shared     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;OO&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;    L&#9492;&#9472;&#9472;&#9496;R    &#9474;
&#9474;                                                                    CAPTUR    &#9474;
&#9474;   71<>71      0      55<>55    0<>0                71        0      0<>0     &#9474;
&#9474; < Master >Master M    PCM    Surround Surround   Center    LFE      Line     &#9474;

```

so the .asoundrc seems to do nothing because I cannot change the right device. Also if I select the Logitech USB Device in Skype there is the ringing and after that a problem with sound device...but not always

Another problem is that the headset changes positions randomly as it is now on 2 before on 0 and sometimes on 3.

So what could I do to get things to work or have I dine something wrong?

Greets

Matt

---

### Post by bodhi.zazen on 2007-01-10
Nice How-to

This thread has been added to the UDSF wiki.

[http://doc.gwos.org/index.php/Skype_with_headset]()

---

### Post by dvarsam on 2007-01-20
Hello!

[QUOTE=NobodySpecial]Many thanks to the devs for all their hard work, because now Skype and the Logitech 350 USB Headset work *great* on Edgy![/quote]

Can you please add a snapshot of your product "**Logitech USB Headset**" on your original "HowTo" post?
It is always better to add a picture of the product you are talking about...

Thanks.

P.S.1> If you don't know how to do this:

1. visit the site: [www.photobucket.com](www.photobucket.com)

2. Create an account inside that site.

3. Upload your product's picture in that site.
Note: If you don't have a picture of your product, you can search for one in the internet.

4. Under the list of all your uploaded pictures:

a. Click on the right of the box named "IMG Code" & the text named "[I M G]http://i69.photobucket.com/albums/i58/your_account_name/your_picture's_name.png[/I M G]" will be selected.

b. Perform a copy (on the selected text) & paste it inside your original post.

---

### Post by alextj on 2007-02-07
If someone is having problem adjusting volume of USB microphone (and/or if recording only gives you silence), here is **how i think it should be done**:

1. Look up for your USB card number (microphone) as the guide above explains: [COLOR="DarkRed"]cat /proc/asound/cards[/COLOR]. I am using Logitech USB Mic, which shows as "USB-Audio - AK5370" and in my case it has card number 2.
2. Start [COLOR="DarkRed"]alsamixer[/COLOR] with option [COLOR="DarkRed"]-c[/COLOR] followed by your card number, like this: [COLOR="DarkRed"]alsamixer -c 2[/COLOR]
3. Then you need to switch to "capture" view mode, do so by pressing [COLOR="DarkRed"]F4[/COLOR] on keyboard. Then you will see volume adjustments for your microphone.
That's it.

By default, if you do not specify your card number in alsamixer options it will show only the first audio device. Also the default view mode is "playback", which has nothing to do with capturing or microphone, as I understood. That's why we need to switch view mode to "capture", by pressing F4 (F3 - Playback, F4 - Capture, F5 - All).

Alternatively you can use command [COLOR="DarkRed"]alsamixer -c 2 -V capture[/COLOR] or [COLOR="DarkRed"]alsamixer -c 2 -V all[/COLOR] to see volume adjustment for microphone without pressing F4/F5 buttons.

More info on alsamixer usage from [COLOR="DarkRed"]man alsamixer[/COLOR] manpages. 

Hope that helps someone!

---

### Post by NobodySpecial on 2007-02-07
alextj - You rock!!!!  Will update to reflect your info.  The only thing different on mine is that I can see the speaker and mike without any "-V" switch or pressing any function keys.

Thanks so much for your post!

---

### Post by Phanatic on 2007-02-10
To get my Logitech USB Headset work under Feisty, I had to tweak your .asoundrc configuration like this:

```
pcm.!default {
    type plug
    slave.pcm "combined"
}

pcm.combined {
    type asym
    playback.pcm "playback"
    capture.pcm "hw:1,0"
}

pcm.playback {
    type dmix
    ipc_key 1024
    slave {
        **pcm "hw:1,0"**
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
    bindings {
        0 0
        1 1
    }
}

ctl.dmixer {
    type hw
    **card 1**
}
```

Using the original config gave no sound for me, but this one works fine...

---

### Post by Neotinker on 2007-02-13
For anyone who has a problem with the microphone not working, try plugging the usb headset directly into your computers usb port. Don't use a hub. I don't know if this is a problem with later models but I have a Logitech 200 headset and if I use a usb hub between it and my computer the microphone will stop working.

Your computer will be able to see the headset and you can hear audio through the headset but the microphone will stop working. I've tried it will all kinds of hubs (usb1.1, usb2.0, powered and unpowered) and with both the alsa driver (snd_usb_audio) and the oss driver (audio), but it doesn't matter. If I plug it directly into my computer, It works perfectly, headset and microphone.

Hope this helps someone,
Neotinker

---

### Post by Unix_Wizard on 2007-05-05
I got sound for mine by using post12's asoundrc. But I get > function snd_ctl_open failed for default: No such device
If I run alsamixer in the terminal. Is there any way to fix this?

---

### Post by NobodySpecial on 2007-05-05
Unix_Wizard - Try to specify a different card.  Some examples:

For Card 0
```
alsamixer -c 0
```

For Card 1
```
alsamixer -c 1
```

and so on.

---

### Post by MichaelSM on 2007-05-08
I use a Logitech 350 headset for Skype with Edgy. Neotinker's dead right. I have to use a direct USB port rather than a powered USB hub. Why? Dunno. 

Anyway, it all works fine, except that NOT every time, but a lot of the time, I have to visit Skype>Options>Tools>Sound Devices and re-set the Audio in/Audio out/Ringing drop menus. Nearly every every time I SAVE them, they're there next boot, but occasionally they've changed. 

It's just something I've learned to check each time I start Skype. Not to bore anyone too much, but is there a way to fix this?

My system's pretty basic. A built-in Via soundcard, a SBLive soundcard(DEFAULT) and the USB headset. Someone mentioned something about disabling the Via option in BIOS. Is that a serious issue; and if so, how does one manage to do it?

Thanks to everyone who reads my posts. 99% of the time I can figure it out on my own. This one is relatively unimportant in the scheme of things, but a hint would be helpful.

Cheers; Mike.

---

### Post by sickpuppet on 2008-09-30
Thank you NobodySpecial! 

These instructions worked a treat for my "Shike SK-932" branded USB headset on Ubuntu 8.04 Hardy Heron. This headset reports itself as "C-Media Electronics, Inc. Audio Adapter" in lsusb and as "C-Media USB Headphone Set" in /proc/asound/cards.

So, to anyone who's got a generic USB headset, try these instructions, they'll most likely work. Just remember to follow *every step*! ;-)

regards
SP

---

### Post by lesnik on 2008-11-19
Thanks NobodySpecial, and Phanatic for the modification. That one worked for me. :)

btw I use Logitech 960 USB headset...

---

### Post by Folditron on 2009-01-30
My headset worked fine from the start with Intrepid, but when I use the inline(the ones on the usb cord) volume controls it changes my master volume rather than the one specific to the headset. Anyone have any experience with this?

---

