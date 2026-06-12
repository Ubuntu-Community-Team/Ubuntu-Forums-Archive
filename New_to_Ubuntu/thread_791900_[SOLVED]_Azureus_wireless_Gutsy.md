---
title: "[SOLVED] Azureus wireless Gutsy"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Pnkmaggt on 2008-05-12
I just downloaded azureus and it is starting up fine and everything, however Im not sure how to make sure im using/opening the right ports because it 1) wont update and 2) wont pass the connection test . . . 
I have a Dell Latitude D820 running Gutsy Gibbon
I also have firestarter installed, however even when im not running it azureus wont work, AND i tried to make sure that the ports were open or accessible on firestarter but im not sure if i did it correctly

This might be a repost but i couldnt find anything that quite fit what i needed but if you have anything i should look at that might help please send me a link!
thanks!

---

### Post by hyper_ch on 2008-05-12
> **Pnkmaggt said:**
> I also have firestarter installed
There we have the problem... do you have any reason to install firestarter?

> **Pnkmaggt said:**
> however even when im not running it
Firestarter is not a firewall but a frontend for iptables and iptables runs the whole time... so, it does not matter if firestarter is running...[/QUOTE]

---

### Post by Pnkmaggt on 2008-05-12
The person who steered me towards linux said that I should have it . . .   So  i guess ill just give it an uninstall and see how that goes

---

### Post by Pnkmaggt on 2008-05-12
Ok well after a quick uninstall im still not getting any response from azureus.

the updater is still stuck on 0%.

im trying to do this on wireless, but it use to work back when i was on M$ stuff so im thinkin it must be my ports or something
When i test the NAT/Server Port i get this:

Testing port 60000
NAT Error - Connect attempt to 70.63.23.197:60000 (your copmuter) timed out after 20 seconds. THis means your port is probably closed.

Does gutsy come with a firewall somewhere that i wasnt aware of? i need to open this up or soemthing

---

### Post by suprfish on 2008-05-12
Do (in a terminal)
```
$  ufw
```
and if it replies with a usage list do
```
$  sudo ufw status
```
and if it's enabled then
```
$  sudo ufw disable
```

Then try azureus again (ufw stands for 'Uncomplicated Firewall')

EDIT:
> **Pnkmaggt said:**
> Does gutsy come with a firewall somewhere that i wasnt aware of? i need to open this up or soemthing
Did not see this; UFW is shipped with Hardy, not Gutsy, so you can probably ignore the above. Iptables is a firewall that comes with Gutsy, infact it is part of the Linux kernel. It is pre-configured, but it shouldn't be interfering with Azureus... Firestarter is the UI to making configuration changes to iptables, reinstall it (firestarter), open it up, and try again with Azureus. Examine the log messages output...

Other suggestions: check your modem, try other bittorrent clients (Deluge, Transmission)

---

### Post by Pnkmaggt on 2008-05-12
Well the thing is im running gutsy so that command doesnt work . . .

---

### Post by suprfish on 2008-05-12
> **Pnkmaggt said:**
> Well the thing is im running gutsy so that command doesnt work . . .

see edit, sorry

---

### Post by Pnkmaggt on 2008-05-12
ok well i have firestarter back on, and its not showing that its blocking anything.  If i had to pick a port ( say 60000 ) what all would I have to do to firestarter to get it configured properly to allow azureus to work with it?

***
So i decided to just go with deluge lol . . . it seems to work just fine, and if what im reading is correct, then hopefully it uses less cpu/ram anyway 

ty!

---

