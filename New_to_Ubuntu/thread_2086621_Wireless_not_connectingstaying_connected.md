---
title: "Wireless not connecting/staying connected"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by irakresh on 2012-11-21
I am totally new to Ubuntu so I wasn't sure whether to post this here or under the Wireless forum. In any event, I have a new Zbox computer. We have wireless (DSL) at our home. It's working fine on our windows computers and the connection works fine with the Zbox when I run a wired connection. 

But, when I try to connect the Zbox to the wireless, it won't connect and it continually asks for the passphrase. I have entered it several times (and checked to make sure it was right), but still nothing. I have checked to make sure the connection is available to all users, but that's about all I know to do. 

Please tell me what information I need to provide to troubleshoot. Our router is a Netgear N300 Wireless Router and the firmware is up to date.

---

### Post by wildmanne39 on 2012-11-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by irakresh on 2012-11-21
I think I successfully attached the netinfo file. Please let me know if I am missing something.

---

### Post by wildmanne39 on 2012-11-21
Hi, the bottom half of the output from the file is missing but go ahead and try this:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```
Also signal strength is at 50 percent which is low for ubuntu to connect too.
Thanks

---

### Post by irakresh on 2012-11-21
That seems to be better. Thank you Wild Man. Hopefully it stays connected - time will tell. The computer is now in a temporary location - when it's moved to it's permanent location it'll be closer to the router - do you think that will help? Also, can you tell me (in simple terms) what the code did (if you have a chance)?

---

### Post by wildmanne39 on 2012-11-21
Hi, yes it may help to move it closer.

Also channel 1 or 11 is good channels to use.

The code changed encryption from hardware to software.

Please use thread tools at the top of the page in a little while to mark the thread solved.
Thanks

---

### Post by Joshua66 on 2012-11-22
Wild Man, any idea why moving the encryption from hardware to software helped?  Maybe the driver doesn't quite interface with the hardware encryption correctly or the hardware is buggy?

---

### Post by wildmanne39 on 2012-11-22
Hi, it is issues with the driver.
Thanks

---

### Post by irakresh on 2012-11-22
I was trying it again today. It kicked me off the wireless connection (I was prompted for the passphrase again) and now I can't seem to load any websites. I also tried to run the Update Manager as a check on the connection and that too failed. 

Is there something I can post again to help with a diagnosis? I don't know why the bottom half of the output was missing from the original post.

Is there something else driver related I can try? Or anything-related?

Would getting a USB wireless stick work around this problem? If so, do you have a recommendation? Our router is Netgear N300.

---

### Post by irakresh on 2012-11-27
I ended up (with help) blacklisting the driver (rt2800pci) and just using a wireless USB stick. This seems to be working much better.

---

