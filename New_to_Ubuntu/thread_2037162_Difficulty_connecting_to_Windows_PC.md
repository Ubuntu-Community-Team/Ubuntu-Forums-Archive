---
title: "Difficulty connecting to Windows PC"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by JohnTho on 2012-08-03
Hi,
I've posted this in the absolute beginners section rather than the Networking one because although I have worked with computers in one form or another since the mid 70's I am new to Linux and I'm struggling with some of the issues it's raised. I apologise in advance for this rather lengthy and rambling post.

I cut my teeth on command-line OS's, starting with DEC DOS and RT11, CP/M, the ubiquitous MS-DOS and VAX VMS and even dabbled briefly with Unix. It's many years now since I had to use these skills and with the advent of the GUI I've become lazy :). Unfortunately I didn't garner enough experience with Unix to help me get to grips with Linux.

Anyway, out of boredom with Microsoft I decided to put together a linux-based system so have got hold of a secondhand, but well specced, desktop machine and installed 12.04 LTS on it. I got it up and running without too many problems (I have some other threads running here regarding some of the issues) but I seem to have hit a wall when it comes to trying to get it to connect reliably to my main desktop PC which is running Windows 7 Professional 64-bit. I have established a network connection and successfully transferred several GB of files. I've also configured a network printer and printed a test page. In fact it wasn't until I tried to set this printer up, when Ubuntu reported that it needed Samba and installed it, that I was able to get the two macines to connect.

The trouble is the network connection isn't reliable. Sometimes the Windows machine can see the Linux one when the Linux one can't see the Windows one, sometimes it's the other way round. As long as one of them can see the other I find Ican transfer files but after I've been working on the Linux box for a while the connection inevitably disappears from both and then I have to cold boot the Linux box to get it back.

Because I'm a total newbie to Ubuntu I simple-mindedly tried running Samba from a command window to see what it would throw up. To my surprise it said Samba wasn't installed, though I thought it was when I set the printer up. Anyway I used APT-get to download and install it but I have no idea if it is configured properly because the man pages on Samba are like a foreign language to me :confused:. I know that connections to Windows can be problematic but I'd be grateful for any help.

---

### Post by EricG1793 on 2012-08-04
Forgive me if I'm hijacking, but maybe we can kill two birds with one stone here.

I'm networking a Laserjet 1100 (with serial connector) off a Ubuntu 12.04 to a Windows XP computer. Printer installed fine on the Ubuntu computer and works reliably. I went to enable sharing on a folder which prompted the installation of Samba, I changed the Samba configuration file to connect to my "home" workgroup, changed the "enable browsing" (or similar) and guest access option under the [printers] section of the configuration file to "yes", restarted Samba, and connected the PC to "home". The PC recognized the printer on the network, it prompted me to tell it which model the printer was from a list, installed the driver, but it said that it couldn't connect to the print server because either there was an error connecting to the Ubuntu computer or the printer wasn't connected to the Ubuntu computer, which I knew it was. After a while, however, the PC stopped even recognizing that the Ubuntu computer had a printer installed. So I restarted Samba via Terminal on the Ubuntu and the PC again saw the printer but could not connect to it.

Thanks for any ideas! :)

---

### Post by HermanAB on 2012-08-04
Howdy,

Maybe read this:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by JohnTho on 2012-08-04
Hi, thanks for the reply. I've looked through that howto but I have to confess it uses so many terms and concepts I'm completely unfamiliar with that it might as well be written in greek.

Groups I know nothing about. Samba shares I know nothing about. However, from what I have gleaned I can say with some confidence that the account usernames, passwords and workgroup names are the same on both the Linux and Windows machines. I also think that a samba server must be running on both since I have managed to transfer files both ways using each of the machines as the source. I've also successfully printed test pages from the Linux box to the printer connected to the Windows machine. My problems are:-

Only one of them can 'see' the other in its network list at any one time. I haven't been able to figure out what it is that affects this. As far as I can tell it doesn't seem to depend on the order they're booted. Any thoughts on this would be welcome.

After literally a minute or two working on the Linux box the connection is lost and neither machine can then see the other until I cold boot the Linux box. However even though the connection is apparently lost the network printer still works. Any thoughts on this would also be welcome.

One thing I forgot to mention in my initial post is that both machines are connected to the router wirelessly. I don't know if that's likely to have any bearing on these issues.

It would be nice if the Samba wizard in MCC referred to in the howto could be run in Ubuntu but it appears that as MCC is designed for Mandriva Linux it can only be ported over by recompiling the source code.  There is no Samba configuration tool in the Ubuntu System Settings.

I'm stumped so any pearls of wisdom will be hungrily devoured. :confused:

---

