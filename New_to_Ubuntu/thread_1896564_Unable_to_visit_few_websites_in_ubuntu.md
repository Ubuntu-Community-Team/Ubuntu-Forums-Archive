---
title: "Unable to visit few websites in ubuntu"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by rajnikhil on 2011-12-17
Recently a wierd issue cropped up in my two ubuntu machines and wireless router. I can visit a few websites and can't visit others, I've mainly faced this problem visiting some websites which show 'waiting for s7.addthis.com' in the browser. Again this seems to be problem when I'm surfing the net either in ubuntu or when my modem is connected to wi-fi router, when I surf these websites in windows they open up without a glitch.

This problem started after my ISP changed my username recently. Can somebody please help me out on this ASAP as I can't afford to switch back and forth between windows and ubuntu as most of my work is accomplished in Ubuntu.

Please let me know what info you'd need to resolve this and I'll post it.

Thanks in advance.

---

### Post by bwallum on 2011-12-17
I've noticed some Internet issues too. BBC News went wobbly for a day this week, friends report access to bank sites being affected. It seems to resolve itself.

However, I have been getting some error messages than say a Chrome script is running, am I sure I want to close Thunderbird?

I'll start a 'Why do I get messages saying a Chrome script is running when I close Thunderbird' thread.

---

### Post by lovinglinux on 2011-12-17
Use [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/) and [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865/). They block those add/tracking sites that are making your connection time out.

---

### Post by rajnikhil on 2011-12-17
Wow, that was such a simple solution, how stupid of me! Anyways thanks a ton for helping me out Lovinglinux.:guitar:

---

### Post by lovinglinux on 2011-12-17
> **rajnikhil said:**
> Wow, that was such a simple solution, how stupid of me! Anyways thanks a ton for helping me out Lovinglinux.:guitar:

You are welcome. Enjoy a faster and cleaner web.

---

### Post by rajnikhil on 2011-12-26
Ok I seem to have another problem. The issue of not being able to view certain websites was resolved by installing the adblock plus add-on in the firefox but it seems this problem still exists in a different form.

I have a wireless router in my internet circuitry i.e. the internet goes to the modem (UT-300R2U) provided by my ISP which is inturn connected to the Belkin Wireless G Router (model: F5D7230-4) and I'm intermittently able to connect view websites while I'm connecting to internet thourgh the router (generally when the router and modem have been just powered up). This is happening, both, when I try to open website in laptop by wifi and when I try to open website through my desktop which is wired to this router (both linux).

Can somebody please let me know what is the issue and how to resolve it. Its annoying that I can't connect wirelessly as I have several devices which are wifi enabled. 

