---
title: "ndisgtk &quot;Could not find a network configuration tool.&quot;"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by second.exodous on 2008-10-25
I upgraded ubuntu from 8.04 to 8.10 and my wireless doesn't work anymore, so I tried to set up ndiswrapper, the driver is still loaded but when I go to configure network with ndisgtk I get an error saying 'Could not find a network configuration tool.'

I searched the forums and couldn't find anything pertaining to ndisgtk, anyone know how to use this?

Thanx much in advance,
Stan

---

### Post by lenordbater on 2008-11-02
I'm having the exact same problem.  Any suggestions?

---

### Post by coldswell on 2008-11-04
I also have the same problem. Have you managed to find a way to fix it?

---

### Post by coldswell on 2008-11-04
I have found a way to fix it. I just followed the instructions on here starting from part 10.

[http://ubuntuforums.org/showthread.php?t=943848](http://ubuntuforums.org/showthread.php?t=943848)

---

### Post by MrGumba on 2008-11-09
i changed the managed=true but when i tried to configure my network it still gave me the same message. Is there anything else i can try?

---

### Post by MrGumba on 2008-11-10
oh nvm =]

i fixed the problem... for some reason i didnt have the network administration tool installed to actually configure.oops

thanks anyway:lolflag:

---

### Post by williamsjk on 2008-11-19
> **MrGumba said:**
> oh nvm =]

i fixed the problem... for some reason i didnt have the network administration tool installed to actually configure.oops

thanks anyway:lolflag:

I'm in exactly the same position, I think.  I've got the network manager 0.7 that came with 8.10 installed - but it's not detecting the wireless card.  Is there another network administration tool I need?  If so where can I get it (my ubuntu machine can't get online without the wireless).

Or do I need to change a setting in network manager? 

Thanks!

---

### Post by megajosh2 on 2008-11-22
I have the same problem, I've been trying all day to get wireless working... :(

---

### Post by deviant937 on 2008-11-23
I was having a very similar problem. I solved it by installing gnome-network-admin.

---

### Post by broomie on 2008-12-09
Coldswell fixed worked for me - thanks very much!

PaulB

---

### Post by ZanexGt on 2008-12-12
> **second.exodous said:**
> I upgraded ubuntu from 8.04 to 8.10 and my wireless doesn't work anymore, so I tried to set up ndiswrapper, the driver is still loaded but when I go to configure network with ndisgtk I get an error saying 'Could not find a network configuration tool.'

I searched the forums and couldn't find anything pertaining to ndisgtk, anyone know how to use this?

Thanx much in advance,
Stan

Open Synaptic Package Manager and search for 'Network Administration'.

Install the gnome-network-admin package and you will not get that message again.

---

### Post by talofo on 2008-12-18
> **williamsjk said:**
> I'm in exactly the same position, I think.  I've got the network manager 0.7 that came with 8.10 installed - but it's not detecting the wireless card.  Is there another network administration tool I need?  If so where can I get it (my ubuntu machine can't get online without the wireless).

Or do I need to change a setting in network manager? 

Thanks!


I'm like William.

William have you managed to work with the Network Manager that comes with Ubuntu 8.10?



Regards,
MEM

---

### Post by jvanhare on 2009-03-25
If you are lucky enough to have Broadcom drivers, like my Dell B120, which has the 4318,  Ubuntu 8.10 has proprietary drivers available.  Connect to the internet with your wired ethernet, and go to System-Administration-Synaptics Package Manager on your pull down menu on the top menu bar; search for the package fwcutter mark it for installation, and click Apply.  It should connect to the internet and download the Broadcom proprietary drivers for your notebook.  Reboot and it should work.  If not got to System-Administration-Hardware Drivers, and see if your wireless network card shows up.   Click Activate if it did not activate.  Theoretically you could do this first but mine just hung at downloading drivers 0% and I realized that fwcutter is not installed by default on a new install, so I had to go and add the package first.

---

### Post by Monoplex on 2009-04-07
I'm having the same "Could not find a network configuration tool" problem. with 8.10 and 9.04.

I have a d-link DWA-130. ndisgtk sees the device. so I think that's working.

I didn't have a problem with anything on my 8.04 installation, and am now trying to configure everything to how it was.
But at least I learned how to partition an ext3 and to not fix what's not broken.

---

### Post by fr0gg on 2009-04-08
Hey guys, i'm trying to get my Intrepid working with my wireless network adapter..i've already attempted adding a new wireless connection, but still nothing. I searched for help and found this thread, tried the ndisgtk command, tried to install it but it can't find the package? It cannot find the fwcutter package when i search for that either. Any suggestions/tips?
Thanks.

---

### Post by frankida on 2010-03-05
> **deviant937 said:**
> I was having a very similar problem. I solved it by installing gnome-network-admin.


wow.. after troubleshooting on the threads for two days.. this fixed my problem.  Thanks!!!

---

### Post by JG850 on 2010-09-10
What if i Have that and still get the message?

When I open up the windows wireless connections, it says it's unable to tell if hardware is present, but in the window by the driver name it says hardware present : yes. When i say configure network, it tells me it couldnt find a network configuration tool. i have ubuntu 10.04

---

