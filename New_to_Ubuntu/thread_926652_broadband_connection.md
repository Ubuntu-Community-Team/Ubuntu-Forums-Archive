---
title: "broadband connection"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by manoindia2020 on 2008-09-22
I have problem in connecting to broaband connection in my ubuntu....
it first sensed  my connection but later remote server didnot respond and i could not connect...
can any one help me in fixing this issue...

---

### Post by aeiah on 2008-09-22
how are you connecting? usb modem, ethernet cable or wifi?

are you sure the modem is connected to the internet? if you're using ethernet or wifi (ie, a normal network connection) you could refresh it by going to the terminal and doing ```
sudo dhclient
```. this'll refresh things, although if there's an actual problem it wont solve much.

we really need more info about how you're connecting. you could also do with finding out what your modem IP is so you could ping it and see if the problem lies with the modem or your computer.

---

