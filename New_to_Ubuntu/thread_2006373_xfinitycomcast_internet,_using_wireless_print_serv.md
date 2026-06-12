---
title: "xfinity/comcast internet, using wireless print server"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by anewguy on 2012-06-19
We just updated to xfinity/comcast broadband from the old DSL last week.  The result is that the router for the DSL used to be in the office, so the printer was connected to an ethernet port on that router.  Now that router is no longer in use, and the xfinity/comcast "box" (cable modem/wireless router/phone) had to get installed at the cable connection by the main TV as there is no cable in the office and the easiest install for both cable and phone was by the main TV.

So, I go to Ebay and pick up a Dell 3300 wireless print server (it's a Dell 1600n, so I'm hoping Dell's print server will support it).  I dual boot with Windows 7 on my desktop, so I used Windows to try to config the device.  I had to change the encryption on the router as the printer server only supports WEP (yuck!) or WPA-PSK.  The print server never gets connected to the network.  I don't know if perhaps there is a firewall issue on the PC, or a firewall issue on the router, or if I have to do some kind of port forwarding but keep it to the local network.  Since I don't know how to try to set this up in Ubuntu (it's an USB device, so wine shouldn't work), so I've been using Windows and the Dell software to try to set it up.

So, this a combination Ubuntu and Windows question:

- does anyone know how to make this device actually find/connect to the network?

- I believe in Windows it requires a special driver - does anyone know if this can be made to work in Ubuntu?  I personally don't use the printer - I have my own here in the basement that is wireless but works (HP).


any ideas/help on this would be greatly appreciated!

Thanks in advance!
Dave ;)

p.s. - I also ordered some power line networking adapters off Ebay with the HOPE that if the wireless print server doesn't work hopefully the power line adapters will.

---

### Post by anewguy on 2012-06-22
OK, I tried the powerline adapters on the same circuit, just plugging one in to my laptop and the other in to my desktop and turned the wireless off on my laptop.  Sure enough, both computers can see each other, share things (when I enabled sharing, of course, to test).  Tried it again but this time with the printer on a different circuit upstairs and my desktop here in the basement.  Alas, can't see the printer.  I did, however, check and I noticed it's not using IPv4 or IPv6, so I *think* I'll need to connect the one I'm testing with on my desktop into the router upstairs before it will show up.  I need to set the IP address, etc., like I did before.  

BTW - yes, the printer is network enabled.

---

