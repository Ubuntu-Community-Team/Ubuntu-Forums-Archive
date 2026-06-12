---
title: "Wireless is not working anymore on 11.04"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by bilbo.san on 2012-05-06
Hi everyone!
I was doing OK using Ubuntu 10.10 (coming from 9.04). I decided to take a chance and upgraded to 11.04 AND WHAT A TERRIBLE MISTAKE!
For some reason, it reported a problem with FLASHPLUGIN, which I finally was able to delete manually, blue-tooth and wireless is not longer working.

I tried to ran an update and even having the Internet wired in, it reports that there is no internet connection. I can surf the web though (wired).

Should I get the CD for 10.10 again and re-install from scratch?
Should I upgrade to 11.10 to see if it fixes?

What should I do???

Many thanks for the help.
e.

---

### Post by Ms. Daisy on 2012-05-08
I recommend that you burn some live CDs of 11.10 and 12.04.  Run them on your computer & see if things work better.  

I wouldn't recommend going back to 10.10 because support for it ended in April.  Support for 11.04 ends in November this year.

This forum can help you get bluetooth & wireless working again, but you probably want to find the version you prefer first.

---

### Post by TBABill on 2012-05-08
I'd recommend first finding out what hardware you have. Could be a very simple fix for the wireless. You can find out what it is by opening a terminal and ```
lspci | grep Network
``` and paste that back here. Sometimes Ubuntu sets up the driver incorrectly or you could need a proprietary driver. 
 
I probably wouldn't move any further than 11.04 for right now as far as installing the OS unless you try 11.10 or 12.04 and the hardware works in the live environment. Otherwise you'll install and be in the same boat you are now. If it works with either of those live, then install should (should!) work fine as well.
 
Note: 12.04 is a big improvement over 11.04 with Unity so if the wireless works in 12.04, or if you get it going with some help, you will probably feel like you are using a more responsive system in 12.04. Plus, as mentioned, support ends for 11.04 this year and 12.04 is supported for 5 years.

---

### Post by bilbo.san on 2012-05-10
Thank you both.
You know... I tried testing and a live cd I had for Ubuntu 9.10, and it detected the wifi. 
Installed 12.04 and WIFI is NOT working.
But will post another support request on this forum as you suggested.

Thanks again.
e.

---

### Post by anewguy on 2012-05-10
You shouldn't need another thread - just post back what TBABill asked for here in this thread.  If your wireless is USB, the post back the output of lsusb.

---

### Post by bilbo.san on 2012-05-10
Got it working.
Here is what I did, I de-activated the driver that was on, didnt reboot, but instead, installed the new drivers through the terminal

```
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```

And it is working again!

PS, thanks to Chilli555 for the help!

---

