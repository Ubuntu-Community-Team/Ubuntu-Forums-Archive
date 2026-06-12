---
title: "[SOLVED] Apache 2.2.8 IP Adrress"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-05-03
Hi. I just set up Apache 2.2.8 on Ubuntu. I have it working so that my html directory is in the home folder. I can navigate to the website by using localhost however I can't get to it using my IP address. So my question is how do I get to it using my IP address.

---

### Post by halitech on 2008-05-03
which IP (Internal or external)? are you behind a router? does your ISP block port 80 if you aren't behind a router?

---

### Post by Promaster91 on 2008-05-03
The External IP (The one I can navigate to from another computer). Yes I am behind a Router (do i need to forward a port?). I have Comcast as my ISP (How can you tell if they block port 80).

---

### Post by halitech on 2008-05-03
if you are behind a router then you will need to forward a port so the router will pass the request along to the server. before we worry about that, can you load a page on your server locally by using the internal IP address assigned by the router?

---

### Post by Promaster91 on 2008-05-03
Yes, the interal ip (192.168.1.7) is working. I can navigate to my website using the ip adrress.

---

### Post by halitech on 2008-05-03
ok, so that confirms Apache is working properly. you will need to do some digging on the next part as I don't know alot about routers but in the setup there should be an option on port forwarding. You need to go in that section and forward port 80 to the internal IP of the server machine. Once you do that, try it and see if it works, if it does good to go, if not, might be comcast blocking port 80 (which I think they do if I remember rigth)

---

### Post by Promaster91 on 2008-05-03
Hey it works! I forwarded port 80 and used my external ip and it brought me to my webpage. Thanks!

---

### Post by halitech on 2008-05-03
glad it is workign, don't forget to mark the thread solved so others will know in the future that you fixed it :)

---

### Post by Joeb454 on 2008-05-03
You may want to look at dyndns.com - They allow you to have a domain name (sort of) for free, if your router supports dyndns I would definitely recommend it.

For example I have [http://www.joeb454.com]("http://www.joeb454.com") - which just points to the dyndns address off [http://joeb454.selfip.com]("http://joeb454.selfip.com")

Oh and there's a flash game (has sound too) on that page - though it may take a while to load on my 448kbps upload speed :p

---

### Post by Dr Small on 2008-05-03
> **Joeb454 said:**
> You may want to look at dyndns.com - They allow you to have a domain name (sort of) for free, if your router supports dyndns I would definitely recommend it.

For example I have [http://www.joeb454.com]("http://www.joeb454.com") - which just points to the dyndns address off [http://joeb454.selfip.com]("http://joeb454.selfip.com")

Oh and there's a flash game (has sound too) on that page - though it may take a while to load on my 448kbps upload speed :p
FlashBlock caught it. Saved my browser :D

---

### Post by Promaster91 on 2008-05-05
Cool. I will check that out.

---

### Post by Promaster91 on 2008-05-06
Hey thanks, Joeb454. I was able to register a free domain at the website. I was looking all over for a free domain site.

---

### Post by Joeb454 on 2008-05-06
No worries - thats why I like dyndns. I just got that domain because a company was doing it half price ;)

---

