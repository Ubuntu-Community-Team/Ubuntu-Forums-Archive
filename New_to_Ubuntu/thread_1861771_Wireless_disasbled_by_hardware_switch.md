---
title: "Wireless disasbled by hardware switch"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by cwkooistra on 2011-10-16
I recently upgraded to 11.10 64 bit from the 32bit.  My wireless was working fine, but now I am confronted with the hardware switch problem.  Like others, I have no switch and the fn+f5 toggle is useless.  I also couldn't find a toggle in BIOS. My wireless card info was lspci is 
> **02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)**I would greatly appreciate some help or direction to a thread where this fix has been discussed, as access to a wired connection is difficult to come by. 
Thanks.

---

### Post by sadaruwan12 on 2011-10-16
First of all welcome to the forum.

And please run the below code and past the out put here so we can get better idea.

Run this in the terminal Ctrl+Alt+t

```
rfkill list all
```

---

### Post by cwkooistra on 2011-10-16
> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Thanks for responding;  I'm at my wits end.

---

### Post by zeroseven0183 on 2011-10-16
Hi! I have the same problem which I am now fixing. This happened to my laptop also before when I upgraded to Natty and now it is also an issue on Oneiric. Good news is that this problem is fixable.

You already have the first step in solving. You have identified your wireless card. What is the brand and model of your notebook? Mine is HP Pavilion dv3t.

So here's what I did: (There's probably more steps to be done than these so I'll check this thread once in a while)

```
sudo rfkill list
``` to identify the devices then ```
sudo rfkill unblock all
```. I then restarted the network manager by ```
sudo service network-manager stop && sudo service network-manager start
```. Then added hp_wmi to /etc/modprobe.d/blacklist.conf to permanently fix it.

---

### Post by sadaruwan12 on 2011-10-16
Ah, It looks like the same issue I had when I installed 11.04 on my B560 lenovo lap here do these steps this have to work.

Open the terminal and put this code in and press enter.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

You'll get a file opened up in gedit into that text file copy and past this code to the last line.

```
blacklist [COLOR="Red"]acer-wmi[/COLOR]
```

Now, proof read it to see you haven't made a mistake and save the file and close it.

Go to the terminal again and type this in,

```
sudo gedit /etc/rc.local
```

Another text file will open up in that file put this code in above the word [COLOR="DarkRed"]exit 0[/COLOR].

```
rfkill unblock all
```

Proof read it and save it.

Now reboot your pc and see whether your WiFi works.

---

### Post by cwkooistra on 2011-10-16
I'm using a Toshiba, and the pattern I'm seeing here "acer-wmi," "hp-wmi" suggests I should add "toshiba.wmi" to the blacklist?

---

### Post by cwkooistra on 2011-10-16
None of this worked, and I think its because the linux driver provided by realtek only supports the kernel up to 2.6 and oneiric is 3.  So I'm trying ndiswrapper.  I'll report back.

---

### Post by cwkooistra on 2011-10-16
No luck.  Hardware not present despite it being the correct driver.  I was looking around some other forums and it appears that for Toshibas ( I use a Satellite L656D-s5145) there is no equivalent of an acer-wmi, or I assume, an hp-wmi. (adding toshiba-wmi did not produce any results).  Running out of ideas and combinations of key words to google.

---

### Post by gandaran on 2011-10-16
didn't you install drivers for the RTL8188CE chipset in the previous Ubuntu release?
did some search on the chipset and I think you have to install the driver.
the linux drivers are available on the realtek website.

---

### Post by gandaran on 2011-10-16
> **cwkooistra said:**
> None of this worked, and I think its because the linux driver provided by realtek only supports the kernel up to 2.6 and oneiric is 3.  So I'm trying ndiswrapper.  I'll report back.
there are two drivers, one for up to Linux driver for kernel 2.6.34 (and earlier) and another Linux driver for kernel 2.6.35 (and later)
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

---

### Post by cwkooistra on 2011-10-16
Got it to work.  Went into BIOs and hit restore system defaults.  Since there was no option in BIOS for me to toggle the wireless myself, I figured this was the only way to turn it back on.  And Voila.  Thanks for all your help guys, I appreciate it.

---

### Post by theOGRE on 2012-11-03
Thank you cwkooistra.  I have tried so many things, none of which worked. I never would have thought of reseting BIOS settings, because I already used the defaults. This worked for me straight away.  I have a Dell Inspiron Mini with the rtl8188ce wireless. Thanks again!

---

