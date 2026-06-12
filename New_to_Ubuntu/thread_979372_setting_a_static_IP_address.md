---
title: "setting a static IP address"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-11
how can i go about setting a static IP address in ubuntu 8.10?  when my computer boots up ubuntu automatically assigns an IP address via DHCP from my home network router.  so i then go into Network Configuration and modfy the autoeth0 entry to be a manual IP address, which works fine and i am connected.  however when i rebot the computer ubuntu automatically reassigns the IP address via DHCP and i have to reassign the static IP address again.  so i'm not sure how to make the static IP address change permanent.

thanks.

---

### Post by drakeman007 on 2008-11-11
> **Matt26 said:**
> how can i go about setting a static IP address in ubuntu 8.10?  when my computer boots up ubuntu automatically assigns an IP address via DHCP from my home network router.  so i then go into Network Configuration and modfy the autoeth0 entry to be a manual IP address, which works fine and i am connected.  however when i rebot the computer ubuntu automatically reassigns the IP address via DHCP and i have to reassign the static IP address again.  so i'm not sure how to make the static IP address change permanent.

thanks.

Hello you have to remove the ubuntu network manager
```
sudo apt-get remove network-manager
```
and then edit the interfaces file
```
sudo gedit /etc/network/interfaces
```
and pu your dns with
```
sudo gedit /etc/resolv.conf
```

you need the format in how to put the ip info?
thanks

---

### Post by ghost_ryder35 on 2008-11-11
right click network manager, click edit connections, then click add.

---

### Post by ghost_ryder35 on 2008-11-11
> **drakeman007 said:**
> Hello you have to remove the ubuntu network manager
```
sudo apt-get remove network-manager
```and then edit the interfaces file
```
sudo gedit /etc/network/interfaces
```and pu your dns with
```
sudo gedit /etc/resolv.conf
```you need the format in how to put the ip info?
thanks
you do NOT have to remove network manager at all

---

### Post by drakeman007 on 2008-11-11
> **ghost_ryder35 said:**
> you do NOT have to remove network manager at all

Yes, i have to do in this way, because, everytime i put the ip info in network manager, everytime i restart ubuntu, the ipconfig reset and put in dhcp again, and somebody here told me that this is a bug in intrepid, and the solution is uninstalling network manager... and edit the files to set the ip address manually!

But you can try first the ghost ryder solution and see what works for you, try first with the gost ryders solution...
thanks

---

### Post by ghost_ryder35 on 2008-11-11
> **drakeman007 said:**
> Yes, i have to do in this way, because, everytime i put the ip info in network manager, everytime i restart ubuntu, the ipconfig reset and put in dhcp again, and somebody here told me that this is a bug in intrepid, and the solution is uninstalling network manager... and edit the files to set the ip address manually!

