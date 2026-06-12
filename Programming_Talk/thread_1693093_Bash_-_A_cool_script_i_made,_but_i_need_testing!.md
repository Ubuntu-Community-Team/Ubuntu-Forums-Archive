---
title: "Bash - A cool script i made, but i need testing!"
date: 2011-02-22
forum: Programming Talk
---

### Post by ~Middle on 2011-02-22
So i made a really neat little script this morning, basically the idea is that i can use it with a VPN and SSH so if my laptop gets lost/nicked i can find it again. So everything works, but the one issue is that i need someone in a different location to me to test it!

If you could run it, and just tell me if what it outputs is correct, and then just give me some general feed back that would be really really appreciated!

So here is the code:

[http://pastebin.com/2E7XnuZV](http://pastebin.com/2E7XnuZV)

Or if you just want to download it:

[http://dl.dropbox.com/u/8387960/tracker](http://dl.dropbox.com/u/8387960/tracker)

It requires php5-cli and a wireless card to work, and it should be able to find your location pretty accurately!

Thanks a lot!

---

### Post by Tony Flury on 2011-02-22
Does not work - I get the following errors on the find location menu option : 

PHP Notice:  Undefined offset: 1 in /home/tony/geo.php on line 3
PHP Notice:  Undefined index: location in /home/tony/geo.php on line 32
PHP Notice:  Undefined index: location in /home/tony/geo.php on line 34

---

### Post by ~Middle on 2011-02-22
Did you install the php5-cli package?

And if so, do you have a home directory?

The script downloads a php file to analyse the MAC address, so if it failed to download for some reason then that is why...

Thanks for trying it!

EDIT: Oh and you need to have a wifi card obviously....

---

### Post by Tony Flury on 2011-02-22
I installed the right package - it downloaded the geo.php file fine and I have a wifi card.
(it would fail with a "could not find input file" if the download fails)

if i manually download the geo.php file and execute it using the php command - it fails with the same errors.

I think i have it tracked down though - the bug is in your code - you assume that the only functioning wifi card is wlan0 - mine is wlan1.

Spookily though it does seem to work - that is pretty scary - it got the location to within less than a mile.

---

### Post by ~Middle on 2011-02-22
Ah yes that is an assumption on my part, i coded this for personal use really, so i didn't think about wlanX but that is an easy fix!

And yeah it is scary, i got a street view picture of my house XD

Would you know of a way that i could enter the lat/long into google maps from the CLI? That would be awesome!

Thanks a lot for your help!

---

### Post by Up1Fish on 2011-02-22
Neat little script, I like this a lot. How exactly are you implementing this on your laptop?
 
> **~Middle said:**
> 

Would you know of a way that i could enter the lat/long into google maps from the CLI? That would be awesome!

Thanks a lot for your help!

You could try opening google maps like this:

[http://www.google.com/maps?q=%s](http://www.google.com/maps?q=%s)

That seems like it would work.

Cheers.

---

### Post by ~Middle on 2011-02-22
I have set up a VPN with hamachi that my laptop automatically connects to once it has connected to the internet, then i have another script on my PC that waits for the laptop to get online, then it spawns an SSH connection. 

So when the laptop goes online i can locate it ;]

But since this was really neat i thought i would share it with everyone, once i had it perfected of course!

Thanks a lot for the google link i will test that out now!

EDIT: Thanks a lot!!!! That google link works perfectly! 

I just need to work ona way to autodetect what interface name the WLAN card is using (i.e wlan1), im sure i can do that but im tired XD

Thanks!

Oh and if you download the link at the top it will be updated ;]

EDIT: FIxed the wlanX issue, so as long as you have a wireless card connected to the internet you can find out where you are!

I think i will refine this into a more of a 'Locate me' application... but yeah, thanks for your help, any other feedbak/testing is greatly appreciated!

---

### Post by ~Middle on 2011-02-23
Just bumping because of the amount of edits in my last post that went un-noticed XD

---

