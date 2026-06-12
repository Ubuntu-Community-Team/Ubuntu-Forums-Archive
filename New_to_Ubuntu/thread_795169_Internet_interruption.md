---
title: "Internet interruption??"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by thejeremyking on 2008-05-15
I am brand new to using ubuntu.

I have a Brother MFC-5840CN printer/scanner/copier/fax machine that uses ethernet connection.  

I have previously used it connected via ethernet to my router, and then my Windows and Mac machines would just automatically detect it on the network and use it.  

Now if I even connect the ethernet cable from the MFC to the router, my internet connection to my ubuntu machine drops out.  my windows and mac machines still connect... :confused::confused:

I'm hoping somebody here knows what to do??

And then once that's squared away, how do I go about installing the MFC so that my ubuntu machine can use the printer/scanner??

Thanks!

---

### Post by OffAxis on 2008-05-15
What are the IP's of your MFC and your ubuntu machine?
There's probably a conflict with the same address being assigned to both.

you should be able to check both IPs in the router setup page (192.168.0.1 or 192.168.1.1 most likely).

```
ifconfig
```
will tell you the IP of the ubuntu box from the command line.

If you set both machines to 'Obtain Address Automatically from DHCP' then the router will sort it out (usually). 

You can manually assign addresses if need be; on the ubuntu box it's under System Settings and the MFC you should be able to assign from the panel.

---

### Post by Paqman on 2008-05-15
I'd start by going to the router's control panel and checking the devices attached to your router before and after connecting the printer. Do you use dhcp, or have you got static IPs?

---

### Post by thejeremyking on 2008-05-15
I'm using DHCP-- it seems they both want to use 192.168.0.10.

How do I tell the ubuntu box to take 192.168.0.13?? (11 and 12 go to my windows and mac).

thanks

---

### Post by Paqman on 2008-05-15
> **thejeremyking said:**
> 
How do I tell the ubuntu box to take 192.168.0.13?? (11 and 12 go to my windows and mac)

You should be able to assign a set IP to your Ubuntu machine from your router's control panel. Exactly how depends on what brand of router you've got.

---

### Post by thejeremyking on 2008-05-15
I'm using a Netgear gateway from comcast.  unfortunately, comcast put in their own custom interface for the router settings which pretty much cripples it, so there's no way I can find to manually assign addresses from the router.  

Is there some option in ubuntu networking preferences that can tell it to request a certain address??

---

