---
title: "Dual boot"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Gorganteris on 2008-08-07
Hello, i am a linux beginner so sorry for the noob question. I want to make a dual boot, kubuntu+windows xp SP2. How can i do that? Can you please tell me the steps.
Thanks very much in advance!

---

### Post by Elfy on 2008-08-07
Firstly welcome to the forum.

I would be inclined to have a read of these, when you have specific questions come back - generally it is quite painless and fairly easy to accomplish.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) This does deal with installing ubuntu but the steps for the install are the same - maybe a different look though.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Good luck - when you come back with questions, try and gather enough information and be succinct with your problems and the answers will be easier to arrive at :D

---

### Post by Gorganteris on 2008-08-07
Thanks for the quick reply. But i haven`t managed to install linux with windows already on it. That documentation you`ve provided me says "How to instal linux and windows with linux already installed on it". The second link explains for Ubuntu and i`ve asked for Kubuntu. I tried to install it but i don`t know what to do when i reach the partition manager in Kubuntu. I tried the first option and nothing. It says that i need to specify the root folder. Please help me because i need to install Kubuntu on windows quick. 
Thanks!

---

### Post by snowpine on 2008-08-07
The instructions are the same for Kubuntu and Ubuntu, and I would recommend taking your time and educating yourself, rather than doing it as quickly as possible. :)

---

### Post by Elfy on 2008-08-07
On the apcmag page there is a dropdown menu - where you can choose the permuatation.

To specify root partition you have to edit the partition and choose a mountpoint of /

Howewver you need to be very careful that you choose the correct partitions or you could install over the top of the xp install.

Did you not get the option to resize the xp partition.

---

### Post by sandysandy on 2008-08-07
defragment ur windows.

then using gparted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) u can resize ur windows partition. 

in the free space generated, u can create additional partitions.

create at least two partitions.

first partition for root ( [COLOR="Red"]/[/COLOR] )

second partition for [COLOR="Red"]SWAP[/COLOR].

after u finish, u can boot into ubuntu live Cd and follow installation procedure.

regards

---

