---
title: "[SOLVED] I always have to configure wireless"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by duruttye on 2008-11-04
Hey there!

I installed a command line ubuntu 8.04 from an alternate cd, then installed xorg, xterm, xwm icewm, and some lightweight apps.

I have an usb wireless adapter I had managed to install and connect to the internet, but I have to configure it every time I boot up. These are the commands I have to use:

[HTML]ifconfig wlan0 up
iwconfig wlan0 enc ***
iwconfig wlan0 essid ''
iwconfig wlan0 mode managed
dhclient wlan0 -d[/HTML]

Is there a way I can make it permanent so I don't have to do this all the time??

Sometimes I have to do this two, or three times to make it work, unplug it, and plug it back in, restart the network.

Thank you guys!

---

### Post by renzokuken on 2008-11-04
stick it all in a bash script and have that bash script either set to run at startup, or by setting alias in your bashrc so you can run the script with one command

e.g. use nano to create the script

```
nano wirelessup.sh
```

insert the following
```
#!/bin/bash          
ifconfig wlan0 up
iwconfig wlan0 enc ***
iwconfig wlan0 essid ''
iwconfig wlan0 mode managed
dhclient wlan0 -d

```

make the script executbale

```
chmod +x wirelessup.sh
```

then you can simply run

```
./wirelessup.sh
``` to run all the commands automatically in your script.

if you wanted to be even lazier, you could add an alias to your .bashrc (its in your home folder)

```
nano .bashrc
```

and add something like 

```
alias wlanup='./wirelessup.sh'
```

so to run it now all you need to type is ```
wlanup
```

alernatively you can add it to the start up scripts menu (cant remember how to do this without GUI)

edit: making it fully permanent/automatic so you wouldnt even have to do any of the above depends on your wireless chipset.....although i might be an idiot and you could just put it all in the **/etc/network/interfaces** file.....someone with a bit more knowledge might be able to confirm this

---

### Post by duruttye on 2008-11-04
Wao, thanx, I will definitely give this a try!

thanx again :)

---

### Post by renzokuken on 2008-11-04
i just realised i completely forgot about superuser permissions.

you'll probable have to stick a 'sudo' in front of the script to run it properly

---

### Post by duruttye on 2008-11-04
I would've figured out myself :)

In a few hours will give you an update of my progress :)

---

### Post by hyper_ch on 2008-11-04
just put the bash script into /etc/network/if-up.d/ and make it there executable. It should then be run during bootup.

---

### Post by duruttye on 2008-11-04
It works like a charm!!!

thanx guys!

---

