---
title: "Dial up help me..."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by iption on 2008-06-21
Hi all!! I completely new to linux and I need a little help.

I'm connecting to the internet with USB modem, GPRS modem. I found how to set it up for linux and it works. To go online I'm using wvdial.conf

Is there an easier way to go online? I don't like to open the terminal every time I go online. And I can't disconnect (unless I unplug the modem).

The things I need to setup for the modem is initialization code, phone number, user&pass, and of course the modem location.

i tried to manually configure it with network settings, but I can't find anywhere to write initialization code. 

Can you tell me how to set it up with network settings or, to help me write a script to go online and offline?

Thanks!!

---

### Post by phil66 on 2008-06-21
Download Kppp or Gppp from synaptic and configure

---

### Post by iption on 2008-06-22
Well I won't be downloading any software until I fix my wireless. This dialup is really slow to download something.

---

### Post by sleepingdragon on 2008-06-22
When I was on dialup I had a preference for Kppp as it enabled me to fine-tune everything I needed for my connection. It might take a long time to download, but it'll be worth it.

---

### Post by nowshining on 2008-06-22
gnome-ppp and kppp should be really really smal ie: gnome-ppp is under 100kb. Also if dial-up is super slow for you u've got a problem - it's fast for me, not as fast as highspeed modems, but it's quick. u just gotta be patient.

---

### Post by iption on 2008-06-22
Gnome ppp was really small :D but I don't see how it helps me. When I run it I have a small window called gpppwrap and when I choose wvdial and on nothing happens. I read somewhere that this program has seetings and I can setup the connection inside, but only thing this program has is a File->Quit and Help

:confused:

---

### Post by nowshining on 2008-06-22
alt+print screen and post a screenshot of it - make sure ur mouse cursor is on the gnome-ppp window. + did u install from a deb file?

---

### Post by iption on 2008-06-22
No I downloaded it with Add/Remove

---

### Post by phil66 on 2008-06-22
What you have downloaded and installed is "gpppon"

Which is another way to access the internet

What you want is gnome-ppp or a better one is KPPP

Go to synaptic and search gnome-ppp and you will see the two different programs side by side

Do you know how to get to synaptic package manager

Which distro do you have installed

---

### Post by rraj.be on 2008-06-22
Here is another easy way by a small script.

Just open 

System-->preferences-->sessions.

In that click ADD

It will open a new window.

In that select add custom command.

I think its the first in the list box.

Click it.

Then type the following in Command text box

wvdial.

And name as Dial up Connection.

Click OK.

Now when ever you start your computer if your mobile is connected It will automatically dials up the connection.

---

### Post by iption on 2008-06-23
COOL Gnome PPP worked nicely... it even has a notification icon 
:D me be happy :D

---

