---
title: "Windows Server Security?"
date: 2010-06-04
forum: Recurring Discussions
---

### Post by kevin11951 on 2010-06-04
From an objective point of view, what is the quality of the security of Windows Server 2008 R2 (or 2003, etc...)?

In comparison to Debian Stable 5 for example.

If I setup a LAMP (WAMP) stack on both, identical software versions of Apache, MySQL, and PHP.  Who has better security in the end?

What about **IIS**, MySQL, and PHP (also in terms of security)?

I have been looking on Google, and a few other places, and have yet to find anything definitive on the subject.  The Microsoft hatred has died down around here, so I figure its safe to ask, and get a legitimate response.

Thank you,
-Kevin

---

### Post by jerenept on 2010-06-04
This is a subject likely to be volatile...
but, in my view, the LAMP (Linux/Apache/MySQL/PHP) stack is waay safer and more secure, and can serve more customers on the same hardware (besides being Free!)

---

### Post by kevin11951 on 2010-06-05
> **jerenept said:**
> This is a subject likely to be volatile...
but, in my view, the LAMP (Linux/Apache/MySQL/PHP) stack is waay safer and more secure, and can serve more customers on the same hardware (besides being Free!)

2 days, no posts... Volatile? Not quite. ;)

aka... Bumb!

---

### Post by cariboo on 2010-06-05
The Cafe may not be the right place to ask your question, Moved to Security Discussions, but it could just as well be in the Server Platforms sub-forum

---

### Post by bodhi.zazen on 2010-06-05
> **cariboo907 said:**
> The Cafe may not be the right place to ask your question, Moved to Security Discussions, but it could just as well be in the Server Platforms sub-forum

Moved to recurring discussions as it appears to be a Windows vs Linux.

If you run a server learn to secure it, all OS can be hardened.

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

Try a Windows forums for Windows security.

---

### Post by Wiebelhaus on 2010-06-05
A secure totally windows server doesn't exist.

---

### Post by kamaboko on 2010-06-05
The definitive answer is: it's only as secure as your knowledge of the OS.

---

### Post by aysiu on 2010-06-05
Doesn't it depend on what you want to run on the server?

For example, if you want to run a server for Microsoft Exchange / Active Directory / Cisco CallManager, can you do that on a Linux server?

And if you want to run Apache, MySQL, and PHP, any good reason to run that on a Windows server?

---

### Post by Xianath on 2010-06-05
aysiu is right. You have to run the right tools for the job. Microsoft has a lot to offer on the server front but WAMP is not its strong point.

Windows Server, IIS, ASP.NET and SQL Server offer significant advantages over LAMP in a lot of areas. For example, setting up a Windows cluster to handle high availability is a pretty straight-forward job that Tier-1 support can handle. Same goes for database management such as users, permissions, backup, restore, migration etc. Those tasks in LAMP require significant knowledge, higher risk, and generally more human time.

LAMP can be completely free and even with a commercial Linux distribution the license costs are lower than those of a Microsoft server. It does however require higher running costs in terms of maintenance. Downtime, costs of human error, and the sheer cost of good geeks can outweigh differences in license prices in less than a year.

To your original question, a properly administered Windows server is probably as secure as any LAMP box out there. Attacks against the server itself are extremely rare as compared to those exploiting the human factor. Failure to properly harden, patch and configure a server will expose it regardless of the underlying technology used. Exploring zero-day vulnerabilities is rare and Microsoft IMHO pays much more attention to its server products when it comes to patching those.

On one of my previous jobs we encountered several issues with SQL Server 2005 which caused it to crash under load, and Microsoft sent us a beta patch over the weekend. It was later released separately, and then as part of SP1. In comparison, Novell failed to provide a patch for the 2.6.8.5 kernel (SLES9) which caused it to panic under heavy CIFS load. Ultimately we had to migrate all of our users to SLES10, but not before moving to a third-party commercial CIFS client to avoid crashes.

To summarize, Microsoft server products, as far back as Windows 2000 Server, have been a completely different world from their desktop OS'es in terms of stability, performance and stability. I've had Windows servers run for months, only rebooting on updates that required it. In fact I've never had a Windows server crash hard on me, which alas I can't say about Linux, much as I like it. Part of that likely states from the fact that many Windows servers run on specialized hardware from respectable vendors, and Linux ones are more likely to be retired desktops or underpowered servers. Also, certified administrators are common in the Windows world whereas self-taught enthusiasts seem to be the norm in the Linux world. So all in all, the groundwork is there in both OS'es, it's how one manages them that makes the biggest difference.

---

### Post by juancarlospaco on 2010-06-05
@aysiu: Zimbra / LDAP / Asterisk(?)

---

