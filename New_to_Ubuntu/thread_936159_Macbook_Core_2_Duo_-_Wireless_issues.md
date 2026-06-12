---
title: "Macbook Core 2 Duo - Wireless issues"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by jackbusch on 2008-10-02
Hello, lost my OS X discs so decided to switch over to Linux. Anyway, I have no idea what I'm doing. I have Ubuntu (Hardy Heron) installed but can't seem to get wireless working.

I did this:

[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

and now I can see my wireless network and I put in all the pertinent info (passkey, auto setup DHCP, etc) but when I try to browse, no dice.

I noticed an error msg during the installation of ath9k but it got scrolled off...it said something about kernels and CONFIG_NETWORK_MULTIQUEUE 

I think that might have something to do with it.

---

### Post by shifty_powers on 2008-10-02
can you post the output of

```
ifconfig
```

and

```
sudo iwlist scan
```

and

```
lspci
```

please :D

---

### Post by shifty_powers on 2008-10-02
plus i'm fairly sure you'll be able to use

[http://madwifi.org/](http://madwifi.org/)

the madwifi drivers, which will make your life far easier...

---

### Post by shifty_powers on 2008-10-02
look ath this installation script as well :D

[http://ubuntuforums.org/showthread.php?t=798485&highlight=ath9k+madwifi](http://ubuntuforums.org/showthread.php?t=798485&highlight=ath9k+madwifi)

edit:

have you considered a pre-release version of 8.10m (which i am using myself)? it has support for your card already built in...

---

### Post by jackbusch on 2008-10-02
Thanks for helping out. I tried that madwifi script but got snagged when I was supposed to put in:

chmod +x madwifi.sh
sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz

and it says for the first line:

chmod: cannot access 'madwifi.sh': no such file or directory

and the second line returns

sudo: ./madwifi.sh: command not found


Sorry, I'm feeling really dunce-y here.


Anyway, here's what the other stuff returned:

ubuntu@ubuntu:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:17:f2:d1:b3:4d
  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16
 

lo        Link encap:Local Loopback
  
          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:10330 errors:0 dropped:0 overruns:0 frame:0

          TX packets:10330 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 
          RX bytes:518768 (506.6 KB)  TX bytes:518768 (506.6 KB)



ubuntu@ubuntu:~$ sudo iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.



ubuntu@ubuntu:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

ubuntu@ubuntu:~$

---

### Post by jackbusch on 2008-10-02
you know i think i will try the pre release.

---

### Post by shifty_powers on 2008-10-02
heh, well i could helo you get mad wifi uo and running, but i have to say, 8.10 is shaping up very well...

why don't you try kubuntu 8.10? i have been a long time gnome user, but have been mightily impressed with kde 4.1 :D

---

### Post by jackbusch on 2008-10-02
how do kubuntu and ubuntu compare? Is Kubuntu more cut out for big dummies like me?

---

### Post by shifty_powers on 2008-10-02
heh kubunut is a funny one, on the one hand it is more familiar to windows users, but yet there are arguably more system controls...

it is very easy to use though and i really like it...

[[IMG]http://img229.imageshack.us/img229/4831/desktopyo0.th.png[/IMG]](http://img229.imageshack.us/my.php?image=desktopyo0.png)[[IMG]http://img229.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

is my desktop :D

---

### Post by billgoldberg on 2008-10-02
> **jackbusch said:**
> how do kubuntu and ubuntu compare? Is Kubuntu more cut out for big dummies like me?

No.

kde 4.1 still isn't ready for normal users. 

If you like to beta test it, feel free too.

I suggest you use gnome.

Also all the guides on the web are for ubuntu and you'll get better support.

Also the theming of Gnome is easier then Kde.

--

Oh, at user above me:

Please use thumbnails that link to the full image.

---

### Post by billgoldberg on 2008-10-02
> **jackbusch said:**
> Thanks for helping out. I tried that madwifi script but got snagged when I was supposed to put in:

chmod +x madwifi.sh
sudo ./madwifi.sh --tarball /path/to/madwifi-VERSION.tar.gz

and it says for the first line:

chmod: cannot access 'madwifi.sh': no such file or directory

and the second line returns

sudo: ./madwifi.sh: command not found




You will have to specify the path to the script.

So for me it would be

chmod +x /home/rw/Desktop/madwifi.sh

sudo /home/rw/Desktop/madwifi.sh --tar /home/rw/Desktop/madwifi-123.tar.gz

--

Note that these paths are fictional.

And if you are wondering, "rw" is my username.

---

### Post by shifty_powers on 2008-10-02
ok, sorry but i plain disagree with some of your points.

1). i have actually found kubuntu 8.10 to be very stable, easy to use and very well put together.

2). actually, there is plenty of support for kde, and to suggest you use gnome purely for support is plain wrong in my eyes.

3). theming is easing in gnome? not in kde 4.1 it isn't. when you go to themes, it gives you the option of downloading and installing new themes, of which there is a good selection with two or three clicks, and certainly without going anywhere near a browser.

4). given my experience with kde 4.1, i fail to see on what basis it is not ready.


having said all this, i do recognise that 8.10 is still pre-release and this must be borne in mind. however, i have found it to be a pretty flawless experience, have found the kde apps to be actually very, very good. I have had no problems with support, and whilst i still like gnome, i feel that kde 4.1 is becoming an increasingly viable alternative, and has surpassed gnome in certain areas.

i also say this as someone who had been using gnome for the last 4-5 years....

(sorry about the image, was bit distracted at the time, will change it when i get a chance)

---

### Post by jackbusch on 2008-10-02
OK Sounds good. However, I can't even get my wired internet to work ( I think this is a different issue though because I can't even get it to work on my other computer, even though I can get wireless to work) and I don't have any DVDs to burn.

Is there a way to install 8.10 off of a usb drive or an external usb hard disk? 8.10 is just a wee bit too big to put on a cd rom

---

### Post by jackbusch on 2008-10-02
nevermind, the i386 one is small enough - which leads me to my next question

with a core 2 duo macbook, should i be using the 64 bit ubuntu?

Thanks to everyone, you people are great.

---

### Post by jackbusch on 2008-10-02
I'd also like to note that I am indeed seeing my wireless network show up. I go into the Network settings and put everything how it should, but it just doesn't work. It doesn't have any indication that its connected either in the taskbar (is that what you call it, still?) the icon merely shows "MANUAL NETWORK CONFIGURATIOn."

This isn't a situation where I'm just good to go but need to flip the switch is it?

---

### Post by jackbusch on 2008-10-02
Hooray! I'm posting this from my computer running UBuntu 8.10.

Thanks all!

---

