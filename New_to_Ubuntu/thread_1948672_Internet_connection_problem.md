---
title: "Internet connection problem"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-28
I am using both WinXP & Ubuntu Lucid.
Since switching Internet/TV providers (from Telus to Shaw), my upstairs computer cannot access wired Internet.
Currently using Trendnet Powerline AV Adapter Kit 200mbps. 
My Windows can now access wired Internet, but Ubuntu cannot. Has anyone any idea how I can connect Ubuntu to this??? Currently trying to install NetworkManager-0.9.4.0 using ./configure, but it fails as current version of intltools is too old. Downloaded intltool_0.41.1.orig.tar.gz in Windows & copied to Ubuntu. Extracted files to intltool folder, but can't understand the README file instructions. I would sincerly appreciate some help here.

---

### Post by BBQdave on 2012-03-28
> **Bumpalot said:**
> Has anyone any idea how I can connect Ubuntu to this?

Ubuntu 10.04LTS:

System > Preferences > Network Connections

This will allow you to manually configure your network connection.

Though you should be able to auto-detect network connections (*network indicator* in top bar of desktop).

---

### Post by Bumpalot on 2012-03-28
I don't have Network Connectins!

---

### Post by BBQdave on 2012-03-28
> **Bumpalot said:**
> I don't have Network Connectins!

Right-click on *network indicator* icon (in top bar on desktop), and from the drop down menu, you can select Edit Connections (Network Connections).

---

### Post by CoDeHacKer on 2012-03-28
Can you open your router setup page ?   What type of router are you using?   Did you change anything with your router ?

---

### Post by Bumpalot on 2012-03-28
No Network Connections Showing.
Can't open the Router Setup page - router supplied by Shaw Cable - has no clue what Linux is!
Have sent Support Ticket to supplier of Trendnet Powerline AV Adapter Kit  re linux & am waiting for a reply re problem - this kit came with Windows install only, but one would think that Ubuntu would be able to detect it somehow - maybe I have to find a way to install intltool so I can install NetworkManager - than I may be able to see some action!

---

### Post by CoDeHacKer on 2012-03-28
I never install the software they send, you should be able to go into windows and find the ip to the device you are connected to, and type that ip into the browser, for me it'''''''s  192.168.2.1   every modem/router is different, and once you type it in, you will get a setup page for the equipment, you may have to unplug it from the internet before you can get the setup page, but perhaps you can find something in there.

The device will ask you for a user/pass, usually it's the user/pass that you use to connect to the internet, but sometimes it's different.

Is your windows wired too, or wireless ?

What sort of modem is it, like who is it made by and what is the model number?

I had to add my machine number from this linux box into my router before it would work, but that's just the way i have it set up.

---

### Post by Bumpalot on 2012-03-28
Thanks for your continued support!! 
The Modem is supplied by the Internet / TV supplier - Model SMC Networks
using WPA/WPA2-PSK .SSDI W220DD & password
The Powerline Utility is Trandnet 200mbs, MAC Address 00:14:D1:7B:10:87
Until I am able to install NetworkManager-0.9.4.0 (I 1st need to know how to install intltool_0.41.1.orig.tar.gz but can't understand the README file instructions. Do you know how to do this???

---

### Post by troymius on 2012-03-28
Synaptic won't install the Network Manager for you?

---

### Post by CoDeHacKer on 2012-03-28
Sorry I don't know how to install it.  You will have to unzip it first.  It sounds to me like you are trying to connect to a wireless connection with a wire, you don't need th ssid and user/pass to hook to it with 
a cable.  

Did you try this to see if you can see your ethernet card ?   This is supposed to be for your 
flavor of linux   [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

I hope you get it straight.

Here is a better one on how to configure your network.

[https://help.ubuntu.com/10.04/internet/C/index.html](https://help.ubuntu.com/10.04/internet/C/index.html)

---

### Post by Bumpalot on 2012-03-28
All I want to install now is NetworkManager-0.9.4.0 (I 1st need to know how to install intltool_0.41.1.orig.tar.gz but can't understand the README file instructions). The Powerline Utility is Trandnet 200mbs, that is Wired connection only. The link to [https://help.ubuntu.com/10.04/server...iguration.html]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") is for wired - that's why I need to install NetworkManager. I cannot use Synaptic because I have not internet connection! (I 1st need to know how to install intltool_0.41.1.orig.tar.gz but can't understand the README file instructions.
hanks again for your help!

---

### Post by troymius on 2012-03-28
> **Bumpalot said:**
> All I want to install now is NetworkManager-0.9.4.0 (I 1st need to know how to install intltool_0.41.1.orig.tar.gz but can't understand the README file instructions). The Powerline Utility is Trandnet 200mbs, that is Wired connection only. The link to [https://help.ubuntu.com/10.04/server...iguration.html]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") is for wired - that's why I need to install NetworkManager. I cannot use Synaptic because I have not internet connection! (I 1st need to know how to install intltool_0.41.1.orig.tar.gz but can't understand the README file instructions.
hanks again for your help!

You wrote that the "upstairs" computer does not connect to the internet anymore under Ubuntu. Can you carry it downstairs, install Network Manager and then carry it back upstairs? it may be the easiest solution unless your mother in law lives downstairs.

---

### Post by CoDeHacKer on 2012-03-28
sorry if I'm not helping much. 

I found this [https://help.ubuntu.com/10.04/](https://help.ubuntu.com/10.04/)

and in it there is a link to 

[https://help.ubuntu.com/10.04/add-applications/C/index.html](https://help.ubuntu.com/10.04/add-applications/C/index.html)


if it's a executable file, once you unzip it, and open it, it should execute, or ask you if you want to 
read it or run it.  

I'm sure somebody here can tell you the commands to do it in a terminal window.

I'm sorry I'm new too, just trying to help. ):P

---

### Post by Bumpalot on 2012-03-29
Thanks for your help CoDeHacker - can't do anything until I get NetworkManager installed. Will check other avenues. THIS THREAD IS NOW CLOSED.

---