### Post by HermanAB on 2010-06-06
The Windows server OSs are OK.  You can get configuration help on the NSA and Microsoft Technet pages:
> Microsoft Windows Security Guidance, National Security Agency United States of America, [http://www.nsa.gov/ia/guidance/security_configuration_guides/operating_systems/microsoft_windows.shtml](http://www.nsa.gov/ia/guidance/security_configuration_guides/operating_systems/microsoft_windows.shtml)

---

### Post by kevin11951 on 2010-06-09
I always heard Linux (Debian Stable) was much more secure than Windows Server...  Is that just flat out not true?

---

### Post by bodhi.zazen on 2010-06-09
> **kevin11951 said:**
> I always heard Linux (Debian Stable) was much more secure than Windows Server...  Is that just flat out not true?

It is an opinion and it depends on who you ask. You will get a very different answer on a Linux Forums and a windows Forums.

A cursory google search will take you to the debate sites.

I think you misunderstand security. Security is NOT install it and forget it. Security is understanding how an OS works under the hood and monitoring for vulnerabilities.

For example:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/index.html)

[http://www.puschitz.com/SecuringLinux.shtml](http://www.puschitz.com/SecuringLinux.shtml)

Similar guides exist for windows.

IMO Linux is more secure out of the box then Windows out of the box, but, security is only as good as your local sys admin, holds true of any OS.

---

### Post by kevin11951 on 2010-06-09
> **bodhi.zazen said:**
> It is an opinion and it depends on who you ask. You will get a very different answer on a Linux Forums and a windows Forums.

A cursory google search will take you to the debate sites.

I think you misunderstand security. Security is NOT install it and forget it. Security is understanding how an OS works under the hood and monitoring for vulnerabilities.

For example:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Security_Guide/index.html)

[http://www.puschitz.com/SecuringLinux.shtml](http://www.puschitz.com/SecuringLinux.shtml)

Similar guides exist for windows.

IMO Linux is more secure out of the box then Windows out of the box, but, security is only as good as your local sys admin, holds true of any OS.

Oh, no I understand security is a "process".  What I mean is things like IIS vs Apache, and how Apache has fewer security bugs and things like that.

---

### Post by bodhi.zazen on 2010-06-09
> **kevin11951 said:**
> What I mean is things like IIS vs Apache, and how Apache has fewer security bugs and things like that.


IMO those discussions are empty opinions.

---

### Post by Xianath on 2010-06-09
> **kevin11951 said:**
> Oh, no I understand security is a "process".  What I mean is things like IIS vs Apache, and how Apache has fewer security bugs and things like that.

Not according to the Common Vulnerabilities (CVE) database. Have a look:

```
ppopov@nas:/tmp$ for prod in windows linux microsoft iis 'information server' apache; do zgrep -i "${prod}" allitems.csv.gz > "${prod}.csv"; done

ppopov@nas:/tmp$ wc -l *.csv | sort -nr
    8310 total
    3278 linux.csv
    2255 microsoft.csv
    2096 windows.csv
     443 apache.csv
     209 iis.csv
      29 information server.csv

```

Linux has ~50% more reported and/or confirmed vulnerabilities than all Microsoft products combined (of which about 80% are attributed to Windows). Apache (including Tomcat and other Apache projects) has 100% more than IIS.

I must admit I was surprised, too.

---

### Post by del_diablo on 2010-06-09
> **Xianath said:**
> Not according to the Common Vulnerabilities (CVE) database. Have a look:

```
ppopov@nas:/tmp$ for prod in windows linux microsoft iis 'information server' apache; do zgrep -i "${prod}" allitems.csv.gz > "${prod}.csv"; done

ppopov@nas:/tmp$ wc -l *.csv | sort -nr
    8310 total
    3278 linux.csv
    2255 microsoft.csv
    2096 windows.csv
     443 apache.csv
     209 iis.csv
      29 information server.csv

```

Linux has ~50% more reported and/or confirmed vulnerabilities than all Microsoft products combined (of which about 80% are attributed to Windows). Apache (including Tomcat and other Apache projects) has 100% more than IIS.

I must admit I was surprised, too.

Now we must ask the crititial question YOU forgot: Why are there more reposted problems on the Linux part?
Has it something to do with that there errors gets REPORTED and FIXED? Which means in practical terms it is more secure?
Or?

---

### Post by Xianath on 2010-06-10
> **del_diablo said:**
> Now we must ask the crititial question YOU forgot: Why are there more reposted problems on the Linux part?
Has it something to do with that there errors gets REPORTED and FIXED? Which means in practical terms it is more secure?
Or?

I was merely stating facts based on numbers. Everything else, including my answer below, is personal opinion and therefore speculation.

I think a lot of it has to do with distro proliferation. Many of these issues are distro-specific. Remember the Debian RNG bug? Or the times when RedHat was dubbed "RootHack"? Also take into account market penetration. Few vulnerabilities are reported against desktop systems (browsers are an exception) and Linux is a strong player on the server market. It may also have something to do with the FOSS development model itself. Few FOSS projects  have the benefit of a fully dedicated security team under their own steam.

That said, the breakdown by years shows an interesting picture. In the past five years, Linux security has been steadily improving and is now above the 10-year average, whereas in Windows it's exactly the opposite. Here's another speculative question: do you think this is related to Ubuntu and Vista? If yes, do you think the spike in Linux vulnerabilities in 2004 is related to the introduction of Ubuntu Desktop and its market penetration, and the steady improvement a direct result of Ubuntu Server introduced in 2007?

Statistics is a funny science. According to it, everyone has, on average, just about one testicle :)

---

