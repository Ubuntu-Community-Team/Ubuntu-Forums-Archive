---
title: "wireless internet not working D-Link DWL-G122 adapter"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by sickgirl485 on 2008-08-30
This has been a long term ongoing problem, that I cannot get wireless internet when I am using Ubuntu. I tried this once before, and I gave up after a while because I was having absolutely no luck. So I thought I would take another crack at it, although I still have no idea how to install the adapter. Can anyone walk me through it?

---

### Post by david sousa on 2008-08-30
[Does this help?]("http://ubuntuforums.org/showthread.php?t=905350")

---

### Post by sickgirl485 on 2008-08-30
> **david sousa said:**
> [Does this help?]("http://ubuntuforums.org/showthread.php?t=905350")

Will that work even though I am using Hardy Heron?

---

### Post by david sousa on 2008-08-30
Im using hardy to ;)

---

### Post by scheck32 on 2008-08-30
From what I've seen, alot of the D-Link wireless adapters are compatible with Ubuntu. It is a possibility that you might have to use NDISWRAPPER as a solution. I do not have the time to look for your adapter myself but you can use the website to see if it will work. 

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Good Luck...wireless is one part of linux that is slowly evolving.

---

### Post by knattlhuber on 2008-08-30
> **sickgirl485 said:**
> This has been a long term ongoing problem, that I cannot get wireless internet when I am using Ubuntu. I tried this once before, and I gave up after a while because I was having absolutely no luck. So I thought I would take another crack at it, although I still have no idea how to install the adapter. Can anyone walk me through it?

Hmm. Strange. The DWL-G122 has the RT73 chipset, which should work out-of-the-box under Hardy. I don't have any first hand experience though as I don't have this adapter (just another RT73-based one).

---

### Post by sickgirl485 on 2008-08-30
> **scheck32 said:**
> From what I've seen, alot of the D-Link wireless adapters are compatible with Ubuntu. It is a possibility that you might have to use NDISWRAPPER as a solution. I do not have the time to look for your adapter myself but you can use the website to see if it will work. 

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Good Luck...wireless is one part of linux that is slowly evolving.

I have no idea how to use ndiswrapper.

---

### Post by sickgirl485 on 2008-08-30
> **david sousa said:**
> Im using hardy to ;)

Got stuck at step 6...what is he talking about, an exe? I tried unzipping the setup.exe file in the driver I downloaded from the D-Link website and I just get errors. I even went System -> Administration -> Windows Wireless Drivers and loaded the .inf file from the package I downloaded, but apparently it's an "invalid driver file"

---

### Post by Slug71 on 2008-08-30
sickgirl, got to Adimn-Hardware Drivers and see if theres anything there.
If there is and says not in use then enable it.

Have you kept up with the updates?

---

### Post by knattlhuber on 2008-08-30
OK, I don't wanna confuse you completely but I think that there's a good chance that the card might be working without any additional installation.
Can you type ```
iwconfig
``` in a terminal window and post the output?

---

### Post by knattlhuber on 2008-08-30
zszafran posted a script for RT73-based card that installs everything for you if your card doesn't work ootb:

