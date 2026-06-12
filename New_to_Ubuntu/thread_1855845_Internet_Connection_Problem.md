---
title: "Internet Connection Problem"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Itzmir_Heman on 2011-10-07
Hey all,

I have recently stumbled across this issue with my update manager and Ubuntu Software Center. It seems that something is wrong with my internet connection. I am unable to update and download my Ubuntu (NN). I did check upon the possible solutions online but it didn't seem to work. I have changed the mirror and it didn't make any difference at all. Here are the results from Terminal.


itzmir@Itzmir:~$ sudo apt-get update
[sudo] password for itzmir: 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                         
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/lucid/InRelease](http://archive.canonical.com/dists/lucid/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/natty/InRelease](http://archive.canonical.com/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

Hope that someone could help me up! I am not really well versed in this topic so please pardon me! :-)

Cheers,
Itzmir Heman

---

### Post by amjjawad on 2011-10-07
Hello there,

What type of Internet Connection do you have?

---

### Post by Itzmir_Heman on 2011-10-07
I am using broadband. I am not sure about your question and I hope that was a correct answer.

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> I am not sure what do you mean but **I am using wifi to connect my laptop to the internet**.

That's what I meant :)
Is it possible to connect to the interent via LAN/Wired Connection?

What is the output of:

```
sudo lshw -C network

```

Please wrap up the output text with "CODE" tags or "#".
[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by Itzmir_Heman on 2011-10-07
> Is it possible to connect to the interent via LAN/Wired Connection?
The answer is YES! :-) And thank you for being so awesomely helpful!

```
itzmir@Itzmir:~$ sudo lshw -C network
[sudo] password for itzmir: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:24:a4:62:2e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f4300000-f4303fff ioport:2000(size=256) memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:0d:77:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f4200000-f420ffff

```

Oh I edited the previous reply because I was really unsure of the answer. But hey there is your code! :-)

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> The answer is YES! :-) And thank you for being so awesomely helpful!

That's good, try to connect via LAN/Wired Connection and see if that makes any difference.

You welcome but I haven't done much :)

> ```
itzmir@Itzmir:~$ sudo lshw -C network
[sudo] password for itzmir: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:24:a4:62:2e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **[COLOR=Red]driver=sky2 [/COLOR]**driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f4300000-f4303fff ioport:2000(size=256) memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:0d:77:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[COLOR=Red]driver=ath5k [/COLOR]**driverversion=2.6.38-11-generic firmware=N/A **[COLOR=Red]ip=192.168.0.101[/COLOR]** latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f4200000-f420ffff

```I don't see any problem with your output. Your LAN is not connected as per above and your Wireless Connection is working.

As explained above, try to connect via LAN and if that didn't change anything, please do this:

1- Restart your Modem or Broadband Device.
2- Restart your machine
3- From Terminal run:

```
sudo apt-get clean
``````
sudo apt-get update
```4- Post the output and don't forget the "CODE" tags ;)
5- You can also change the server in Synaptic:

Synaptic > Settings > Repositories > Ubuntu Software Tab > Download From > Other > Select Best Server > Choose Server when it will find the best server.

---

### Post by Itzmir_Heman on 2011-10-07
> As explained above, try to connect via LAN and if that didn't change anything, please do this:

1- Restart your Modem or Broadband Device.
2- Restart your machine
3- From Terminal run

I have done all of the things above and unfortunately the results are still the same.

