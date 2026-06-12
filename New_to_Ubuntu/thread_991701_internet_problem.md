---
title: "internet problem"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by ja660k on 2008-11-24
there is probably an easy fix to this but, what happened is i installed another network manager; and it didnt work properly so i got rid of it...

and what i think has happened is it has got rid of ubuntu's knetwork manager; 

so i have a laptop with no internet at all.
wireless/ wired

can anyone help me get this back?

my laptop doesnt have bluetooth or any other connectivity
so downloading onto my pc and sending it is a no no

and to make matters worse i cant find 8.4 cd =( 
i have the previous one, before 8.4

please help

---

### Post by porchrat on 2008-11-24
You can either do it through synaptic package manager (you'll find this under "System -> Administration -> Synaptic package manager" menu) or you can do it through the console using apt-get.

I think for you the easiest thing to do would be to use the synaptic package manager as it is a little more user-friendly.

What you do is open synaptic package manager and press the binoculars icon in the top middle of the window.  It should open a search text box.  In there type "network-manager-gnome".  It should bring up only one entry, click on the checkbox next to the name and then select "mark for installation".  It should then tell you that you need to install "network-manager" in addition to "network-manager-gnome" and when you press ok it will mark them both for installation.  You should double check though by doing another search for "network-manager" just to check that that is marked for installation as well.

Then click "apply" and it will install all those things.  Restart and you will be good to go again.

Please note this only works if you are running ubuntu and not kubuntu.

---

### Post by ja660k on 2008-11-24
i dont have the internet at all...
well i do but i dont have a manager to manage it

not the manager doesnt pop up

i dont have it
i cant download things from the ubuntu respo if i dont have the net

=(

i tried burning knetworkmanager to cd then putting it onto my laptop and compiling it
but that doesnt work either i get an error

```

checking how to run the C++ processor "/lib/cpp" fails sanity check
See config.log for more details

```

---

### Post by porchrat on 2008-11-24
As long as you didn't completely uninstall or purge it the packages should still be on your drive.  You shouldn't need to download them, hence you shouldn't need an internet connection.  Just give it a try and find out.

Another way is to just get the internet running without the network manager by altering the configuration file /etc/network/interfaces

If you want to do that then please let me know how you connect to the internet (i.e. do you use a router? and whether or not that router uses DHCP)

If you connect to the internet through a DHCP enabled router then you only need to add 2 lines to the /etc/network/interfaces file:

```
auto eth0
iface eth0 inet dhcp
```

That should give you an internet connection so that you can download the network-manager.

If for some reason your package cache has been purged and you don't want to mess with configuration files then you'll either have to get another ubuntu ISO from a friend and install it from there or you'll need to go to a friends place that has 8.04 installed on his system and download it to his drive (instead of installing it) then put it on a flash drive and install it at home.

Please note though that if you do this you'll need both the frontend (network-manager-gnome") and the network-manager.

---

### Post by ja660k on 2008-11-24
i think its gone...
when i type knetwor then tab into terminal it doesnt auto complete 
and it says 
```

-bash: knetworkmanager: command not found

```

i try to apt-get install
it doesnt work, it says 
```

could not resolve 'au.archive.ubuntu.com 
failed to fetch http://au.archive.ubuntu...etc

```

if i download ubuntu 8.4 again and insert it to the laptop and go to sympatic then change the sources to the cd? then that way can i install it?
i think it should be in the cd

---

### Post by porchrat on 2008-11-24
> **ja660k said:**
> i think its gone...
when i type knetwor then tab into terminal it doesnt auto complete 
and it says 
```

-bash: knetworkmanager: command not found

```

Why are you trying to install "knetwork"?  if you are running normal ubuntu you need "network-manager" and "gnome-network-manager".  Are you running Kubuntu?

> i try to apt-get install
it doesnt work, it says 
```

could not resolve 'au.archive.ubuntu.com 
failed to fetch http://au.archive.ubuntu...etc

```

Makes sense as you don't have a network connection and hence you don't have an internet connection.

> if i download ubuntu 8.4 again and insert it to the laptop and go to sympatic then change the sources to the cd? then that way can i install it?
i think it should be in the cd

Yes that is what I meant when I said that you could use the 8.04 CD.  Sorry if I didn't make myself clear.  That is at this point probably your best option.

However before you try that please copy and paste the ouput of this command into the thread:
```

cat /etc/network/interfaces
```

---

### Post by Sealbhach on 2008-11-24
Try connecting your wired ethernet connection with this:

```
sudo dhclient eth0
```

See if it connects you up to the net.

.

---

### Post by porchrat on 2008-11-24
By the way please note that this is all assuming your ethernet device is called "eth0".  If for some strange reason you have named it something else then please replace "eth0" with whatever you decided to call your ethernet device.

It is also best that you use an ethernet cable (as opposed to wireless etc.) until you get everything up and running again.  That is why we are all telling you to start with "eth0".

---

### Post by ja660k on 2008-11-25
```
sudo dhclient eth0
```

did the trick i can now use sympatic n get what i needed.. as for knetworkmanager

i dont know why i have it

and no i dont have kununtu


thanks for all your help

---

### Post by porchrat on 2008-11-25
Awesome hope you come right with reinstalling your original packages.  Please mark the thread as solved.

---

