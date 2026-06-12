---
title: "Pre GDM Login window"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by jombeewoof on 2008-07-03
I don't know what I did to enable it, but just prior to GDM loading there is a screen with the "human" look with a dialog box in the middle that have all of the different IP's associated with my box.

I can get a pic if neccesary, but it's like the system is asking me to log on to a particular box, but all 3 options are just different interfaces on the same machine.

if it matters the interfaces are eth0 eth1, and vmnet1

---

### Post by bab1 on 2008-07-04
Do you have multiple NIC's in this host?  It appears so.  In addition they are on different networks.  I guess the question is why?  What are you trying to accomplish?

-BAB1

---

### Post by jombeewoof on 2008-07-04
> **bab1 said:**
> Do you have multiple NIC's in this host?  It appears so.  In addition they are on different networks.  I guess the question is why?  What are you trying to accomplish?

-BAB1

Yes I do have multiple nic's

eth0 192.168.0.101 this is my main network and leads to the internet
eth1 192.168.87.1 connects to a couple of units in my closet that are mostly for backups.
wlan0 192.168.0.102generally unused
vmnet1 192.168.14.1 vmware virtual interface

I am trying to accomplish not having to see that screen prior to logging in.

---

### Post by kornhead127 on 2008-07-04
system -> administration -> Login Window

Click the 'Remote' tab and disable remote login.

---

### Post by bab1 on 2008-07-04
Why do you need 3 nic's?

---

### Post by jombeewoof on 2008-07-04
> **kornhead127 said:**
> system -> administration -> Login Window

Click the 'Remote' tab and disable remote login.

Thank you

---

### Post by jombeewoof on 2008-07-04
> **bab1 said:**
> Why do you need 3 nic's?

I guess I'm obsessively organized. 

The main one is there to keep the box online, the secondary one is to keep my backups separate from my main network, the wireless is basically just extra, while the vmware adapter comes standard with vmware workstation 6. 

I could have made the guest OS part of my primary network, but I didn't like that idea, they'll just be test boxes no need to let them out of their sandbox.

---

### Post by bab1 on 2008-07-04
Oh.  I think you are needlesly complicating things.  In essense you are using your main machine as a router to the other hosts.  This means you are backing up across networks as well as between hosts.  But, if the solution kornhead127 suggested works and your networks are happy, the great!

Having said that, I would bridge the VMware interface virtually (no external NIC) and put all the hosts on the same network.  The main host should only have 1 NIC. Multi-homed hosts are a bad thing. Use a proper router to place hosts on different networks.

Just me though, whatever works for you.  :-)

---

### Post by jombeewoof on 2008-07-06
> **kornhead127 said:**
> system -> administration -> Login Window

Click the 'Remote' tab and disable remote login.

So I finally rebooted my pc after doing this, and now the screen comes up, but there is nothing to log into. 

I have to drop to a new terminal with ctrl+alt+F1 then stop gdm, then startx to get back into my gui.

If I try to open the login manager again, it tells me I don't have gdm running. While technically correct, this is a bit of a pain in the ***.

If I start gdm, it tells me I have X already running, also correct and it will start a new gdm session on vty8 (ctrl+alt+F8)

But that brings me back to the original issue of no machine to log into.


Hmm, I wonder if I just install KDM this will resolve itself and I can just deal with it.

---

