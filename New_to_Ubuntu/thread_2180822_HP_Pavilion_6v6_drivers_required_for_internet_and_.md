---
title: "HP Pavilion 6v6 drivers required for internet and graphics"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by kfehr911 on 2013-10-14
Hello All,
Well I'm certainly glad to be back.  I previously had a desktop that I ran ubuntu on for about 4 years, it was an excellent machine.  I have purchased a used  hp pavilion 6v6 with a amd a8 -3500 apu with radeon graphics 1.50GHz with 8 GB of RAM and 750GB hard drive. also has a bluray disc drive.  i would like to find more spec to post but alas I don't know where to find such information on windows 7.

when I first installed ubuntu with window installer (great program) I was able to connect to the internet wirelessly in ubuntu.  then I received an warning that I didn't have the driver necessary to card the wireless card.  now I'm unable to connect to the internet wirelessly.  I have tried but I'm assuming that i will be able to connect via Ethernet cord and download necessary drivers etc.. 

Although I have used ubuntu before I'm not really and experienced user. I have forgot alot of how to use terminal so if the instructions be cut and paste I would be every so grateful.

please post where i can find all the drivers and programs to really improve this machine.  so I can play blurays, use the HDMI port, play music etc.

I remember doing all these things on my desktop using Hardy Heron and after. once the necessary programs and drivers were found I had a machine that ran like a top until a hardware failure. I would like to find myself with the same experience very soon with this laptop.

Awaiting your Instruction,
Kyle

---

### Post by UltimateCat on 2013-10-15
Hi:

In order to find out what NIC your computer has you can run this command to find out-
```
lspci | grep -i network

```

I didn't have a NIC so I had to purchase one and install it on my motherboard-

To find out what Network Ethernet is on your motherboard you can run:
```
lspci | grep -i -color 'network|ethernet

```

If you want more information including your processor and graphics card you can run:
```
lspci

```

>  I have tried but I'm assuming that i will be able to connect via Ethernet cord and download necessary drivers etc.. 

You should be able to if your Internet provider is providing you with a DSL line. Or some other type of wired line.
Other wise you may have a wireless modem- or wireless router-

> please post where i can find all the drivers and programs to really improve this machine.

I can't provide you with the website to the drivers until I know what NIC or Ethernet card you have-

---

### Post by mastablasta on 2013-10-15
connect with wire and it iwll offer the drivers. it is quite possible that drivers are also on install CD since you say it worked before.

do you have wubi install now? wubi is not supported/developed anymore. though i think it still works with 12.04.

---

### Post by kfehr911 on 2013-10-17
Thanks for the information. I will post the information at a later time. 

I have discover that the issues is a proprietary issues with the type of wireless modem my roommate has. I was at a friends house and was about to connect in Ubnutu without a problem.  

The Ethernet connection works fine as well. 

So at my apartment we have the modem (from service provider shaw) then the wifi router 
Is there a particular broadband wifi  router that I should be looking to purchase that is compatible with Ubuntu ? 

Thanks for your help

---

### Post by mastablasta on 2013-10-17
no. likely the problem is then a setting on router. e.g. some routers offer to block MAC addres etc...

---

