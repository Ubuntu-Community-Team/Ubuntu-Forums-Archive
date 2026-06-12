---
title: "error -failed to execute child process &quot;/usr/bin/chromium-browser&quot; (Permission denied"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by magneto2010 on 2012-01-27
Hello...I have the xandros 7 inch screen 8G asus eee and a using ubuntu 10.04 on an 8G SD card...I just have firefox and chromium icons..all of a sudden - I click on the chrome icon and get

failed to execute child process "/usr/bin/chromium-browser" (Permission denied)

I tried bitbleach...nothing

can only use firefox now

how can I fix this please

thanks

---

### Post by Bölvaður on 2012-01-27
I wouldn't expect that.

Can you run chromium-browser with sudo?

in terminal or Alt+F2 type:```
gksu chromium-browser
```

If it fails please do it in the terminal and tell us the output.
IF it does not fail , please come back and lets celebrate together :popcorn:

---

### Post by magneto2010 on 2012-01-27
I know nothing about ubuntu

I hit alt F2 and get run application run in terminal....run with file

I copied and pasted sudo etec and hit run with file box...nothing THAT I KNOW OF happened

should I check run in terminal box???

I dont want to brick my SD card

thanks

---

### Post by magneto2010 on 2012-01-27
I meant i copied and pasted 

gksu chromium-browser

---

### Post by Bölvaður on 2012-01-27
that was very silly of me:

```
[3622:3622:2093812968081:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root.
```

The only way to run chrome or chromium as root is to tell them to use user profiles that doesn't belong to the root.

How did you install chromium?

---

### Post by magneto2010 on 2012-01-27
Hello...I just got the SD card and both firefox and chrome were part of 10.04...the previous SD card was 8.04 and just had firefox

all I do is update   firefox  chrome and adobeflash from the update manager when NEW versions appear...I have never installed ANYTHING and dont know how to do it

I can get by with firefox- I will wait for the next chrome version in the update manager OR every now and then I get the ubuntu is checking the disc drives for errors thing which starts at 70% and takes an hour and 1/2 to finish...that may fix it

OR I will just get a new 10.04 SD card 

ALSO...I have read that 10.10 11.04 and 11.10 are all buggy and that 10.04 is still the best

is THAT true

By the way..I have NO IDEA what to do with the stuff written in your reply...you are dealing with someone who knows NOTHING about ubuntu or computers

thanks

---

### Post by Bölvaður on 2012-01-30
Your problem is extremely weird.
I would like you to open the terminal by :
Alt+F2 and type ```
gnome-terminal
```
Then type ```
chromium-browser
```
Copy and paste everything in the terminal window into here (use the mouse to copy as the terminal uses ctrl+c to close programs but ctrl+shift+c to copy)

I hope that by doing that you'll be able to tell me more about this error.

> **magneto2010 said:**
> 
I can get by with firefox- I will wait for the next chrome version in the update manager OR every now and then I get the ubuntu is checking the disc drives for errors thing which starts at 70% and takes an hour and 1/2 to finish...that may fix it
**I dont think the SD card has anything to do with your problem with chromium.**
The hard drive check is set with a fixed interval (which you can disable or change the interval of). Everyone with standard ubuntu install will get this error check. On my computer it takes about 30-45 minutes to go over my (slow) hard disk, which is either 500 GB or 1 TB. I dont know why it would take this long time for you to finish this check on a SD card as they are much faster and smaller than what I have.

> **magneto2010 said:**
> 
ALSO...I have read that 10.10 11.04 and 11.10 are all buggy and that 10.04 is still the best

is THAT true

11.04 and 11.10 are not "all buggy" as they have had enough time now to get most of their kinks ironed out. But it is true that 10.04 is still better because there they have fixed almost all the bugs directly related to the Ubuntu. The only problem running 10.04 is that you cannot get the latest versions of software through the software center, but you can get it through other ways (for an example would going to the program's website)

---

