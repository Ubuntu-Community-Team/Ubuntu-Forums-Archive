---
title: "capturing video is easy"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by spannerman1 on 2008-06-12
hi folks,it`s cheating,but it works.
The only way i`ve managed to capture video with ubuntu,is by recording video from tv/satbox,onto a rw disc using my dvd recorder that resides under my tv.
When the dvd is full of my fav` tv stuff, i take the dvd and put it in my computer,and use one of the dvd ripping programs to store the video on to my computers hard disk.
After hours of searching internet,it seems this is the easiest/cheapest way to capture video with linux.Maybe i am missing something somewhere.
It is a shame that i cannot use my instant videoXpress with linux,but it doesn`t work with vizta either.I have had very similar problems trying to capture video with linux and vizta,is it all something to do with these new copying laws that were passed?
Anyway,i like ubuntu better than vizta.I just need to get started with learning how to program a computer.If i could just figure out how to make my computer rip the signal from an external device,the same way it rips the digital signal from a dvd module/disc.
regards spannerman

---

### Post by billgoldberg on 2008-06-12
I'm no expert at this kind of thing, but doesn't "myth tv" let you do that?

I'm sure there are others ways as well.

I believe vlc can do this, not sure though.

---

### Post by spannerman1 on 2008-06-12
thanks for advice fella,i will give myth tv,and vic a try,although my temptation is to remove the dvd module from my computer,and have a go at connecting something up to the modules connector pins,,,,sort of trying to fool the computer into thinking the digital signal is coming from a dvd disc,when really it has a signal coming from something else,but probably some sort of signal remodulation would be required to perform this task.Anyways i`ll have a play with myth/vic.
I cant get my computer to recognise my external usb devices with ubuntu,but when i have a look in device manager,i see all the details of the connected device.
Lots of stuff to learn with this subject,lol
regards spannerman

---

### Post by eldragon on 2008-06-12
if your capture card is not supported you are at a dead end...
i would definately consider buying compatible hardware.

if its analogue, then any card with the saa7134 chipset will do. i think the bt787 or something like that works too.

if its digital, i wouldnt know, never tried a digital capture card since i dont get digital reception here :(

once you got your hardware working (try first tvtime). you could set out to install and configure mythtv. which is a time shifting recorder (pause, schedule, skip commercials...you name it).

im actually using mythtv to record from my server, and get live feeds through wireless with no problems to my notebook.

once you try mythtv, you wont conceive any other way to watch television.

---

### Post by OffAxis on 2008-06-12
could you post more specifics on your card? (make and model)

If it's recognized, I think it would show up with 

```
lscpi
```

Mythtv is king; solid and feature rich.

Your card should be registered someplace like /dev/video0
so a simple redirect of the stream (to say, test your card out) would be 

```
cat /dev/video0>stream.mpg
```

to save it to a file. To view it in real time try
```

mplayer /dev/video0

```

---

### Post by spannerman1 on 2008-06-12
Hi,i installed mythtv,and my hard-drive started making a constant clicking sound,it sounded as if it was gonna self destruct,so ive uninstalled it.
I also realize that myth tv needs an internet connection,my various antennas/motorized dishes,already pick up thousands of tv/radio stations without an internet connection.
I would just like to get my instant video express working with ubuntu,so i could connect the composite outputs of my dvd recorder/satellite receiver/dvd player/radio scanner,up to my computer and record to hard-drive my fav` content.
The ADS Tech instant video express is a small box,that has a composite video input[yellow],left and right audio[red/white],and s video input.On its other side it has a usb output.
I think its driver is called usb av191,but i`ll report another check on it later,thanks for advice folks,nice ta meet ya in cyberland.
regards spannerman

---

### Post by Ripfox on 2008-06-12
xawtv rips from my tv card

---

### Post by spannerman1 on 2008-06-12
Hmmm,i had another look in device manager,and when i clicked on one of the usb ,it came up on the right side of the page along with vendor details"insufficient power to operate USB device".
This registering stuff,,,,do i have to manually enter the device details myself somewhere on the computer?or is it registered somewhere automatically?
How do i find /dev/video0  ?
Might i have to solder up a small power supply,to power the device?
Which pins on a usb socket are for carrying voltage,and would it need a split rail power supply,or just + - dc 5volts?
What would be the method of typing in mplayer /dev/video0 ?
Can someone point me to a place where i might learn about this registering stuff,and how to type the right stuff in the right place,and how to find the right location to type the stuff.
Sorry for my ignorance with computers,but i will get there eventually,with a little help,then i can help other folk.
regards spannerman

---

### Post by cariboo on 2008-06-13
For the do it yourself person check out this thread:

[http://ubuntuforums.org/showthread.php?t=606993](http://ubuntuforums.org/showthread.php?t=606993)

Jim

---

### Post by OffAxis on 2008-06-13
> Hmmm,i had another look in device manager,and when i clicked on one of the usb ,it came up on the right side of the page along with vendor details"insufficient power to operate USB device".
Sounds like you don't have USB 2.0 plugs on your system.

> This registering stuff,,,,do i have to manually enter the device details myself somewhere on the computer?or is it registered somewhere automatically?
How do i find /dev/video0 ?
It'll happen automatically (if your device has a driver available and is detected). By 'register' I mean that the system recognizes it and makes it available.
For example, if you go to a terminal (Applications->Accessories-> Terminal) and type in 
```
ls /dev/
```
you'll see all the devices currently available to your system. A few of them (fd0, cdrom) are physical devices. That's how your capture card would show up, probably named video0.

> Might i have to solder up a small power supply,to power the device?
I'd go another route; the easiest, fastest (and probably cheapest) thing to do would be to add a USB 2.0 PCI card to your system. $10 or $15 here in the States.

So, buy the card, install it, plug your video Xpress in, and see if it registers (by going to a terminal or console and typing this in)
```
ls /dev/vid*

```
which will display all devices that start with "vid" because it won't necessarily be video0; it could be video1.

Also, to see what's plugged into your USB sockets you can try typing in
```
lsusb
```

to get a brief overview of what's attached. 
For more detail type this is
```
lsusb -v

```
That'll show you things like maximum power draw of the device.

---

### Post by spannerman1 on 2008-06-14
thanks folks,fer getting me started with using my keyboard,,many thanks.Its a laptop i`m using for ubuntu at the moment,when i have got the full understanding of multibooting[i`m nearly there],and i have got the extra hard drives set up for my other laptop and desktop,i should be well on my way to making windows a thing of the past for me.
many thanks again.
regards spannerman.
ps,i`m always ready to post help if someone has problems with satellite reception/equipment

---

### Post by iwannalearn on 2008-06-14
I am really new to ubuntu but, one question (if i am not missing something) what sat box do you have. I have a linux set top box and i am able to record direct on to my pc hdd through network settings on the stb.

---

### Post by spannerman1 on 2008-06-14
Hi iwanna`,i`ve got quite a few satboxes,some with blind scan,somewithout,also a skystar 2 pci,and a usb version.I am thinking that maybe you have a dreambox,i heared they are a linux reciever,capable of surfing net/filegrabber/etc,but i never got the courage up to spend that much dosh on a sat reciever.It would be nice to get the skystars working with ubuntu.I saw one of the programs in ubuntu have settings for a lnb[downconvertor] that i recognized,when i have my ultimate computer setup sorted[1 multiboot laptop for internet,and other multiboot desktop and laptop for offline],i will investigate that ubuntu program further.A few more days and i should be able to get my teeth into linux/ubuntu.
Phew,digital signals,things were a lot easier in the analogue days.
regards spannerman

---