```
itzmir@Itzmir:~$ sudo apt-get clean
[sudo] password for itzmir: 
itzmir@Itzmir:~$ sudo apt-get update
Err http://ubuntu.mmu.edu.my natty InRelease                                   
  
Err http://ubuntu.mmu.edu.my natty-updates InRelease                           
  
Err http://ubuntu.mmu.edu.my natty-security InRelease                          
  
Err http://archive.canonical.com natty InRelease                               
  
Err http://archive.canonical.com lucid InRelease                               
  
Err http://archive.canonical.com natty InRelease                               
  
Err http://ubuntu.mmu.edu.my natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err http://ubuntu.mmu.edu.my natty-updates Release.gpg                         
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                             
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com lucid Release.gpg                             
  Unable to connect to 219.93.178.162:3128:
Err http://ubuntu.mmu.edu.my natty-security Release.gpg                        
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                             
  Unable to connect to 219.93.178.162:3128:
Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://dl.google.com stable InRelease                                      
  
Err http://extras.ubuntu.com natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err http://dl.google.com stable Release.gpg
  Unable to connect to 219.93.178.162:3128:
Reading package lists... Done
W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/lucid/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/natty/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-security/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/lucid/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

> 5- You can also change the server in Synaptic:

Synaptic > Settings > Repositories > Ubuntu Software Tab > Download From > Other > Select Best Server > Choose Server when it will find the best server.

I did go and check on Google on how to fix this problem and most of the threads I have found asked me to do the same. I have done that and changed it to the best server and unfortunately it doesn't make any difference. I am still unable to download and get updates.

Instead of having an "Install" button on the highlighted software, the "Use this Source" button appeared instead. I would so post a screenshot right now but I do not know how! :-p

This is what I get from Terminal after changing my server.

```
itzmir@Itzmir:~$ sudo apt-get update
[sudo] password for itzmir: 
Err http://dl.google.com stable InRelease                                      
  
Err http://ubuntu.mmu.edu.my natty InRelease                                   
  
Err http://ubuntu.mmu.edu.my natty-updates InRelease                           
  
Err http://ubuntu.mmu.edu.my natty-security InRelease                          
  
Err http://dl.google.com stable Release.gpg                                    
  Unable to connect to 219.93.178.162:3128:
Err http://ubuntu.mmu.edu.my natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err http://ubuntu.mmu.edu.my natty-updates Release.gpg                         
  Unable to connect to 219.93.178.162:3128:
Err http://ubuntu.mmu.edu.my natty-security Release.gpg                        
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty InRelease                               
  
Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://archive.canonical.com lucid InRelease                               
  
Err http://archive.canonical.com natty InRelease
  
Err http://archive.canonical.com natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com lucid Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err http://extras.ubuntu.com natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg
  Unable to connect to 219.93.178.162:3128:
Reading package lists... Done
W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/lucid/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/natty/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://ubuntu.mmu.edu.my/ubuntu/dists/natty-security/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/lucid/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> I did go and check on Google on how to fix this problem and most of the threads I have found asked me to do the same. I have done that and changed it to the best server and unfortunately it doesn't make any difference. I am still unable to download and get updates.

Go to Synaptic and choose the Main Server then Reload.
Does it make any difference?
Check the attached screenshot, please.

Sometimes it happens and it's advisable to wait for sometime and then try again but not sure if that applies to your case or not?!


> Instead of having an "Install" button on the highlighted software, the "Use this Source" button appeared instead. I would so post a screenshot right now but I do not know how! :-p

Software Center you mean? I never use it anyway :)

Screen shot is easy. If you are using Ubuntu, press "Print Screen" button on your Keyboard and a pop up window will show up on your desktop asking you to save this file or not? choose save and before choose where you want to save it :)

Then:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8046[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8047[/IMG]

---

### Post by Itzmir_Heman on 2011-10-07
> Go to Synaptic and choose the Main Server then Reload.
Does it make any difference?
Sometimes it happens and it's advisable to wait for sometime and then try again but not sure if that applies to your case or not?!

As Chuck Testa would say, Nope! No difference. Do check the screenshot below! I did wait for about a week plus now. I thought that it was a bug since I just installed Natty Narwhal!

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> As Chuck Testa would say, Nope! No difference. Do check the screenshot below! I did wait for about a week plus now. I thought that it was a bug since I just installed Natty Narwhal!

I have Lubuntu Natty and Ubuntu Natty and I have no problem at all since I installed both. 

Is there any proxy or something that you are using?

What do you have in this screen (attached):

---

### Post by amjjawad on 2011-10-07
Could you please post your Source List?

```
**[COLOR=Red]gedit[/COLOR]** /etc/apt/sources.list
```

gedit is the default text editor in Ubuntu. I'm using Lubuntu now and my default is leafpad.
If you have another text editor then:

```
cat /etc/apt/sources.list
```
The output will be in Terminal itself.

Post here and wrap up the text with "CODE" tags please :)