### Post by Ubun2to on 2012-08-04
Well, you just gave me an inspiration. You are using WiFi. Well, unless you have static IPs, your computer won't always have the same address.
So, to setup static IPs, go to the Network menu, and select Connection Information.
Now, open up the Edit Connections window from the Network menu.
Go to the Wireless tab. Select your network and click Edit.
Go to the IPv4 tab.
Next to the Method list, select Manual.
Now, enter the information from the Connection Information window into here. Select Add on the Edit Connections window. You will be copying information from the Connection Information in to the Edit Connections window.
For Address, put what is listed next to IP Address.
For Netmask, put what is listed next to Subnet Mask.
For Gateway, put what is listed next to Default Route.
For DNS Servers, put what is listed next to Primary DNS.
Static IPs are more stable, as your computer can't change the its address every few minutes.
On Windows 7, go to the Network and Sharing Center. On the left, you will see a link that says "Change adapter settings." Click on it.
Right click on your WiFi connection icon, and go to Properties.
Go to Internet Protocol Version 4 (IPv4), and select Properties.
Now, select Use the following IP address.
Open Command Prompt, and type this in:
```
ipconfig /all
```
The IP address, subnet mask, and default gateway are listed. Enter those into the IPv4 Properties window.
For the DNS server, type in what is listed in Command Prompt. You might have to hunt for this, depending on how many connections your computer has. But, it is in there if you put /all in the command. Once you find it, enter it into the Preferred DNS server box.
For the Secondary DNS server box, you can put in 8.8.8.8 or 8.8.8.4-those are the Google DNS servers. Or, you can contact your ISP and ask them for the DNS servers that they own.

---

### Post by NikTh on 2012-08-06
Hi , 
first of all I must say that Agreed with @Ubun2to's idea about static IP address. 

On errors and difficulties , it will be useful if you had a look in logs.  
Usually logs record useful information about the error .
Take a look in /var/log/samba/ for any useful recorded log. 

Thanks

---

### Post by audiomick on 2012-08-06
> **Ubun2to said:**
> 
Static IPs are more stable, as your computer can't change the its address every few minutes.

This doesn't happen, unless the perhaps the DCHP server is set to issue really short leases. Generally, the computer will retain the same IP until it is disconnected. There is, however, no gaurantee that the computer will get the same IP the next time. I am also a big fan of issuing static IP addresses. The only time I don't is when the computer is definitely only heading for the internet, and not doing anything on the local network.

---

### Post by madjr on 2012-08-06
you can also try nitroshare:


[http://www.ubuntubuzz.com/2012/06/nitroshare-share-file-over-local-area.html](http://www.ubuntubuzz.com/2012/06/nitroshare-share-file-over-local-area.html)

[http://www.webupd8.org/2012/07/nitroshare-send-files-computers-lan-network.html](http://www.webupd8.org/2012/07/nitroshare-send-files-computers-lan-network.html)


this might be useful too:
[http://www.ubuntubuzz.com/2011/11/use-pidgin-for-chatting-and.html](http://www.ubuntubuzz.com/2011/11/use-pidgin-for-chatting-and.html)

---

### Post by JohnTho on 2012-08-06
Many thanks to everyone for your suggestions. I haven't got any further with this yet. To be honest the fact that it didn't work "out of the box", as so much of Ubuntu does, has discouraged me somewhat.

I was used to setting up static IPs on the machines at my workplace. There, all the machines on the internal LAN used them. I was/am also aware that in the outside world the servers routinely use DHCP. Until I tried to network the Ubuntu system this has never caused any problems so presumably the Windows systems have some way of handling the changing IP addresses (as does the Mac running OS10.4.11 which is hard-wired to my router). My IP's don't seem to change very often (not for several weeks usually) so it seems unlikely that this would explain why the Ubuntu connection gets lost so quickly. Interestingly the Ubuntu machine can always 'see' the Mac when it's active (not asleep) but the Mac can't see Ubuntu. That seems surprising since MacOS is Unix-based.

I'm not sure where I'm going to go with this. I don't know if I want the hassle of setting everything up with static addresses. Quite apart from any other considerations I'll probably have to pay my ISP extra for the feature and since I've built the Ubuntu system purely as an experiment this wouldn't currently be justified. I haven't found the Unity GUI quite as user-friendly as the Mac and the Windows PC but that may be due to unfamiliarity. I probably need a bit longer to play with it. It's also a bit hamstrung by the fact that I'm having to use a 15" 16:9 flat-screen TV as a monitor whereas the Windows system has an 18" 4:3 monitor. It would be nice if the GUI-based System Settings page had a few more features to save having to 'get into the works' via a terminal window. Not that I don't like doing that, it's quite enjoyable and nostalgic. :P It's just the learning curve involved that's a bit off-putting. Maybe in the boring long winter evenings I'll feel more motivated to get to grips with it.

---

### Post by madjr on 2012-08-06
> **JohnTho said:**
> I haven't found the Unity GUI quite as user-friendly as the Mac and the Windows PC but that may be due to unfamiliarity. I probably need a bit longer to play with it. 

these should help get more familiar:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)

[http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04](http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04)


Also, were you able to try nitroshare?

---

### Post by JohnTho on 2012-08-06
> **madjr said:**
>  were you able to try nitroshare?
Not yet. As I explained I'm still considering what is the best approach. I'd prefer a normal network connection if that can be reliably established. At present I can at least transfer files, albeit it may need a prior cold boot of Ubuntu, so I don't need to rush to any particular solution.

Thank you for those links. All such information is very welcome. Due to commitments it will be a day or two before I have a proper opportunity to peruse them.

---

### Post by Ubun2to on 2012-08-08
> **audiomick said:**
> This doesn't happen, unless the perhaps the DCHP server is set to issue really short leases. Generally, the computer will retain the same IP until it is disconnected. There is, however, no gaurantee that the computer will get the same IP the next time. I am also a big fan of issuing static IP addresses. The only time I don't is when the computer is definitely only heading for the internet, and not doing anything on the local network.

Depending on what hardware you have, static IPs can make or break a network. I had to set static IPs on my devices because I don't have the time to find the new IPs for each of my devices and change the settings every time I turn them on.

---

