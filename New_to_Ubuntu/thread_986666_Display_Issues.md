---
title: "Display Issues"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Tru7h on 2008-11-18
I booted up 8.10 for the first time and I wanted to get the drivers for my 9600 GSO, but when I finished downloading and installing the driver and I restarted I got the splash screen, then no video and the login screen sound.  Thinking that it was a glitch I restarted and got the same thing.  I was able to pull up the gui by using recovery mode and xfix but I need to do this every time I turn on my computer.  Can someone please help me?  I want to have the driver and eventually compiz.

Specs:
Core 2 Duo Wolfdale 2.5GHz
8.10 64-bit
I used the 177 nvidia driver

---

### Post by Tru7h on 2008-11-18
Bump

---

### Post by oldsoundguy on 2008-11-18
try another driver .. this is a major issue between 8.10 and NVidia that neither seems to want to solve.

There are many threads similar to this all over the forums.

Go to the Envy site and read the blog there and you will see that the problem is being addressed .. but not by those that SHOULD be doing the work.

I had to go into synaptic and find the driver that would work .. took several tries, but I have a display at least .. no bells and whistles (compiz) possible and no display rotation.  But it WORKS, and that is the important thing.

Once you find the driver, you will have to enable it .. system> administration> hardware drivers 
IF you have selected the driver that will work with your set up, it will show up there.

---

### Post by Tru7h on 2008-11-18
Link to envy site?  Which version do you use?

---

### Post by Crafty Kisses on 2008-11-18
I'm pretty sure Envy is in the repositories, go to Synaptic Package Manager, and search "Envy", and it should be there.

---

### Post by oldsoundguy on 2008-11-18
Google sez: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Select the blog.

You will also see that there is NO Envy program for Intrepid on the site .. what is in the repositories if for Hardy and won't work.

---

### Post by Tru7h on 2008-11-18
Well that was a bust
I ran Envy and after it did pretty much the same thing as the Ubuntu restricted drivers window (except it used ver 173) and I got the same black login screen.
Take a look at the screen shot.  The driver is installed but it says a different version is in use.

---

### Post by Crafty Kisses on 2008-11-18
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X server again.
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```
Once it's rebooted and you are able to log in again, look in **System ---> Administration ---> Hardware Drivers** to see if your graphics card is on the list. Click the appropriate driver for the appropriate card. Don't forget to go into the BIOS to turn off the onboard video card controller first before you boot into the recovery mode from the GRUB menu.

---

### Post by Tru7h on 2008-11-18
After running recovery mode, xfix, and the code you gave me the restricted driver window is the same as the screenshot in the earlier post.

---

### Post by Crafty Kisses on 2008-11-18
In an earlier post you said you used the "177" driver, try using the "173" driver and see if you get different results.

---

### Post by oldsoundguy on 2008-11-19
I had to use the 96 driver ... wide screen monitor (cinema display) off of an fx5500 card.  No bells, no whistles, no rotation, no compiz will work with it.

Please save some grief and go to the site I liked above and read what is REALLY going on.

---

### Post by Tru7h on 2008-11-19
same result

---

### Post by Tru7h on 2008-11-19
These are the choices envy gives me for nvidia install.  Only choices 0 and 1 are compatible/recommended. 
```
+---------------------------------------------------------------------------------+
 | Number | Candidate Version    | Installed Version    | Compatible | Recommended |
 |---------------------------------------------------------------------------------|
 | 0      | 177.80-0ubuntu2      | -                    | +          | -           |
 |---------------------------------------------------------------------------------|
 | 1      | 173.14.12-1-0ubuntu4 | 173.14.12-1-0ubuntu4 | +          | +           |
 |---------------------------------------------------------------------------------|
 | 2      | 96.43.09-0ubuntu1    | -                    | -          | -           |
 |---------------------------------------------------------------------------------|
 | 3      | 71.86.04-0ubuntu10   | -                    | -          | -           |
 +---------------------------------------------------------------------------------+
```

---

### Post by oldsoundguy on 2008-11-19
once again .. the EnvyNG installer for Hardy will not work in Intrepid according to the Envy site itself.

---