---

### Post by Itzmir_Heman on 2011-10-07
> Post here and wrap up the text with "CODE" tags please 

I think I am not catching your drift here mate. I did what you have asked me to do with the hash for code. Am I missing something here?! :-)

> Could you please post your Source List?

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/ natty partner
deb-src http://archive.canonical.com/ natty partner
```

I hope that this is what you were looking for.

---

### Post by amjjawad on 2011-10-07
[http://ubuntuforums.org/showpost.php?p=11318220&postcount=10](http://ubuntuforums.org/showpost.php?p=11318220&postcount=10)

You forgot to reply that post ;)

Thanks, yes, that what I was looking for. I'll have a look and get back to you :)

---

### Post by Itzmir_Heman on 2011-10-07
Ooops.. Sorry about that! :-)

> Is there any proxy or something that you are using?

What do you have in this screen (attached):

I am not sure about that proxy thing. But I reckon that I didn't touch any of those since I know nothing about proxy.

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Ooops.. Sorry about that! :-)



I am not sure about that proxy thing. But I reckon that I didn't touch any of those since I know nothing about proxy.

Ok, thanks :)
Have you upgraded 9.10 to 10.04 then 11.04? or this is a new fresh installation of 11.04? because I see some lines from older versions.

I'll send you the source list after I update it, just give me few mins ;)

---

### Post by amjjawad on 2011-10-07
Before I send you the updated source list, I think we can fix it this way:

Check my screenshot and please untick/uncheck the unnecessary options from the second tab (Other Software):

Please highlight, for example: Canonical Partner and Click Edit. Make sure it says "natty" in distribution field.

After you uncheck the other unneeded entries, Reload and I guess your problem will be fixed :)

---

### Post by Itzmir_Heman on 2011-10-07
> Have you upgraded 9.10 to 10.04 then 11.04? or this is a new fresh installation of 11.04?

Yes indeed! I was using Ubuntu Karmic Koala before!

---

### Post by Itzmir_Heman on 2011-10-07
> **amjjawad said:**
> Before I send you the updated source list, I think we can fix it this way:

Check my screenshot and please untick/uncheck the unnecessary options from the second tab (Other Software):

Please highlight, for example: Canonical Partner and Click Edit. Make sure it says "natty" in distribution field.

After you uncheck the other unneeded entries, Reload and I guess your problem will be fixed :)

Everything is pretty much the same mate! I didn't change anything at all. After skimming through the distribution fields, 3 of them do not have use "natty". They are:

[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner (Source Code)
[http://dl.google.com/linuxchrome/deb/stable](http://dl.google.com/linuxchrome/deb/stable) main

Apart from that, they are all the same! :-)

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Everything is pretty much the same mate! I didn't change anything at all. After skimming through the distribution fields, 3 of them do not have use "natty". They are:

[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
[http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner (Source Code)
[http://dl.google.com/linuxchrome/deb/stable](http://dl.google.com/linuxchrome/deb/stable) main

Apart from that, they are all the same! :-)

Just make sure to uncheck the duplicate and keep it like my screenshot:

Also, on your source list, please remove this:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
```

Then Save it.

I posted the command earlier :)

---

### Post by Itzmir_Heman on 2011-10-07
Hey mate, how do I make it to a writeable form? It is Read-Only form right now and I can't update the file.

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Hey mate, how do I make it to a writeable form? It is Read-Only form right now and I can't update the file.

```
sudo **gedit** /etc/apt/sources.list
```

replace gedit with whatever text editor do you have. If you haven't changed that, keep the command as it's ;)

---

### Post by Itzmir_Heman on 2011-10-07
Done mate! Tried to update the system again and still couldn't get through.

