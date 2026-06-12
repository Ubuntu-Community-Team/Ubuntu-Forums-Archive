---
title: "Lost all network connectivity"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by kyphos on 2012-04-03
I'm a Linux neophyte struggling up the learning curve. A few months ago, I downloaded the 10.04 LTS LiveCD and successfully configured my first Linux system. Great fun - I got Firefox running, installed a few applications, and explored the many capabilities.  Then I had to put the project on hold due to some family obligations.

Today, I booted up the system and found it had no network connectivity. After eliminating bad ethernet cables and routers, I started looking under the covers. Oddly, the Network Connections page was completly empty, so I added a new Wired Connection. Configured it for DHCP. Rebooted. No luck.  Changed from DHCP to Manual, and specified an unused IP address (plus subnet mask, gateway, and DNS).  Rebooted again. Still no joy.

So off to the world of ifconfig. I read many man pages and troubleshooting web sites. Fairly quickly, I discovered that eth0 was DOWN, so I turned it UP, but that was insufficient.   Eventually, I was able to reactivate the network by (1) assigning it an IP address, (2) defining the default gateway, and (3) specifying a DNS server. To wit:

```
sudo ifconfig eth0 192.168.1.250 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
```And I edited the /etc/resolv.conf file (which was empty) to add a line: ```
nameserver 192.168.1.1
```With these 3 changes, my system is back on the air. But the fixes don't survive a reboot.

I hoping someone can point me in the right direction to get the proper network parameters permanently configured. I would have thought the Network Connections tool was the way to specify a network interface, but as far as I can tell, it has absolutely no impact on my system.

And I'm mystified as to what could have wiped out my entire network configuration when it used to work just fine a couple months ago.

I should mention that having manually specified the network settings, I was able to run Update Manager. It downloaded a couple hundred MBs of new and improved code, so my 10.04 LTS is fully up-to-date. Yet if I reboot it, it once again is network-less.

Thanks.

---

### Post by Zill on 2012-04-03
> **kyphos said:**
> ...And I'm mystified as to what could have wiped out my entire network configuration when it used to work just fine a couple months ago...
Personally, I am not a great fan of the Gnome Network Manager and so I prefer to configure networks the old-fashioned way.  ;-)

I suggest you first open a terminal and take a look at the file /etc/network/interfaces with the "cat" command:
```
cat /etc/network/interfaces
```
You will probably find that it just contains the following two lines:
```
auto lo
iface lo inet loopback
```
If you use an editor (such as nano) to add your wired-connection details to this file it should make it persistent after a reboot.  eg.
First copy the old file as a backup:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_orig
```
Then edit the file:
```
sudo nano /etc/network/interfaces
```
Add the following details of your connection. eg.
```
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
```
Also add the following line:
```
auto eth0
```
Save the file in nano with Ctrl-o then Ctrl-x to exit nano.
Check the resulting file looks like the following with the cat command:
```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```
Reboot and check if the wired connection works OK.

---

### Post by kyphos on 2012-04-03
@Zill,
Thanks for the late night response!

In general, I agree with you re doing things the old-fashioned way, but alas I have insufficient expertise to be old-fashioned with Ubuntu. The learning curve is steep.

In any event, I found a fix for my problem before I saw your reply. Thanks to a posting at ubuntugeeks.com, I learned that the secret was to add a **Notification Area** to the panel at the top of screen.

(right-click on the black stripe at the top of the screen, choose **Add to Panel...**, and then select** Notification Area** from the list of goodies).

Having done that, a little exclamation mark appeared in the panel. It was notifying me that networking was disabled. I checked a box to Enable Networking, and then as if by magic, the Network Manager applet appeared in the panel. With it, I was able to select the wired interface (eth0), and disable wireless networking (since I don't want it). My system (a little Zotac nettop) has a really crappy WiFi interface in it).

With that, I'm back in business. Networking survives across a reboot:-)

I'm not quite sure how the Network Manager applet disappeared in the first place. It was present in the Panel following the installation from the LiveCD, but I must have done something to delete it.  And I sure don't understand why adding a Notification Area is a pre-requisite to getting the NM applet to appear. That is not at all obvious.

Thanks again for your reply, and the pointer to /etc/network/interfaces. I may go spelunking in there when I have some time.

Cheers from The Colonies (Canada)

---

### Post by Zill on 2012-04-04
kyphos:  Congratulations on getting your network connection working again.  One of the great things about Linux is that there are often multiple ways to solve a problem - we are not forced to do things a certain way, unlike some other OS's. ;-)

FWIW, I prefer to configure my /etc/network/interfaces file simply because it "just works" and is not dependent upon the vagaries of the latest GUI applet.

I do use the Gnome Network Manager on a netbook because it is quite handy while roaming away from home.  However, for other wireless connections I prefer to use the [Wicd]("http://wicd.sourceforge.net/") network manager, rather than the Gnome version (the default in Ubuntu).

---

### Post by kyphos on 2012-04-04
@zill,
Thanks for the pointer to WICD. I will check it out.

Should I decide to configure the my networking directly with the /interfaces file as you recommend, how do I stop the Gnome Network Manager from meddling with my settings? Do I have to uninstall Network Manager, or otherwise prevent it from launching at boot time?

Thanks again for your help. This forum is quite useful for newcomers.

---

### Post by Zill on 2012-04-04
> **kyphos said:**
> ...Should I decide to configure the my networking directly with the /interfaces file as you recommend, how do I stop the Gnome Network Manager from meddling with my settings? Do I have to uninstall Network Manager, or otherwise prevent it from launching at boot time?...
I always configure the interfaces file *first* to ensure I have a working wired connection.  I then generally install Wicd to give additional control over wireless connections, but this also picks up the wired info from the /interfaces file.  I am not certain if Network Manager will pick up this info in the same way so you will just have to experiment to find out.  However, I don't think Network Manager will *change* the settings in the /interfaces file as I believe it stores its data elsewhere.

If you install Wicd (in the repos) then you should remove *all* installed network-manager packages (eg. network-manager and network-manager-gnome etc) to avoid a conflict with Wicd.  The best way to do this is to use the Synaptic package manager, as this allows you to see all the packages together and then select wicd for installation and network-manager for removal *all at the same time*.  You have to be careful not to get in a situation where you have no network connection, otherwise you won't be able to install a network manager. ;-)

---

### Post by kyphos on 2012-04-04
OK - thanks again for all your advice.

---

