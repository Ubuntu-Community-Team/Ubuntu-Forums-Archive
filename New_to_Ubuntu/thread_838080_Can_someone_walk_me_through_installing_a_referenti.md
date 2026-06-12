---
title: "Can someone walk me through installing a referential into /etc/apt/sources.list file?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-06-23
Yeah, I'm a bit of a noob and I've never done it before. I tried (it didn't seem too hard) but I got a weird error in synaptic AND the driver wasn't functioning, so I uninstalled it. In case you are wondering what it is, it's the ricoh webcam driver that I got from Arakhnê.com (more information here: [http://www.arakhne.org/spip.php?rubrique31](http://www.arakhne.org/spip.php?rubrique31) ; [http://www.arakhne.org/spip.php?article50](http://www.arakhne.org/spip.php?article50) ; [http://www.arakhne.org/spip.php?article51](http://www.arakhne.org/spip.php?article51))

Can someone help? I got this working before but I had to get a new hard drive and lost all my progress....getting this to work again would be mighty sweet :p

-Stropko

---

### Post by ukripper on 2008-06-23
it is very simple just follow the steps below:

add this to your sources.list:

go to terminal and type:
> sudo gedit /etc/apt/sources.list

addd below to the file
> deb [http://download.tuxfamily.org/arakhne/ubuntu](http://download.tuxfamily.org/arakhne/ubuntu) hardy universe

at bottom of the file.

and then in terminal type or paste the below in quotes:
The packages are signed. To add the GPG public key into your apt key list.

       > wget -q [http://download.tuxfamily.org/arakhne/public.key](http://download.tuxfamily.org/arakhne/public.key) -O- | sudo apt-key add -

after that in termianl type this:
> sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by stropyboy11 on 2008-06-23
Umm I'm a bit confused. What do you mean "type one of the below"? Are you talking about the thing you have as your quote or the whole "The packages are signed" thingy?

-Stropko

---

### Post by ukripper on 2008-06-23
> **stropyboy11 said:**
> Umm I'm a bit confused. What do you mean "type one of the below"? Are you talking about the thing you have as your quote or the whole "The packages are signed" thingy?

-Stropko

sorry thought i would give you more options just ignore that bit and follow exactly.

---

### Post by RomeReactor on 2008-06-23
Hi. The commands in the second post should work; just don't forget to run:
```
sudo aptitude update
```
before trying to install the driver.

EDIT: It's already added to the post.

---

### Post by stropyboy11 on 2008-06-23
Umm when I ran > sudo apt-get update && sudo apt-get dist-upgrade  and > sudo aptitude update I get 404 errors whenever I get to the tuxfamily download. Any ideas?

-Stropko

---

### Post by ukripper on 2008-06-23
> **stropyboy11 said:**
> Umm when I ran  and  I get 404 errors whenever I get to the tuxfamily download. Any ideas?

-Stropko

i think i know ehy.

Can you go to sources.list file again and  replace the last line to this 
```
deb http://download.tuxfamily.org/arakhne/ubuntu hardy-arakhne universe
```
delete the previous one i gave you earlier.

then save and exit and do follwoing:
```
sudo aptitude update
```

---

### Post by stropyboy11 on 2008-06-23
Ok, it looks like it has downloaded successfully. The only problem is my webcam still isn't functioning. *Scratches head*

For all interested it's a webcam built into an HP DV6000T

I'm gonna do a quick reboot and check if it's working...in the meantime can I get some ideas?

Thankies!

-Stropko

---

### Post by ukripper on 2008-06-23
> **stropyboy11 said:**
> Ok, it looks like it has downloaded successfully. The only problem is my webcam still isn't functioning. *Scratches head*

For all interested it's a webcam built into an HP DV6000T

I'm gonna do a quick reboot and check if it's working...in the meantime can I get some ideas?

Thankies!

-Stropko

you can test whetehr it is working or not using camorama app:
```
sudo apt-get install camorama
```

---

### Post by stropyboy11 on 2008-06-23
I tried running camorama and got hit with the follwing error: 

> Could not connect to video device (/dev/video0). Please check connection.

-Stropko

---

### Post by ukripper on 2008-06-23
reboot and try again.

---

