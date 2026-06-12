---
title: "how to set up wireless network with wpa"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by codixion on 2012-11-03
Hi everyone,

I want to set up a wireless connection with ubuntu 12.04 .
My my wireless card is not compatible so i used the ndiswrapper to install a windows driver.
I have searched the net for two days now and have got very confused.
The security of the router is WPA/WPA2-PSK with AES.

What do i write in etc/networks/interface?
What is the wpa_supplicant and what should i write in there?
And finally after i edit all these what are the commands to connect?

I don't have GUI, so everything is in terminal.

Any help would be very appreciated because i am very confused.

Thank you.

---

### Post by squakie on 2012-11-03
Instead of getting ahead of what you may not need to do, have you:

[LIST=1]
[*]enabled wireless under the network manager drop down?
[*]in network manager, deleted the existing definition for connecting to the old via Edit Connections?
[*]tried connecting to the network?  It should ask for the wpa passphrase/password you defined at the router - just enter it.
[/LIST]

---

### Post by codixion on 2012-11-03
But I don't have GUI.
Everything has to be done through terminal.

This is the problem.

Can I install network manager and use it through terminal?

---

### Post by squakie on 2012-11-04
Oops - missed that in your original post - sorry.  Are you running a server or is there another reason you don't have a gui?  At any rate, text mode would require some of those edits, I just don't know enough to help beyond that.  Good luck!  ;)

---

### Post by squakie on 2012-11-05
I'm not positive, but looking at the man page for iwconfig, it would appear your definitions go through there.

After that, I *think* you do ifup.  I don't think you have to do anything with wpa-supplicant - I think the configuration is actually part of iwconfig.

---

