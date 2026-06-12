---
title: "[SOLVED] Is there an Automatic Internet Lock"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Yumpin_Yimminie on 2008-09-23
I was wondering if there was program available that automatically cut network connections .... say when the screensaver activated?

Seems like life happens.  I'll be on the web and something will distract me like a phone call or whatever.  I'll end being gone for quite awhile and then remember the computer is open to the internet.  For the Windows environment I have ZoneAlarm.  But I was hoping for something for the Ubuntu environment.

Thanks much.

Have a Great Day!
Jim

---

### Post by hyper_ch on 2008-09-23
you could run a cronjob every minute that checks of the screensaver if active and if yes then turns of networking.

---

### Post by Tatty on 2008-09-23
I am not sure I quite follow why you want this to happen.

Ubuntu is by default highly secure in terms of firewall, as it leaves nothing open to the outside world.

If you start opening ports for things such as server-applications then you may want to consider configuring iptables, which firestarter can do for you.  

There may be an internet lock option in firestarter, but I cannot remember as I have only used it once.

---

### Post by hyper_ch on 2008-09-23
> **Tatty said:**
> Ubuntu is by default highly secure in terms of firewall, as it leaves nothing open to the outside world.

Wrong!

By default, the firewall is set to let everything pass - the difference is, that no listening services are running. So it's not closed because of the firewall, it's "closed" because nothing is running by default.

---

### Post by terry_gardener on 2008-09-23
i think there us an option in firestarter for internet lock when screensaver activates. 

check out firestarter if you want/need this function.

---

### Post by hyper_ch on 2008-09-23
firestarter will alter your default rules in the firewall...

---

### Post by Tatty on 2008-09-23
> **hyper_ch said:**
> Wrong!

By default, the firewall is set to let everything pass - the difference is, that no listening services are running. So it's not closed because of the firewall, it's "closed" because nothing is running by default.

I did kinda mean that... honest!  lol :)

Im still a little hazy on exactly how this works so i can never phrase it correctly.

---

### Post by hyper_ch on 2008-09-23
it's ok ;) it is confusing ;)

---

### Post by mikewhatever on 2008-09-23
> **hyper_ch said:**
> Wrong!

By default, the firewall is set to let everything pass - the difference is, that no listening services are running. So it's not closed because of the firewall, it's "closed" because nothing is running by default.

Why then if I scan ports with shieldsup ports are reported as closed? Shouldn't the pings or whatever they send pass as well as everything else?

---

### Post by hyper_ch on 2008-09-23
if nothing listens on a port then nothing can return anything ;)

---

### Post by nowshining on 2008-09-23
> **mikewhatever said:**
> Why then if I scan ports with shieldsup ports are reported as closed? Shouldn't the pings or whatever they send pass as well as everything else?

u also want ot disable pings - one can do that thru sysctl it may disable inbound pings but outboung pings work fine, etc.. :)

alas u want stealth not closed...

---

### Post by Kain000 on 2008-09-23
> **mikewhatever said:**
> Why then if I scan ports with shieldsup ports are reported as closed? Shouldn't the pings or whatever they send pass as well as everything else?

Because they are "open" but there is no damon (service) listening for incoming TCP/UDP connections so the outside world can "scream" at your "open ports" all they want but there is noone there to hear them, and thus they cannot talk to anything on the inside.     

on another note, Linux may be pretty secure when compaired to windows or even mac nowadays, but it's always better to run a firewall then to be sorry afterwerd.    Firestarter is the GUI frontend for the program IPtables (firewall) and will help you congigure your firewall.  You can get very specific with firestater or not, but it's a good idea to have a firewall never the less.  You can mess arround with it as you like, like on of the posts above said there may be a feature somewhere in it allowing it to auto lock the connection when the screen saver time out occors.

If you really want to sceduel a CRON event to check for outgoing traffic on your internet port each min, you can use somthing like this:
```
sudo netstat -ntap | awk '{print $4}' | sed -rn '/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:21/p' | wc -l

```
just subsiture 21/p at the end for what ever #/p    # being the internet port (I dont know off hand)

That will tell you if there is traffic going out.  You may just want to write a script telling CRON to lock the connection after a certain timeout just make sure you are happy with the times, as if you are reading something lengthy for example and discover that you suddenly have no connection.

---

### Post by Yumpin_Yimminie on 2008-09-23
Thanks much to everyone that responded!

Have a Great Day,
Jim

---

### Post by mikewhatever on 2008-09-23
So that's the deal, all ports are open and everything is allowed to pass through. Great security model! Thanks for the update.

---

### Post by Tatty on 2008-09-23
> **mikewhatever said:**
> So that's the deal, all ports are open and everything is allowed to pass through. Great security model! Thanks for the update.

Yes, but as pointed out, nothing is "listening", so there are no security isues with this unless you deliberately make something listen.  In which case a firewall is not hard to set up with the GUI firestarter.

---

### Post by nowshining on 2008-09-23
> **Tatty said:**
> Yes, but as pointed out, nothing is "listening", so there are no security isues with this unless you deliberately make something listen.  In which case a firewall is not hard to set up with the GUI firestarter.

not quite true, apps have bugs and if an app has a bug and ur running it without any firewall at all or router it can get compromised and if may allow one to run code ie: buffer overrun, crash the computer, etc.. - a firewall protects or tries to help mitigate that damage if someone unknown tries to crack into the computer..

a tip for the OP is that iptables is a bit diff. that windows firewalls, whereas you won't get asked for each and every program - which would be nice but one must allow the whole port to be open in/out which is bad, but I think there might be a rule to allow by application only, etc.. but i don't know how to do that myself..

---

### Post by hyper_ch on 2008-09-23
> **nowshining said:**
> a firewall protects or tries to help mitigate that damage if someone unknown tries to crack into the computer..

I wonder how a firewall would do that...

---