(Damn my ISP for changing whatever they changed recently :-(  )

---

### Post by rajnikhil on 2011-12-28
> **rajnikhil said:**
> Ok I seem to have another problem. The issue of not being able to view certain websites was resolved by installing the adblock plus add-on in the firefox but it seems this problem still exists in a different form.

I have a wireless router in my internet circuitry i.e. the internet goes to the modem (UT-300R2U) provided by my ISP which is inturn connected to the Belkin Wireless G Router (model: F5D7230-4) and I'm intermittently able to connect view websites while I'm connecting to internet thourgh the router (generally when the router and modem have been just powered up). This is happening, both, when I try to open website in laptop by wifi and when I try to open website through my desktop which is wired to this router (both linux).

Can somebody please let me know what is the issue and how to resolve it. Its annoying that I can't connect wirelessly as I have several devices which are wifi enabled. 

(Damn my ISP for changing whatever they changed recently :-(  )

Can somebody please help me out on this, feel like hammering the router:(

---

### Post by androssofer on 2011-12-28
> **rajnikhil said:**
>  I'm intermittently able to connect view websites while I'm connecting to internet thourgh the router (generally when the router and modem have been just powered up). This is happening, both, when I try to open website in laptop by wifi and when I try to open website through my desktop which is wired to this router (both linux).  )

could you clarify what you mean by this? 

so you can view websites for a while after turning your router and model. but then it stops working?

and the same thing occurs both on wireless and wired connections?

---

### Post by rajnikhil on 2011-12-28
> **androssofer said:**
> 
so you can view websites for a while after turning your router and model. but then it stops working?

Yes, that is what is happening.

> **androssofer said:**
> 
and the same thing occurs both on wireless and wired connections?

Both, my desktop as well as laptop are usually connected to the net simultaneously. The desktop is connected to the wireless router via ethernet cord and laptop by means of wifi.

feel free to let me know if you require any other info for helping me resolve this issue.

---

### Post by alphacrucis2 on 2011-12-28
> **rajnikhil said:**
> Yes, that is what is happening.



Both, my desktop as well as laptop are usually connected to the net simultaneously. The desktop is connected to the wireless router via ethernet cord and laptop by means of wifi.

feel free to let me know if you require any other info for helping me resolve this issue.

Maybe you should try a fault call to your ISP.

---

### Post by rajnikhil on 2011-12-29
I don't think that'd be much of help because if I am connecting to the internet directly through the modem in Windows then the net seems to be working absolutely fine as ever. The problem arises when I'm trying to view websites in ubuntu either connected directly to modem or through the router. I also have issues viewing websites when connected to the net through the wireless router even in windows. However in all the combinations mentioned above torrent download seem to work absolutely fine.

As I see it, the problem seems to be with either or with both ubuntu and my wireless router and things seems fine with the ISP itself.

---

### Post by androssofer on 2011-12-29
> **rajnikhil said:**
> I don't think that'd be much of help because if I am connecting to the internet directly through the modem in Windows then the net seems to be working absolutely fine as ever. The problem arises when I'm trying to view websites in ubuntu either connected directly to modem or through the router. I also have issues viewing websites when connected to the net through the wireless router even in windows. However in all the combinations mentioned above torrent download seem to work absolutely fine.

As I see it, the problem seems to be with either or with both ubuntu and my wireless router and things seems fine with the ISP itself.

does ubuntu die when its direct though the modem? 

seems like an ISP or router problem to me. Happens to me on sundays when students come home from the country and kill the internet in the area. i restart the router and its fine. Both on windows and ubuntu. 

how new it the router? i had to replace my mums 1 because its from the stone age and would die if you tried to stream more than 1 youtube video. 

next time it dies. open up the terminal and type:

```
traceroute www.google.com
```

it will show all the network devices your signal goes through to get to google. the first few will be to your router and to your isp, they should be quite quick (<100ms i think). if they are large it should show where the hold up is.

if you can, post the output here, but take out any ip addresses in the first few results, for safety :-)

---

### Post by rajnikhil on 2012-01-01
Ok so the ISP technician confirmed that there is no issue no issue with settings of the ISP  and I'm getting a decent internet speed of 256Kbps and when connected to the modem directly in wondows the connection works just fine so the issue has definetly got to be with ubuntu and router. 

To confirm if there is a problem with buntu settings I tried to connect to it through live cd option but no change and the connection was just as bad, that's wierd.

Any ideas any body what could be wrong?

---

### Post by z3nhakr on 2012-01-01
are you running ubuntu and windows on the same machine?
what is the output of ifconfig

---

### Post by rajnikhil on 2012-01-03
> **z3nhakr said:**
> are you running ubuntu and windows on the same machine?
Yes I have both windows and ubuntu on my laptop

> **z3nhakr said:**
> what is the output of ifconfig
Following is the output of ifconfig when my desktop is directly connected to the modem:

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:94:83:5c  
          inet6 addr: fe80::21a:4dff:fe94:835c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1130813 (1.1 MB)  TX bytes:200071 (200.0 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2524658 (2.5 MB)  TX bytes:2524658 (2.5 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.195.134.180  P-t-P:117.195.128.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:171822 (171.8 KB)  TX bytes:14474 (14.4 KB)

Another thing I noticed is that now my dynamic ip address starts from 117.xxx.xxx.xxx whereas ealier it used to be like 95.xxx.xxx.xxx

---