```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/lucid/InRelease](http://archive.canonical.com/dists/lucid/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/natty/InRelease](http://archive.canonical.com/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by amjjawad on 2011-10-07
To be removed in RED:

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties
**[COLOR=Red]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted[/COLOR]**
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B][COLOR=Red]# deb http://my.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse[/COLOR][/B]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B][COLOR=Red]# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner
[/COLOR] [/B]
deb http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
[B][COLOR=Red]deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner[/COLOR][/B]
deb http://archive.canonical.com/ natty partner
deb-src http://archive.canonical.com/ natty partner
```

---

### Post by Itzmir_Heman on 2011-10-07
Allright! Here is the finalized sources.list

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.


deb http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/ natty partner
deb-src http://archive.canonical.com/ natty partner
```

And then I tried to get the update again and this thing came out again.

```
itzmir@Itzmir:~$ sudo apt-get update
Err http://archive.ubuntu.com natty InRelease                                  
  
Err http://archive.ubuntu.com natty-updates InRelease                          
  
Err http://archive.ubuntu.com natty-security InRelease                         
  
Err http://archive.canonical.com natty InRelease                               
  
Err http://archive.canonical.com natty InRelease                               
  
Err http://archive.ubuntu.com natty Release.gpg                                
  Unable to connect to 219.93.178.162:3128:
Err http://archive.ubuntu.com natty-updates Release.gpg                        
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                             
  Unable to connect to 219.93.178.162:3128:
Err http://archive.ubuntu.com natty-security Release.gpg                       
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                             
  Unable to connect to 219.93.178.162:3128:
Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://dl.google.com stable InRelease                                      
  
Err http://extras.ubuntu.com natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err http://dl.google.com stable Release.gpg
  Unable to connect to 219.93.178.162:3128:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/natty/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by amjjawad on 2011-10-07
```
# deb cdrom:[Lubuntu 11.04 _Natty Narwhal_ - i386 (20101203)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main


```

Ok, above is my list.

I think something was opened when you ran "sudo apt-get update".

Honestly, I'm running out of ideas here :(
I suggest to go through my list above then ... check the posts here ... I feel you have missed something so simple :)

Do you have any PPA or stuff? any extra stuff? try to keep the default settings.

I have included all the screenshots you may need.

I'm so sorry but I must leave my home now ... catch you later :)

---

### Post by Itzmir_Heman on 2011-10-07
Thanks for the help. I reckoned that a program was running when I was trying to get an update. And then I retried it and still giving me the same problem. Thanks for your time bruv!

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Thanks for the help. I reckoned that a program was running when I was trying to get an update. And then I retried it and still giving me the same problem. Thanks for your time bruv!

I have done nothing so far. I'm sure you'll manage to fix it.
Take an advice? leave your machine now, have a walk then come back later. You'll figure it out then with no time :)

I'll check on you once I'll be back!

Thanks a lot and you most welcome :)

---

### Post by .hfxdesign on 2011-10-07
What type of network setup do you have? Are you connected through a router, possibly multiple routers? Any information on this could be helpful. :)

---

### Post by Itzmir_Heman on 2011-10-07
> What type of network setup do you have? Are you connected through a router, possibly multiple routers? Any information on this could be helpful. 

Yeah, I guess. Connected through a Wi-Fi router. Only one router to be honest. Further information regarding my case. I would say that previously, there were no issues at all. After I upgraded to Natty Narwhal, I tried to download Java 6 so that I could play Minecraft in peace. And that is when I realized that there is an issue with the internet.

I hope that this helps though! :-)

---

### Post by .hfxdesign on 2011-10-07
You're not getting a DNS error when using a web browser are you?

---

### Post by Itzmir_Heman on 2011-10-07
Nope! Not at all mate!

---

### Post by .hfxdesign on 2011-10-07
I'm running out of ideas myself. It has to be something trivial. What type of router are you using?

---

### Post by Itzmir_Heman on 2011-10-07
D-Link DIR - 615 wireless router. It is so weird mate! I can't download anything related to Ubuntu! I can download music and what not. I thought that it was the server/mirror issue but it seems unlikely.

