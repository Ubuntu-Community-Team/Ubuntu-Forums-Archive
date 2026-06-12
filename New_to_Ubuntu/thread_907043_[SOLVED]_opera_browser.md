---
title: "[SOLVED] opera browser"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by soloman498 on 2008-09-01
How can I get Opera browser to connect to my Internet? Firefox works o'k::confused:

---

### Post by aloshbennett on 2008-09-01
If you havent installed opera yet, you could do that by 
> sudo apt-get install opera

It should work out of the box. If you have proxies set for firefox, you will have to set the same for opera too.

---

### Post by soloman498 on 2008-09-01
I have already installed Opera but it will not connect to the internet

---

### Post by aloshbennett on 2008-09-01
How are you connected to internet? Via router or a PPPoE connection?

---

### Post by soloman498 on 2008-09-01
via a router.I uninstalled opera then tried to get it by the terminal as you suggested but it said that the package Opera is not available

---

### Post by aloshbennett on 2008-09-01
> apt-cache search opera?

---

### Post by billgoldberg on 2008-09-01
Download the .deb file from their website, double click to install.

If you have a internet connection, it will work the second you open it.

If not, go to the Opera forums, they will be able to help you more.

--

If you are just looking for another browser, try epiphany (remember to install the add ons).

---

### Post by soloman498 on 2008-09-01
aloshbennett. I tried that. It downloaded a lot of stuff but I couldn't see Opera.

---

### Post by soloman498 on 2008-09-01
Bill Goldberg,I downloaded the .deb file and it was installed but still not working on the internet.can't even get ebay

---

### Post by aloshbennett on 2008-09-02
this might sound silly, but from terminal did you try for 'opera' with a lowercase 'o'?

---

### Post by soloman498 on 2008-09-02
yes, it was with a little o

i downloaded epiphany and this is what I am useing now.it worked first time.the only trouble is i downloaded the extensions and for some reason the package ended up on my desktop.how do i add them to epiphany please?

---

### Post by Elfy on 2008-09-02
The easiest way would be to install from the repositiories - from a terminal, incidentally you could have done the same with epiphany.

```
sudo apt-get install epiphany-extensions
```

I think the download will be the source package.

---

### Post by soloman498 on 2008-09-02
thanks for that forestpixie.i suppose opera will have to wait for another time until i have checked out epiphany.:guitar:

---

### Post by Elfy on 2008-09-02
You could tryto move the .opera config and run opera it should start again.

```
mv ~/.opera ~/operaback
```

---

### Post by soloman498 on 2008-09-02
tried  that forestpixie but didn't work,although i did have to agree to their terms.

---

### Post by Elfy on 2008-09-02
Maybe check the connection information in firefox and comapre to the connection information in opera, but it's a bit on the odd side if they are the same.

---

### Post by aloshbennett on 2008-09-03
Seems like opera is no more in the repositories. It is available only for partner repository for 32 bit ubuntu.

If you still feel like giving it a shot, delete the ~/.opera folder before installing from the .deb files.

---

### Post by soloman498 on 2008-09-06
thanks for trying to help me.I give up.I have loaded it 3 times and it still wont work.I will mark this thread as solved and try later to get it working.thanks again.

---

### Post by Elegorod on 2008-11-22
I solved such problem by disabling IPv6
[http://my.opera.com/community/forums/topic.dml?id=256797](http://my.opera.com/community/forums/topic.dml?id=256797)
How to disable IPv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) , I used the second way for Hardy. It works for Intrepid too.

---

