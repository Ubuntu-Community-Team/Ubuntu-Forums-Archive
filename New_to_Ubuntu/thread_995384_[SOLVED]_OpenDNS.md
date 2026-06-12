---
title: "[SOLVED] OpenDNS?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-11-27
I'm trying to get OpenDNS working in Ubuntu 8.10 as my router doesn't support a custom DNS so I tried following the Ubuntu guide on [there website]("https://www.opendns.com/homenetwork/start/device/ubuntu") but I type the command

```
gksudo network-admin
```

and I get presented with a box asking for  the root password which I enter correctly and then nothing happens?

Thanks in advance!:guitar:

---

### Post by mike555 on 2008-11-27
I don't know what router you have, but you should be able to set it to use the numbers OpenDNS gives you...... or you could just set your computer to use their numbers in ubuntu , just go to; system,administration, network, (unlock with your password) DNS tab , delete the numbers that are in DNS servers box , and add the OpenDNS numbers .......

---

### Post by kamitsukai on 2008-11-28
> **mike555 said:**
> I don't know what router you have, but you should be able to set it to use the numbers OpenDNS gives you...... or you could just set your computer to use their numbers in ubuntu , just go to; system,administration, network, (unlock with your password) DNS tab , delete the numbers that are in DNS servers box , and add the OpenDNS numbers .......

As I've said above I'm using Ubuntu 8.10...there is no "network" in the admin menu

---

### Post by Sealbhach on 2008-11-28
> **kamitsukai said:**
> As I've said above I'm using Ubuntu 8.10...there is no "network" in the admin menu

It may be you don't have Metwork Manager installed. 

I would suggest going into Synaptic and searching for it. If it's not installed, install it. 

Unless you're using wicd?
.

---

### Post by kamitsukai on 2008-11-28
> **Sealbhach said:**
> It may be you don't have Metwork Manager installed. 

I would suggest going into Synaptic and searching for it. If it's not installed, install it. 

Unless you're using wicd?
.

all installed

---

### Post by Sealbhach on 2008-11-28
But it's not in your menu?


.

---

### Post by kamitsukai on 2008-11-28
> **Sealbhach said:**
> But it's not in your menu?


.

Not that I can see unless it's "network tools" but that doesn't have a DNS tab

---

### Post by bhadotia on 2008-11-28
Right click on the NetworkManager icon (nm applet) on the right side of the top panel and select "Edit Connections" and then configure the ipv4 settings for your connection.
There also a menu for that in the System>Preferences.

---

### Post by kamitsukai on 2008-11-28
> **bhadotia said:**
> Right click on the NetworkManager icon (nm applet) on the right side of the top panel and select "Edit Connections" and then configure the ipv4 settings for your connection.
There also a menu for that in the System>Preferences.

I'm still pretty nooby at this could you explain what goes in the boxes and things:confused:

---

### Post by bhadotia on 2008-11-28
> **kamitsukai said:**
> I'm still pretty nooby at this could you explain what goes in the boxes and things:confused:

Change the method to manual or Automatic (DHCP) addresses only.
In the first case (manual) you will have to add the IP address, Subnet Mask, and Default Gateway in the appropriate fields in the addresses box after clicking Add button on the right. And then add the OpenDNS servers in the DNS servers field. 
In the second case (Automatic (DHCP) addresses only). You will only have to fill the DNS servers field with the required addresses (208.67.222.222,208.67.220.220).
You would probably want to go with the first option if you use a static IP address, or, if you use DHCP follow the second option.

---

### Post by kamitsukai on 2008-11-28
Ok trying the second option (screenshot below) do i have to restart now or should it just work after clicking close?

---

### Post by Sealbhach on 2008-11-28
What I did was follow the instructions on the Open DNS page and it worked fine:

[https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

> To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

   ```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```

    ```
gksudo gedit /etc/dhcp3/dhclient.conf
```

    
# append the following line to the document

    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    
# save and exit

   ```
sudo ifdown eth0 && sudo ifup eth0 
```


.

---

### Post by bhadotia on 2008-11-28
> **kamitsukai said:**
> Ok trying the second option (screenshot below) do i have to restart now or should it just work after clicking close?

It works instantaneously on my laptop (sometimes I disconnect and then reconnect to make sure) but I don't know about router.

---

### Post by kamitsukai on 2008-11-28
Is there a site you can visit to check if it's working?

---

### Post by bhadotia on 2008-11-29
> **kamitsukai said:**
> Is there a site you can visit to check if it's working?

[http://welcome.opendns.com/]("http://welcome.opendns.com/")

---

### Post by kamitsukai on 2008-11-29
> **bhadotia said:**
> [http://welcome.opendns.com/]("http://welcome.opendns.com/")

didn't work:(

---

### Post by bhadotia on 2008-11-29
> **kamitsukai said:**
> didn't work:(

What does it say?

EDIT:
Did you create the openDNS account (step-2 in the tutorial at their website).

---

### Post by kamitsukai on 2008-11-29
> **bhadotia said:**
> What does it say?

EDIT:
Did you create the openDNS account (step-2 in the tutorial at their website).

site tells me it's just not working and yep I created an account

**_***EDIT***_**
I Never removed the Hash symbol from the line in the dhclient.conf file:oops: Thanks again for your constant patience!!:lolflag:

---

### Post by bhadotia on 2008-11-30
> **kamitsukai said:**
> site tells me it's just not working and yep I created an account

**_***EDIT***_**
I Never removed the Hash symbol from the line in the dhclient.conf file:oops: Thanks again for your constant patience!!:lolflag:

Great! Please mark the thread as solved now.

---

