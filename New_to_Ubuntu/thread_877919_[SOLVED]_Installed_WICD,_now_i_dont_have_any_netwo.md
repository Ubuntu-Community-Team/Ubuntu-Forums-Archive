---
title: "[SOLVED] Installed WICD, now i dont have any network manager!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-02
Ok here is the story: i posted another thread, asking for a way to hard-code my ipaddress on my router. someone suggested WICD. I opened Synaptics Package Manager, and did a search for it. 

Now the tricky part: It said it would install WICD, and uninstall gnome-network-manger, and some other network-manager. My initial thought was "I hope it doesnt uninstall my network manager first so it losses network connection before it downloads WICD.... Nah linux is smarter than that."

Sure enough, my internet stopped working, i go to the details of the install, and network-manager was uninstalled first, and the WICD installed failed due to time out or something. 

So how do in stall one or the other back? (dont really care at this point, i just need any network manager). I assume i have to downlaod from another computer, and run binaries? I was hoping to learn a little about linux b4 i jumped into that. I do also have my install disc, so if i could get some instructions oh how to do a recovery, that could also work.

I'm new at linux, so what do u guys suggest?

---

### Post by eightmillion on 2008-08-02
I've had this happen before also. What I did was uncommented the apt cdrom line in my sources file and then grabbed network manager from my install cd.

---

### Post by eightmillion on 2008-08-02
Here's an example.

```

gksu gedit /etc/apt/sources.list

The first line should look something like this:
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

Remove the pound sign from the front of that line and save the file.
Insert your install CD.

sudo apt-get update
sudo apt-get install network-manager-gnome

```

Then you should have your network manager back.

---

### Post by stevoo on 2008-08-02
Go to 
System->Administration->Network

Unlock it  ,and make sure that Wired Connection has a Tick instead of a -.

---

### Post by deathvalleyjoker on 2008-08-02
cool i commented out the CD in the sources.list. i enabled the network again. now maybe you can help me with my original problem:

how can i give myself a static ipaddress on my network?

thanks again for all the help.

---

### Post by chuckyp on 2008-08-02
If you are given a dynamic ip on your net work of something like 192.168.0.130 or something to that effect.  You just need to specify an ip in that same class but outside of the routers DHCP.  Most routers are set to hand out approximately 50 ips so they would be 192.168.0.100 through 192.168.0.150.  Try specifying an ip in this case of 192.168.0.200.  Keep in mind your network you may be 192.168.1.*** So run ipconfig in terminal and see what your router is handing to you.

Also you can right click on the network manger applet by the clock to change the settings of your card.  Or you can System > Administration > Network

---

### Post by eightmillion on 2008-08-02
I'm not sure how to do it with the gnome gui, but you can set it up through your /etc/network/interfaces file.

```

gksu gedit /etc/network/interfaces

```
The file should look like this:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dynamic

```
You want to change it to something like this:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1

```
You'll have to change address, gateway and netmask to be appropriate for your network.

---

### Post by deathvalleyjoker on 2008-08-02
chuckyp jsut made me relize something: the network icon is now gone from my panel.and  the +add to panel downt have it in there. any thoughts?

8M: sweet ill try that and let u know how it works out.

thanks again all.

---

### Post by eightmillion on 2008-08-02
You might try running it from the command line with 'nm-applet'. If that works, chances are you'll just have to log out and log back in to get it working.

---

### Post by deathvalleyjoker on 2008-08-02
I got the static ip to work! and i created a backup of the original for when i move bac to college, incase i have any connection issues. 

its a nogo on the nm-applet however:

mikey@mikey-desktop:~$ nm-applet
The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>
bash: nm-applet: command not found

mikey@mikey-desktop:~$ sudo apt-get install nm-applet
[sudo] password for mikey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nm-applet
mikey@mikey-desktop:~$ 

p.s. how do i put things in a code box like you did above? thanks.

---

### Post by eightmillion on 2008-08-02
You need to install 'network-manager-gnome'.
```
sudo apt-get install network-manager-gnome
```

> p.s. how do i put things in a code box like you did above? thanks.
To put code in a code box you surround it with:
[HTML]```

```[/HTML]
Code should be all caps also. I can't get it to display right.

---

