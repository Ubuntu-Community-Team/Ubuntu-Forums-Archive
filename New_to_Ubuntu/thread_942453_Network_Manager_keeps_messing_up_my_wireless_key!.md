---
title: "Network Manager keeps messing up my wireless key!"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Dreen on 2008-10-09
Hello,

Apologies if this has been already covered somewhere, I have done some searching and didnt find much.

So each time I make a connection it seems to be incorrectly saved to /etc/network/interfaces.

My WPA-PSK is JDBKIDPK.
Lets assume my network SSID is "MyNetwork"

Each time I log into the system, I have to:
1. Go to Manual Network Configuration
2. Unlock this with my password
3. Go to properties of my wireless connection
4. Change the wireless key to JDBKIDPK and save

When the c onnection is up I check the /etc/network/interfaces:
```

auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0



iface wlan0 inet dhcp
wpa-psk f7baf82bdcef72a68c30135e10c5f6da1144755ca61938a9b34fdf2ffa96bab5
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MyNetwork

auto wlan0

```

Indeed, when Im inserting a correct key at sturtup, there is some very long key already entered, which I assume is f7baf82bdcef72a68c30135e10c5f6da1144755ca61938a9b34fdf2ffa96bab5. What the hell is it? 
I tried putting my normal key into this interfaces file both as "JDBKIDPK" and as "s:JDBKIDPK" (I saw the latter somewhere on this forum) but neither helped!

Is there some way to get this fixed or at least automate the process in some sturtup script?

Regards

---

### Post by Papa-san on 2008-10-09
That very long key is the 64 character key that your passphrase gets converted into by the WPA encryption. It's the right key, but it is not being found where it is supposed to be. (It's actually being copied into a place where it's _not_ supposed to be located, to be precise, and that is where the problem makes itself apparent...) I have the same issue, and have my own thread running  on it [here]("http://ubuntuforums.org/showthread.php?t=925528"). I have found a temporary workaround, but when I re-boot (which is frequent due to some unexplained system-wide crashes that are not being dealt with [here]("http://ubuntuforums.org/showthread.php?t=940420")) I am able to repeat the process and make it work for a while. Sometimes it stops working without the crash and has to be done again... It's a pain, so I know where you are coming from...

---

### Post by Dreen on 2008-10-09
Bump !

---

### Post by Papa-san on 2008-10-10
What wireless manager (GUI) do you use? Give wicd a try. I haven't had to re-enter my passphrase through four or five re-boots...

I wish I could be more helpful, but I really don't know enough. I'm just seeing that not too many others have ideas to share...

---

### Post by bodhi.zazen on 2008-10-10
I had that problem also. I struggled with network manager for a few weeks.

Then I found wicd.

Wicd is very easy to install and replaces network manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Miljet on 2008-10-10
Try making a backup of your /etc/network/interfaces file. Then open the /etc/network/interfaces file with gedit. Remove everything except the first 2 lines. Save the file and reboot. Your wireless should work right.

I had this exact same problem and got this tip from:
[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

Good luck.

---

### Post by Dreen on 2008-10-11
Wicd worked very well! And it does look so much better than default gnome manager!

Thanks everyone for involvment.

---

### Post by Papa-san on 2008-10-12
Awesome!

Glad you got it working. Now, if you mark the thread as solved, (Thread tools at the top) you will help narrow the results for the next guy that runs into this!

---

