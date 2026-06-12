---
title: "Wired Network not connecting with Firefox"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Sylvester the Cat on 2012-01-07
I have an Asus netbook Eee PC series 1011 and I have installed Ubuntu 11.10. I have read that people have had luck just installing Ubuntu desktop on these netbooks over the Eeebuntu versions and it seems for me to be working with a few exceptions that I have no idea how to fix. 

1) First issue is with my internet connection. The wire is plugged in and I setup my IPv4 settings per required with this internet setup we have in this house. I don't have access to the router here, I just have an RJ-45 plug from the wall to my computer. Each of us has an address, with a netmask, a gateway and DNS server numbers. I have the same setup on my normal laptop here using windows. Network and connections all work fine. On the netbook, when I open Firefox it just keep trying to connect. It doesn't return a server not found, interestingly though so I'm sure I'm close but not quite there yet. I can't see how I couldn't use the same IPv4 settings on my netbook unless that is an issue, but that seems rather unlikely. If anyone has any ideas I would love to hear them. 

2) In using the Software Center I never see an Install button. Anyone have an idea why that might be?

Thanks!

---

### Post by BlinkinCat on 2012-01-07
Regarding 2), install button should appear when application is selected - :) - with more info button.

---

### Post by Sylvester the Cat on 2012-01-07
> **BlinkinCat said:**
> Regarding 2), install button should appear when application is selected - :) - with more info button.

Yeah, I saw that with the tutorial, but not for me it doesn't appear. :(

---

### Post by Sylvester the Cat on 2012-01-08
I tried switching to 10.04 LTS and I have exactly the same issues which leaves me dead in the water. I have an Asus 1011PX netbook running Ubuntu 10.04. 

I have set up the network connections with an manual setting same as above per our internet and now there isn't even a wired connection option from the drop down menu for the network. Also again there is no Install button present for any packages from the software center. 

typing in ifconfig renders
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 74:2f:68:8e:61:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Again, I'm dead in the water in knowing what to do next. Any help would be appreciated. Thanks!

---

### Post by Sylvester the Cat on 2012-01-09
I was able to test on wireless network and everything works from that side. So all issues with me are centered on the fact that I cannot detect my ethernet card or hardware for the wired connection.

---

### Post by westie457 on 2012-01-09
Hi my guess is you have IPv6 routing enabled for the wired connection. It is not strictly necessary.

To get around this right-click on the Network-Manager icon and select 'Edit Connections', in the next window you should already be on the Wired tab, select the connection named there and click edit, or if blank click on Add.

I am going with the option of 'Edit'.

In the edit connection window go to the 'IPv6' tab and set the Method to 'Ignore' or 'Automatic'. If choosing automatic check that a small box near the bottom of the window is blank (see attached screenshot).

Click apply, enter your password, then close the window and wait a few seconds for it to connect.

Hope this helps

---

