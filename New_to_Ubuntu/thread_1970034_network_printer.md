---
title: "network printer"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Old Old Duffers on 2012-04-30
[COLOR="Red"]FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.[/COLOR] Help.  This is what I get when I try to enable my network
printer.  What do I do now???  Using 12.4 (gnome classic)

---

### Post by Ms. Daisy on 2012-05-01
We'll need some more information.  What kind of printer is it? You've got it plugged into the router?  Did you follow any tutorials or guides? If so, where did you get this error?

---

### Post by disc9 on 2012-05-17
I got the same useless error. My network runs machines that use Ubuntu 11.4 and have an existing, working Canon printer however a new 12.4 based box cannot see the network printer and thus the error message. Note, all machines run Gnome Classic but I doubt that is relevant.

---

### Post by phalantice on 2012-10-14
Its saying a service isnt running.  you cant get far enough to tell it what printer daisy.   in my case its a xerox 4400 that is connected to the same switch.  its not a network issue its a bug in the printer system.

---

### Post by phalantice on 2012-10-14
> **Old Old Duffers said:**
> [COLOR=Red]FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.[/COLOR] Help.  This is what I get when I try to enable my network
printer.  What do I do now???  Using 12.4 (gnome classic)

go to [http://localhost:631/](http://localhost:631/)   you should be able to directly add a printer through the cups web interface.


duffers have you tried the printer thing in that unity thing?  Im using gnome classic/cinimun as well.  12.4 32 or x64?

disk9 same info plz I wonder if we are being hit with a bug because we dont use the default

---

