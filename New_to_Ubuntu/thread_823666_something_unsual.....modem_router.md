---
title: "something unsual.....modem router"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-09
i want to connect 2 pcs in my router 
one from the ethernet and the other from the usb but i dont know if this is possible though...?

---

### Post by lunaluna on 2008-06-09
wifi is not an option right now because i don't have on the one...too old

---

### Post by ukripper on 2008-06-09
[LIST=1]
[*]You will need either more port router or 
[*]crossover cable to connect two computers to share internet connection (would require extra network card)
[*]or get a switch 
[/LIST]

If i were you I would find cheap 4/5 port router. save you some hassle

---

### Post by Duck2006 on 2008-06-09
> **lunaluna said:**
> i want to connect 2 pcs in my router 
one from the ethernet and the other from the usb but i dont know if this is possible though...?

Is this a cable/DSL modem?
If so yes it can be done.
How are you connecting to the net at the moment?

---

### Post by diablo75 on 2008-06-09
Or you could use a USB>Ethernet adapter.  I picked up a cheap one off ebay worked just fine in Ubuntu after restarting the computer.

[http://www.google.com/products?q=USB%20ethernet%20adapter%20linux&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&sa=N&tab=wf](http://www.google.com/products?q=USB%20ethernet%20adapter%20linux&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&sa=N&tab=wf)

---

### Post by lunaluna on 2008-06-09
> **Duck2006 said:**
> Is this a cable/DSL modem?
If so yes it can be done.
How are you connecting to the net at the moment?

yes it is adsl2
wouldn't need some config..?

---

### Post by ukripper on 2008-06-09
> **Duck2006 said:**
> Is this a cable/DSL modem?
If so yes it can be done.
How are you connecting to the net at the moment?

I highly doubt this would work.

---

### Post by Austin_KW on 2008-06-09
If the router has a usb port you can probably just connect a usb cable and you should see a new ethernet interface appear on the ubuntu PC.

---

### Post by lunaluna on 2008-06-09
> **Austin_KW said:**
> If the router has a usb port you can probably just connect a usb cable and you should see a new ethernet interface appear on the ubuntu PC.

ok i think i'll give it shot..
one more thing can i set my firewall in order not accept anything from the other pc( a lot of people come and go here)  ?

---

### Post by Duck2006 on 2008-06-09
> **ukripper said:**
> I highly doubt this would work.

I have done it in windoze, but not in ubuntu as of yet.

---

### Post by Austin_KW on 2008-06-09
You might try the Uncomplicated Firewall (ufw)
sudo ufw enable
sudo ufw deny from *ip.address.of.otherPC*

See [http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html) for a bit more detail

---

### Post by lunaluna on 2008-06-09
> **Austin_KW said:**
> You might try the Uncomplicated Firewall (ufw)
sudo ufw enable
sudo ufw deny from *ip.address.of.otherPC*

See [http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html) for a bit more detail

btw i just have an update recommadation for ufw how come up?!?

---

### Post by cariboo on 2008-06-09
You should be able to block internet access for any computer on your network right in the router.

Jim

---

