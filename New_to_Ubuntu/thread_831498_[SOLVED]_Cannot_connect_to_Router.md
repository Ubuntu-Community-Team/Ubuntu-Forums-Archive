---
title: "[SOLVED] Cannot connect to Router"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Talleyrand on 2008-06-16
I'm sharing a Dell 4300 between Ubuntu 8.04 LTS and XP Professional. I'm new to Linux (just installed it yesterday), but so far, I'm very pleased with it and want to give it a try. The installation was flawless, and everything worked, except my online connection.

It seems I'm not being able to reach my DSL Router through Linux though I have configured my ethernet connection with DHCP and have all the proper DNSs in place.

I'm using a US Robotics (USR 8000) broadband router (It's an old workhorse, but it works fine) to share my DSL connection among four machines, and all the hardware components are working fine, so it must be some configuration mishap from my part which is impeding the successful pinging of my router/DNSs.

Enclosed you'll find a doc file with some info I've gathered based on other similar threads, that hopefuly will help one of you guys, to come with some suggestions on how to solve this problem. 
Thanks in advance for your help!

---

### Post by wormser on 2008-06-16
Welcome to Ubuntu.  This is your network card. 

>    	 	 	 	 	 	  Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 

Usually your ethernet card just works.  Realtek cards don't have great support with Linux.  Take a look at some of these [threads]("http://ubuntuforums.org/search.php?searchid=43132691").

---

### Post by cariboo on 2008-06-16
Instead of setting the dhcp option try roaming mode, If I set dhcp I can't connect to my router either.

Jim

---

### Post by Talleyrand on 2008-06-17
Nope! It didn`t work. It seems the problem is really my ethernet card (Realtek). Thanks anyway for the suggestion.

---

### Post by Talleyrand on 2008-06-17
Bingo! You`re right Wormser.
I`m writing this reply from Ubuntu 8.04 started in Live Mode (without intalling it to my disk), from a second machine connected to the same router and communication setup. It was a piece of cake to make it work after I circumvented my Realtek ethernet card.

Can you refer me any proven ethernet cards for working with Ubuntu so as I can replace my uncompatible Realtek.

Many thanks for your help so far!

---

### Post by R.E.A.D001 on 2008-07-19
hey evry1 
 i recently installed ubuntu studio on my grandpa's computer and the internet wouldn't work so i went into the network config file and fixed it by by adding    

                      # The primary network interface
                      auto eth0
                      iface eth0 inet dhcp

it worked for about 4 hours then just quit and nothing had changed and i tried a complete reinstall and it did not fix the problem either any help would be much appreciated

---

