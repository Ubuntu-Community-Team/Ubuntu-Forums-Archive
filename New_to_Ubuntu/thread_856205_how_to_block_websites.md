---
title: "how to block websites"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-07-11
can any one please tell me how to block web sites

---

### Post by rxtx on 2008-07-11
You might find [this]("http://ubuntuforums.org/showthread.php?t=168357") post about editing the hosts file useful.

[Here]("http://ubuntu-tutorials.com/2006/12/05/user-feedback-etchosts-explained-ubuntu-510-6061-610/") is a tutorial about it's use if you're not sure.

---

### Post by phanipalagummi on 2008-07-11
i want to know how to block my own desirable wesites.
and when editted the file /etc/hosts and tried to save it said u dont have permission to edit the file.

---

### Post by prismpirate on 2008-07-11
First, enter this command into terminal

```
sudo gedit /etc/hosts
```

A text file should open up :). It should look like this:

> 
127.0.0.1	localhost
127.0.1.1	**YOUR USERNAME**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Now, we need to add your websites right? Lets say you want to block Google. We Change the file till it looks like this

> 
127.0.0.1	localhost
127.0.1.1	kiangtengl-laptop
127.0.1.1	[www.google.com](www.google.com)
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Simple right? If still confused, look at how I add yahoo to the list

> 
127.0.0.1	localhost
127.0.1.1	kiangtengl-laptop
127.0.0.1	[www.google.com](www.google.com)
127.0.0.1	[www.yahoo.com](www.yahoo.com)

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Basically, all you do is add 127.0.0.1 to the list and then followed by the website domain. Enjoy

---

### Post by kpatz on 2008-07-11
You'll need to use sudo (command line) or gksu (GUI) to launch an editor to edit the hosts file.

So, "sudo vi /etc/hosts" or "gksu gedit /etc/hosts".

---

### Post by phanipalagummi on 2008-07-11
thank you,it worked

---

### Post by mriedel on 2008-07-11
I don't think binding google.com to 127.0.0.1 is the best way to do that. A more elegant solution would be to set up a proxy server and block undesired sites through that.

---

### Post by rxtx on 2008-07-11
> **mriedel said:**
> I don't think binding google.com to 127.0.0.1 is the best way to do that. A more elegant solution would be to set up a proxy server and block undesired sites through that.

Does the job, it's quick and simple.

---

### Post by linux6994 on 2008-07-11
Look at the Firefox addons, they have content filters and such that work great.

---

### Post by timcredible on 2008-07-11
> **mriedel said:**
> I don't think binding google.com to 127.0.0.1 is the best way to do that. A more elegant solution would be to set up a proxy server and block undesired sites through that.

just in case anyone is interested in a proxy server to block undesired websites, dansguardian does exactly that, it's similar to netnanny.

---

### Post by mriedel on 2008-07-11
> **rxtx said:**
> Does the job, it's quick and simple.

I could think of a number of reasons why a proxy is better. For example, you can't display any kind of forbidden / stop viewing porn at work / whatever error page at the same time as running a service (like apache) on 127.0.0.1:80.

---

### Post by Pifilatakanemu on 2010-07-22
I created an idea for porting selfcontrol to Ubuntu:

[http://brainstorm.ubuntu.com/idea/25430/](http://brainstorm.ubuntu.com/idea/25430/)

---

### Post by renkinjutsu on 2010-07-22
> **rxtx said:**
> Does the job, it's quick and simple.

What about instances like ```
https://google.com
https://www.google.com
http://google.com
http://www.google.com
www.encryption.google.com

or perhaps even an IP address?
```

I prefer IP tables to block websites, plus I wouldn't like having "google.com" redirect me to my own apache server :p

---

### Post by bodhi.zazen on 2010-07-22
> **renkinjutsu said:**
> What about instances like ```
https://google.com
https://www.google.com
http://google.com
http://www.google.com
www.encryption.google.com

or perhaps even an IP address?
```I prefer IP tables to block websites, plus I wouldn't like having "google.com" redirect me to my own apache server :p

Honestly, it depends on what you are trying to block or filter.

If it is a few sites, it is easy to maintain a hosts file or iptables. As the number of blocked sties grows, however it becomes unwieldly.

iplist is another option:

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

If it is ads, IMO, it is easiest to use a firefox extension (adblock plus) or use a proxy. 

Privoxy and bfilter do a nice job with adblocking. Dansguardian will do porn and other undesirable sites.

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/adblock-with-bfilter/](http://blog.bodhizazen.net/linux/adblock-with-bfilter/)

Dansguardian will almost certainly need a few tweaks to the defaults as not set of defaults can possible satisify everyone with this type of content filtering (we all have unique thresholds for what is acceptable).

You can also use squid / squidguard , but IMO squid is better for large LAN then individual desktops.

The advantage of a proxy is that it is easier to configure for multiple users and multiple boxers. On my SBHO LAN I use a proxy and it is "one stop shopping" for all clients, much easier to maintain then installing adblock on each and every client.

Another option is to use opendns.

---

### Post by compweisen on 2010-07-28
I am newbie and this is the closest thread I have found to my problem.
This is the first linux box I have built and it has been rebuilt 5 times so far to correct some of my mistakes.(probably could have just uninstalled items that i did not need and moved on) but at least i feel this server will be sound.

I want to block url's and ip's current config follows

ubuntu server
sudo root problem taken care of no user
eth0 dhcp
eth1 192.168.5.1 ....
openssh installed so i can remote from laptop
other installed and WORKING packages are
shorewall
dnsmasq
squid3 same as squid
end


so here is my question
I have been in and out of many forums including this one.
I see how I can block urls and have done so. however some webmasters are more responsible than others...meaning that if i go to the ip instead of url i get redirected to the url.
but... if the web is not so responsible i do not get redirected and eve though I am blocking the URL i can still get there.

I am looking for a list like shalla or malware(which works great)
that I can easily configure to use... or if needed dansgaurdian or squidguard or something similar.
the problem is the IP addresses are not being blocked only domain urls.
the malware list work via regex..

would be a ton of work to bisect the blocklists and seperate ip's from urls and create regex lists and url lists ...


is there a better way?

---

### Post by linuxyogi on 2010-09-09
Suppose I want to block an entire TLD, like ".com" or ".net".
What exactly should I type at /etc/hosts ?

I have already tried *.com  
                      .com

None worked.

---

### Post by bodhi.zazen on 2010-09-09
> **linuxyogi said:**
> Suppose I want to block an entire TLD, like ".com" or ".net".
What exactly should I type at /etc/hosts ?

I have already tried *.com  
                      .com

None worked.

I would suggest you use a proxy server such as (depending on the size if your networks and other features) squid or privoxy.

Privoxy is easier to configure (IMO) but squid may be better on a large LAN or if you want to configure options per user or password authentication.

---

### Post by linuxyogi on 2010-09-09
> **bodhi.zazen said:**
> I would suggest you use a proxy server such as (depending on the size if your networks and other features) squid or privoxy.
.

Actually this pc is not connected to a LAN.
I have never used any proxy server before.
Just wanted to ask you, will a proxy server work on a single pc ?

---

### Post by bodhi.zazen on 2010-09-09
> **linuxyogi said:**
> Actually this pc is not connected to a LAN.
I have never used any proxy server before.
Just wanted to ask you, will a proxy server work on a single pc ?

For a single PC try privoxy. Provoxy will do, among other things, adblock out of the box.

You would need to add a rule to block all ".com".

Privoxy has a web interface which is more intuitive then the privoxy documentation.

This link may get you started :

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

---

