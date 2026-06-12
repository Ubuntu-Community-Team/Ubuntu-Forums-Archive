---
title: "My search in the firefox are redirected to OpenDNS.com, what does it means?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-08
Hi
sometimes my searches in the firefox are redirected to OpenDNS web site?
search that I try by entering keywords in address bar.

does it means that my ubuntu is infected by male ware or ad ware?

I have ubuntu 8.04.
thanks.

---

### Post by hyper_ch on 2008-05-08
did you checkout what opendns.com is?

---

### Post by Znort_Ubern00b on 2008-05-08
No, no malware or adware.

You cant search for keywords in your address bar, you need to use [google]("http://www.google.com") for searches.

what is happening is that it is unable to locate the address you have entered so defaults to a DNS resolving site...see this [wikipedia entry]("http://en.wikipedia.org/wiki/OpenDNS")

---

### Post by kpkeerthi on 2008-05-08
That means your DNS server is not able to resolve the host names you are trying to access. You should be using [openDNS]("http://en.wikipedia.org/wiki/OpenDNS") as your DNS server. What do you have in /etc/resolv.conf?
```
cat /etc/resolv.conf
```

---

### Post by angry_johnnie on 2008-05-08
You know, you could go to google, or yahoo or whatever, and then right-click on the search box, and scroll down the context menu to where it says **add a keyword for this search**, and then entering something like gg for google or yh for yahoo.  That way you can type --for example-- **gg whatever** in your address bar and it will go looking for **whatever** in **google**. :-)

---

### Post by Cheat King on 2008-05-08
I think you must have signed up for it, try going into your Network Manager, I'm away from my Linux machine at the moment so I do not know the exact name, but go to your DNS settings and see if there is an option to reset, I'm not sure if there is, but there probably is, and it may be different depending whether you have KDE or GNOME. You may have gone into your Firefox settings and changed it from there, if that is the case and what I have said doesn't work, try what the person above me just said.

---

### Post by legolas_w on 2008-05-08
Thank you for all reply.
What made me worry is that:
In ubuntu 7.10 when I entered any expression in the address bar, it automatically search my keywords using google with "I am feeling lucky" option enabled.

for example :
typing : movie Doomsday 2008 imdb directly open the imdb page related to doosday movie.

now when I type something like that it does not do the same and instead it open opendns page or usual google search result.
I should mention that I use 4.2.2.4 as my dns server.
Thank you for all your replys.

---

### Post by Cheat King on 2008-05-08
This may not be the switch from 7.10 to 8.04, but it may be caused by your actions or the upgrade from FF2 to the FF3 BETA that you may/may not have had in 7.10.

---

### Post by cotcaro on 2008-07-09
that is completely an ubuntu problem.

---

### Post by nowshining on 2008-07-10
what isp do u use for dns server ```
4.2.2.4
```

---

