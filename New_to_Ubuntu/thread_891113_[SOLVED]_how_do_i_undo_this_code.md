---
title: "[SOLVED] how do i undo this code?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-15
I entered the code 

```
sudo iwconfig wlan0 rate 54M
sudo /etc/init.d/networking restart 
```

and lost my internet... can anyone tell me how to undo that code? i'm a little deperate since I can't stay on this computer long and need the internet on my ubuntu system back???


or is it not that simple...?

---

### Post by tahina on 2008-08-15
Have you tried turning the computer off and on again? (I don't know if that would get you back to the original configuration, but I'd try that first.)

---

### Post by crjackson on 2008-08-15
Try ```
sudo ifconfig wlan0 up
```

or

Try rebooting

---

### Post by Gone fishing on 2008-08-15
I think you can go into /etc/network/interface and edit the file.

sudo gedit /etc/network/interfaces

Mine looks like so:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:xxxxxxxxxxxxx
wireless-essid fish

auto wlan0

Obviously you will need to edit yours to fit probably just removing the line about rate will do.

---

### Post by nicedude on 2008-08-15
Hey tahina you must watch "IT Crowd" on BBC, I love that show.

---

### Post by phantomjoker on 2008-08-16
> Hey tahina you must watch "IT Crowd" on BBC, I love that show.

can you please not spam my thread with a differant topic - conversation conserning British TV should be taken up the in backyard forum (Purple/Pink Ponies)

Thankyou..

---

### Post by Canis familiaris on 2008-08-16
Could you post the output of ```
iwconfig
```

EDIT: Oh! Is this thread solved.
My mistake.

EDIT #2: In the future instead of posting against spam or offending post, it would be more elegant to report the post.

---

