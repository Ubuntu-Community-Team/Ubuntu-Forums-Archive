---
title: "Ubuntu and uTorrent"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-04-30
Hey guys,

Ok, I just installed Linux a couple nights ago on my computer. Specifically Ubuntu 8.04. I've been using Windows XP for the past few years. But I tried Linux and I loved it. So right now I have both Ubuntu and XP on my computer.

So, I installed Wine, and then uTorrent 1.7.7. And everything went fine. But...I'm having a problem with opening a port on Ubuntu. For the past two years or so I've been using uTorrent on Windows, and I was able to forward a port with no problem. uTorrent always had the green icon on the bottom of the client, and when I did the port test uTorrent always told me I was connectable.

But I can't achieve this on Ubuntu, and it's driving me crazy. I opened a separate port on my router(the same method that I always used in Windows) for Ubuntu. Then I added that port number in uTorrent. But I'm still unconnectable.

So does anyone know if there' sanything special I need to do since I'm using Ubuntu? I don't know if Ubuntu has a firewall or not. So maybe I'm behind a firewall, but I don't know how to find out.

Also, I opened the same port on Ubuntu as I have open on Windows. So is having the same port open on both OS's the problem? Should I open a different port on Ubuntu, then I have open on Windows?

Any info or help you can give me will be greatly appreciated. I've been messing with this for the past couple nights now.

Thank you.

EDIT: Ok, I tried using a different port for Ubuntu than the one I'm using on Windows, and that didn't work either. uTorrent is still showing me as unconnectable.

EDIT AGAIN: By the way, I installed Ubuntu through Wubi. Would that make a difference at all? Maybe a traditional dual boot would get me connectable?

Also, is there anything special I'm suppose to do with Wine? All I did was install it. That was it. Is there any settings I should set it to?

---

### Post by hyper_ch on 2008-04-30
why don't you use a native linux torrent client?

Transmission, Deluge, KTorrent, Azureus, ....

or even a cli one:   rtorrent

---

### Post by h8uthemost on 2008-04-30
I've tried those. I can't get a port to open for any of those too. So there's definitely something wrong, but I don't know what. I've been messing with this for a couple days now.

I got into my routers page, open port, input that port into a torrent client. But the port is still shown as closed.

Any other ideas? I just can't see why the port will open in Windows, but not Ubuntu.

---

### Post by Ek0nomik on 2008-04-30
> **h8uthemost said:**
> I've tried those. I can't get a port to open for any of those too. So there's definitely something wrong, but I don't know what. I've been messing with this for a couple days now.

I got into my routers page, open port, input that port into a torrent client. But the port is still shown as closed.

Any other ideas? I just can't see why the port will open in Windows, but not Ubuntu.

Test the port to see if it's actually open or not.

Ubuntu will have all your ports closed by default, but once a program starts running and signals that it needs a port to function, it will open.

---

### Post by hyper_ch on 2008-04-30
Do you have firestarter installed on your linux machine?

---

### Post by vishzilla on 2008-04-30
I recommend you to use native torrent clients like Deluge, Transmission, Azureus, rtorrent, BitTornado or Ktorrent. Hardy comes installed with Uncomplicated Firewall (ufw) a command line firewall tool. Its very easy to set it up. Go to System>Help and Support and search for 'ufw manual'

---

### Post by h8uthemost on 2008-04-30
Ek0nomik, yeah, the uTorrent port checker(the tab that says Test if Port is Forwarded Properly) is showing it as closed.

hyper_ch, I don't think so. How could I tell? Actually, someone on the Transmissions forums said something about firestarter too. But I thought Ubuntu didn't have a firewall. So maybe I have to add the bittorrent clients to the acception list? Should I install firestarter?

vishzilla, I'll try it out. I'm very bad with the command prompt though. But I'll try it.

Thank you so much for the help guys! You have no idea how much I'm appreciating this.

