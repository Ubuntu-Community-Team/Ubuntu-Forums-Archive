---
title: "making a server (have extra desktop...)"
date: 2009-07-01
forum: Programming Talk
---

### Post by Xender1 on 2009-07-01
Hey, so I have an extra desktop that I dont really use much anymore now that I got my laptop. I dont want it to just sit there and I have lots of ideas for it but not sure what I need to do.

What I am thinking is making it a server (I think thats the correct term). Essentially I want to be able to store files on there, movies, etc. and be able to access them from other computers on my network (like my laptop). I was also thinking of hosting stuff from it such as a website (maybe heh).

Just wondering if anyone could point me in the right direction as to what I need to do/consider to go about doing something like this. Mainly I want to do as a learning experience so if you have any ideas please let me know! Thanks.

---

### Post by Reiger on 2009-07-01
HTTP server (websites): Apache 2
(S)FTP server (ftp storage): VSFTPD
Media server ... (streaming stuff): VLC apparently can handle both music and video streaming (it can act as server besides client/player).

---

### Post by unknownPoster on 2009-07-01
The LAMP Stack wouldn't hurt, [http://en.wikipedia.org/wiki/LAMP_(software_bundle](http://en.wikipedia.org/wiki/LAMP_(software_bundle))

---

### Post by Geoff918 on 2009-07-01
I can agree in principle with the LAMP stack, but why does he need MySQL or PHP? For log-in authentication? If you're just hosting files, etc. a standard Ubuntu Server install will come pretty well configured out of the box. You can just store your files in the right directory. vsftp is fine, or most any ftp software available on linux is fine. I've used many, they each have their own strengths and weaknesses. Anyway, server install with some default options should be fine for you.

---

### Post by Xender1 on 2009-07-02
Hey thanks for the responses. I going to do the ubuntu server and then just play around with stuff. Definitely looking to learn lots so going to see whats up with the LAMP stack. Again, Thanks!

---

### Post by paul_be on 2009-07-02
Hey if you are just playing around with an extra machine you could try an Astaro secuirty gateway.  It is linux based and you can get a free home version, I use one that acts as a vpn, email filter and many other things.

[http://www.astaro.com/our_products/product_overview/landing_pages/free_home_edition](http://www.astaro.com/our_products/product_overview/landing_pages/free_home_edition)

---

