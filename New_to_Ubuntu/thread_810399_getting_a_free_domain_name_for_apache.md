---
title: "getting a free domain name for apache"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-05-28
I've set up apache on my pc but I don't have a domain name. 

Do I have to buy one or can I get one for free? :confused:

---

### Post by inportb on 2008-05-28
Get your free domain names at uni.cc, freedns.afraid.org, or the like.
Remember to set up port forwarding if you're behind a router.

---

### Post by pluckypigeon on 2008-05-28
Thanks for your quick response. 

Do you know how I can use this with apache? :confused:

---

### Post by spiderbatdad on 2008-05-28
Put your domain name in httpd.conf on a line like this:
ServerName localhost
ServerName YourDomain.com

---

### Post by pluckypigeon on 2008-05-28
how do I link freedns.afraid.org to my apache

---

### Post by spiderbatdad on 2008-05-28
[www.whatismyip.com](www.whatismyip.com)

visit that site. use your public ip to link the dns to your computer

---

### Post by punx45 on 2008-05-28
and if you are like most consumers, your ISP assigns you a dynamic IP, so you should probably look into a dynamic domain name system like dyndns.org (which also provides free (sub)domain names.)

---

### Post by pluckypigeon on 2008-05-28
I cant seem to get this working. It asks me to register my domain name with ICANN which I have no idea to do.

Does anyone know?

---

### Post by pluckypigeon on 2008-05-28
it says my domain is broken. how do i solve this?

---

### Post by dasunst3r on 2008-05-28
Another Dynamic DNS service you can look into is [www.dyndns.org](www.dyndns.org)

---

### Post by pluckypigeon on 2008-05-28
I'm looking for a site that can get me a [www.my-chosen-](www.my-chosen-) website-name.com type address which i can use with apache

---

### Post by bsharp on 2008-05-28
Yes, you do need to register with ICANN. You do this through a site like [www.godaddy.com](www.godaddy.com) (personal favorite), and it does cost money.

---

### Post by pluckypigeon on 2008-05-28
i dont have any money

does anyone know a free one

---

### Post by perlluver on 2008-05-28
> **pluckypigeon said:**
> i dont have any money

does anyone know a free one

I don't think there is a way you can get a [www.my-name.com](www.my-name.com) website without paying for it.

---

### Post by inportb on 2008-05-28
> **perlluver said:**
> I don't think there is a way you can get a [www.my-name.com](www.my-name.com) website without paying for it.

In most cases, you can't. But if you're willing to do a bit of work (like forum-posting), there are choices. Check out ddboard.com or similar (which is where I got inportb.com).

I was under the impression that you did not need a second-level domain. Why not choose a good third-level domain to start? (especially if you're experimenting)

To answer a previous question, you'd set an A record to your IP address. If you have your own nameserver(s) as well, set the NS record(s) instead.

---

### Post by Nythain on 2008-05-28
aye, most hosting plans or domain servers are going to charge for a 'www' addy, or any prefix for that matter...

im a big fan of no-ip... thier free service is effective, and thier pay service is pretty good too... not sure how they rate on price compared to others domain registration services... but you could check em out

---

### Post by pluckypigeon on 2008-06-02
> **inportb said:**
> 

I was under the impression that you did not need a second-level domain. Why not choose a good third-level domain to start? (especially if you're experimenting)

What do you mean by second-level domain and third level-domain?

---

### Post by Joeb454 on 2008-06-02
Perhaps this link will be of interest to you? :)

[http://freedomain.co.nr/](http://freedomain.co.nr/)

---

### Post by durand on 2008-06-02
If you want a domain name to host a webserver, you should probably use a free one from dyndns.org or afraid.org. With afraid.org, you don't need to change anything in apache. (This might apply to dyndns.org as well). You just have to run a script which sends afraid.org your current ip address and it will autoforward to your ip address. Its pretty easy to setup.

For paid domain names, eg, [www.test.com](www.test.com), you will most definitely have to pay. You could also use freedomain.co.nr or dot.tk which are not really domain names but they will require a similar setup.

---

### Post by saratchandra on 2008-06-02
Firstly, it is highly recommened not to host a real website on your home computer no matter how secure you think it is. There are many free webhosts that let you host your own domain if you own one or use their subdomain like [http://yourname.freehost.com/](http://yourname.freehost.com/)
Coming to the point, although there are a couple of sites that let you register your domain for free, it takes a lot of work like posting on their forums or taking surveys. Domains are as cheap as 5 dollars these days. I'm sure somebody living in london can afford 3 or so pounds a year;)

---

### Post by saratchandra on 2008-06-02
> **durand said:**
> If you want a domain name to host a webserver, you should probably use a free one from dyndns.org or afraid.org. With afraid.org, you don't need to change anything in apache. (This might apply to dyndns.org as well). You just have to run a script which sends afraid.org your current ip address and it will autoforward to your ip address. Its pretty easy to setup.

For paid domain names, eg, [www.test.com](www.test.com), you will most definitely have to pay. You could also use freedomain.co.nr or dot.tk which are not really domain names but they will require a similar setup.

.tk is actually a real domain. You just don't have any freedom or ownership over it.

---

### Post by durand on 2008-06-02
Its not "real" unless you buy it. For example, you can't get mydomain.tk in your httpd.conf and make it so that you can just go to mydomain.tk/testfolder. It will either mask the url or redirect you to your actual ip/domain name.

EDIT: When I said "real", I meant real to the user, not the www.

---

### Post by pluckypigeon on 2008-06-02
is their a way to start your own domain names?

for example

[www.mywebsitename.my_chosen_extension](www.mywebsitename.my_chosen_extension)

---

### Post by Joeb454 on 2008-06-02
> **saratchandra said:**
> Firstly, it is highly recommened not to host a real website on your home computer no matter how secure you think it is.

Why's that? I run a website from an old 1GHz P3 in my back room :) It's been up for months.

---

### Post by durand on 2008-06-02
> **pluckypigeon said:**
> is their a way to start your own domain names?

for example

[www.mywebsitename.my_chosen_extension](www.mywebsitename.my_chosen_extension)

Yes but it's not free. Look up domain names on google. my_chosen_extension cannot be completely your choice. There is a set number of extensions.

---

### Post by saratchandra on 2008-06-02
> **Joeb454 said:**
> Why's that? I run a website from an old 1GHz P3 in my back room :) It's been up for months.

It is against the TOS of most ISPs unless you're on a commercial package. 
Your computer is never as secure as a server in a datacenter. 
Your computer can't hold high loads especially if you use a GUI in your os.

---

### Post by saratchandra on 2008-06-02
> **pluckypigeon said:**
> is their a way to start your own domain names?

for example

[www.mywebsitename.my_chosen_extension](www.mywebsitename.my_chosen_extension)

You have to choose from a large set of extensions. My advice is buy a domain. It is really worth the few bucks and you'll probably get back your money in a year.

---