EDIT: Ok, I went into the Synaptic Package Manager, and it looks like Firestarter is not installed. Should I install it?

---

### Post by thisiam on 2008-04-30
I use [this]("http://www.utorrent.com/testport.php?port=29537") to check if the port is open. you can change the port number at the end of the link to whatever you may have it set to.

---

### Post by fraser_m on 2008-04-30
Try using 'sudo wine {whatever}'.
If this works, you know it has nothing to do with your connection, as some ports (under 1024, I think) are reserved for root. I might be completely wrong though... :D

---

### Post by h8uthemost on 2008-04-30
Thank you thisiam. But that is what I've been using to test if the port is open. It's accessed by clicking on the little graphical button on uTorrents status bar. It always tells me that the port is closed.

---

### Post by vishzilla on 2008-04-30
Some of the commands for ufw as far I remember
```
sudo ufw enable [COLOR="DarkOrange"](to start and enable ufw)[/COLOR]
sudo ufw allow port# [COLOR="DarkOrange"](to set a new rule to open port#)[/COLOR]
sudo ufw delete allow port# [COLOR="DarkOrange"](to delete the above rule)[/COLOR]
sudo ufw disable [COLOR="DarkOrange"](to turn off firewall and disable)[/COLOR]
sudo ufw status [COLOR="DarkOrange"](to check status of ufw)
```[/COLOR]

---

### Post by h8uthemost on 2008-04-30
Yeah, I found some of the commands in that Help you suggest. And I allowed my port(58788 .), but it still doesn't appear to be open.

---

### Post by kpkeerthi on 2008-04-30
> **h8uthemost said:**
> Yeah, I found some of the commands in that Help you suggest. And I allowed my port(58788 .), but it still doesn't appear to be open.

Since you are behind a hardware firewall (your router), you may probably don't need a software firewall (ufw/iptables) which is redundant. 

You can uninstall ufw/iptables with
```
sudo apt-get remove ufw iptables
```

Reboot ubuntu (and your router, to be sure) and try for open ports again.

* NOTE: If you ever need to go 'mobile' (like in a cafe) with your system you may still need software firewall as you may be exposed to threads directly.

---

### Post by h8uthemost on 2008-04-30
Thank you kpkeerthi. I definitely will try that. Is there anything i need to do after I install ufw itables? Like enable anything, or something like that? Or I'll be good to go right after I install it?

Thank you.

---

### Post by mivo on 2008-04-30
> **h8uthemost said:**
> But I thought Ubuntu didn't have a firewall. So maybe I have to add the bittorrent clients to the acception list? Should I install firestarter?

Ubuntu does have a firewall (iptables), but it comes without rules, so it's technically the same as not having one. ;) Firestarter will let you configure iptables, so installing it won't do any harm. But I don't believe that this is the problem, unless you set up the firewall before. Have you tried Deluge with the random ports setting?

---

### Post by kpkeerthi on 2008-04-30
Make sure your router is forwarding the right port to the right IP address. If your ubuntu is configured to use DHCP (by default it uses DHCP), the IP ubuntu is using may not be the same your router is trying to forward.

---

### Post by billgoldberg on 2008-04-30
Very strange. 

I use transmission and hardy without a firewall.

Transmission tells me the port is open.

So it should be the same in your case.

---

### Post by vishzilla on 2008-04-30
Did you try with any of the native clients like Transmission or Deluge?

---

### Post by h8uthemost on 2008-05-01
Yep, I tried with both of those. I tried opening a port with ufw, and that still didn't work.

So, I'm going to try installing firestarter, and opening access to the port with that. Hopefully that will work.

Do you guys think that it's because I installed Ubuntu through Wubi, and that's what's giving me the problem?

EDIT: Also, would I have the same IP address on Ubuntu as I do in Windows?

---

### Post by daimaru on 2008-05-01
> **h8uthemost said:**
> Yep, I tried with both of those. I tried opening a port with ufw, and that still didn't work.

