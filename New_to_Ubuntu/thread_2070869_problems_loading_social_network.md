---
title: "problems loading social network"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by gestus on 2012-10-13
hello to everyone, I am new to Ubuntu and I'm trying to learn how everything works here...

I ran into a problem and I cannot solve it... I have search without success. 

My problem is that when I want to open vkontake (a popular social network site in Russia and the CIS countries) a message appears saying "Oops! Google Chrome could not find vk.com" or "Server not found, Firefox can't find the server at [www.vk.com](www.vk.com). It does not matter what explorer I use. I know the site works because if I change to windows the page opens with out any problem. 

I really need help, I am trying to completely move to ubuntu but vk.com is necessary for my social life:guitar: 

tahnks for the help ):P

---

### Post by sandyd on 2012-10-13
Weird.
Opens here.

---

### Post by newb85 on 2012-10-13
Try to narrow the problem down a little bit.

What kind of internet connection are you using?  Have you confirmed that it works for other things in Ubuntu?

By default, both Windows and Ubuntu should use the DNS server provided by your ISP, but just to rule that out, try connecting directly to the IP address
```
ping -c 1 87.240.131.119
```

---

### Post by gestus on 2012-10-14
> **newb85 said:**
> Try to narrow the problem down a little bit.

What kind of internet connection are you using?  Have you confirmed that it works for other things in Ubuntu?

By default, both Windows and Ubuntu should use the DNS server provided by your ISP, but just to rule that out, try connecting directly to the IP address
```
ping -c 1 87.240.131.119
```

I tried with the IP address and it did't work. Then I changed the DNS server and it worked like a charm...

Thanks!!

---

