---
title: "Problem installing Xubuntu 12.10 64bit"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Brianrh on 2013-01-06
I downloaded the iso for the above once torrent and the next time from mirrors and tried Unetbootin and USB Image Writer to create a Live USBs but I get the same problem with any combination. I can run a live session with wireless enabled with no problem but as soon as I try to install it hangs at the wireless setup screen. This is the case if I select the no wireless option or if I set the wireless up.

I have Linux Mint 14 running on another partition and have in the past installed earlier versions of Ubuntu with no problems.

Can anybody suggest what my problem can be or if I need to supply any further information? 

Thanks.

Brian

---

### Post by Marzata on 2013-01-06
Is your hard disk ok?

---

### Post by fantab on 2013-01-06
Just a suggestion: Boot with LiveUSB and choose option to "Try Ubuntu" and let *Buntu set itself up. Play around and set up your wireless, let it be UP. The from Desktop choose to install *Buntu... when setting up the install choose NOT to download any updates or any third party codecs and manually select the HDD partition you want to install to; reformat the selected partition with ext4.

Hope it works.

If it does not then (assuming that your downloaded .iso is fine) you have to 'fsck' the HDD partition in question... 

Also use "Disk Utility" from LiveUSB to check if your HDD and the Partition in question are in 'healthy' condition by running "SMART".

---

### Post by Marzata on 2013-01-07
> **fantab said:**
> Ubuntu is an ancient African word, meaning "can't configure Debian".

Xubuntu is an ancient African word, meaning "can configure Ubuntu".

---

### Post by Brianrh on 2013-01-07
> **fantab said:**
> Just a suggestion: Boot with LiveUSB and choose option to "Try Ubuntu" and let *Buntu set itself up. Play around and set up your wireless, let it be UP. The from Desktop choose to install *Buntu... when setting up the install choose NOT to download any updates or any third party codecs and manually select the HDD partition you want to install to; reformat the selected partition with ext4.".

I've tried installing from the boot menu on the Live USB and from the desktop from "Try *buntu", and I've tried choosing NOT to download updates and 3rd party stuff and to continue without wireless enabled but it doesn't get pass this wirelss setup screen. IIt doesn't get as far as any harddisk options, etc. However it runs perfectly with working wireless when I run it as a "Try *buntu". From this state, with everything working,  I have tried to install and it still hangs at that same wireless setup screen with and without the two boxes ticked.

Yesterday morning I created an ISO of the new Bodhi release and that installed fine so it is all rather strange that Xubuntu has a problem.

I think I will try a fresh download on a different correctly formatted USB memory stick and re-trace my steps.

Thanks for the help so far.

---

### Post by Bucky Ball on 2013-01-07
When you get to the options of Try Ubuntu, Install Ubuntu etc, try hitting F6 and choose 'nomodset'.

Incidentally, the jokes aren't funny. Xubuntu = xfce4 on a Ubuntu base install with different default apps ...

---

### Post by Brianrh on 2013-01-07
Thanks BB, I will give that go as well tonight when I get home.

---

### Post by fantab on 2013-01-07
By the way, are you trying to install on a laptop? What kind of wireless do you have? I have had some issues installing Xubuntu on my bro's laptop with Broadcom drivers... br43 or something like that.  There are a few SOLVED Threads on these forums search for them... Also try nomodeset option as suggested.

---

### Post by Brianrh on 2013-01-07
I had the same problem with re-created Live USBs with exactly the same characteristics.

> **Bucky Ball said:**
> When you get to the options of Try Ubuntu, Install Ubuntu etc, try hitting F6 and choose 'nomodset'.

I tried hitting F6 at the menu options but all that happens is the automatic count down to the default action, goes back to 10 seconds each time.

I tried again installing with the wifi turned off ( laptop wifi  switch to turn off wifi) and at the wifi screen no wifi signals were detected so I choose to install with no wifi and it still stuck at this screen.

The only other thing I can think of to do is to burn the iso to DVD and try that.

Thanks again guys.

---

### Post by Brianrh on 2013-01-08
I downloaded another ISO and burnt it on to a DVD and tried to install Xubuntu again with this but I got the exactly same problems.

I tried installing Linux Mint 14 Xfce and this worked perfectly. I'm confused.

---

### Post by opiumpoetry on 2013-01-13
I recommend Linux Lite. It's a redesigned Xubuntu without all the bugs.

---

### Post by Marzata on 2013-01-13
To install anything than official Xubuntu (Ubuntu, etc.) is not recommended. For example Linux Mint Xfce is such a catastrophe.

---

### Post by Brianrh on 2013-01-16
> **Marzata said:**
> To install anything than official Xubuntu (Ubuntu, etc.) is not recommended. For example Linux Mint Xfce is such a catastrophe.

Ha! I did install Linux Mint 14 Xfce and it seemed to be okay. However when I rebooted it had lost the desktop but seemed have a semi-graphical front end. It It had a blue screen but a working right mouse click giving desktop menu which referred to Cinnamon. Tried to re-install a couple of times but still the same.

---

