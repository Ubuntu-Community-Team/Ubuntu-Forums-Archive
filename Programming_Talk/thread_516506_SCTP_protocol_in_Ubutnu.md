---
title: "SCTP protocol in Ubutnu"
date: 2007-08-03
forum: Programming Talk
---

### Post by tomcio on 2007-08-03
Hi!

I'd like to take a look at SCTP protocol during I have holidays and write some small apps to see how it works i practice.

I read, that SCTP support was included in Linux since kernel v2.4, but i haven't found any "sctp.h" header file in "/usr/inlude/netinet" in default installation. Can someone explain me, why it isnt available by default?

While searching repository I found two different implementations. One is developed by "Linux Kernel SCTP" adn second comes from [http://www.sctp.de/](http://www.sctp.de/) .

Which one is "the only right" and which one should I use?

---

### Post by PaulFr on 2007-08-08
SCTP protocol is indeed supported in the Linux kernel. However if you want to use it in your applications, please install ```
sudo apt-get install libsctp-dev lksctp-tools
```Once these are successfully installed, to test whether SCTP is working, you can run a SCTP server in one terminal ```
sctp_darn -H 0 -P 2500 -l
``` and in another terminal, you can run a SCTP client in another terminal ```
sctp_darn -H 0 -P 2600 -h 127.0.0.1 -p 2500 -s
```Now type any text in the client which will be reflected in the server output. Once this is working, please hop on over to **[http://lksctp.sourceforge.net/index.html](http://lksctp.sourceforge.net/index.html)** for more details about SCTP. The test commands above are from **[http://lksctp.sourceforge.net/testing.html](http://lksctp.sourceforge.net/testing.html)** with the port numbers changed to be above 1023 so you do not need sudo. Hope this helps.

---

### Post by weishigoname on 2009-11-27
Oh!that is great ,I am looking for it ,thanks very much

---

