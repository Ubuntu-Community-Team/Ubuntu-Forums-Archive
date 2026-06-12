---
title: "[SOLVED] ip addresses"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by tazz4vr on 2008-09-07
I am trying to find out some info.  Is there anywhere I can go to seek assistance in the tracing of an ip address or computer.  Is that legal?  Is that something that I can do?  Basically, received email and just want to verify that it is from where the person is stating it's from.
I was advised to seek info from a tech person, thought i was, so need help with this one.

---

### Post by iaculallad on 2008-09-07
> **tazz4vr said:**
> I am trying to find out some info.  Is there anywhere I can go to seek assistance in the tracing of an ip address or computer.  Is that legal?  Is that something that I can do?  Basically, received email and just want to verify that it is from where the person is stating it's from.

It's not illegal to trace an IP address. Use this [link]("http://www.geobytes.com/ipLocator.htm") to start tracing an IP.

EDIT: It's not illegal as long as you "Just look but don't touch".

---

### Post by jemate18 on 2008-09-07
> **tazz4vr said:**
> I am trying to find out some info.  Is there anywhere I can go to seek assistance in the tracing of an ip address or computer.  Is that legal?  Is that something that I can do?  Basically, received email and just want to verify that it is from where the person is stating it's from.
I was advised to seek info from a tech person, thought i was, so need help with this one.

As far as I know... Taking a peep into an IP address ain't illegal.. Just looking at wont hurt.... but doing something out of that..(malicious things).. thats a different thing...

---

### Post by tazz4vr on 2008-09-07
> **jemate18 said:**
> As far as I know... Taking a peep into an IP address ain't illegal.. Just looking at wont hurt.... but doing something out of that..(malicious things).. thats a different thing...

Thanks for the info.  I assure you, nothing malicious, just wanting to verify info before continuing with a particular person.  As I am a newbie on the research info in regards to the ip address, i am told that the emails are coming from a place of employment, will the ip address tell/show me that it's coming from that specific job or a place of residence?

---

### Post by tuxxy on 2008-09-07
Use Ubuntu Network Tools

System > Admin > Network Tools

---

### Post by Tatty on 2008-09-07
> **tazz4vr said:**
> will the ip address tell/show me that it's coming from that specific job or a place of residence?

Its unlikely, although i am not an expert, however it should be able to show you the rough geographic area it is coming from, and the ISP they are connecting through. 

To find out further information you would have to contact their ISP with the details you know.  But of course they are unlikely to give you any information on their customer unless you are a law enforcement agency.

---

### Post by chrisod on 2008-09-07
If the email is coming from a company you may get the company name from a whois lookup. If it was sent from a home PC more likely all you'll get is the ISP. You can try a traceroute to the IP address and maybe pick up some more location info. A lot of ISPs have their routers named by city so on the final hops before it gets to a mail server you may see router.address.nyc.something that may or may not be an indicator that the sender is in or near NYC. If it's a smaller regional ISP then they probably are. If it's AT&T who knows how they are routing stuff.

---

### Post by tazz4vr on 2008-09-07
Thank you all for your input and helpful tips.  I will definitely be putting these to use.  As I already know the person, not sure has been completely honest with me as to place of business.  For my own peace of mind, want to verify that an email originated from where he said it did, after recent conversation, things are just a little sketchy, enough for the questions now.
Thank you for all your help.

---

### Post by bab1 on 2008-09-07
Use ```
whois nnn.nnn.nnn.nnn
``` where nnn=IP address.  This will give you the owner of the IP address.  Note that IP addresses can be spoofed.

---

### Post by tazz4vr on 2008-09-07
> **bab1 said:**
> Use ```
whois nnn.nnn.nnn.nnn
``` where nnn=IP address.  This will give you the owner of the IP address.  Note that IP addresses can be spoofed.

Unfortunately, i did not know that ip addresses can be messed with.  Thanks for the info, so it is possible that if this person knows the ip address of a particular company, they could make theirs look the same, if they thought it would be researched?  I don't think that is the case here, they more than likely do not think it's something that I would question at this point.

---

### Post by tazz4vr on 2008-09-08
Was able to get enough info to proceed.  Unfortunately the ip address found in the email is definitely not from where this person claims to work.  
Thank you all so much for the help and keeping me from making a big mistake by continuing further communication with this person.  Thank you very much.

---

### Post by IusedTObeSOMEONEelse on 2008-09-08
> **bab1 said:**
> Use ```
whois nnn.nnn.nnn.nnn
``` where nnn=IP address.  This will give you the owner of the IP address.  Note that IP addresses can be spoofed.

My question for this:
when receiving E-Mails, how do you get the numerical address? I mean that I am shown only that it's from:** ***.@ddd.com**
 no number to put in** whois**

---

### Post by tazz4vr on 2008-09-08
> **MustangSallydd said:**
> My question for this:
when receiving E-Mails, how do you get the numerical address? I mean that I am shown only that it's from:** ***.@ddd.com**
 no number to put in** whois**

Not sure on other emails, but via yahoo, it shows in the full header.  Didn't know this until needed to find the origination of an email.  Although info that was provided in this post was great, ultimately a member of this forum helped me get the info I needed, not that I was looking forward to it, but I got what I needed.

---

### Post by billgoldberg on 2008-09-08
> **tazz4vr said:**
> Thanks for the info.  I assure you, nothing malicious, just wanting to verify info before continuing with a particular person.  As I am a newbie on the research info in regards to the ip address, i am told that the emails are coming from a place of employment, will the ip address tell/show me that it's coming from that specific job or a place of residence?

No.

It will show you a general location somewhere in the neighborhood of the address.

This could be off by a few cities.

If they are using a proxy, this could be off by a few continents :p
--

The only way to be sure it's coming from that address is asking it to their ISP. But they won't give you that information as it would violate privacy laws in just about all countries.

---

### Post by tazz4vr on 2008-09-08
With the information I was provided with and under the impression on, the orig email should have came from a specific company, however, it appeared to have orig in USPS office, perhaps a public puter or something.  In any case, it didn't provide physical address or name of user, but it gave me the info I needed.

---

### Post by tazz4vr on 2008-09-09
fyi...knowing that I am not too knowledgable with the computer stuff, he wasnt aware that I know where to seek assistance and the amount of knowledge known by the Ubuntu crew. Our conversations have ceased to exist at this point. [-(
Thank you again for your help.

---

### Post by aomlives on 2008-09-09
You can mark your thread as "solved" by going to "Thread Tools". I think that's what you were trying to do with the "(Resolved)" in your post title. :)

---

### Post by tazz4vr on 2008-09-09
yes, that is what I was trying to do...thank you..im such a duh sometimes....

---

