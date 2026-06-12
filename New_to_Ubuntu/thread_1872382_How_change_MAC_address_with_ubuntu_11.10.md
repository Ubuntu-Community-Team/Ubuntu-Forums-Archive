---
title: "How change MAC address with ubuntu 11.10?"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by xavi fernandez on 2011-10-30
Hi all, I'm really interested in keep anonymity meanwhile I'm surfing in internet, my doubt is how is possible change the MAC address in my computer running ubuntu 11.10, I'm really newbie in Linux so, any answer I really will appreciate in a very easy way to understanding.

thanks in advance

---

### Post by jramshu on 2011-10-30
```
sudo apt-get macchanger
```

Read the man page on options.

EDIT: This isn't going to make you anon. I mainly use it when traveling and the hotels boot me from the web because of using too much bandwidth. I change my mac and can continue surfing. lol

---

### Post by haqking on 2011-10-30
Changing your MAC on your machine will not provide you with much internet anonymity and though easy to do doesnt provide much anonymity at all in any case

Your packets will be destined for your router and WAN IP and MAC

If you want to take some steps towards anonymising your surfing take a look at a friends tutorial on using Tor it is easy to set up, though can be slow.

[http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

There are lots of other choices also

---

### Post by xavi fernandez on 2011-10-30
Thanks a lot for your fast answer, I will install it at the moment I switch to ubuntu, I try transfer as well my vpn from windows to ubuntu, but is getting hard, I hope changing the MAC and with the vpn, my data will be more secure through the net.

---

### Post by xavi fernandez on 2011-10-30
Thanks haqking, I will check it out, even like that I read in a post from the security section que vpn is much better than tor for surf anonymously, what do you think???

---

### Post by haqking on 2011-10-30
> **xavi fernandez said:**
> Thanks haqking, I will check it out, even like that I read in a post from the security section que vpn is much better than tor for surf anonymously, what do you think???

Yes a secure VPN is often a common choice

---

### Post by jramshu on 2011-10-30
SSH tunnel to VPN.

---

### Post by Dangertux on 2011-10-30
I'm confused as to why or even how you would SSH tunnel through a VPN. Since most VPN's are created via an SSL tunnel to begin with.

That being said its important to note that most VPN's will not offer any anonymity they will however offer security of the data between the destination and endpoint at the VPN. 

Hope this clarifies a little bit.

---

