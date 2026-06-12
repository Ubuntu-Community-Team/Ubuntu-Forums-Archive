---
title: "Dial-up not treated as a network connection"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by ub07 on 2012-07-11
I am running K/Ubuntu 12.04, and with the help of the good people here, I've almost ironed out all of my problems. However, there is one problem that is inhibiting me from using all features.

I connect to the internet through a dial-up connection. I managed to get both Gnome PPP and wvdial working (after considerable effort). Now my problem is that even though I can use the internet, the system does not view the dial-up connection as a network connection. Hence, programs like Evolution and Empathy think that I am offline when in reality I am online with a dial-up connection.

Is there anyway that I can make the system view the dial-up connection as a network connection?

---

### Post by ub07 on 2012-07-13
Any ideas? Anyone?

---

### Post by jtarin on 2012-07-13
When connected....what does the result of the command ```
ifconfig 
```give you?

[Check this link]("https://answers.launchpad.net/ubuntu/+source/evolution/+question/130802")

---

### Post by ub07 on 2012-07-13
Here are the results of ifconfig:


$ ifconfig

eth0      Link encap:Ethernet  HWaddr e8:11:32:c3:59:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1852 (1.8 KB)  TX bytes:1852 (1.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:4.252.99.64  P-t-P:209.247.21.179  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1180413 (1.1 MB)  TX bytes:234027 (234.0 KB)

wlan0     Link encap:Ethernet  HWaddr 4c:ed:de:eb:84:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by jtarin on 2012-07-13
You may have started Evolution with the "--offline" command-line option.

If this isn't the case and Evolution normally works but has suddenly stopped connecting, you may have unintentionally clicked on the connection icon in the lower left corner. When connected, the icon resembles a pair of sockets joined together. If the sockets are open, there is no connection (and the Send/Receive button is grayed out). Click on the icon to change its state.

If the problem persists and you are sure you haven't clicked the icon, but you can still reach the network from other apps on your system (browsers, FTP, Ssh, ping etc.) it may be that NetworkManager (NM) is not properly configured. Many Linux distributions now use NM to manage their connections, and if it's installed Evolution will use it to detect if the network is up. However NM can be installed but not properly configured, leaving the network working but not detectable by Evolution. (Note that some other GNOME-based apps, e.g. Firefox, may also fail for the same reason.) The solution is to configure NM to manage your network interface. 
Look to the link below for help in configuring NM.
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by ub07 on 2012-07-13
Thanks jtarin, but the problem is not just Evolution. I can use Thunderbird if need be (it works).

The problem is that Ubuntu itself doesn't think that I am connected to the internet. For example, I cannot install software from the software center because it "thinks" that I am not online. And the update manager "thinks" that I am not online.


I'm thinking that there must be a switch that I can set somewhere (maybe from the command line) or create some kind of link so that the system will associate my dial-up connection with a network connection.

---

### Post by Ubun2to on 2012-07-13
Are you using an actual dial-up modem or are you plugging your phone line into your computer? If you plug it right into your computer, you might need dial-up modem drivers.
Also, how are you on these forums right now?

---

### Post by ub07 on 2012-07-13
> **Ubun2to said:**
> Are you using an actual dial-up modem or are you plugging your phone line into your computer? If you plug it right into your computer, you might need dial-up modem drivers.
Also, how are you on these forums right now?

I'm on these forums now through my dial-up USB modem and Chromium browser. Gnome PPP recognizes my modem, and I am able to surf the web just fine. It's just that Ubuntu doesn't view my PPP session as a network connection. Hence, software that requires a network connection doesn't work. Only browsers work.

It's very frustrating.

---

### Post by kigconker on 2012-07-13
Most mobos don't come with modems anymore. DialUp is a fossil, There is not much in the way of support for it anymore.

---

### Post by ub07 on 2012-07-13
> **kigconker said:**
> Most mobos don't come with modems anymore. DialUp is a fossil, There is not much in the way of support for it anymore.

It may very well be a fossil, but it is all that is available in my area except maybe satellite.

---

### Post by jtarin on 2012-07-13
Insure you have Network Manager properly configured. All you applications(mostly) rely on NM to provide them with the information as to the connection. Check the link I gave you for proper setup of NM.

---

### Post by ub07 on 2012-07-14
> **jtarin said:**
> Insure you have Network Manager properly configured. All you applications(mostly) rely on NM to provide them with the information as to the connection. Check the link I gave you for proper setup of NM.

My network manager looks nothing like the network manager in that link. I'm using Ubuntu 12.04. There is no modem option in my network manager - just wired and wireless. And the wired just refers to my network adaptor (which I have no use for at present).

Gnome PPP and wvdial are properly configured.

---

### Post by jtarin on 2012-07-14
To get Empathy working without NM....try here[https://live.gnome.org/Empathy/FAQ#How_to_connect_when_not_using_NetworkManager.3F]("https://live.gnome.org/Empathy/FAQ#How_to_connect_when_not_using_NetworkManager.3F")
All else fails go with another mail client and another chat client like Kopete. I know its KDE but its an alternate to what you have.

---

### Post by ub07 on 2012-07-14
Thanks, jtarin. I appreciate the link and the help. I think that the core problem is that I cannot install software or do updates normally without going through the network manager.

---

### Post by jtarin on 2012-07-14
> **ub07 said:**
> Thanks, jtarin. I appreciate the link and the help. I think that the core problem is that I cannot install software or do updates normally without going through the network manager.No I think the core problem here is the non-support for dial-up by network manager. In their rush to advancement they leave some behind without warning...or care.
Hope you find a workaround. There's nothing wrong with dial-up when its all you have. I kinda miss my Zoom modem.:P

---

### Post by ub07 on 2012-07-15
I took a radical step in trying to resolve this problem, and I think that it has paid off. I have removed the network manager. Now I can install software through the Software Center! It gives me an error message, but it doesn't crash and, as I said, I can now install software. Also Evolution works. I haven't tried Empathy yet.

I'm happy to have it working, but lord help me if I ever have to set up Wi-Fi.

---

### Post by ub07 on 2012-07-15
Update: Empathy works!

---

### Post by Ubun2to on 2012-07-15
> **ub07 said:**
> It may very well be a fossil, but it is all that is available in my area except maybe satellite.

That must really stink-I've heard satellite is terrible as well in terms of reliability (and speed-about equivalent to dial up).
You should consider getting a dial up modem from your ISP. It's hard for them to clear out their stock completely, especially since they could get a bad rep from customers who claim they are discriminating. Plus, dial up modems come with Ethernet out, so it would trick your network manager into thinking you have a high speed connection (sorta).

---

### Post by jtarin on 2012-07-15
> **ub07 said:**
> I took a radical step in trying to resolve this problem, and I think that it has paid off. I have removed the network manager. 
I'm happy to have it working, but lord help me if I ever have to set up Wi-Fi.
Not too radical....I removed mine long ago, but I was reluctant to advise that here. Wicd is another manager some people find more than adequate foe wireless.

---

### Post by ub07 on 2012-07-15
jtarin, how do you deal with the boot delay while the system is waiting for the network configuration?

---

### Post by jtarin on 2012-07-15
I'm sending you two links on how to possibly resolve your issue.
[http://ubuntuforums.org/showthread.php?t=1844819](http://ubuntuforums.org/showthread.php?t=1844819)
[http://ubuntuforums.org/showpost.php?p=11242427&postcount=37](http://ubuntuforums.org/showpost.php?p=11242427&postcount=37)

---

### Post by ub07 on 2012-07-15
Thanks for the links. I really appreciate it. The workaround that I am using now is to comment out all the delays in the /etc/init/failsafe.conf. I'm not altogether satisfied with this work around because I think the problem could be resolved at a less superficial level, namely not loading network services until after boot.

Also, my /etc/network/interfaces file is not the source of the problem because I commented out all the "auto" items.

---

### Post by sebsalva on 2013-01-18
Hi, i have used this workaround on Ubuntu 12.04.1:

first i looked for the launcher of the application "evolution.desktop" 
# su -
#find / -name evolution.desktop
/home/<user>/.local/share/applications/evolution.desktop
/usr/share/applications/evolution.desktop
#

not been sure which one rules on which situation i edited both, changing the row of the command from "Exec=evolution %U" to "Exec=evolution --force-online %U"

After that, when i'm connected with Gnome-PPP or sakis3g, clicking on the launcher of evolution, it works, forcing the application to go online.

---

