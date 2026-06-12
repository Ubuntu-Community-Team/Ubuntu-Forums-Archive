---
title: "Better than a dual boot system?"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-15
Here I am switching between XP and 11.10, shutting down and re-booting, and I got this idea.

Keep the Win machine, buy a $100 PC for Ubuntu and switch a single monitor between the 2 systems.

In today's marketplace a fast P4 or even a dual processor can be bought for very little at flea markets and Goodwill.

I am not whining am I?  

Why not?

---

### Post by Gremlinzzz on 2012-04-15
Why not? because you can buy something else with the $100.
I am not whining am I? I dont think so:popcorn:

---

### Post by Bucky Ball on 2012-04-15
Why not install one as a virtual machine inside the other???

[http://au.search.yahoo.com/search?p=virtual%20box%20ubuntu&fr=altavista&fr2=sfp]("http://au.search.yahoo.com/search?p=virtual%20box%20ubuntu&fr=altavista&fr2=sfp")

That way you won't need to keep rebooting to use one or the other. You just need the space and enough RAM ...

---

### Post by 3Miro on 2012-04-15
Depending on what you do under XP and Ubuntu, but if a P4 computer is enough, then you can just get a decent machine and use VirtualBox.

---

### Post by Boyntonstu on 2012-04-15
> **3Miro said:**
> Depending on what you do under XP and Ubuntu, but if a P4 computer is enough, then you can just get a decent machine and use VirtualBox.

In my OP and where I am now, Ubuntu is not 100% operable.

I never used a virtual machine so I ask, Can you quickly switch operating systems to allow using the working OS to fix/repair the other OS?

---

### Post by theknightlinux on 2012-04-15
You'd be running the virtual machine from inside the OS. A virtual machine doesn't operate any OS to its full performance as of now. So if you install XP to a virtual machine, you wouldn't be able to do some things as you normally would do, such as playing games. And Ubuntu deserves to be run from a real machine or have its own hardware, because... it's Ubuntu. What is the problem you're trying to solve? To switch between the two OS's faster, and not wait the boot time?

---

### Post by Hendronicus on 2012-04-15
> **Boyntonstu said:**
> Here I am switching between XP and 11.10, shutting down and re-booting, and I got this idea.

Keep the Win machine, buy a $100 PC for Ubuntu and switch a single monitor between the 2 systems.

In today's marketplace a fast P4 or even a dual processor can be bought for very little at flea markets and Goodwill.

I am not whining am I?  

Why not?

I don't think you're whining. Just use two entire computers. I do. Pretty much all the time, and I usually run one for games and such, and another for surfing and work. It's easy with a router.

---

### Post by QIII on 2012-04-15
> **Boyntonstu said:**
> Can you quickly switch operating systems to allow using the working OS to fix/repair the other OS?

Doubtful.

But if you want to have two separate machines running two OSes natively and switch a single monitor (and keyboard, presumably) between them, you just need a KVM switch.

---

### Post by Boyntonstu on 2012-04-16
> **Hendronicus said:**
> I don't think you're whining. Just use two entire computers. I do. Pretty much all the time, and I usually run one for games and such, and another for surfing and work. It's easy with a router.


My "Whining" comment was a pun.

I meant that I need not use Wine to run Win programs.

I am not whining/wine-ing if I use 2 computers!

---

### Post by forrestcupp on 2012-04-16
> **3Miro said:**
> Depending on what you do under XP and Ubuntu, but if a P4 computer is enough, then you can just get a decent machine and use VirtualBox.

Good point. Assuming your main computer is a decent computer, running an OS directly on a P4 probably wouldn't be any better than running the same OS in a virtual machine on your main computer. 

And yes, you can switch quickly between the OSs that way. You'll have one OS that is installed directly on your system as the host, and the other one installed as a guest OS in a virtual machine running within your host OS. In VM programs like VirtualBox, you can take a snapshot of your guest OS, which means you don't have to boot back into it. You just open your VM with VirtualBox, and it's almost immediately (it does take a few seconds) right back to where it was last time you left it, even if you have shut your computer off.

If you use XP to play games, I would suggest having it be your host OS that is installed directly on your hardware, and let Ubuntu be the guest OS. It really wouldn't hurt to at least try this out before you go spending $100 on a crappy computer.

---

### Post by audiomick on 2012-04-16
My two cents: as has been pointed out, in a virtual machine, you will not get the same ultimate performance from the guest system as you would if it were really in charge of the computer. Whether this is an issue or not is the relevant question. To find out, install VM or Virtual Box on your Linux install ( I don't know which one is the "preffered option") and try out whatever it is you need windows for in it. It may work, and you will have learned something new. 

If you decide to run two machines, look into a little program called Synergy. It is in the Repos. It may be in "universe", but it is there.

Here is the home page
[http://synergy-foss.org]("http://synergy-foss.org")

I need a Windows install for a couple of programs for work that can not be run in a VM. I use synergy at home when I have my Ubuntu desktop running and the Laptop next to it, both when the laptop is running Vista and when it is booted into Ubuntu. The advantage over a KVM switch is that you have access to both installs all the time, and can even copy and paste stuff from one to the other. The only prerequisite is that both machines are in the same LAN (network).

---

### Post by Boyntonstu on 2012-04-16
> **audiomick said:**
> My two cents: as has been pointed out, in a virtual machine, you will not get the same ultimate performance from the guest system as you would if it were really in charge of the computer. Whether this is an issue or not is the relevant question. To find out, install VM or Virtual Box on your Linux install ( I don't know which one is the "preffered option") and try out whatever it is you need windows for in it. It may work, and you will have learned something new. 

If you decide to run two machines, look into a little program called Synergy. It is in the Repos. It may be in "universe", but it is there.

Here is the home page
[http://synergy-foss.org]("http://synergy-foss.org")

I need a Windows install for a couple of programs for work that can not be run in a VM. I use synergy at home when I have my Ubuntu desktop running and the Laptop next to it, both when the laptop is running Vista and when it is booted into Ubuntu. The advantage over a KVM switch is that you have access to both installs all the time, and can even copy and paste stuff from one to the other. The only prerequisite is that both machines are in the same LAN (network).

Thanks.

My problem is that 11.10 is not connecting to the wifi adapter.

I believe that I would need to run 11.10 in the VM of windows to have connectivity.

Correct?

---

### Post by IHeequ5i on 2012-04-16
I use dual boot because I keep running into issues with getting everything I need to run properly on Ubuntu.

Two computers is a nice solution if you have the space for a second CPU, and sufficiently robust wiring in your house to support the additional drain on the circuit. I have neither. If I was going to use a second computer, though, I would go with a KVM switch.

---

### Post by audiomick on 2012-04-16
> **Boyntonstu said:**
> 
My problem is that 11.10 is not connecting to the wifi adapter.

I believe that I would need to run 11.10 in the VM of windows to have connectivity.

No, at first guess, I'd say you are missing a driver or something. In principle, your Ubuntu should be able to connect via WiFi. I haven't tried it using a VM, but I think that is a little complicated.

In the Ubuntu install, have you looked to see if there are proprietary drivers for your WiFi available? Plug it into a cable and make sure it has an internet connection. You shouldn't have a problem here; generally it "just works". Open the dash and type "hardware" in the search box and click on the "hardware drivers" icon. Let it look, and see if a driver is suggested for your WiFi. If so, install it and then try the WiFi again.

This, however, is not the point of this thread. If you want to pursue the matter, I believe the done thing is to start a new thread for it with an appropriate title. If you do that, you might want to post a link to the continuation here for the benenfit of anyone who might want to follow the discussion.

---

### Post by Boyntonstu on 2012-04-16
> **audiomick said:**
> No, at first guess, I'd say you are missing a driver or something. In principle, your Ubuntu should be able to connect via WiFi. I haven't tried it using a VM, but I think that is a little complicated.

In the Ubuntu install, have you looked to see if there are proprietary drivers for your WiFi available? Plug it into a cable and make sure it has an internet connection. You shouldn't have a problem here; generally it "just works". Open the dash and type "hardware" in the search box and click on the "hardware drivers" icon. Let it look, and see if a driver is suggested for your WiFi. If so, install it and then try the WiFi again.

This, however, is not the point of this thread. If you want to pursue the matter, I believe the done thing is to start a new thread for it with an appropriate title. If you do that, you might want to post a link to the continuation here for the benenfit of anyone who might want to follow the discussion.

Thanks,

The USB wifi adapter used a proprietary driver.

I have a copy of it in /home/gsky/driver.tar.gz

Stuck at this point.

---

### Post by perspectoff on 2012-04-16
IOGear has a very inexpensive KVM switch that does exactly what you are describing for about $31.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417](http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417)

I have done that for about a decade (I use that device with an Ubuntu system without a problem).

It's not particularly eco-friendly to run 2 computers at the same time, but it works pretty well. Plus, if one computer is a server that is never turned off, and the other is a Windows computer you only use occasionally, it's a very nice solution.

Virtual machines are painfully slow, in general, unless you have really high-end computing power.

---

### Post by Boyntonstu on 2012-04-16
> **perspectoff said:**
> IOGear has a very inexpensive KVM switch that does exactly what you are describing for about $31.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417](http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417)

I have done that for about a decade (I use that device with an Ubuntu system without a problem).

It's not particularly eco-friendly to run 2 computers at the same time, but it works pretty well. Plus, if one computer is a server that is never turned off, and the other is a Windows computer you only use occasionally, it's a very nice solution.

Virtual machines are painfully slow, in general, unless you have really high-end computing power.

Thanks, looks like a good solution.

Another possible complication, I use a Microsoft USB headset.

I would need to switch between the 2 USB ports.

---

### Post by perspectoff on 2012-04-16
That device has USB cables, too.

I haven't tried that part, though.

---

### Post by forrestcupp on 2012-04-16
> **Boyntonstu said:**
> Thanks.

My problem is that 11.10 is not connecting to the wifi adapter.

I believe that I would need to run 11.10 in the VM of windows to have connectivity.

Correct?

You're right about this. If your wifi works in Windows, it should work in Ubuntu running in a VM. Programs like VirtualBox and VMware use virtual hardware, including wifi, that will work fine in Ubuntu. So Ubuntu will detect the virtual wifi hardware that works with Ubuntu, and not your real wifi that doesn't work in Ubuntu. Like I suggested earlier, you would be much better off using Windows for your host OS and Ubuntu as the guest, if you're not going to have a dual boot setup.

---

### Post by Boyntonstu on 2012-04-16
> **perspectoff said:**
> That device has USB cables, too.

I haven't tried that part, though.

This manual switch is cheap:

2 Port USB KVM VGA Switch Box Hub Adapter for Keyboard Mouse VGA Monitor

[http://tinyurl.com/87vs6vb](http://tinyurl.com/87vs6vb)

[http://www.ebay.com/itm/2-Port-USB-KVM-VGA-Switch-Box-Hub-Adapter-for-Keyboard-Mouse-VGA-Monitor-/320844116345?pt=COMP_EN_Networking_Components&hash=item4ab3ccb179#ht_1200wt_928](http://www.ebay.com/itm/2-Port-USB-KVM-VGA-Switch-Box-Hub-Adapter-for-Keyboard-Mouse-VGA-Monitor-/320844116345?pt=COMP_EN_Networking_Components&hash=item4ab3ccb179#ht_1200wt_928)


and:
[http://tinyurl.com/cwovdes](http://tinyurl.com/cwovdes)

	
2 Port USB KVM VGA Switch Box Hub Adapter for Keyboard Mouse VGA 
For the USB headset

[http://www.ebay.com/itm/2-Port-Sharing-Switch-for-Printer-Scanner-USB-A-B-Cable-/300611700426?pt=LH_DefaultDomain_0&hash=item45fdda86ca#ht_1771wt_970](http://www.ebay.com/itm/2-Port-Sharing-Switch-for-Printer-Scanner-USB-A-B-Cable-/300611700426?pt=LH_DefaultDomain_0&hash=item45fdda86ca#ht_1771wt_970)

---

