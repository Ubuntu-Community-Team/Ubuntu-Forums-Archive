---
title: "How to set up a wired netw. with a Win7 machine and Lubuntu machine -help plz-"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by Redzky on 2012-10-29
I have been at this for a day, googling and whatnot. I was wondering if anyone has done this before. 

I am trying to get internet enabled on my Lubuntu machine via cat5e cable from a Windows 7 machine. My Windows 7 machine has internet connected through an IpV4 connection. Which is a USB tether through my phone.

I'm able to connect to wifi networks on the Lubuntu machine with a USB Wifi Adapter but I want to learn how to set up a wired network as well. Thanx :guitar:

---

### Post by reptilezone2002 on 2012-10-29
ok u want to here ur windows 7's internet conection with ur lubuntu machine using a wired network??? is it..
if so 
i hope u have a router with u??

---

### Post by Mark Phelps on 2012-10-29
Are you asking if you can share the Internet connection the Win7 box has by plugging a network cable into it -- and then plugging the other end of the cable into the Ubuntu machine?

In the Windows world, that is known as Internet Connection Sharing (ICS) -- and that is a Windows feature.  I'm not aware that you can do this with a non-Windows machine.

---

### Post by mike555 on 2012-10-29
If you want to use one incoming ethernet cable , just buy a "switch", it will split the connection between them .
   like this one;   [http://is.gd/uesHzQ](http://is.gd/uesHzQ)

---

### Post by Redzky on 2012-10-29
Ok that explains everything thanx guys.

---

### Post by reptilezone2002 on 2012-10-30
> **Redzky said:**
> Ok that explains everything thanx guys.

yes u can share internet connection on ubuntu too. if u r trying to do this without a switch or a router ( directly connecting 2 mechines make sure ur cable is crossed

---

### Post by Redzky on 2012-10-30
as in crossover right? good thing there's a 30 day refund period hah

---

### Post by Mark Phelps on 2012-10-30
What they're suggesting is something called a Crossover cable -- it's a standard ethernet cable with some of the leads switched.  This allows two machines to talk to each other without requiring them to be connected to a hub or switch.

The software product  Crossover is an app that builds off Wine and makes it easier to run SOME MS Windows programs in Ubuntu.  It has nothing to do with networking machines.

But ... you will also need some software running on each machine that can access the file system on the other machine -- and as I said, MS Windows ICS can not read Ubuntu filesystems.

---

### Post by amjjawad on 2012-10-31
> **Mark Phelps said:**
> What they're suggesting is something called a Crossover cable -- it's a standard ethernet cable with some of the leads switched.  This allows two machines to talk to each other without requiring them to be connected to a hub or switch.

+1

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

If you want to share files, etc between the two machines, that is a different story.

---

### Post by reptilezone2002 on 2012-10-31
> **Redzky said:**
> as in crossover right? good thing there's a 30 day refund period hah
  yes if u r connecting pc to pc directly u need a crossed patch cable

---

### Post by Mark Phelps on 2012-10-31
> **reptilezone2002 said:**
> yes if u r connecting pc to pc directly u need a crossed patch cable

The quote you included in your response was (as I had already indicated!) referring to the CrossOver SOFTWARE product, NOT to a crossover cable.

---

### Post by Redzky on 2012-10-31
So are you saying I should download crossover app on both machines to communicate with each other and not buy a crossover cable?

---

### Post by reptilezone2002 on 2012-11-01
> **Redzky said:**
> I have been at this for a day, googling and whatnot. I was wondering if anyone has done this before. 

I am trying to get internet enabled on my Lubuntu machine via cat5e cable from a Windows 7 machine. My Windows 7 machine has internet connected through an IpV4 connection. Which is a USB tether through my phone.

I'm able to connect to wifi networks on the Lubuntu machine with a USB Wifi Adapter but I want to learn how to set up a wired network as well. Thanx :guitar:
[U][B]How to share the internet connection using windows 7
[/B][/U]
First u need a router or a switch, 2 network interfaces (2 Lan cards or 1 lan card 1 usb 3G mbile broadband modem) & cross over patch cable(if u r connecting pc to pc directly )

GO to

1 Control Panel > Network & sharing centre 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226505&stc=1&d=1351761454[/IMG]

2 from the left hand panel choose Change Adapter settings

3 Be sure that _**ip address are "not  asigned"**_ to eny of ur lan connections.  from that right click on ur internet connection (in my case 3Connect usb Mobile Broadband or which ever ur lan connection that u have connected to the internet)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226506&stc=1&d=1351761600[/IMG]
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=226507&stc=1&d=1351761616[/IMG]

5 select properties then select sharing tab
6 from that tick the Allow other network users to connect..........
7 from Home networking connection select the other network interface (in my case local aria connection) & click OK thats it 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226508&stc=1&d=1351761736[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226509&stc=1&d=1351761736[/IMG]

---

### Post by Mark Phelps on 2012-11-01
> **Redzky said:**
> So are you saying I should download crossover app on both machines to communicate with each other and not buy a crossover cable?

NO -- Crossover app has NOTHING to do with networking.  It is an enhancement to the Wine app -- which allows you to run SOME Windows apps in Linux.

The crossover CABLE is what you need to connect two PCs directly together. You must use that to have the PCs connected before you do the stuff shown in reptilezone2002's post.

---

### Post by Redzky on 2012-11-01
> **Mark Phelps said:**
> NO -- Crossover app has NOTHING to do with networking.  It is an enhancement to the Wine app -- which allows you to run SOME Windows apps in Linux.

The crossover CABLE is what you need to connect two PCs directly together. You must use that to have the PCs connected before you do the stuff shown in reptilezone2002's post.

Gotcha, and thanx guys

---

