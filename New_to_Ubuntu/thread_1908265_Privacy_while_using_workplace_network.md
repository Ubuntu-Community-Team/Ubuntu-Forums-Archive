---
title: "Privacy while using workplace network"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by JuanNZ on 2012-01-13
Hi All,

I have been reading a bit about how to secure privacy while using a public network. However, I am completely lost with all the jargon and acronyms (e.g. LAN, VPN, etc).

My concise question is: if I am accessing the internet from my workplace using my personal computer, is there anyway I can prevent the network provider/administrator to track the contents of the material I am accessing? If so, can anybody recommend me a tutorial on how to achieve this?

I understand that privacy and security are not the same thing. But that will be the topic of a new tread I suppose.

I use Ubuntu 11.04 and I am very happy with it. My preferred browser is Mozilla firefox.

Cheers,

J

---

### Post by Blojic on 2012-01-13
[https://www.torproject.org/]("https://www.torproject.org/")

Is this the kind of thing you're after?

It's a bit of a sledge-hammer to crack a nut though.

---

### Post by Mark Phelps on 2012-01-13
> **JuanNZ said:**
> ... if I am accessing the internet from my workplace using my personal computer, is there anyway I can prevent the network provider/administrator to track the contents of the material I am accessing?

If you're worried about this, then basically, you should not be doing this in your workplace.

Some companies will FIRE people if they discover they are doing Internet stuff on company time.

You may be risking your very job by doing this.

---

### Post by drmrgd on 2012-01-13
> **Mark Phelps said:**
> If you're worried about this, then basically, you should not be doing this in your workplace.

Some companies will FIRE people if they discover they are doing Internet stuff on company time.

You may be risking your very job by doing this.

Absolutely!  Their network, their rules!  I would highly recommend avoiding anything that is the least bit questionable on their network.  As Mark says, doing that is cause for immediate termination at many companies.  And, if IT finds out that you've been bypassing their network monitoring tools, I believe the consequences would be just as bad.  Save the private stuff you don't want your network admin to find out about until you get home :)

---

### Post by nethero on 2012-01-13
As others have mentioned....  You risk losing your job if you access content over your employers network that is forbidden.  Also, even if you set up your computer so that your employer couldn't monitor your online activities, you may still get in trouble for attempting to bypass whatever type of network monitoring your employer has in place.  Finally, most employers networks require some type of login (unless your employer has a guest network) so even if you did conceal your data, your employer would still be able to see that encrypted data is being sent by someone using your login credentials.  Anyway, if I still haven't convinced you that what you want to do is a bad idea and you still want to go through with this then here is the knowledge you seek....

Tor and Privoxy encrypt AND bounce your data through proxies.  It is very difficult to impossible for someone to trace you when using this or to see what content you are accessing.  With that said it is NOT foolproof, especially if you don't have these applications configured properly.    I'd also recommend disabling javascript with the firefox plugin  "NoScript" and disabling flash as both javascript and flash can leak your identity to whatever sites you are accessing.  I've also heard of people using mac spoofing programs like macchanger as mac addresses can also be stored and can uniquely identify you.  Also, I'd refrain from using a computer with a hostname or username such as "JuanNZ" or anything else that can uniquely identify you.  WARNING:  This is just the stuff I know about that can be used to uniquely identify you.  Even the Tor developers admit that Tor does not provide complete anonymity.

Tor Overview here...
[https://www.torproject.org/about/overview.html.en#stayinganonymous](https://www.torproject.org/about/overview.html.en#stayinganonymous)

More Tor info...
[https://www.torproject.org/download/download.html.en#warning](https://www.torproject.org/download/download.html.en#warning)

---

### Post by Double.J on 2012-01-13
I think the previous posts sum it up, so I'll just defend the companies that employ these rules a little. It isn't just that they don't want the entire HR department spending the hour after lunch poking each other on facebook; of course they expect you to work, and some will let you take personal emails if it's relevant - the same way a personal call to your partner about picking up children from school is okay, but calling your friend to arrange going to see a film is not ;)

It's important to remember that most of the things you're not allowed to do are actually to keep the system up and safe - not just stopping you from going on youtube, but reducing the risk of you letting malware into the system- it's much easier to stop it getting in than get rid of it. You may also accidentally open their system up to attack; that could not just bring the computer network down for the rest of the day, and cause IT to work late into the evening on it, but also potentially cause the loss or theft of valuable or sensitive information.

Once you understand why they restrict and monitor communications you can see why encrypting could look so bad - if they detected an encrypted connection on their network trying to stop them seeing what's being sent and who's doing it, does that look like someone updating their twitter, or potentially stealing sensitive information?

If it's something simple such as facebook on your lunch break on your own mobile phone connected to their wifi, just ask if you can do it - if they say no, respect it.

---

### Post by Lars Noodén on 2012-01-13
In 2010 and even more so in 2011, it has been the trend to allow or even passively encourage staff to use their own devices:

[http://www.zdnet.com/blog/sybase/the-year-of-bring-your-own-computer-to-work/113](http://www.zdnet.com/blog/sybase/the-year-of-bring-your-own-computer-to-work/113)

In some cases it is turning out necessary to get the job done.  

But all that is not answering the original question. To address the original question, if you have access to an outside machine with SSH then you can use a SOCKS proxy with your web browser.  With Firefox you need to set [font=Courier New]network.proxy.socks_remote_dns[/font]=true

---

### Post by Ms. Daisy on 2012-01-13
+1 to pretty much all the previous replies.

Yes, you can prevent your employer from tracking the contents of the material you access by browsing on a network you control.  Use tor/privoxy AT HOME if it's imperative that your employer not see what you're doing.

---

### Post by nethero on 2012-01-13
> **Lars Noodén said:**
> But all that is not answering the original question. To address the original question, if you have access to an outside machine with SSH then you can use a SOCKS proxy with your web browser.  With Firefox you need to set [FONT=Courier New]network.proxy.socks_remote_dns[/FONT]=true

I wasn't aware this was possible.  I thought a web browser required a HTTP proxy in front of a socks proxy.  Like  Browser->Privoxy->Tor.  So you're saying I can do Browser->Socks Proxy->RemoteMachineWithSSH?

---

### Post by Lars Noodén on 2012-01-13
Yes.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#SOCKS_Proxy](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#SOCKS_Proxy)

Note that the example uses -C for compression.  Depending on the CPU power (or lack thereof) on either end, it might be faster without compression.  It's one of those things that you have to test and evaluate.

Also, as mentioned before, be sure to close the dns leak.

---

### Post by Frogs Hair on 2012-01-13
As stated , the employer owns everything you do at work. Some companies have very strict policies regarding intrernet use . Any failed attempt to mask your activities could result in dismissal . There is very sophisticated hardware and software available for tracking employee activity on company computers . They don't know what information you are sharing and trying to hide anything only complicates matters .

---

### Post by JuanNZ on 2012-01-13
Thanks everybody, I really appreciate your good advice. I can see that mostly everybody agrees is a bad idea to cover up your activities as that might fire the network alarms. Obviously, I would not like to loose my job.

I understand that the best way of protecting yourself against censorship and liability while at work is by avoiding using their network against their policies. 

J

---

### Post by Rainbow_Dash on 2012-01-13
I guess what you could do is setup VNC or ssh on a box at home and remotely access it so that no one would know what you're browsing unless they look over your shoulder.

---

