---
title: "HOWTO: DWL-G122 on Ubuntu."
date: 2006-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jISh on 2006-07-04
This guide has been moved, and will be periodically maintained here:
[http://doc.gwos.org/index.php/HowToDWLG122](http://doc.gwos.org/index.php/HowToDWLG122)

---

### Post by jnutter on 2006-07-09
Nice post. It was a lot easier to understand than some that I've seen.  

I'm a Linux newb and I'm trying to get a DWL-G122 working on an old box with an AMD K6-III, 400  mhz processor. My DWL-G122 is hardware version B1 with the Ralink RT2500 chip set. I'm using Ubuntu 6.06. 

I followed your directions, except for substituting the .inf and .sys file from my CD. I set everything up for a static IP. Put in my wireless network name, key and channel. Also made sure my router had my MAC addres entered in the exceptions box to accept that MAC id. 

When I first went to my network settings box it was there but not active and it needed all the properties filled in. I did that and re-started. Now when I go to my network settings box it shows up as a wireless connection, but is not active. I click to activate it and it says it is active and the light lights up, but I can't ping my router at 192.168.0.1 or my other machine at 192.168.0.99

I can plug the D-link into my XP box and it works fine. 

Any ideas?

Edit/Update: 

Solved the problem with the DWL-G122 not coming up active on a re-boot by using the GUI network settings editor under the system > administration menu. This created an entry in the network interfaces file, but I still had to go in and manually delete the entries I had made from the above instructions. At this point the DWl-G122 started up on a re-boot, but still couldn't ping anything. 

I put my router and my XP box back to DHCP. Still couldn't ping. Finally figured out that the WEP key was set for ASCII in the network settings>properties for the DWl-G122. Changed it to hex and now it will at least ping the router and my other box, still can't find any internet sites other than my ISP though. Probably some DNS issue...

---

### Post by dicecca112 on 2006-07-09
well I don't totally agree with your guide.  I have found that the dapper ndiswrapper is terrible.  I have always done this

Download latest Ndiswrapper

extract to my home
cd ndiswrapper-x.xx
make distclean
make 
sudo make install

sudo ndiswrapper -i "PRISMA02.inf"
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

then manually went to System -> Adminstrative -> Networking were I go to the properties of the wireless device and add my SSID.  Has worked flawlessly.  with the stock ndiswrapper I get random freezes and hardlocks

---

### Post by jnutter on 2006-07-09
One more bit of info - I get lockups often when I try to use the GUI networking tool. If I stay out of that it seems to be OK (will post again if I learn otherwise). Using the text style editor and then re-booting after changes seems to the the best for me using the stuff I outlined in my first post. 

Thanks for the help. I've wanted ot get this machine setup like this for a while. I'm very happy to have this done.

---

### Post by jISh on 2006-07-11
@dicecca112:
I never had a problem with the original ndiswrapper, it worked flawlessly. The updated one from the repos also has had no problems for me. I wonder why there is a difference?

@jnutter:
Wireless networking is the usual cause of Linux locking up. However, I haven't had a single one due to networking on this Ubuntu box.

The Networking box just modifies whats in the text file, I'm not sure what is causing your lockups. However, I would stick to modifying the text file as your method of changing settings. The auto wlan0 line should have kept it coming up at boot, as well as the sudo modprobe ndiswrapper -m command.

Anyways, glad you got it working! It was a real hassle, I couldnt' even get it to work at all back on MEPIS. Locked up every 5 mins ;/

---

### Post by wislon on 2006-07-30
I posted about the hardlocks (especially with wifi radar) and stuff elsewhere on the forum before stumbling across this post. I am using the stock ndiswrapper and WPA. I am using the DWL-G120 myself (but USB registers it as a 'Cohiba' something, had to check out the ndiswrapper  wiki for the right driver), but the problems seem similar. 

As soon as I use a GUI network manager tool, I run into problems. Even without, it's still flaky, dropping the connection and requiring a deactivation and then reactivation of the wlan0 interface (using the applet under System | Networking)

I'd be interested to see if getting a non-stock ndiswrapper helps here. One of the other posts suggested blacklisting 'islsm' and 'p54u' from the modprobe list. If it helps, I'll post here :)

[Update]
Ok, 'islsm' and 'p54u' didn't exist on the machine, so the blacklisting was a no-go anyway. However, as soon as I removed the 'auto wlan0' line in the /etc/network/interfaces file, and rebooted, wifi-radar started working perfectly. It's rock solid now. The network manager applet doesn't show my wlan0 device until wifi-radar has me connected to something tho.

Hope this helps someone :)

---

### Post by Frafra on 2006-08-03
In my cd there aren't the driver. in drivers/ there is only a setup.exe. Could you send me to francesco.it [at] gmail [dot] com these files? Please! Tomorrow night I've a linux conference in Italy an I have to use my wifi connection. Thanks!

---

### Post by Straumoy on 2006-08-31
Hey there,

Your guide looks very good though there are a few problems that I've encountered along the way, and due to my linux n00bness, I'm unable to sort them out.

First problem is with ndiswrapper. I don't find a package called ndiswrapper,  I find ndisgtk, ndiswrapper-source and ndiswrapper-utils. To play it on the safe side, all of these are downloaded and installed.

Second problem is with the driver files, the *.inf and *.sys guys. Now you did mention that the files names would differ, which is cool, but when I go into D:\drivers\drivers I find no files of any kind, just two other folders called Win98ME and WinXP2K. So I dig deeper into the WinXP2K folder and there I find NetRTUSB.cat, NetRTUSB.inf, rt25u98.sys and rt2500usb.sys.

So which one is it, of the *.sys files I mean. Normally (under "good ol'" windows) I'd just give it a swing, since there's a 50% chance of success and if things go wrong I can undo it (in theory), but since I'm clueless of just what I'm doing, how to do it, what gets changed and how to reverse the process, I'd rather not take any chances at this point, especially since I might have run into a potential problem with ndiswrapper earlier on.

---

### Post by jISh on 2006-08-31
Hi.

First of all, you are right I will clarify my guide some more, as I was also pretty new to Linux when I wrote it. 

Now I am not entirely sure what exact files you need, but if I had to guess, I'd say from the WinXp2k folder you should use:
NetRTUSB.inf and rt2500usb.sys

You can simply 
```

ndiswrapper -i NetRTUSB.inf

```

*Note: Linux is case sensitive, so be sure to include correct capitalization*
And see if it works. If not, try the other two files, and mixing/matching them. Check using 
```

ndiswrapper -l

```
To see if it worked properly. You should see the name of the
driver you installed, followed by "driver present" and "hardware present"

Good luck!

---

