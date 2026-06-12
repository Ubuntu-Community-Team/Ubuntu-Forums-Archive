---
title: "Toshiba Satellite: No internet connection on 10.04"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by shemdroid on 2012-02-02
OK I have a Toshiba satellite c655d-s5130 laptop. I am running win ultimate on duel boot with Ubuntu 10.04.3. 
I have located and installed hot the wireless (realtek) driver and the Ethernet (atheros) driver using ndiswrapper.  In the in the windows wireless drivers app it accepted both drivers and shows hardware present: yes.
I have been scouring the forums for a clue weeks trying different things. I couldn't even tell you what I've tried but its been a lot. 
using sudo lshw .... something or other (lol) it shows both pieces of hardware as network UNCLAIMED.
this is the only version of Linux j have been able to install and run without freezes etc. so please help cuz without wifi it with be just windows till I get a new laptop and that won't be anytime soon :(

---

### Post by wolfen69 on 2012-02-02
Please post the output of
```
sudo lshw -C network
```

---

### Post by shemdroid on 2012-02-02
shemdroid@shemdroid-laptop:~$ sudo lshw -C network  
   *-network UNCLAIMED      
        description: Network controller  
        product: Realtek Semiconductor Co., Ltd.  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: ioport:3000(size=256) memory:d0200000-d0203fff  
   *-network UNCLAIMED  
        description: Ethernet controller 
        product: AR8152 v2.0 Fast Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        version: c1  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress vpd bus_master cap_list  
        configuration: latency=0  
        resources: memory:d0100000-d013ffff ioport:2000(size=128)

---

### Post by shemdroid on 2012-02-02
also the only other solid thing i know right off hand is  when i   iwconfig   it shows 
lo        no wireless extensions.

easytether0  no wireless extensions.
easytether is how im online. im using my phone to pick up the wireless signal and tethering it to my ubuntu via usb.   uhg, its slow and its a hassle ya know!?

---

### Post by wolfen69 on 2012-02-02
What does it say in *Additional Drivers*?

---

### Post by shemdroid on 2012-02-02
as of yet it hasnt detected any proprietary drivers nor do i have any installed.  is that what you mean?

save the 2 i manually loaded with ndiswrapper.

---

### Post by 3rdalbum on 2012-02-02
Did you try Additional Drivers BEFORE you used Ndiswrapper?

My understanding is that Ndiswrapper doesn't always work, and it will certainly stop native Linux drivers from attaching to the hardware.

Try removing Ndiswrapper completely and then see what Additional Drivers says.

Ubuntu 10.04 is kinda old. It simply might be too old to have the driver you need. Have you tried the latest Ubuntu, 11.10?

---

### Post by shemdroid on 2012-02-02
k, ill try deleting ndiswrapper.  11.10 freezes up as soon as the gui loads, same with mint12, same with fedora 14 or was it 16, idk the newest one.  opensuse 12.1 loads and works for the most part but no networking on that one either. 

ok, ndiswrapper is gone, additional drivers says nothing



is there a terminal command to turn the network card on?? i suspect that may be the problem with the wireless anywho or part of it.  as for the ethernet idk

---

### Post by shemdroid on 2012-02-02
OK THIS MAY HELP!   
I just tried to run the installer for opensuse 12.1 and at the network card setup it showed both cards and it said the link was disconnected on both of them.  is that an IP link perhaps? could this be my problem?

---

### Post by wolfen69 on 2012-02-03
> **shemdroid said:**
> OK THIS MAY HELP!   
I just tried to run the installer for opensuse 12.1 and at the network card setup it showed both cards and it said the link was disconnected on both of them.  is that an IP link perhaps? could this be my problem?

Opensuse does things a little differently, so I can't really speak about it. But as of now, it seems like your computer is linux incompatible if all of those distros are having major problems on your hardware. I wish I could be of more help, but hopefully someone else can shed some light on this.

---

### Post by shemdroid on 2012-02-03
hopefully, I don't I tend to give up just yet

---

### Post by shemdroid on 2012-02-03
ideas anyone???

---

### Post by shemdroid on 2012-02-10
upgraded to ubuntu 10.10 and did these commands:
```

sudo add-apt-repository ppa:lexical/hwe-wireless sudo apt-get update sudo apt-get install rtl8192ce-dkms


```

---

