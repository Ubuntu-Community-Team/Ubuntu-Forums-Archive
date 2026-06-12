---
title: "Speed up internet - does this tweak still apply for Ubuntu 8.04?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-01
Found this ipV6 tweak from an old post [_here_]("http://ubuntuforums.org/showthread.php?t=202838").

Do we need to do it for Hardy Heron with Firefox 3?

> [COLOR="Blue"]Basically you disable ipV6 which apparently conflicts with ipV4, I'm no expert on the whys or hows but like I said, it worked for me.

1. Open your Gnome Terminal/ KDE Konsole and type :-
For Gnome

Quote:
gksudo gedit /etc/modprobe.d/aliases  

or For KDE

Quote:
kdesu kate /etc/modprobe.d/aliases  

2. Kate or Gedit will open and show you this file :-
(scroll down to see what to copy and paste)


Quote:
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here. 
alias ipv6 off --
#alias net-pf-10 ipv6 =========comment (put #) the original line
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet  

3. Now "Save" and "Reboot" 

There's another way too: instead of changing aliases file, create fie named bad_list in /etc/modprobe.d containing this line:


Quote:
alias net-pf-10 off  

This method will work even if /etc/modprobe.d/aliases get replaced at some update.[/COLOR]

---

### Post by sujoy on 2008-05-01
you do not probably NEED to do it, but IMO its better, ipv6 aint needed for the moment and i have seen that generally disabling it improves the performance

---

### Post by BB_DaKraxor on 2008-05-01
Some say disabling ipv6 speeds up internet. If you're a believer too, you should do the tweak. It's regardless to the distro you're using because most distros have ipv6 enabled by default.

---

### Post by Fate Reconciled on 2008-05-01
IPv6 is still enabled by default in FF3 as well. Both tweaks still worked like a charm for me. :grin:

---

### Post by cartisdm on 2008-05-01
I did that a while ago, but I've since re-installed.  Honestly I haven't really noticed any difference but I could just be oblivious.  Anybody have any actual evidence that this boosts the speed up at all?

---

### Post by Fate Reconciled on 2008-05-01
Not as far as I know, except what the eye can see. Maybe someone should research this.

---

### Post by nowshining on 2008-05-01
it's more appearant with dial-up users than it is other higher speed users of the WWW. Alos the speed is more apparant for those running older processors than those with the new higerspeed ones.

---

### Post by cubeist on 2008-05-01
> **Fate Reconciled said:**
> IPv6 is still enabled by default in FF3 as well. Both tweaks still worked like a charm for me. :grin:

Yes, worked well for me too.  ipv6 was still slowing down the initial loading of pages by a few seconds...

---

### Post by Sealbhach on 2008-05-05
Just done this tweak, there's a very big improvement in speed, especially page loading.

I'm using a dial up wireless usb modem so for me it's making a very big difference.


.

---

### Post by pacrep on 2008-05-06
Also Satellite connection, makes a good difference for me.

---

### Post by drs305 on 2008-05-14
Hardy, AMD 64 bit, 6.0 DSL: This made a noticeable difference in the initial page loading times on my machine. I changed the settings as soon as I installed Hardy and noticed the delays.

---

### Post by Adola on 2008-11-18
Ummm, I can verify that it DOES work for 8.10 Kubuntu

I have a connaxan modem. SOooo. OF THE FEW THINGS THAT COST!
Linuxant provides a SUCKY free driver!  So, I'm limited to 14k.

(I don't even get that) 
BUT, I seen a DRAMATIC increase for some reason.

not only that, because of those Oh-so great pains of dial-up!
Pidgin USED to hate itself and me!

But now, we can be friends.

Thanks for this tip. :D

---

### Post by luca_blight13 on 2009-03-10
this works for me too! I have a DSL connection and the speed improvement of my browser's display is so obvious..

---

### Post by Bölvaður on 2009-03-10
I tried it and took the times.
For my computer (dual e7600 core and okish adsl connection) I lost about 0.2 seconds on every page load, with few exceptions.
Exception 1. a preloaded page loads up 1 second faster
Exception 2. ubuntuforums loaded 1.2 seconds slower

other than those two it was always 0.2 slower after the change.

Im going back and taking down the times again and report if they do not get into the original times.
*added*
went back and it seems very unreliable imo, too unstable loading time to know if it is faster or slower now. It is both way faster and way slower than both after turning ipv6 off, before that and after I changed back to original settings.

---

### Post by spcwingo on 2009-03-10
Wouldn't it be easier to just open Firefox, type about:config in the address bar, and then type ipv6.  Change the value from false to true then restart Firefox.  This accomplishes the same thing...just easier.

---