I have been doing a lot of research about this and it seems that mine is the worst. I now that it is not helping though but it is stressing me out too. Just to let you know that when I was on Karmic Koala before, I used to have the same problem. I was not able to update nor download anything from Ubuntu Software Center for 1 year until recently. My mate passed me the Natty Narwhal's file and I installed it.

Everything worked perfectly only until recently. And thats the story of my life! Hahaha! But I am super cereal about this because I want to be able to play Minecraft again! :-p

---

### Post by .hfxdesign on 2011-10-07
It's possible during the update one of your configs got corrupted, I'm still somewhat new to linux myself, I just have an eye for detail. I noticed something odd about the output you posted:
```
Err http://extras.ubuntu.com natty Release.gpg                                 
  Unable to connect to 219.93.178.162:3128:
Err http://dl.google.com stable Release.gpg
  Unable to connect to 219.93.178.162:3128
```

It seems to be resolving extras.ubuntu.com and dl.google.com to the same IP address.

---

### Post by ashwinrao on 2011-10-07
It appears that all the addresses are resolving to your ISP IP. I have checked at [http://whois.domaintools.com/219.93.178.162](http://whois.domaintools.com/219.93.178.162) .

---

### Post by Itzmir_Heman on 2011-10-07
> It appears that all the addresses are resolving to your ISP IP What is that supposed to mean mate?

---

### Post by .hfxdesign on 2011-10-07
I ran a whois and got the same thing.

For good measure, could you flush your DNS cache by bringing your network interface down, then up?

---

### Post by Itzmir_Heman on 2011-10-07
> For good measure, could you flush your DNS cache by bringing your network interface down, then up?

Yeah, I could do that but the problem is, how?

---

### Post by .hfxdesign on 2011-10-07
Try using this, not sure if it still works or not:
```
sudo /etc/init.d/networking restart
```

---

### Post by Itzmir_Heman on 2011-10-07
```
itzmir@Itzmir:~$ sudo /etc/init.d/networking restart
[sudo] password for itzmir: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

Done!

---

### Post by .hfxdesign on 2011-10-07
Alright, give updating a shot now. If that doesn't work, I'm really at a loss.

---

### Post by Itzmir_Heman on 2011-10-07
Ah! It is ok mate! I am more than happy that someone actually tried to help! Unfortunately it is a no go.

```
itzmir@Itzmir:~$ sudo apt-get update
Err http://archive.ubuntu.com natty InRelease                                                                                                                
  
Err http://archive.ubuntu.com natty-updates InRelease                                                                                                        
  
Err http://archive.ubuntu.com natty-security InRelease                                                                                                       
  
Err http://archive.canonical.com natty InRelease                                                                                                             
  
Err http://archive.canonical.com natty InRelease                                                                                                             
  
Err http://archive.ubuntu.com natty Release.gpg                                                                                                              
  Unable to connect to 219.93.178.162:3128:
Err http://archive.ubuntu.com natty-updates Release.gpg                                           
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                                                
  Unable to connect to 219.93.178.162:3128:
Err http://archive.ubuntu.com natty-security Release.gpg                                          
  Unable to connect to 219.93.178.162:3128:
Err http://archive.canonical.com natty Release.gpg                                                
  Unable to connect to 219.93.178.162:3128:
Err http://extras.ubuntu.com natty InRelease                                                      
  
Err http://dl.google.com stable InRelease                                                         
  
Err http://extras.ubuntu.com natty Release.gpg                                                    
  Unable to connect to 219.93.178.162:3128:
Err http://dl.google.com stable Release.gpg
  Unable to connect to 219.93.178.162:3128:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/dists/natty/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://archive.canonical.com/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to 219.93.178.162:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by ashwinrao on 2011-10-07
> **Itzmir_Heman said:**
> What is that supposed to mean mate?

All those update requests are ending at your Internet Service Provider IP address. Might be issue is due to the ISP block. It would be better if you check with them once.

---

### Post by Itzmir_Heman on 2011-10-07
> All those update requests are ending at your Internet Service Provider IP address. Might be issue is due to the ISP block. It would be better if you check with them once.

Since this is not the first time, I have spoken to my ISP's rep a while back and they have no clue over what's going on. What do you think is the problem here?

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Since this is not the first time, I have spoken to my ISP's rep a while back and they have no clue over what's going on. What do you think is the problem here?

OK, I'm BACK :D

Do you have another machine at home? 
Have you tried to connect via LAN as I mentioned one the first page of this thread? just give it a try and I'm not expecting much though.
Disconnect your Wireless and connect via LAN.

---

### Post by Itzmir_Heman on 2011-10-07
> Do you have another machine at home?

Yes and they are all using Windows. Working fine and having no problems updating their machines.

> Have you tried to connect via LAN as I mentioned one the first page of this thread? just give it a try and I'm not expecting much though.
Disconnect your Wireless and connect via LAN.

I did try it and there was no difference! I still am unable to update/download though!

---

### Post by Itzmir_Heman on 2011-10-07
> Do you have another machine at home?

Yes and they are all using Windows. Working fine and having no problems updating their machines.

> Have you tried to connect via LAN as I mentioned one the first page of this thread? just give it a try and I'm not expecting much though.
Disconnect your Wireless and connect via LAN.

I did try it and there was no difference! I still am unable to update/download though!

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Yes and they are all using Windows. Working fine and having no problems updating their machines.
I was hoping that one one them has Linux. Never mind :)