So, I'm going to try installing firestarter, and opening access to the port with that. Hopefully that will work.

Do you guys think that it's because I installed Ubuntu through Wubi, and that's what's giving me the problem?

EDIT: Also, would I have the same IP address on Ubuntu as I do in Windows?
to check your ip type in terminal:

```
ifconfig
```
that should tell you your ip address. And as the guy way at the beginning said just install firestarter click the "policy" tab and then right click in the top field -> choose open port enter port number select "open for all" and click apply .

I use utorrent (which i love by the way, since deluge just keeps crashing on my machine) and it works perfectly fine.

---

### Post by blithen on 2008-05-01
> **fraser_m said:**
> Try using 'sudo wine {whatever}'.
If this works, you know it has nothing to do with your connection, as some ports (under 1024, I think) are reserved for root. I might be completely wrong though... :D
You should never do this, there is never a reason to do this. The wine devs say don't do it. So don't.

---

### Post by h8uthemost on 2008-05-01
> **daimaru said:**
> to check your ip type in terminal:

```
ifconfig
```
that should tell you your ip address. And as the guy way at the beginning said just install firestarter click the "policy" tab and then right click in the top field -> choose open port enter port number select "open for all" and click apply .

I use utorrent (which i love by the way, since deluge just keeps crashing on my machine) and it works perfectly fine.

I did exactly all this. And yeah, my IP address is different in Linux than Windows. So I opened the port for that address in my routers config page. I installed Firestarter, then added that port number. And still nothing. I tried it in both uTorrent and Transmission. And I am not connectable.

All you guys that are connectable, how did you install Ubuntu. I'm trying to figure out if that has something to do with it. Because now, I am completely out of ideas. Looks like I'm going to have to go back to Windows.

EDIT: And clicking on the top field of firestarter lets you set the host connection. The bottom part is for the ports.

---

### Post by daimaru on 2008-05-01
> **h8uthemost said:**
> EDIT: And clicking on the top field of firestarter lets you set the host connection. The bottom part is for the ports.
sorry was in windows had no way to check which was the right one. I am going to restart (just for you right now) so i can check what goes on with my utorrent in ubuntu hardy heron, including settings. By the way did you (after opening ports) try to start a torrent ? I'm not sure (but i guess i check in a minute, since i'll restart to ubuntu) but I think my utorrent does not show any green light either, but it runs at my maximum speed of 1.6mb per second so it definately does not have any connection problems.

---

### Post by daimaru on 2008-05-01
ok just to check i have wine version 0.9.60 running utorrent 1.7.7 (built 8179) on ubuntu hardy heron (i386). 

i have my tcp and udp port open in my router ( > 50000 ) ; pick a number >10000. 

utorrent gives me the green checkmark (network OK) ...
firestarter has in the "bottom field" --> yes you were right; the same port open as does my dsl modem/router. 

Testing if the port is forwarded --> [FONT=verdana,arial]**OK!** Port 50012 is open and accepting connections.

Quite frankly everything should work for you too.
Try downloading this torrent [http://www.gameupdates.org/details.php?id=2194](http://www.gameupdates.org/details.php?id=2194) it runs at a nice 1.4mb/sec guess its not the fastest torrent out there but hey it should give you an estimate of if your 
connection is working ..
ps: under utorrent preferences -> connection i got port 50012 as the one thats accepting incoming connections, but i guess that you had already configured accordingly.
[/FONT]

---

### Post by h8uthemost on 2008-05-03
Thank you for your help daimuru. But still no go. I guess I'm going to uninstall Ubuntu, and do a traditional dual boot. Maybe it's because I installed Ubuntu with Wubi is why it won't become connectable. Who knows.

I am still getting faster speeds in uTorrent with Linux then I did in Windows. So that's definitely a plus. I just hate knowing that I'm not connecting to everyone.

Thanks.

---

