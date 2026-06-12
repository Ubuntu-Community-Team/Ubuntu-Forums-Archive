---
title: "Domain server not working after subnet change?"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by rick7 on 2013-09-03
Hi all, I'm in a bit of a bind, here. I work for a small private school and they've had this ubuntu 10.10 box running for several years as a student domain controller. I'm not really a linux buff but the last guy left me some procedures and I've done ok so far. 

The problem is, last week we had to change the school's subnet, and since then, the kids have not been able to log on. We get errors like "Windows cannot contact the domain" and what not. I am about 95% sure the problem is just the IP address - somewhere in the system it says 192.168.1.whatever where it should have the new subnet. However, I've been through all the smb.conf files I can find and haven't been able to figure anything out. I got ahold of the guy who set up the server but he hasn't really been any help.

I'm wondering if anyone can give me any help.

Thanks,
Rick

---

### Post by SeijiSensei on 2013-09-03
If the machine is a server, it probably has a static IP address configured in /etc/network/interfaces.  Scroll down to the section on "static IP address assignment" in this document:  [https://help.ubuntu.com/13.04/serverguide/network-configuration.html](https://help.ubuntu.com/13.04/serverguide/network-configuration.html)

You'll need to use sudo and become the root user to edit that file.  If you haven't done that before, run the command:

```
sudo nano /etc/network/interfaces
```

and enter your password when prompted.  Nano provides a convenient menu of commands at the bottom of the screen.  Most of them are "control-key" sequences where you hold down the Ctrl key and hit a letter.  The Ctrl key is represented by the carat (^), so "^X" means hold down Ctrl and press X.

---

### Post by rick7 on 2013-09-03
Thank you, that was very helpful. I checked in the Interfaces file and it was still on all the old IP settings. Now, my file looks a little different than the example in the link you gave me; there are two extra lines. My file looks like this:

  address xxx.xxx.x.200
  network xxx.xxx.x.0
  netmask xxx.xxx.xxx.0
  broadcast xxx.xxx.x.255
  gateway xxx.xxx.x.1

Obviously there's numbers where I have placed xxx's because I'd rather not post my internal IP scheme, but you'll see I've got the broadcast and network lines in there that aren't in the example. Would it be safe to just comment those out?

Another problem I notice: using either ifconfig or lshw -network class, I can see that my only ethernet adapter is eth2, while severla config files(including this one) have listed eth0. I have been changing it to eth2.

Now, I did try changing everything over to the new IP scheme and chaning eth0 to eth2, but I'm still not able to log in.

---

### Post by Doug S on 2013-09-03
> but you'll see I've got the broadcast and network lines in there that  aren't in the example. Would it be safe to just comment those out?They should be O.K. to leave there, assuming you have made them correct for the new sub-net.> Another problem I notice: using either ifconfig or lshw -network class, I  can see that my only ethernet adapter is eth2, while severla config  files(including this one) have listed eth0.I wonder why your server is now making your NIC eth2. was the NIC changed to another card? What does this reveal, if anything:```
cat /etc/udev/rules.d/70-persistent-net.rules
```You might want to rename that that file to something else (in case you have to put it back later) and re-boot, as it will automatically be reconstructed upon re-boot.
Going back to more basic things, if you try to "ping" your server by name from the computer you want to log in from, does it work? What I am wondering is if you have some legacy obsolete name to IP address conversions around? (assuming you changed "interfaces = eth0", or whatever your line is, in smb.conf to eth2).

---

### Post by rick7 on 2013-09-04
I can ping, I can even remote in(using RealVNC) from anywhere on the network. It responds to pink by name and IP address. Now, from a windows machine the command net view \\servername yields System Error 5 has occurred. Access is denied. So, ya know, there's that.

So I ran the command Doug S gave me 3 different interfaces, named eth0, eth1, and eth2. I then renamed the file and rebooted, now there is only one entry... eth0. 

But ifconfig still tells me I'm on eth2.

All I can really say here is ????

---

### Post by Doug S on 2013-09-04
> **rick7 said:**
> So I ran the command Doug S gave me 3 different interfaces, named eth0, eth1, and eth2. I then renamed the file and rebooted, now there is only one entry... eth0. 
But ifconfig still tells me I'm on eth2.After you have it so that your only see eth0 in that file, then you would have to go back and change the other edits you did back from eth2 to eth0.

---

### Post by rick7 on 2013-09-04
Well I commented out all of the lines that included interfaces in the smd.conf file. The only other config file that listed eth2 was the interfaces file, which I just changed back to eth0

After rebooting, I still have the same static IP, but ifconfig still listed eth2 and cat/et still says eth0. Is there another config file where I can change eth2 to 0? So far smb.conf and interfaces are the only files I've touched to this regard.

---

