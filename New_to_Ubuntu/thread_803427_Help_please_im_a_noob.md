---
title: "Help please im a noob"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by daniel000 on 2008-05-22
Hi ive started a post before about this i think but i have a little bit more of a understanding so it may help here

Ok, ive installed ubuntu on my dell inspiron 9400

i have the intel pro/wireless card on here that when i load up ubuntu the wifi logo doesnt light up therefore meaning it isnt on

i tried fn f2 to turn it on but doesnt work

what drivers do i need, and how do i install them cuz im not sure what to type in the console thingie

---

### Post by StumpyXL on 2008-05-22
[http://www.linux-laptop.net/dell.html](http://www.linux-laptop.net/dell.html)

That should help you out. :)

---

### Post by pedro_orange on 2008-05-22
Do a lshw:

```
pedro@pedro-laptop:~$ sudo lshw | grep eth
                logical name: eth1
                capabilities: pm bus_master cap_list ethernet physical wireless
                logical name: eth0
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

```

That should tell you if Linux can see it or not :)

---

### Post by Sealbhach on 2008-05-22
Hi Daniel,

I just started using Linux about a month ago. 

It takes a bit of getting used to, but it all starts to come together eventually. It takes time, but it works for just about most things.


.

---

### Post by anotherdisciple on 2008-05-22
Do you have a Intel 3945 A/B/G? If so... open the terminal (Applications>Accessories>Terminal) and type this:

```
sudo aptitude install linux-backports-modules-hardy
```

Then...

```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```


I have that card... and my light wasn't working... but this fixed it... hope it helps... you may neet to restart X for it to turn on... but maybe not... if it doesn't seem to work... hit Ctrl+Alt+Backspace

---

### Post by anotherdisciple on 2008-05-22
PS- you can change that code to your wireless card if it is different... just replace 3945 with your number

---

### Post by daniel000 on 2008-05-22
ok thanks guys ill try the few things listed

and thanks for the quick responses its much appreciated 

Sealbhach, now that u have it running an that, do u like it? and is it better than windows?

also are u running both?

---

### Post by daniel000 on 2008-05-22
i did the 2nd code , and its picked up my rangemax wireless internet

but when i type in the wep key, it looks as if it is trying to join, but it goes on for a minute, and then the message box appears again asking for me to put the key in


also the wifi logo is not on either

---

### Post by anotherdisciple on 2008-05-22
Well.. that means the card is working now... so it's a password problem... either you have the wrong WEP or you are choosing the wrong type ex) You have it set to 128 bit but it's really a 64bit... know what I mean?

and the wireless light that isn't working should have been fixed with this code...
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

Assuming you have an Intel Pro 3945 A/B/G ... I'm assuming you do if you have a newer computer from dell. Is that the wireless card? It would help a lot to know what type of card you have.

---

### Post by daniel000 on 2008-05-22
ok, well the card i have is 

Intel(R)PRO/Wireless 3945ABG Network Connection

---

### Post by daniel000 on 2008-05-24
lol yeah im strugglin, cant seem to get ubuntu to find my modem again


ahwell i didnt think this would be so hard to use so i think i mite give it the flick lol


also like, how do u install like programs cuz i mite need to install the software of the wireless card - Intel(R)PRO/Wireless 3945ABG Network Connection

---

