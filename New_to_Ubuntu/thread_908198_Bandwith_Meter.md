---
title: "Bandwith Meter"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by misswham on 2008-09-02
My isp is going to start limiting bandwith.  Is there a bandwith meter for linux that I can install to track it and if it is will it be able to track it with dualboot with XP?

---

### Post by Trail on 2008-09-02
Naturally, you can't install one program that will work on both of you dualboot OSes, now, could you? You'll need a separate meter for each system, then manually add up the values (or have a script read the windows values, or something similar).

I do not know of any bandwidth meters (seriously, though, change ISP :D), but ifconfig provides such information. For example:

```

eth0      Link encap:Ethernet  HWaddr 00:1D:09:B3:14:E6
          ...
          RX bytes:142370948 (135.7 Mb)  TX bytes:10354785 (9.8 Mb)
          Interrupt:17

```


Geek mode: It should be easy to write a little script that calculates this in 1 minute increments (using cron, ifconfig, the boot-timestamp so you can associate ifconfig readings, and grep/awk).

---

### Post by Cypher on 2008-09-02
On Comcast are ya? :) I think a lot of people get a little worked up about the bandwidth limitation. Comcast is saying they're going to limit to 250 GBs a month of transfer. For a 100% of regular Internet users this is completely fine and will not pose any problems.

The only people this will likely cause issues for are those who torrent a lot, and the bandwidth limitation is likely focused at those users anyway.

Even if a regular user were to Internet surf all day, do emails, listen to music online they will be nowhere near the bandwidth limit imposed by ISPs..

---

### Post by billgoldberg on 2008-09-02
> **misswham said:**
> My isp is going to start limiting bandwith.  Is there a bandwith meter for linux that I can install to track it and if it is will it be able to track it with dualboot with XP?

You will be able to read it from your ISP's home page.

---

### Post by jemate18 on 2008-09-02
> **misswham said:**
> My isp is going to start limiting bandwith.  Is there a bandwith meter for linux that I can install to track it and if it is will it be able to track it with dualboot with XP?

Check this... Its a cool way to check your speed
> [http://pldt.speedtest.net/](http://pldt.speedtest.net/)

---

### Post by arpanaut on 2008-09-02
> **billgoldberg said:**
> You will be able to read it from your ISP's home page.Nope, at present Comcast FAQ is saying that you will need to monitor your usage yourself.

As you say, "most" users have nothing to worry about, as the limit at the present time is pretty generous... may not be in the future.

Another example of the "Few spoiling things for the Many."
Such is life!

---

### Post by jemate18 on 2008-09-02
did you guys visited the link I gave above?

It really works and not to mention a cool design

---

### Post by Cypher on 2008-09-02
> **jemate18 said:**
> did you guys visited the link I gave above?

It really works and not to mention a cool design

Speedtest is great for measuring throughput/bandwidth for a single action. The OP was looking for info about total data transmitted..

---

### Post by arpanaut on 2008-09-02
Yeah, technically bandwidth is speed/capacity of a connection at a given time.

What we are concerned with here is "bandwidth volume" i.e. data volume over a given connection over a period of time. (re: monthly usage limits)

Yes that is a useful site but not pertitant to this discussion... Matter of semantics/definitions. 

No Biggie

---

### Post by jemate18 on 2008-09-02
> **arpanaut said:**
> Yeah, technically bandwith is speed/capacity of a connection at a given time.

What we are concerned with here is "bandwidth volume" i.e. data volume over a given connection over a period of time. (re: monthly usage limits)

Yes that is a useful site but not pertitant to this discussion... Matter of semantics/definitions. 

No Biggie

oh.. sorry guys.. i misunderstood the first post...

---

