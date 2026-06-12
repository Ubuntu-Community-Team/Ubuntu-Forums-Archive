---
title: "Ubuntu 9.04 help"
date: 2009-04-28
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-04-28
I just downloaded the Latest version of ubuntu but it cant download any of its updates or packages. it can't also open any web page but it can detect networks through wireless lan so there is a network cnnection or internet... 

what do you think is the Problem????



please help

---

### Post by Script Warlock on 2009-04-28
its also good to know if you included the specs of your macine and the system message logs..hirap maghula

---

### Post by loell on 2009-04-28
in the command line type **ifconfig**

see if theres actually an assigned address.

---

### Post by Lila_IT_CMU on 2009-04-29
ok i will try the ifconfig...how about the address? anu po b ung ilalagay kong address?

tnx...

---

### Post by loell on 2009-04-29
if it's DHCP then the address is supplied automatically , this is the usual case with wireless.

just copy paste the output.

---

### Post by adredz on 2009-04-29
it could be that you're connectoin can't pass through your DNS? maybe there's a maintenance going on? hula lang :)

---

### Post by Lila_IT_CMU on 2009-04-30
here is my ifconfig:




eth0      Link encap:Ethernet  HWaddr 00:90:f5:8a:09:3c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:19 Base address:0xdead  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
 
wlan0     Link encap:Ethernet  HWaddr 00:15:af:d5:df:1c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-D5-DF-1C-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


:confused:

---

### Post by loell on 2009-04-30
```
wlan0 Link encap:Ethernet HWaddr 00:15:af:d5:df:1c
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

detected naman sya, pero wala ngang address, baka yung wireless router di pa nacoconfigure.

---

### Post by wersdaluv on 2009-04-30
Are you sure that you're connected to the wireless router?

---

### Post by dodimar on 2009-04-30
Anong laptop to? yung ibang laptop may switch ng wireless network.. baka naka lagay sa off.. detected yung hardware pero di mag transmit ng signal...

---

### Post by Lila_IT_CMU on 2009-04-30
anu po b ung wireless router and paano po iconfigure un??
Realtek rtl8187b ung wireless ko


NEO Basic po ung laptop ko. 


nakakadetect cya ng wireless signal at nakakaconnect din pero hindi maka open ng kahit anung website and hindi rin makakadownload ng mga packages at updates...

---

### Post by Lila_IT_CMU on 2009-04-30
Re: Ubuntu 9.04 help 

--------------------------------------------------------------------------------

anu po b ung wireless router and paano po iconfigure un??
Realtek rtl8187b ung wireless ko


NEO Basic po ung laptop ko. 


nakakadetect cya ng wireless signal at nakakaconnect din pero hindi maka open ng kahit anung website and hindi rin makakadownload ng mga packages at updates...

---

### Post by Lila_IT_CMU on 2009-04-30
Re: Ubuntu 9.04 help 

--------------------------------------------------------------------------------

anu po b ung wireless router and paano po iconfigure un??
Realtek rtl8187b ung wireless ko


NEO Basic po ung laptop ko. 


nakakadetect cya ng wireless signal at nakakaconnect din pero hindi maka open ng kahit anung website and hindi rin makakadownload ng mga packages at updates...

---

### Post by Script Warlock on 2009-05-01
bka pwede mo muna derekta konek yung lan cable sa laptop mo para madali trobolsoting. i'm neo too wala problema sa akin its plug and play even the wif. dun lang ako nagkaproblema sa nadownload kung 9.04 installer may error kaya nagdownload ako uli ng iso/torrent. didn't mean reinstall since this is an inresting trobol. cguro naginstall ka with wifi? or install ka with lan. kung naginstall ka with wifi tapos wifi mo di pala gumana yung inet connection ewan bka di lahat naextract ng ubuntu during installation. have you tried sa live cd lahat before installing including the lan and wifi? dami speculations.

---

### Post by Lila_IT_CMU on 2009-05-01
> **loell said:**
> ```
wlan0 Link encap:Ethernet HWaddr 00:15:af:d5:df:1c
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

