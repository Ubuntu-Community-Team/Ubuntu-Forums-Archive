---
title: "wimax-tools?"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by Daniel Tan on 2012-11-15
Hello.

I am trying to make Intel® Centrino® Advanced–N + WiMAX 6250 work (i.e. scan and connect) on my Ubuntu 12.10.

```
dmesg | grep 6250
[    2.270218] usb 2-1.4: >Product: Intel(R) Centrino(R) Advanced-N + WiMAX 6250
[   13.180421] iwlwifi 0000:05:00.0: >Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84

dmesg | grep 2400
[   13.029184] i2400m_usb 2-1.4:1.0: >WiMAX interface wmx0 (00:1d:e1:34:0e:74) ready
[   16.759666] i2400m_usb 2-1.4:1.0: >firmware interface version 9.3.2
[   16.767532] usbcore: registered new interface driver i2400m_usb
```
Both commands did not return errors which I believe is good.

I have a feeling i need wimax-tools for my wimax card to work ([https://github.com/ago/wimax-tools](https://github.com/ago/wimax-tools)).
Where should
> $ ./configure --with-i2400m=/path/to/i2400m/driver
be pointing? (this command is listed in the link above)

Do I even need wimax-tools for Ubuntu 12.10?

---

### Post by wildmanne39 on 2012-11-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Thank you for your reply. Here is the file:

---

### Post by wildmanne39 on 2012-11-15
Hi, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Done

---

### Post by wildmanne39 on 2012-11-15
Did it work? if not please run the script again and post the textfile after you delete the first text file.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Sorry but I have no idea how to scan for networks and connect to a network on ubuntu.
I tried wimaxcu on terminal but I received ```
wimaxcu: command not found

```as a respond instead.

I added a screenshot too, just in case if it helps.

---

### Post by wildmanne39 on 2012-11-15
Hi, please detach your ethernet cable and reboot and see if it will connect, if not please post a new text file so we can see what it is doing with the ethernet cable unplugged.

I have to leave for a while in about 30 minutes but I will be back as soon as possible.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Still no luck. By the way it is past 1am over here. I might not be available when you come back.

---

### Post by wildmanne39 on 2012-11-15
Do you have an usb adapter plugged in if so you need to unplug it and reboot then try to connect with the internal card.
Thanks

---

### Post by Daniel Tan on 2012-11-15
There are no usb adapter or usb drive plugged in. Am I still required to reboot?

---

### Post by wildmanne39 on 2012-11-15
Hi, this > 8086:0187 says there is an usb adapter plugged in so I will have to do some research when I get back.
Thanks

---

### Post by Daniel Tan on 2012-11-15
I guess it could be my mouse. Is that possible?
Thanks

---

### Post by wildmanne39 on 2012-11-15
I think it is because of wimax.

---

### Post by Daniel Tan on 2012-11-15
Oh okay. Thank you

---

### Post by wildmanne39 on 2012-11-15
Hi, please try:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
if it works we will need to make it permanent but in your case I do not think it will work.
Thanks

---

### Post by Daniel Tan on 2012-11-15
No. It did not work.

---

### Post by wildmanne39 on 2012-11-15
Hi, click on the internet icon in the top right corner of the screen and put a check by enable wireless.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Done that. Right now I am using wifi to connect to the internet by the way.

---

### Post by wildmanne39 on 2012-11-15
That is great, please use thread tools at the top of the page to mark as solved.
Thanks

---

### Post by Daniel Tan on 2012-11-15
Actually, I am asking for wimax. Wifi is already known to be functioning on ubuntu.

---

### Post by wildmanne39 on 2012-11-15
Sorry, I do not understand why wimax is needed if wifi is working.
Thanks

---

### Post by Daniel Tan on 2012-11-16
The Intel® Centrino® Advanced–N + WiMAX 6250 allows me to connect to both wifi and wimax, not simultaneously though (on windows).

I would like to connect to wimax in my dorm because wifi is not available for me there.

I am at home, which explains why I am able to use wifi.

---

### Post by wildmanne39 on 2012-11-16
I see, I know that you could not connect to wifi before because it was soft blocked when we began.

Do you have a wimax connection to connect to at home? if not it may be working now as well but we will not know until you are where you can use wimax.
Thanks

---

### Post by Daniel Tan on 2012-11-16
Yes. I have wimax connection at home too but as I mentioned earlier, I have no idea how to connect to my wimax. 

The internet status on the top right corner of the screen said > Wired Network (Intel(R) Centrino(R) Advanced–N + WiMAX 6250)
disconnected

I am unsure if I need to key in any commands in terminal.

I did disable the "Enable wireless" option on purpose because on windows, I had to disable wifi in order to be enable wimax.

---

### Post by Daniel Tan on 2012-11-17
**_Here are some snapshots on Intel® PROSet/Wireless WiMAX Connection Utility:_**

**When my wimax is enabled [wifi is automatically disabled]:**

_Case 1 - Not connected to wimax._
[IMG]http://123talk.in/wimaxonwindowsdc.jpg[/IMG]

_Case 2 - Connected to wimax._
[IMG]http://123talk.in/wimaxonwindows.jpg[/IMG]

**When my wifi is enabled [wimax is automatically disabled]:**

_Case 1_
[IMG]http://123talk.in/wimaxonwindowswifi.jpg[/IMG]

---

### Post by wildmanne39 on 2012-11-17
Hi, I have been doing research and I have not found anyone that has made wimax work in ubuntu only wifi.
Thanks

---

### Post by Daniel Tan on 2012-11-18
Thank you very much for helping. Do let me know if you happen to find any solutions.

By the way someone has made wimax to work on slackware. Can this be it be applied to ubuntu as well?
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/linux-and-intel-wimax-6250-a-856685/]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/linux-and-intel-wimax-6250-a-856685/")

---

### Post by wildmanne39 on 2012-11-18
Hi, from the looks of it I believe that person just got the wifi to work and not the wimax but it is hard to tell from what they have posted.

That link is old and I do not think it will work with the newer ubuntu.
Thanks

---