> I did try it and there was no difference! I still am unable to update/download though!

Ok then, one more thing to try.

I already posted my source list, right?
I want you to use the same list but first you need to save a backup for your current list.

To do so:
```
sudo gedit /etc/apt/sources.list
```

From File, choose "Save As" and save it as:
```
sources.back

```

Close gedit and run the command again to open sources.list.

sources.back will be your backup file which can be used later in case anything may go wrong. You can access it the same way:

```
sudo gedit /etc/apt/sources.back
```
and then Save it As: **sources.list** but I hope you won't need that :)

---

### Post by Itzmir_Heman on 2011-10-07
Right but just to double check, the list that you gave was for Ubuntu yea? Not for Lubuntu init? I saw the word Lubuntu being mentioned a few times in your sources.list

---

### Post by amjjawad on 2011-10-07
> **Itzmir_Heman said:**
> Right but just to double check, the list that you gave was for Ubuntu yea? Not for Lubuntu init? I saw the word Lubuntu being mentioned a few times in your sources.list

My bad, yes, you are right and I'm not sure whether that would make any difference or not because both are Natty, it's just the Desktop Environment which is different. 

If you want, I can reboot to Ubuntu 11.04 and post back from there but hey, as long as we'll have a backup, so don't worry :)
Do it for now and I'll be right back :)

---

### Post by amjjawad on 2011-10-07
```
# deb cdrom:[Lubuntu 11.04 _Natty Narwhal_ - i386 (20101203)]/ natty main restricted
```This is the only line where Lubuntu is mentioned.
You can remove this line or put "#" in the front.

As long as you are not using the CD as a source, then you don't need that line as of now. I hope I'm not wrong about that.

Anyway, I'm rebooting to Ubuntu 11.04 now.

---

### Post by amjjawad on 2011-10-07
Sorry for being late, I had a network problem myself :D
Don't worry, it's not like yours!


```
# deb cdrom:[**Ubuntu 11.04** _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.qualitynet.net/ubuntu/ natty main restricted
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.qualitynet.net/ubuntu/ natty-updates main restricted
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.qualitynet.net/ubuntu/ natty universe
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty universe
deb http://ubuntu.qualitynet.net/ubuntu/ natty-updates universe
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.qualitynet.net/ubuntu/ natty multiverse
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty multiverse
deb http://ubuntu.qualitynet.net/ubuntu/ natty-updates multiverse
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ubuntu.qualitynet.net/ubuntu/ natty-security main restricted
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-security main restricted
deb http://ubuntu.qualitynet.net/ubuntu/ natty-security universe
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-security universe
deb http://ubuntu.qualitynet.net/ubuntu/ natty-security multiverse
deb-src http://ubuntu.qualitynet.net/ubuntu/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

