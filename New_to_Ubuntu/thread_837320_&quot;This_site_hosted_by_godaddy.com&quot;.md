---
title: "&quot;This site hosted by godaddy.com&quot; ?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by muguwmp67 on 2008-06-22
I've been getting this message and placeholder site quite often lately.  It seems to come up when a site's reply has been delayed.  Although I'm sure that some of the sites involved are hosted by godaddy, I got this message from my isp's (cable company) webmail server today.  

I find it really hard to believe that my isp would host their systems on another server.

Is there some sort of Firefox exploit involved here?  Can anyone tell me whats going on?  I'd much rather get a 401 error than a list of sketchy sponsored links.

---

### Post by cariboo on 2008-06-22
To find who owns a web site and who is hosting it use whois. In a Applications-->Accessories-->Terminal: enter the following:

```
whois www.example.com
```

Replace example.com with url of the site you want to check. If you know the ip address you can enter that instead.

Jim

---

### Post by muguwmp67 on 2008-06-22
Okay, as I expected, its says that bex.net is registered by Buckeye Cablesystem.  

> Registrant:
Buckeye Cablevision, Inc.
   5566 Southwyck Boulevard
   Toledo, OH 43614
   US

   Domain Name: BEX.NET

   ------------------------------------------------------------------------
   Promote your business to millions of viewers for only $1 a month
   Learn how you can get an Enhanced Business Listing here for your domain name.
   Learn more at [http://www.NetworkSolutions.com/](http://www.NetworkSolutions.com/)
   ------------------------------------------------------------------------

   Administrative Contact:
      Buckeye Cablevision, Inc.		[email]pshryock@CABLESYSTEM.COM[/email]
      5566 Southwyck Boulevard
      Toledo, OH 43614
      US
      (419) 724-9802 fax: 999 999 9999

   Technical Contact:
      Network Solutions, LLC.		[email]customerservice@networksolutions.com[/email]
      13861 Sunrise Valley Drive
      Herndon, VA 20171
      US
      1-888-642-9675 fax: 571-434-4620

   Record expires on 26-Dec-2012.
   Record created on 03-Sep-2004.
   Database last updated on 22-Jun-2008 15:12:04 EDT.

   Domain servers in listed order:

   NS1.BUCKEYECOM.NET           72.240.1.105
   NS2.BUCKEYECOM.NET           72.240.1.106
   NS3.BUCKEYECOM.NET           67.130.82.97


So I ask again, why would I be redirected to a godaddy placeholder?

---

### Post by ThreeLies on 2008-06-22
Just a random thought, could you possibly have some hosts rediect.

Look into your file at "/etc/hosts", see if there is any strange entries.

---

### Post by muguwmp67 on 2008-06-22
I don't know what the following is, but it looks pretty mundane.

> # The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

It just happened to me at live.xbox.com, there's no way that xbox.com is hosted by godaddy.

[http://live.xbox.com/default.html?aspxerrorpath=/en-US/default.aspx](http://live.xbox.com/default.html?aspxerrorpath=/en-US/default.aspx)

Everything was fine after refreshing the link.

---

### Post by Moop on 2008-06-22
It could be your dns server redirecting the non-responding sites. Try changing the dns server you use to opendns or a public dns server.

---

### Post by nashphyl on 2008-06-22
this is actually a bit unrelated to this thread but i am desperate. I dont know how to make a new post, only reply to existing posts. Can someone send me a message telling me how i can do this? Thanks

---

### Post by unutbu on 2008-06-22
How to post: [http://ubuntuforums.org/showthread.php?t=726150&highlight=make+thread](http://ubuntuforums.org/showthread.php?t=726150&highlight=make+thread)

---

