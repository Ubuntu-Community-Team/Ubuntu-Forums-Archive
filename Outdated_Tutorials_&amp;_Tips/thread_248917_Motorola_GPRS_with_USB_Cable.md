---
title: "Motorola GPRS with USB Cable"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Uncle Che on 2006-09-01
I posted this over on another forum a month or so ago and I figure it is high time I put it here as I see the question keeps popping up. 

Ok, this works on the Motorola L6, Motorola V220, and the Motorola C390 phones. I know support sites only work when people post their own solutions and since a simple search of Motorola Gprs yields nothing of value, here goes:

1. Plug in the motorola phone. It should be recognized as ttyACM0.

2. Open a terminal window and type:
sudo wvdialconfig /etc/wvdial.conf

You get a long list of checks that it runs. Basically it checks for a modem and the location.

3. next type:
sudo vi /etc/wvdial.conf

In the file, you need to edit a few entries, like edit out the semicolons at the start of the line for phone number, password and username. For user name and password, you can enter anything for those values. For phone number, I used *99#.

Next, add a line:
Stupid Mode = 1

You might want to change the baud rate, I used 230400 even though it detected that it could do 460800. GPRS is slow so I can't personally think of a good reason to send data to and from the modem 10 times faster than it can deal with it.

4. Save the file.

5. Next open another terminal window and type
sudo wvdial

You are now connected to the internet and you can surf. I don't know if you can close the window and keep the connection or not. I am just happy to be connected. I can deal with any quirks.

I hope this can serve as a little bit of help to any searching the forums for how to use a gprs modem with Ubuntu/Kubuntu. It seems really simple, but I have been searching on and off for 6 months for a way to connect through Ubuntu like this.

---

### Post by adewale on 2006-09-28
uncle che,
am glad about your post, but didn't work for me. am new to linux and i use ubuntu 6.06 lts, previously used redhat 9. i use a motorola l6 and buntu detects it as an e398 GSM phone and not as a modem and also the first command replies command not found. on my previous redhat 9 it recognized the phone and even the modem in the hardware browser. plz what can i do as this is my only means of connecting to the internet:-|

---