detected naman sya, pero wala ngang address, baka yung wireless router di pa nacoconfigure.



ano po ba ung wireless router? paano po iconfigure un??

---

### Post by Lila_IT_CMU on 2009-05-01
> **boyet said:**
> bka pwede mo muna derekta konek yung lan cable sa laptop mo para madali trobolsoting. i'm neo too wala problema sa akin its plug and play even the wif. dun lang ako nagkaproblema sa nadownload kung 9.04 installer may error kaya nagdownload ako uli ng iso/torrent. didn't mean reinstall since this is an inresting trobol. cguro naginstall ka with wifi? or install ka with lan. kung naginstall ka with wifi tapos wifi mo di pala gumana yung inet connection ewan bka di lahat naextract ng ubuntu during installation. have you tried sa live cd lahat before installing including the lan and wifi? dami speculations.


ok try ko i-connect sa LAN cable... susubukan ko rin mag reinstall...dual boot w/ Windows Vista kasi tong Laptop ko...

---

### Post by Script Warlock on 2009-05-01
no probs yan kahit dual, triple or multi kc were tracing the why and how it started...reinstall ka? wak muna bka pwede pa trobolsot natin dami pa mga master di pa nag butt-in.

kung konekted ka na sa inet update sa cli at kung may error sa update something like cdrom go to software sources at unchek ang cdrom tapos reload and update again. kung di ka makaupdate puro failed to fetch then chek if you have inet koneksyon.

---

### Post by Lila_IT_CMU on 2009-05-01
> **boyet said:**
> no probs yan kahit dual, triple or multi kc were tracing the why and how it started...reinstall ka? wak muna bka pwede pa trobolsot natin dami pa mga master di pa nag butt-in.

kung konekted ka na sa inet update sa cli at kung may error sa update something like cdrom go to software sources at unchek ang cdrom tapos reload and update again. kung di ka makaupdate puro failed to fetch then chek if you have inet koneksyon.


ahmm... ok... ung main problem ko talaga is nakakaconnect sya via wireless pero hindi talaga nakakaupdate and hindi nakakaopen ng kahit anung website...hindi ko pa po nagagalaw ung software sources ko...pati pag find ng best server error kasi ndi daw connected sa internet eventhough nakaconnect na sya kasi nakalagay sa network sa upper right ng screen "Connection Established"... Un po...Ano sa tingin mo??

---

### Post by loell on 2009-05-01
> **Lila_IT_CMU said:**
> ahmm... ok... ung main problem ko talaga is nakakaconnect sya via wireless 

base sa output mo, wala kang connection sa wireless. 

re: **what is wireless router,** best describe in the diagram.

[IMG]http://www.neoplayer.com/multibox/shop/images/Linksys-wireless-router.jpg[/IMG]

[IMG]http://z.about.com/d/compnetworking/1/0/g/3/wireless-diagram-1.jpg[/IMG]

kita mo yung laptop? yun dapat ang kadalasang setup.

---

### Post by Script Warlock on 2009-05-01
> **Lila_IT_CMU said:**
> ahmm... ok... ung main problem ko talaga is nakakaconnect sya via wireless pero hindi talaga nakakaupdate and hindi nakakaopen ng kahit anung website...hindi ko pa po nagagalaw ung software sources ko...pati pag find ng best server error kasi ndi daw connected sa internet eventhough nakaconnect na sya kasi nakalagay sa network sa upper right ng screen "Connection Established"... Un po...Ano sa tingin mo??

konek muna direct sa modem ng isp mo tapos lets see if makaupdate ka na tapos ...#-o kaya cguro di ka makaupdate or open anything sa browser kc wala koneksyon inet mo...tingin diagram ni boss loell

---

### Post by Lila_IT_CMU on 2009-05-01
> **boyet said:**
> konek muna direct sa modem ng isp mo tapos lets see if makaupdate ka na tapos ...#-o kaya cguro di ka makaupdate or open anything sa browser kc wala koneksyon inet mo...tingin diagram ni boss loell


ok po tnx...try ko lahat ng paraan...ill tell u all na lng pag ok na po...

---

