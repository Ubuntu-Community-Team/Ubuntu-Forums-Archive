---
title: "struggling with wifi (8.04) (linksys WPC11,  Realtek RTL8180L chip set)"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by heddleston on 2008-05-02
I have a Linksys WPC11 with a: Realtek RTL8180L chip set.  the link given on the ndiswrapper site to download the drivers doesnt have the drivers, and couldnt find them elsewhere. any ideas?

---

### Post by MattBD on 2008-05-02
Just Googled that chipset and I found the drivers on the company's site at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true) and they actually do a Linux driver there, but I don't think it's compatible with Ubuntu (it's marked as Fedora 3, and was last updated in 2005), so I think you'll have to get the Windows XP driver and use it with ndiswrapper.

---

### Post by heddleston on 2008-05-02
thanks, matt! ill see what i can do with that!

---

### Post by heddleston on 2008-05-02
it worked!

---

### Post by aduplat on 2008-05-04
> **heddleston said:**
> it worked!

Hi>

I have the Same problem. But, I dont know how to use ndiswrapper. 
Can anybody show me how to resolve this part, step by step.

Thanks,

Alfredo

---

### Post by MattBD on 2008-05-04
> **aduplat said:**
> Hi>

I have the Same problem. But, I dont know how to use ndiswrapper. 
Can anybody show me how to resolve this part, step by step.

Thanks,

Alfredo

Try this link, that should hopefully get you going with ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=(ndiswrapper))

Ndiswrapper is available on the Ubuntu CD in the "pool" directory - you need to install both packages, or if you have an alternative means of connecting, you can download it from the repositories.

There's also a graphical program for it called ndisgtk which you can install if you're struggling with the command line.

---

### Post by manosdvd on 2008-05-04
Everyone talks about ndiswrapper, but it's not easy for new people to use. ndisgtk is a VERY valuable graphical frontend for ndiswrapper that makes installing windows drivers a million times easier for people who don't speak code.

---

### Post by MattBD on 2008-05-04
> **manosdvd said:**
> Everyone talks about ndiswrapper, but it's not easy for new people to use. ndisgtk is a VERY valuable graphical frontend for ndiswrapper that makes installing windows drivers a million times easier for people who don't speak code.

Amen to that. I really struggled with Kubuntu Edgy when I first started out, partly because I couldn't get the wireless driver working using ndiswrapper. If I'd known about ndisgtk I might have been able to get it working, but as it was I had to buy a book about it and still couldn't get it working till Feisty came out.

---