[http://ubuntuforums.org/showthread.php?t=848445]("http://ubuntuforums.org/showthread.php?t=848445")

---

### Post by david sousa on 2008-08-30
> **sickgirl485 said:**
> Got stuck at step 6...what is he talking about, an exe? I tried unzipping the setup.exe file in the driver I downloaded from the D-Link website and I just get errors. I even went System -> Administration -> Windows Wireless Drivers and loaded the .inf file from the package I downloaded, but apparently it's an "invalid driver file"

One possibility is that you downloaded the wrong file and so it shouldn't work. Have you tried cabextract instead of unzip?

---

### Post by sickgirl485 on 2008-08-30
> **knattlhuber said:**
> zszafran posted a script for RT73-based card that installs everything for you if your card doesn't work ootb:

[http://ubuntuforums.org/showthread.php?t=848445]("http://ubuntuforums.org/showthread.php?t=848445")

I followed the instructions for this, which weren't that difficult. I downloaded the tarball, extracted it, and all that, and this is what happened when I tried to install the script that was inside the tarball:

```
:~$ sudo sh install-rt73.sh
sh: Can't open install-rt73.sh
```

I get these errors a LOT when it comes to performing commands

---

### Post by sickgirl485 on 2008-08-30
> **david sousa said:**
> One possibility is that you downloaded the wrong file and so it shouldn't work. Have you tried cabextract instead of unzip?

I tried both when I was unzipping the file

---

### Post by sickgirl485 on 2008-08-30
> **Slug71 said:**
> sickgirl, got to Adimn-Hardware Drivers and see if theres anything there.
If there is and says not in use then enable it.

Have you kept up with the updates?

The only thing that was there was an ATI graphics card driver, and nothing to do with the wireless adapter.

---

### Post by sickgirl485 on 2008-08-30
> **knattlhuber said:**
> OK, I don't wanna confuse you completely but I think that there's a good chance that the card might be working without any additional installation.
Can you type ```
iwconfig
``` in a terminal window and post the output?

The output is: 

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by james_vanb on 2008-08-30
May be a stupid question, but do you have the install CD and have you tried ndiswrapper?

---

### Post by knattlhuber on 2008-08-30
> **sickgirl485 said:**
> 
```
:~$ sudo sh install-rt73.sh
sh: Can't open install-rt73.sh
```

I get these errors a LOT when it comes to performing commands

How about

```
chmod +x install-rt73.sh
```

and then

```
:~$ sudo sh install-rt73.sh
```

?

---

### Post by knattlhuber on 2008-08-30
> **sickgirl485 said:**
> The output is: 

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

OK, definitely no wireless card recognized. Then we should focus on getting zszafran's script working.

---

### Post by Slug71 on 2008-08-30
did you check Admin-Hardwire Drivers?
Sorry my bad, didnt see your earlier post.

Id wait a week and just install Intrpeid Ibex Alpha5

---

### Post by sickgirl485 on 2008-08-30
> **knattlhuber said:**
> How about

```
chmod +x install-rt73.sh
```

and then

```
:~$ sudo sh install-rt73.sh
```

?

This is what happened:

```
~$  chmod +x install-rt73.sh
chmod: cannot access `install-rt73.sh': No such file or directory

```

ughh......

---

### Post by sickgirl485 on 2008-08-30
> **james_vanb said:**
> May be a stupid question, but do you have the install CD and have you tried ndiswrapper?

ndiswrapper keeps coming up, but I have absolutely no idea how to use it

---

### Post by starcannon on 2008-08-30
> **sickgirl485 said:**
> I followed the instructions for this, which weren't that difficult. I downloaded the tarball, extracted it, and all that, and this is what happened when I tried to install the script that was inside the tarball:

```
:~$ sudo sh install-rt73.sh
sh: Can't open install-rt73.sh
```

I get these errors a LOT when it comes to performing commands

shell scripts need to be run with full path in the command.

so try running it this way instead
```

sudo chmod a+x ~/folder/that/script/is/in/install-rt73.sh
sudo ~/folder/that/script/is/in/install-rt73.sh

```

that should work.

---

### Post by sickgirl485 on 2008-08-30
> **starcannon said:**
> shell scripts need to be run with full path in the command.

so try running it this way instead
```

sudo chmod a+x ~/folder/that/script/is/in/install-rt73.sh
sudo ~/folder/that/script/is/in/install-rt73.sh

```

that should work.

it's on the desktop though. and the prompt thing in the terminal is already pointing to the desktop. but i will try it anyway

---

### Post by sickgirl485 on 2008-08-30
> **starcannon said:**
> shell scripts need to be run with full path in the command.

so try running it this way instead
```

sudo chmod a+x ~/folder/that/script/is/in/install-rt73.sh
sudo ~/folder/that/script/is/in/install-rt73.sh

```

that should work.

it did work! it installed the files and everything, and now i will check if the wireless works now

---

### Post by sickgirl485 on 2008-08-30
> **sickgirl485 said:**
> it did work! it installed the files and everything, and now i will check if the wireless works now

I got the wireless working! I ended up using WiFi Radar to get on the network, because the thing in the upper right corner is not doing anything. Cross your fingers for me that it stays working!

---

### Post by knattlhuber on 2008-08-30
> **sickgirl485 said:**
> I got the wireless working! I ended up using WiFi Radar to get on the network, because the thing in the upper right corner is not doing anything. Cross your fingers for me that it stays working!

Super! I'm glad to hear that. Welcome to Ubuntu!

If 'the thing in the upper right corner' gives you problems, you could replace it with [Wicd]("http://wicd.sourceforge.net/").

---

### Post by GepettoBR on 2008-08-30
I have a D-Link DWL-G122 too and it workd OOTB on Hardy. Mine is probably a different H/W version than yours. Talk about bad luck ;)

---

### Post by sickgirl485 on 2008-08-30
> **knattlhuber said:**
> Super! I'm glad to hear that. Welcome to Ubuntu!

If 'the thing in the upper right corner' gives you problems, you could replace it with [Wicd]("http://wicd.sourceforge.net/").

Haha I don't think I will be touching it until it stops working :-P

---

### Post by knattlhuber on 2008-08-30
> **sickgirl485 said:**
> haha i don't think i will be touching it until it stops working :-p

lol

---

### Post by sickgirl485 on 2008-08-31
false alarm...just as i suspected, it stopped working once i restarted....now when i use WiFi Radar it won't connect to the network

---

### Post by knattlhuber on 2008-08-31
> **sickgirl485 said:**
> false alarm...just as i suspected, it stopped working once i restarted....now when i use WiFi Radar it won't connect to the network

What's

```
iwconfig
```

saying now?

---

### Post by sickgirl485 on 2008-09-02
> **knattlhuber said:**
> What's

```
iwconfig
```

saying now?

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-66 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

astro@astro-desktop:~$ 


```

It's more than what it said before I ran the script to install the driver.

---

### Post by knattlhuber on 2008-09-02
> **sickgirl485 said:**
> ```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-66 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

astro@astro-desktop:~$ 


```

It's more than what it said before I ran the script to install the driver.

That looks quite good. It recognizes the card. Do you see any networks when you do

```
iwlist wlan1 scan
```

---

### Post by knattlhuber on 2008-09-02
Also, do

```
gksudo gedit /etc/network/interfaces
```

and check if it contains these lines:

```
auto wlan1
iface wlan1 inet dhcp

```

If not, add them to the file, save it, and restart.

---

### Post by sickgirl485 on 2008-09-02
> **knattlhuber said:**
> That looks quite good. It recognizes the card. Do you see any networks when you do

```
iwlist wlan1 scan
```

This is what happened:

```
~$ iwlist wlan1 scan
wlan1     No scan results

```

Although if I open Wifi Radar, it shows the network of my house but shows that there is no signal. I click connect and it says "acquiring IP address" and then goes back to the regular screen, which still says "not connected"

---

### Post by knattlhuber on 2008-09-02
Thanks for your patience, sickgirl485.

Now, that's really strange that you can't connect despite seeing the network. The only thing that I can think of is that maybe the RTxxxx drivers aren't blacklisted but the installer script that you ran should have taken care of that.

In any case, can you please run

```
cat /etc/modprobe.d/blacklist
```


Does anybody else have a good idea to get this running?

---

### Post by GepettoBR on 2008-09-03
If it doesn't appear in iwlist and wifi-radar shows no signal, amybe it's just a weak signal?

Can you connect if you move the computer right next to the AP?

---

### Post by sickgirl485 on 2008-09-03
> **GepettoBR said:**
> If it doesn't appear in iwlist and wifi-radar shows no signal, amybe it's just a weak signal?

Can you connect if you move the computer right next to the AP?

The problem with that is that my iPod touch and my laptop connect to the wireless and show an excellent signal.

---

### Post by sickgirl485 on 2008-09-03
> **knattlhuber said:**
> Thanks for your patience, sickgirl485.

Now, that's really strange that you can't connect despite seeing the network. The only thing that I can think of is that maybe the RTxxxx drivers aren't blacklisted but the installer script that you ran should have taken care of that.

In any case, can you please run

```
cat /etc/modprobe.d/blacklist
```


Does anybody else have a good idea to get this running?

This is what I got:

```
:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#Added when rt73 modle was installed
blacklist rt73usb
blacklist rt2570
#RT73 SerialMonkey Fix:
blacklist rt2570
blacklist rt73usb
blacklist rt2500usb
blacklist rt2x00lib
#END.
```

---

### Post by knattlhuber on 2008-09-03
OK, so the RTxxxx are blacklisted. Good. But still no connection.

I just took another look at zszafran's thread with the installer script. The second post in that thread by heinorr says that you need to modify /etc/network/interfaces if you use WPA encryption.
[http://ubuntuforums.org/showthread.php?t=848445]("http://ubuntuforums.org/showthread.php?t=848445")

Does your network have WPA encryption?

---

### Post by sickgirl485 on 2008-09-03
> **knattlhuber said:**
> OK, so the RTxxxx are blacklisted. Good. But still no connection.

I just took another look at zszafran's thread with the installer script. The second post in that thread by heinorr says that you need to modify /etc/network/interfaces if you use WPA encryption.
[http://ubuntuforums.org/showthread.php?t=848445]("http://ubuntuforums.org/showthread.php?t=848445")

Does your network have WPA encryption?

Nope, it's a completely open network.

---

### Post by steve33 on 2008-09-12
i'm installing the g122 also on hardy using the script, so far i've extracted the files to directory 'home/steve1';can i ask what the type command is to navigate to a directory? thanks

---

### Post by knattlhuber on 2008-09-12
> **steve33 said:**
> i'm installing the g122 also on hardy using the script, so far i've extracted the files to directory 'home/steve1';can i ask what the type command is to navigate to a directory? thanks

The command is

```
cd /path/to/folder
```

In your case, it'd be

```
cd /home/steve1
```

or shorter

```
cd ~
```

---

