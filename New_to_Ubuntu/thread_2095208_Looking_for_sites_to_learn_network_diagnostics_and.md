---
title: "Looking for sites to learn network diagnostics and security"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Acharn on 2012-12-16
I've had many years of experience with computers, so I'm not afraid of the command line, but I don't know as much as I need to know about networking and how to analyze what's going on. I hope somebody can recommend some web sites that can teach me how to use the tools that are available in the Un*xes. I know, for example, there is a program called netstat, but I'd like to find a web site that is a little easier to understand than the man page. I remember, years ago, on guy showing me a program that captured and examined packets, but I don't remember what its name was. I think I really need some sites that teach beginners about basic security administration for Linux, too.

---

### Post by chadk5utc on 2012-12-16
> **Acharn said:**
> I've had many years of experience with computers, so I'm not afraid of the command line, but I don't know as much as I need to know about networking and how to analyze what's going on. I hope somebody can recommend some web sites that can teach me how to use the tools that are available in the Un*xes. I know, for example, there is a program called netstat, but I'd like to find a web site that is a little easier to understand than the man page. I remember, years ago, on guy showing me a program that captured and examined packets, but I don't remember what its name was. I think I really need some sites that teach beginners about basic security administration for Linux, too.

Ill get you started a little
[http://www.linuxhowtos.org/Network/netstat.htm](http://www.linuxhowtos.org/Network/netstat.htm)
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)
There are probably a dozen packet/network analyzers wireshark,etherape

---

### Post by Ms. Daisy on 2012-12-16
The way I started learning was to just fire up wireshark and look at the output. When I encountered something I didn't understand I googled it. I never found a less ADHD way to learn it although I'm sure there's a way.

Some other resources to look at:
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)
[http://msdaisysramblings.blogspot.com/2012/12/reading-firewall-logs.html](http://msdaisysramblings.blogspot.com/2012/12/reading-firewall-logs.html)

Wireshark has oodles of tutorials on their website.
[http://www.wireshark.org/docs/](http://www.wireshark.org/docs/)

Basic linux hardening:
[http://www.irongeek.com/i.php?page=videos/derbycon2/3-3-4-chris-jenks-intro-to-linux-system-hardening](http://www.irongeek.com/i.php?page=videos/derbycon2/3-3-4-chris-jenks-intro-to-linux-system-hardening)

---

### Post by Acharn on 2012-12-17
Thank you. That looks like what I had in mind but couldn't articulate well yesterday. I stumbled across one of the old bookmarks that was very important to me, the ONLAMP website.They used to have dozens, maybe hundreds, of accessible articles. I never heard of wireshark; sounds very interesting. I've forgotten so much over the last five years of not working with it. The technicians from my ISP came today and replaced my router, so now I'm experiencing what I thought the Internet should be. It helps.

---

### Post by JKyleOKC on 2012-12-17
> **Acharn said:**
> I never heard of wireshark; sounds very interesting.The name "wireshark" is comparatively new but the program itself isn't. It got the new name a year or two ago and I've already forgotten what the old name was. It's probably the same program you mentioned originally that let you see all the packets and told you what each meant!

I second Ms. Daisy's suggestion that you simply trawl around and read anything that looks at all relevant. I've been into networking one way or another for more than 50 years and helped set up the first cross-country connections (Phoenix, AZ to Boston via Oklahoma City) back in the early 70s, but that's not a lot of help with today's technology. Following discussions such as this one gets much quicker results!

---

### Post by haqking on 2012-12-17
> **JKyleOKC said:**
> The name "wireshark" is comparatively new but the program itself isn't. It got the new name a year or two ago and I've already forgotten what the old name was. It's probably the same program you mentioned originally that let you see all the packets and told you what each meant!

I second Ms. Daisy's suggestion that you simply trawl around and read anything that looks at all relevant. I've been into networking one way or another for more than 50 years and helped set up the first cross-country connections (Phoenix, AZ to Boston via Oklahoma City) back in the early 70s, but that's not a lot of help with today's technology. Following discussions such as this one gets much quicker results!

It has been called Wireshark for about 6 years, originally it was Ethereal, it is really a GUI based pretty TCPDump

---

