---
title: "Troubles, and lack of tutorials..."
date: 2012-07-03
forum: New to Ubuntu
---

### Post by pooloo1 on 2012-07-03
My goal is to have a fully functional server that provides web hosting, minecraft hosting, as well as mumble voice communications. I have the hardware, and bandwidth.

Routing my domain using Name Servers instead of the servers hard IP address. I believe this is accomplished with BIND9? I've found several tutorials and will follow them to hopefully get my domain directed to my server. I also have access to several different IP's, so mumble can have one, and the website would use one, and the game server would use another.

The main issue is I am trying to setup links to each service, but I cannot find a documentation or article or tutorial describing what I need to teach me. For example, I want a mumble.example.com:64738 which is used in the Mumble client, game.example.com:25565 which is used in the Minecraft client, and a generic [www.example.com](www.example.com).

(example.com is for examples.)

What am I looking for exactly to get this properly setup?

Also, nginx or Apache2? I want to get python environment up and running using uWSGI more then likely. But I am unsure which direction to go...

Please help me out, been destroying my brain for a few days now. 

Ubuntu 12.04 32-bit, might switch to 64-bit if needed.

---

### Post by Cheesemill on 2012-07-03
There's really no need to set up your own BIND server, it just adds uneeded complexity to your set up.

You should just be able to use the name servers of the company that you register your domain name with. All you need to do is add a record for each of your subdomains (game.example.com, mumble.example.com etc) that points to your IP address.

Also as the applications you are installing all use different ports there is no reason for you to set up subdomains. You could just have [www.example.com](www.example.com) that gets used for all of the applications.

---

### Post by pooloo1 on 2012-07-03
Registered the domain with Godaddy, but its only domain not hosting. I am providing my own hosting, so I would have to setup my own nameserver not?

---

### Post by CharlesA on 2012-07-03
> **Cheesemill said:**
> There's really no need to set up your own BIND server, it just adds uneeded complexity to your set up.

Agreed.

> You should just be able to use the name servers of the company that you register your domain name with. All you need to do is add a record for each of your subdomains (game.example.com, mumble.example.com etc) that points to your IP address.

The domain registrar I use allows DNS management, but when I had to transfer my domain to a webhost in order to get everything started, that host didn't allow DNS administration.

In any case, you should be able to just add an A (host) record for whatever subdomain you want to use.

> Also as the applications you are installing all use different ports there is no reason for you to set up subdomains. You could just have [www.example.com](www.example.com) that gets used for all of the applications.

Yep, you would still have to specify the port. DNS does not allow you to specify what domain name goes to what port.

> **pooloo1 said:**
> Registered the domain with Godaddy, but its only domain not hosting. I am providing my own hosting, so I would have to setup my own nameserver not?

No. Just add an A record for the IP of the box you are hosting it on.

See here for more info on configuring dns:
[http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names](http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names)

---

### Post by Cheesemill on 2012-07-03
> **pooloo1 said:**
> Registered the domain with Godaddy, but its only domain not hosting. I am providing my own hosting, so I would have to setup my own nameserver not?
No.

Just use Godaddy's DNS Manager to point your domain name to your IP.
[http://support.godaddy.com/help/category/915/managing-your-dns](http://support.godaddy.com/help/category/915/managing-your-dns)

---

### Post by pooloo1 on 2012-07-03
> **CharlesA said:**
> 
The domain registrar I use allows DNS management, but when I had to transfer my domain to a webhost in order to get everything started, that host didn't allow DNS administration.

In any case, you should be able to just add an A (host) record for whatever subdomain you want to use.

No. Just add an A record for the IP of the box you are hosting it on.

> **Cheesemill said:**
> No.

Just use Godaddy's DNS Manager to point your domain name to your IP.
[http://support.godaddy.com/help/category/915/managing-your-dns](http://support.godaddy.com/help/category/915/managing-your-dns)

Ahh.. I've found the small tiny little hidden box that allows for creating my own "host" sub-domains. Had to scroll down in an area that didn't look like it existed.

Wouldn't in be beneficial to learn how to create my own name server though? LOL

Appreciate all the help for my blindness and stupidity, that I've provided in this post. I feel really stupid for missing that option now...

-------
Now, my other question(s).

Any recommendations as to Nginx vs Apache? For python uWSGI, and maybe some php. I also want to do some educational play with Node.js/Go Language/etc.

---

### Post by CharlesA on 2012-07-03
I use Apache for my web server, but I have heard good things about Nginx.

---

