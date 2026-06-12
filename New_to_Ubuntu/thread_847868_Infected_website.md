---
title: "Infected website"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Paraphysicist on 2008-07-03
I was configuring my /etc/hosts file to block a website, and I thought I would test it by trying to connect to the site.  I should've tried a harmless site and **restarted the computer** but I didn't and connected to the site.  ](*,)

The site is here: [http://www.siteadvisor.com/sites/pcpop.com](http://www.siteadvisor.com/sites/pcpop.com)

I am running Firefox 3 with NoScript, Flashblock, and QuickJava.  Cookies are set to 'not accepted'.

After connecting, I restarted my computer and ran chkrootkit and rkhunter.  I got a few warnings, but googling the entries showed them to all be false positives.  

I thought I would ask about this, since any site one visits might be potentially bad:

1. Is there anything else I should check or run (especially for a browser exploit)?

and

2. What kind of security breaches/mistakes are the bare minimum that warrant a reinstall of Ubuntu?

I've been wondering about #2 for a while.  Any insights would be hugely appreciated.  Tthanks

---

### Post by AliTabuger7 on 2008-07-03
Simply because you are using ubuntu makes you pretty safe. You're also using noscript and such, which makes it almost impossible on any machine.

The biggest thing to be concerned about is not your browser when on linux, but the things you install. Make sure that programs you install are from trustworthy sources, like an ubuntu mirror.

So far, I've found it safe to be trusting of open source projects, but not blindly. Make sure you are using stable versions of applications. Maybe check a social network that reviews webpages for reviews on the webpage you found it on.

---

### Post by Paraphysicist on 2008-07-03
Thanks Ali, those are some pretty good ideas.  I'm very careful about what I install, I just wish there was a way to do a hosts file for scripts.

---

### Post by nowshining on 2008-07-04
u don't need to restart ur computer after editing /etc/hosts

once u connect u gotta wait roughly 5-10m minutes for the DNS cache to clear and re-check ur hosts file. If you want, u can download an older copy of my hosts file - i gotta update it soon, now that I post this I should update it within this month. :P

[http://freewebs.com/blocksites](http://freewebs.com/blocksites)

other than the above - I have made a few changes of commenting out good sites, etc.. As always if you find a site that should be commented out - let me know and i'll do that. :)

edit: to configure ur DNS cache the GUI way - install a add-on called fasterfox - then custom in options -  cache - u can set the seconds there along with how many ips, etc.. can be cached. Oh and more than likely it was scanning ur browsers disckcache. :P - i don't trust siteadvisor - not since Mcafee took them over. :/

---

### Post by Paraphysicist on 2008-07-05
Nowshining, thanks for that reply.  I didn't know that about  the DNS cache.  I'll check out that hosts file.  I'm not so sure about siteadvisor, they gave a full green light on a site that firefox said is bad.

---

### Post by nowshining on 2008-07-05
DNS cache makes it where it won't query ur ISPs DNS for the ip, when u type in the url it has to go find the associated IP, :) this of course goes very fast. If ur ISP DNS doesn't know it, itta ask other DNS machines, etc.. across the net until one knows it, again this is done super fast esp. with all the people on the net.

here is a good article: [http://www.technize.com/2007/06/25/what-is-a-dns-cache/](http://www.technize.com/2007/06/25/what-is-a-dns-cache/)

for a pdf on poisoning of it, etc..

[www.infosecwriters.com/text_resources/pdf/DNS_TOlzak.pdf](www.infosecwriters.com/text_resources/pdf/DNS_TOlzak.pdf)

---