But you can try first the ghost ryder solution and see what works for you, try first with the gost ryders solution...
thanks
If you believe you have found a bug please submit a bug report [https://launchpad.net/ubuntu/+filebug/+login](https://launchpad.net/ubuntu/+filebug/+login) and document the problem and the workaround [http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

---

### Post by handydan918 on 2008-11-11
> **drakeman007 said:**
> Yes, i have to do in this way, because, everytime i put the ip info in network manager, everytime i restart ubuntu, the ipconfig reset and put in dhcp again, and somebody here told me that this is a bug in intrepid, and the solution is uninstalling network manager... and edit the files to set the ip address manually!

But you can try first the ghost ryder solution and see what works for you, try first with the gost ryders solution...
thanks

Ahhh, garbage. Ubu will accept whatever dhcp address is assigned to it. So tell you router to assign a specific IP via dhcp.
That's what I do...

---

### Post by drakeman007 on 2008-11-11
This is the topic i create when i have this problem

[http://ubuntuforums.org/showthread.php?t=973410&highlight=ip+config+restart](http://ubuntuforums.org/showthread.php?t=973410&highlight=ip+config+restart)

---

### Post by stmiller on 2008-11-11
Don't instruct someone to remove network-manager. Especially in the Absolute Beginner Talk forum. That is just prompting for disaster...

To answer the question as someone mentioned above, leave Ubuntu as DHCP / dynamic. Set the static ip address in your router. 

:)

---

### Post by ghost_ryder35 on 2008-11-11
> **drakeman007 said:**
> This is the topic i create when i have this problem

[http://ubuntuforums.org/showthread.php?t=973410&highlight=ip+config+restart](http://ubuntuforums.org/showthread.php?t=973410&highlight=ip+config+restart)
No bug on Network Manager relating to it not accepting static configurations see[ Launchpad]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=network+manager&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---

### Post by Matt26 on 2008-11-12
> **ghost_ryder35 said:**
> right click network manager, click edit connections, then click add.

thanks, that worked- although i had to remove the autoeth0 entry for this to work, which makes sense.

---

### Post by hovzio on 2008-11-12
> **handydan918 said:**
> Ahhh, garbage. Ubu will accept whatever dhcp address is assigned to it. So tell you router to assign a specific IP via dhcp.
That's what I do...


I have to agree to the later part of this statement, I wouldnt even mess with ubuntu. In your router, you can assign static IP's via dhcp using the mac address of the box. That is probably the simplest way, that way the pc always has the same ip. Removing the network manager (in my opinion) should be a last resort.


EDIT: nevertheless, the question was how to set a static ip in ubuntu, happy it worked for you using the NM.

---

### Post by drakeman007 on 2008-11-12
Sorry guys, i just was trying to help, im newbie to, sorry, but glad to read that you solve your problem!

---

### Post by Matt26 on 2008-11-12
> **Matt26 said:**
> thanks, that worked- although i had to remove the autoeth0 entry for this to work, which makes sense.

i guess i spoke to soon- once i rebooted my computer the automatic DHCP configuration came back (i had previously removed it) and reassigned an IP address again- is there a way to get rid of the DHCP assignment permanently?

---

### Post by fidamehran on 2008-11-13
> **Matt26 said:**
> i guess i spoke to soon- once i rebooted my computer the automatic DHCP configuration came back (i had previously removed it) and reassigned an IP address again- is there a way to get rid of the DHCP assignment permanently?

So.......
What's the solution?
On one hand,people are discouraging network manager removal and the advanced stuff. On the other hand people are advising changing settings through menu which is not working always (not working for me too).
Unlike my friend here, I want the DHCP to stay also. because, my ISP changes my IP sometimes. A few days back it gave me a statiz IP, but before that I had a DHCP (Automatic connect to Internet) kind of option. So, better have both.
So what's the solution?

---

### Post by blackened on 2008-11-13
> **fidamehran said:**
> So.......
What's the solution?
On one hand,people are discouraging network manager removal and the advanced stuff. On the other hand people are advising changing settings through menu which is not working always (not working for me too).
Unlike my friend here, I want the DHCP to stay also. because, my ISP changes my IP sometimes. A few days back it gave me a statiz IP, but before that I had a DHCP (Automatic connect to Internet) kind of option. So, better have both.
So what's the solution?

I think you're misunderstanding the concepts being discussed.

[http://en.wikipedia.org/wiki/IP_address#Static_and_dynamic_IP_addresses]("http://en.wikipedia.org/wiki/IP_address#Static_and_dynamic_IP_addresses")

---

### Post by fidamehran on 2008-11-13
> **blackened said:**
> I think you're misunderstanding the concepts being discussed.

[http://en.wikipedia.org/wiki/IP_address#Static_and_dynamic_IP_addresses]("http://en.wikipedia.org/wiki/IP_address#Static_and_dynamic_IP_addresses")

I'm not sure I misunderstood. I am going through the same problem. Let me be elaborate. I used to have a Dynamic IP which I was using through the DHCP option. Then I was given a Static IP from my ISP, and I changed the settings to Manual Configuration once again. I was using Hardy Heron then. 3 days back I installed Intrepid and now I see the new problem.
What I wanted to say here is that, I am also afraid of using sudo to remove stuff in Ubuntu (as I am quite a newbie).
Then comes the second option.
It was GUI based, but I also tried it and failed.
By the way, I found a new solution here:
["http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/"]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/")
Hope it will work.

---

### Post by Jose Catre-Vandis on 2008-11-13
You seem to know enough about what you are doing to not be unduly concerned about network manager (whilst I agree with previous posters about removing things for newbies)

This does depend on what you use your computer for, but lets assume it just sits there and will always and only ever connect to your router.

Go into your router and assign a static IP for your PC, using the MAC address to tie it in. Leave DHCP server running if you need DHCP connections to your home network, otherwise assign static IPs for all the PCs / devices on your network.

Once that is done, back on your PC, find the startup programs section and untick Network Manager (sorry, but right now on an XP machine, and can only remember how to do this in xubuntu Menu > Settings > Settings Manager > Autostart Apps). This will ensure it doesn't start up, but will mean you have no connection if you don't configure further. 

Next edit your /etc/network/interfaces file and set it up for the static IP you set for your PC in your router. Restart networking:
```
sudo /etc/init.d/networking restart
```
You should be connected.

You also mention that your ISP has provided you with a static IP. If you want your PC to be "open" to the internet, you will need to use the port forwarding feature in your router to set your PC as the internet IP address. You do not need to change anything on the PC for this, but bear in mind that security issues then become a concern.

If this doesn't work, put the tick back in Autostart Apps, and network Manager should pick up your connection again.

I always follow this approach for my "static" machines and never have any problems

---

### Post by Matt26 on 2008-11-13
> **Jose Catre-Vandis said:**
> You seem to know enough about what you are doing to not be unduly concerned about network manager (whilst I agree with previous posters about removing things for newbies)

This does depend on what you use your computer for, but lets assume it just sits there and will always and only ever connect to your router.

Go into your router and assign a static IP for your PC, using the MAC address to tie it in. Leave DHCP server running if you need DHCP connections to your home network, otherwise assign static IPs for all the PCs / devices on your network.

Once that is done, back on your PC, find the startup programs section and untick Network Manager (sorry, but right now on an XP machine, and can only remember how to do this in xubuntu Menu > Settings > Settings Manager > Autostart Apps). This will ensure it doesn't start up, but will mean you have no connection if you don't configure further. 

Next edit your /etc/network/interfaces file and set it up for the static IP you set for your PC in your router. Restart networking:
```
sudo /etc/init.d/networking restart
```
You should be connected.

You also mention that your ISP has provided you with a static IP. If you want your PC to be "open" to the internet, you will need to use the port forwarding feature in your router to set your PC as the internet IP address. You do not need to change anything on the PC for this, but bear in mind that security issues then become a concern.

If this doesn't work, put the tick back in Autostart Apps, and network Manager should pick up your connection again.

I always follow this approach for my "static" machines and never have any problems

i understand that this should be a valid option for most users out there however not every home router has this feature available, but more importantly i think that users should not have to resort to this option if they would rather not- some people (myself included) may prefer to setup IP addresses manually on each machine, and if they prefer not to use DHCP on their home router they would be forced to because DHCP needs to be turned on for static DHCP assignment to work (provided my unserstanding of static DHCP is accurate).  i'm going to try out the solution provided by fidamehran in the meantime- i just believe that this should be a simple change to make.  just my opintion.

and according to the link provided, this issue is a bug that was missed in the 8.10 release of ubuntu...

---

### Post by Jose Catre-Vandis on 2008-11-13
"static DHCP" is an oxymoron

Normally, on most home routers you can have your IP configuration setup in three ways:

DHCP - all IP addresses are assigned dynamically (although the router will "remember" your machine from last time if no other machine required that dynamically assigned address (is this what you mean by static DHCP?))

DHCP and Assigned Addresses (usually by MAC address) - the DHCP server still running, but you can assign a static IP to specific machines/devices using their MAC address. Machines not assigned can still connect via DHCP

DHCP off - you must manually assign IP addresses to machines/devices

No doubt there are other settings/configurations.

---

### Post by pablolie on 2008-11-13
I for one simply entered a new connection via the right-click network manager connection. You enter the IP address you want (within your home subnet, but outside the range you allocated to your DHCP server), the subnet mask, the gateway IP address, and off you go.

It is true that 8.10 reverts to eth0 as the default after every restart, but than can be remedied by deleting it.

The other method is to fix the allocation of a certain DHCP managed address to a certain device. I for one like having some IP addresses for some key functions outside of the DHCP space.

---

### Post by Matt26 on 2008-11-13
> **Jose Catre-Vandis said:**
> "static DHCP" is an oxymoron

Normally, on most home routers you can have your IP configuration setup in three ways:

DHCP - all IP addresses are assigned dynamically (although the router will "remember" your machine from last time if no other machine required that dynamically assigned address (is this what you mean by static DHCP?))

DHCP and Assigned Addresses (usually by MAC address) - the DHCP server still running, but you can assign a static IP to specific machines/devices using their MAC address. Machines not assigned can still connect via DHCP

DHCP off - you must manually assign IP addresses to machines/devices

No doubt there are other settings/configurations.

i agree that the term is an oxymoron, however this is the common reference for this type of IP address assignment.  in fact, many routers (including the ones that i have worked on) refer to it as Static DHCP in the router's admin area.

i can't say i have ever seen or heard it called DHCP and Assigned Addresses, but i believe that is the same thing, plus i don't think there is another way of assigning static IP addresses to computers via a router other than based on their MAC address.

---

### Post by Matt26 on 2008-11-13
> **pablolie said:**
> I for one simply entered a new connection via the right-click network manager connection. You enter the IP address you want (within your home subnet, but outside the range you allocated to your DHCP server), the subnet mask, the gateway IP address, and off you go.

It is true that 8.10 reverts to eth0 as the default after every restart, but than can be remedied by deleting it.

The other method is to fix the allocation of a certain DHCP managed address to a certain device. I for one like having some IP addresses for some key functions outside of the DHCP space.

not the case for me unfortunately- i have tried removing the auto (eth0) entry from Network Configuration however it comes right back upon reboot (see my post earlier in this thread).

i am hoping that the steps in the link provided by fidamehran will work out for me.

---

### Post by Matt26 on 2008-11-14
> **Matt26 said:**
> not the case for me unfortunately- i have tried removing the auto (eth0) entry from Network Configuration however it comes right back upon reboot (see my post earlier in this thread).

i am hoping that the steps in the link provided by fidamehran will work out for me.

unfortunately the posted workaround provided here did not do the trick for me- i still have eth0 (DHCP) trying to connect automatically every time i restart the computer, regardless of which options i change for this entry- is anyone else having problems like this?

---

### Post by redbob on 2008-11-14
Well, I'm astonished with this question and answers proposed. What do you want - simply assign a Static IP directly into your eth0 interface? At home, I've got three desktops, even my router has a DHCP activated, all the three has got Static IP. I just assign a Static IP editing /etc/network/interfaces by this way:
> 
iface eth0 inet static
address 10.1.1.13
netmask 255.0.0.0
gateway 10.1.1.1

auto eth0

Perhaps I didn't undestand what do you really want.
:confused:

---

### Post by blackened on 2008-11-15
> **redbob said:**
> Well, I'm astonished with this question and answers proposed. What do you want - simply assign a Static IP directly into your eth0 interface? At home, I've got three desktops, even my router has a DHCP activated, all the three has got Static IP. I just assign a Static IP editing /etc/network/interfaces by this way:

Perhaps I didn't undestand what do you really want.
:confused:

I've accomplished it both ways on 8.10: my laptop ip is assigned via network manager as static, on my server (cli only) I assigned it via /etc/network/interfaces and resolv.conf. Both ways it holds through all reboots and has since intrepid betas.

---

### Post by Matt26 on 2008-11-15
> **redbob said:**
> Well, I'm astonished with this question and answers proposed. What do you want - simply assign a Static IP directly into your eth0 interface? At home, I've got three desktops, even my router has a DHCP activated, all the three has got Static IP. I just assign a Static IP editing /etc/network/interfaces by this way:

Perhaps I didn't undestand what do you really want.
:confused:

yes this is what i want, however as you can probably tell from the responses given here, this is an issue for others as well.  i understand that i can simply edit the connection settings via the interfaces and resolve.conf files, but my issue is that i fail to see why it cannot be done properly via the GUI interface (using the Netowrk Configuration screen) for everyone.

---

### Post by Old Jimma on 2009-01-01
Hi Ubuntu Community:

I read this thread because I wanted to have a static Ip on my network, also.

Some of the suggestions were to remove network manager.

In my attempts, I did this.

The result was to make it impossible to access the internet. I had to scrounge another computer, download the 8.10 iso, and reload the whole system. 

So, IF YOU ARE READING THIS THREAD ask the guy who is recommending that you remove network manager to do it himself first to see what happens. If you don't hear from him, good chance he found out his advice was not so good.

Of course, I could be wrong about all of this... I'm just speaking from my experience. Please note one of the comments above that removing network manager invites catastrophe... that is my experience.

Phil Smith
Duluth, GA

---

### Post by zika on 2009-01-01
_[http://ubuntuforums.org/showpost.php?p=6461701&postcount=5](http://ubuntuforums.org/showpost.php?p=6461701&postcount=5)_

---

### Post by Dedoimedo on 2009-01-01
> **Jose Catre-Vandis said:**
> "static DHCP" is an oxymoron

Normally, on most home routers you can have your IP configuration setup in three ways:

DHCP - all IP addresses are assigned dynamically (although the router will "remember" your machine from last time if no other machine required that dynamically assigned address (is this what you mean by static DHCP?))

DHCP and Assigned Addresses (usually by MAC address) - the DHCP server still running, but you can assign a static IP to specific machines/devices using their MAC address. Machines not assigned can still connect via DHCP

DHCP off - you must manually assign IP addresses to machines/devices

No doubt there are other settings/configurations.

Hello there!

Static DHCP definitely sounds interesting, but it's not exactly an oxymoron. You can use the host directive in the dhcpd.conf file to set static IP address to specific DHCP clients based on their name & mac address.

In other words, clients use dhcp alright, but they get only a specific IP address.


OT, I've managed to set static IP as I've shown in me Ubuntu tutorial (sig), under More about Network Manager.

Cheers,
Dedoimedo

---

### Post by ice031 on 2009-01-30
Solved: You don't have to uninstall Network Manager.
To keep your static ip settings 
1. Right Click on Network Manager icon
2. Select Edit Connection
3. Click on the Add button
This will add a new connection setting

4. Type in your MAC Address
> 
Note:
This can be found typing the ifconfig command in the Terminal. 
Look for your HWaddr(MAC address). e.g. Mine was eth0 Link encap: Ethernet HWaddr 1a:2b:3c:4b:5b:78


5. Click on the IPv4 Settings tab and under method select Manual.

6. Click on Add.
The first box (Address) should be selected already. 
After that just click on eat of the the fields to type them in.

> Note:
Netmask is usually 255.255.255.0
(unless you or your admin has subnetted your address(i.e. 255.255.252.0, type in the default NetMask as mentioned)

Gateway is usually your address with the last number being 1.
(i.e. if your ip is 192.168.100.107
then your gateway will be 192.168.100.1)

Then your DNS Servers. 
If you have more than one, you can separate them with commas
(i.e. 111.111.11.1, 222.222.22.2)

7. Click Ok

8. Restart and that's it.
(Cheers)

---

### Post by ice031 on 2009-01-30
Phil Smith, 
I am sorry that you had to go through all that trouble to reinstall ubuntu 8.10 again. Actually if you did uninstall NetworkManager and find that you don't have internet access anymore,you can always re-install it again by looking for the NetworkManager in the Synaptic Package Manager again. 

Actually, I did the same thing as you and reinstalled the pacakge.
After that---> Please read my post on a detailed solution on how to setup the static IP. 
Cheers! :)

---

### Post by ice031 on 2009-01-30
> **Phil Smith said:**
> Hi Ubuntu Community:

I read this thread because I wanted to have a static Ip on my network, also.

Some of the suggestions were to remove network manager.

In my attempts, I did this.

The result was to make it impossible to access the internet. I had to scrounge another computer, download the 8.10 iso, and reload the whole system. 

So, IF YOU ARE READING THIS THREAD ask the guy who is recommending that you remove network manager to do it himself first to see what happens. If you don't hear from him, good chance he found out his advice was not so good.

Of course, I could be wrong about all of this... I'm just speaking from my experience. Please note one of the comments above that removing network manager invites catastrophe... that is my experience.

Phil Smith
Duluth, GA
Phil Smith,
I am sorry that you had to go through all that trouble to reinstall ubuntu 8.10 again. Actually if you did uninstall NetworkManager and find that you don't have internet access anymore,you can always re-install it again by looking for the NetworkManager in the Synaptic Package Manager again.

Actually, I did the same thing as you and reinstalled the pacakge.
After that---> Please read my post on a detailed solution on how to setup the static IP.
Cheers!

---

### Post by wlraider70 on 2009-01-30
This is what I did to get a static IP

I was told go to /etc/network/interfaces (you may have to change permission)

it looks like this...

(start)

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface , all the 3rd level "1" were "0"
auto eth0
iface eth0 inet static
address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
gateway  192.168.1.1

(end)

As far as i can tell this also disabled some my wired network configuration. 

Your numbers might require some tweaking.

---

### Post by zika on 2009-01-30
> **ice031 said:**
> Actually if you did uninstall NetworkManager and find that you don't have internet access anymore,you can always re-install it again by looking for the NetworkManager in the Synaptic Package Manager again.
it can be a little tricky to re-install once You've lost internet connection ... :)
+1 for not uninstalling NetworkManager but beeing unbending in either entering data in NM or editing interfaces and resolv files.

---

