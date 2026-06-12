---
title: "Need basic help with networking."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Plumtreed on 2008-09-07
I have two PCs both running Hardy. I would like to set up a network so that I can share the files of both computers.

I have one ethernet cable, R52??, connecting via Ethernet cards. I must admit that they seem to have found each other but not in a way that makes any sense to me.

Can you help me in making the connection effective? I don't know anything about addresses, IP numbers, subnet masks or even whether I should use Eth0 or Eth1, or even Lo. I really don't even know what to expect; will I get to view each PCs files and use them as I like. Once setup where do I look for these files.

I have searched here but the talk seems to be about wireless and hooking up to the internet not just plain vanilla wired networking.

It is very rudimentary but it is essentially from the 'ground' up. Look forward to hearing how to do it or where to find the info.

---

### Post by cdtech on 2008-09-07
While we try to help you, here is a little reading about networking.
[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

Do you have a hub or router? and how do you connect to the internet?

---

### Post by men28 on 2008-09-07
If you have an ADSL router, for example, in DHCP mode there is a good chance that you just connect your network card to the router, press on the Firefox icon and you are in the internet. And then you choose something like Remote Places from System Menu (in KDE) and you can see another computers in your local network. 

Ubuntu is very user friendly operating system.

---

### Post by tangibleorange on 2008-09-07
> **Plumtreed said:**
> I have two PCs both running Hardy. I would like to set up a network so that I can share the files of both computers.

I have one ethernet cable, R52??, connecting via Ethernet cards. I must admit that they seem to have found each other but not in a way that makes any sense to me.

Can you help me in making the connection effective? I don't know anything about addresses, IP numbers, subnet masks or even whether I should use Eth0 or Eth1, or even Lo. I really don't even know what to expect; will I get to view each PCs files and use them as I like. Once setup where do I look for these files.

I have searched here but the talk seems to be about wireless and hooking up to the internet not just plain vanilla wired networking.

It is very rudimentary but it is essentially from the 'ground' up. Look forward to hearing how to do it or where to find the info.

I assume you are NOT using a router or hub (you are connecting one PC directly to the other with 1 cable). if this is the case, you need to check you are using a crossover cable. hold up both ends of the cable and look at the colours of the wires - is the colour/wire pattern the same on both ends or different?

---

### Post by men28 on 2008-09-07
I didn't have any problem sharing folders on windows computer and read/write to them via samba from ubuntu computer.
But it is not as simple as I thought even with a router to share folders between two ubuntu computers.

---

### Post by Plumtreed on 2008-09-07
Many thanks for the quick replies, I didn't expect the responses to arrive so quickly.

I was interested in joining two computers without involving a router. I get a hint from both cdtech & men28 that it may be the better way to go!

Thanks Tang, my cable colours appear to be aligned in the same way at each end, obviously not a crossover?

I suppose the course of action I need to follow involves the purchase at least of a cross-overtype cable. Would that, by some 'miracle', connect the 2 PCs as if they were one?

I appreciate your patience and i am trying to absorb cdtech's link!

---

### Post by egalvan on 2008-09-07
> **Plumtreed said:**
> ... I must admit that **they seem to have found each other** but not in a way that makes any sense to me.

How do you mean ? What indications do you see? Lights turning on, messages popping up?

---

### Post by Plumtreed on 2008-09-07
Yes, Egalvan, lights do turn on in the panel icons, they tend to blink especially as the PCs fire-up. This is supposed to suggest a network!

The Network Manager, on right click, tells me there is a wired connection.

However, it sounds like I have to 'buy' more hardware or at least different cableing to make things really work.

Can you give me a hint of the result of all this effort, do I get open access to each PC?

---

### Post by tangibleorange on 2008-09-07
> **Plumtreed said:**
> Yes, Egalvan, lights do turn on in the panel icons, they tend to blink especially as the PCs fire-up. This is supposed to suggest a network!

The Network Manager, on right click, tells me there is a wired connection.

However, it sounds like I have to 'buy' more hardware or at least different cableing to make things really work.

Can you give me a hint of the result of all this effort, do I get open access to each PC?

hmm well you should need a crossover cable to connect two PCs direct with no router. A router would make things easier, but it should be do-able without. Regardless, in order to share files on both computers, they need the samba package installed:

```
sudo apt-get install samba
```

but that will require an internet connection... if you can temporarily plug them into the internet and download that package it would be very useful.

PS. I have generally found the flashing ethernet lights only mean something is plugged in on both ends, not that any sort of usable network is established :S...

---

### Post by Plumtreed on 2008-09-07
I had the impression that Samba had to do with linking windows and Ubuntu. I'll check further on Samba but will download it. Does it need a router??? Do I need a router?

---

### Post by lazyart on 2008-09-07
This can be done with either a crossover cable or a router.  A router would give you the benefit of sharing the internet connection, as well as taking care of assigning IP addresses.

With the crossover cable you'll have to assign the machines addresses and subnets that will work together--

machine 1: IP address 10.0.0.1, Subnet 255.255.255.0
machine 2: IP address 10.0.0.2, Subnet 255.255.255.0

(note- if you get a router you can skip that part as it will assign addresses for you.  Just find out what the address is of each machine and move on...)


From there, right click on the folder you wish to share, select share folder, then choose SMB.
Now go to the other machine, go to Places in the menu and select connect to server.
Enter the IP address of the other machine where is asks for the Server name and the connection type is Windows Share.  Enter your login name and save the connection.  Double click on the newly created icon, enter the password for the other machine and you should be connected.

---

### Post by Plumtreed on 2008-09-07
Thank you, I have decided that a router is a wise thing to buy and i guess I will try to connect one of these PCs as wireless.

Linking to the internet is also an incidental benefit from having a router.

---

### Post by Sef on 2008-09-07
> I had the impression that Samba had to do with linking windows and Ubuntu. I'll check further on Samba but will download it. Does it need a router??? Do I need a router?

You are correct.  Samba is for linking GNU/Linux and Windows.  For GNU/Linux networks, the corresponding software is [NFS]("http://en.wikipedia.org/wiki/Network_File_System_(protocol)").

---

### Post by egalvan on 2008-09-07
> **Plumtreed said:**
> Yes, Egalvan, lights do turn on in the panel icons, they tend to blink especially as the PCs fire-up. This is supposed to suggest a network!

The Network Manager, on right click, tells me there is a wired connection.

However, it sounds like I have to 'buy' more hardware or at least different cableing to make things really work.

Can you give me a hint of the result of all this effort, do I get open access to each PC?

If the lights on both  network cards blink, and Network manager om both machines say you have a connection,

then you have a physical connection, and the cable works.
Modern network gear tends to auto-detect the type of cabling used, and adjust itself to use straight or cross-over.

This is the cheapest type of network you can use, money-wise, but can cost some time in setting up the LAN addresses, as another member here gave examples of.

That said, a router that has several ports will enable you to easily add computers in the future.

And to be technical about it, a router that has more than two ports has a switch included inside, so it's a router/switch. :)

---

### Post by Plumtreed on 2008-09-07
Thanks again Egalvan,I never did get it to make any sense but I am sure things were connected. I gave up because I intend to get a router and try to have a connection to the internet and also the printer. 

I would like to have the 'desktop,printer and perhaps a scanner' linked with cabling and the 'notebook' wirelessly. The notebook is the only one with wireless capability. Do I look for a router with the ability to 'hook-up' with wires and without, or am I on the wrong track?

Thanks Sef and another question, do I need to add anything if I have this Network Manager?

  


i

---

### Post by Redptc on 2008-09-07
They are probably available but I haven't been able to find a router that has the ability to do wired and wireless. They appear to do one or the other because, I think, the trend is towards 'wireless'.

If you get a router that is 'wireless' specific you may have to connect your two computers in a 'wireless' way.

---

### Post by Xiong Chiamiov on 2008-09-07
> **Redptc said:**
> They are probably available but I haven't been able to find a router that has the ability to do wired and wireless. They appear to do one or the other because, I think, the trend is towards 'wireless'.

If you get a router that is 'wireless' specific you may have to connect your two computers in a 'wireless' way.
Hmm?  I've never seen a router that doesn't have LAN ports, wired or wireless.  Most seem to have 4, in fact.

Plumtreed:
If your printer is not network-capable (most likely not, unless it was expensive), then you'll need to either share it through one of the computers (meaning that that computer needs to be on when trying to print) or buy a [print server]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=387&name=Network-Print-Servers").

---

### Post by Redptc on 2008-09-08
Xiong, saw your reply and wondered what you had in mind. Do routers have the ability to link with one PC in a wireless connection and then, if necessary, link with cables to 4 other PCs?

---

### Post by Plumtreed on 2008-09-09
Many thanks to everyone, I purchased a router that does wireless for the notebook and the other PC is hooked up via one of four ports.

I can visit each one but am still baffled by the process required to print! Xiong indicated that there may be a need to buy a print server.

---

### Post by egalvan on 2008-09-09
> **Plumtreed said:**
> Many thanks to everyone, I purchased a router that does wireless for the notebook and the other PC is hooked up via one of four ports.

I can visit each one but am still baffled by the process required to print! Xiong indicated that there may be a need to buy a print server.

What kind of connection does your printer have?
This will determine what you need to connect it.

And despite a previous post, modern printers don't need to be expensive to connect wirelessly. 

Of course, that depends on what you consider expensive. I've seen wireless printers under $200, and wired network printers under $150

---

### Post by Plumtreed on 2008-09-10
The printer is a wired connection and not USB. I have the choice and can make it USB but not wireless.

Once I stumbled on the method of telling one PC to share, I have been able to print from both PCs. This does mean that both PCs have to be turned on.

Do you have another way of connecting the printer, Egalvan? I can assure you that it is not the sort of printer one would consider as 'expensive'!

---

### Post by egalvan on 2008-09-15
> **Plumtreed said:**
> The printer is a wired connection and not USB. I have the choice and can make it USB but not wireless.

Once I stumbled on the method of telling one PC to share, I have been able to print from both PCs. This does mean that both PCs have to be turned on.

Do you have another way of connecting the printer, Egalvan? I can assure you that it is not the sort of printer one would consider as 'expensive'!

Sorry for the delay, I get busy with life.

And let's leave "expensive' aside... I've purchased all my printers at auctions or pawn shops, so it doesn't count.


OK, if you are still having problems, and want/need a solution...

Several ways of connecting a printer. 

I'm trying to establish what kind of physical connections YOUR printer has.
This can vary greatly with price and age....and you know what I feel about "price".

There are several ways, broken into "wired" and "wireless"

wired:
RS-232 (aka serial)
IEEE-1394 (aka parallel, aka Centronics)
USB
proprietary

wireless:
wifi
bluetooth
proprietary

Which one(s) do you have on your printer?

We can go from there.

---

### Post by Plumtreed on 2008-09-15
I appreciate your interest and I hope your part of Texas wasn't the part so badly affected by the storms.

Now that I have things working on a network I am able to print from both PCs. I do need to have both PCs on and the network running via the remote desktop viewer. This seems very satisfactory and is easy to live with!

I don't know what else can be or needs to be done! I guess being able to print from the wireless'laptop' without hooking into the network might be nice but not all that urgent.

My printer is currently connected to the 'desktop' via a USB connection. It is a Epson C67 and I have always been happy with the results. I will say that the manual that came with the router indicated you could run the printer as well, somehow????

---

### Post by egalvan on 2008-09-18
> **Plumtreed said:**
> I appreciate your interest and I hope your part of Texas wasn't the part so badly affected by the storms.

Time out for a weather report... :)
Ike gave us Deep-Southern-Texans a pass, but my brother (just west of Houston) got a few days of 'frontier life'... no electricity, phone, or water :guitar: .
My sister in Florida has had three hurricanes her way.
We got heavy rains from a storm system totally un-related to the hurricanes...

Back to our regurlary-scheduled messages....


> Now that I have things working on a network I am able to print from both PCs. I do need to have both PCs on and the network running via the remote desktop viewer. This seems very satisfactory and is easy to live with!
I don't know what else can be or needs to be done!


Very good to hear that you are well-connected...


> I guess being able to print from the wireless'laptop' without hooking into the network might be nice but not all that urgent.

Don't really understand what you are refering to here...

> My printer is currently connected to the 'desktop' via a USB connection. It is a Epson C67 and I have always been happy with the results. I will say that the manual that came with the router indicated you could run the printer as well, somehow????

Some routers now-a-days have a USB port that allows you to connect either external storage or other USB-style peripherals. I would need to peruse the manual to give you any better idea.

What is the make and model of your router?

Cheers

ErnestG

---

