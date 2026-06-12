---
title: "Webhosting on dynamic ip"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by strategos-ender on 2013-10-27
I've have been on google for days on how to host my own website. So far I've installed the LAMP server successfully. I've bought by own domain name from dynamic dns. I'm stuck on how to bind my server to the domain name using a dynamic ip address. I think BIND9 is some how involved, but I'm not completely sure if thats the right direction. Can anybody confirm this and perhaps point me to a relevent tutorial? I'm running ubuntu 13.10 desktop on a laptop.

---

### Post by ian-weisser on 2013-10-27
You should not need to bind anything.
You usually use a local ddns client to keep the remote ddns provider up to date. Automatically.
The ddclient package is a common example of a ddns client that works with the usual ddns providers.

---

### Post by strategos-ender on 2013-10-27
So configure the ddclient to update my dynamic ip? To whom shall the ddclient update to? The dns of domain registar(dynamic dns), the dns i use(opendns), or of my ISP?

---

### Post by sandyd on 2013-10-27
> **strategos-ender said:**
> So configure the ddclient to update my dynamic ip? To whom shall the ddclient update to? The dns of domain registar(dynamic dns), the dns i use(opendns), or of my ISP?

whats the url of the site that you are using

---

### Post by strategos-ender on 2013-10-28
It's a top level name(.com)

---

### Post by ian-weisser on 2013-10-28
> **strategos-ender said:**
> So configure the ddclient to update my dynamic ip? To whom shall the ddclient update to? The dns of domain registar(dynamic dns), the dns i use(opendns), or of my ISP?

Your client updates your IP to the dynamic dns provider. It determines your IP automatically. It updates your ddns automatically. You usually configure it with your ddns provider account information.

Your ddns provider should have a recommended linux client for you to install (sometimes ddclient, sometimes something else), and complete configuration instructions. If not, choose a better provider.

Since we don't know your provider, we can't really offer more detail.

---

### Post by gerowen on 2013-10-29
If you have a router between you and the internet that is just forwarding specific ports to the server, which I believe you should, then that router may have Dynamic DNS stuff built in, a lot of them do.  I've got an old Linksys WRT-54G.  Here's a screenshot.  I know mine says it's running DD-WRT, but this setting was there with the factory firmware as well.
[ATTACH=CONFIG]247348[/ATTACH]

---

### Post by strategos-ender on 2013-10-30
Okay I configured the ddclient and also port-forwarded to 80. When I ping my website I get packets back, and I use lynx --dump I also get my website. The problem is the site doesn't seem to load on my firefox or browser on my cell phone. Any suggestions?

---

### Post by gerowen on 2013-10-30
> **strategos-ender said:**
> Okay I configured the ddclient and also port-forwarded to 80. When I ping my website I get packets back, and I use lynx --dump I also get my website. The problem is the site doesn't seem to load on my firefox or browser on my cell phone. Any suggestions?

If you don't mind giving it out, what's the URL and I'll see what I get from here.  If you're not comfortable posting it on the forum, you can send it to me in a PM.

---

