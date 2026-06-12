---
title: "wireless connection through command line"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by hdanap on 2012-01-09
**wireless connection** 			
 			 			 		   		 		 		Hi All,

I recently was trying to upgrade from virtual box 4.0 to virtual box  4.1, when trying to do that I realized it wasn't working so I checked  online I found that I had to remove virtualbox 4.0 before i could  install the 4.1 version, which I did.

After that I rebooted my system but on restarting,  everything was gone  from my desktop, like the sidebar with the icons and the top panel that  holds the wireless connect bar, empathy bar, volume, time and settings  are all gone.

So now im trying to upload my files on-line so i can reinstall Ubuntu  completely to try to set everything right but Now i dont know how to  connect to the internet without the top panel that holds the INTERNET  signal thingy that I can just click and connect to my wind mobile  broadband stick.

What is the best advise as I don't want to lose my files and when I tried sending everything to the a usb drive I just cant. 

When i tried using my ubuntu live CD , It wouldn't let me access my  files as it keeps telling me that i have no permission to access the  file even after i tried changing the permission.

Please what can i do.

if i create a back up file will i be able to access it after i reinstall seeing that i can't access it now?

I could upload the files online but i can't access the web. If I can  connect my broadband stick(dongle) to the web, then I could just upload  all files to something like 4shared.com, reinstall ubuntu ocelot 11.10  and download all my files easy, but I dont know how to connect via  command line.

Any advise will be very much appreciated.

Thanks

HELP

---

### Post by Double.J on 2012-01-09
> **hdanap said:**
> **wireless connection**             
                                                                Hi All,

I recently was trying to upgrade from virtual box 4.0 to virtual box  4.1, when trying to do that I realized it wasn't working so I checked  online I found that I had to remove virtualbox 4.0 before i could  install the 4.1 version, which I did.

After that I rebooted my system but on restarting,  everything was gone  from my desktop, like the sidebar with the icons and the top panel that  holds the wireless connect bar, empathy bar, volume, time and settings  are all gone.

So now im trying to upload my files on-line so i can reinstall Ubuntu  completely to try to set everything right but Now i dont know how to  connect to the internet without the top panel that holds the INTERNET  signal thingy that I can just click and connect to my wind mobile  broadband stick.

What is the best advise as I don't want to lose my files and when I tried sending everything to the a usb drive I just cant. 

When i tried using my ubuntu live CD , It wouldn't let me access my  files as it keeps telling me that i have no permission to access the  file even after i tried changing the permission.

Please what can i do.

if i create a back up file will i be able to access it after i reinstall seeing that i can't access it now?

I could upload the files online but i can't access the web. If I can  connect my broadband stick(dongle) to the web, then I could just upload  all files to something like 4shared.com, reinstall ubuntu ocelot 11.10  and download all my files easy, but I dont know how to connect via  command line.

Any advise will be very much appreciated.

Thanks

HELP

I may be missunderstanfing the issue, but can you connect by singing in in 2d Unity? - sign out and select the cog next to the box where you enter your username and select the 2d option?

---

### Post by z3nhakr on 2012-01-09
```

sudo service network-manager stop

iwconfig

sudo iwconfig **"your network device"** essid **“your essid(network name)”** key **"your router key(the password)"**


```BTW if your key is ASCII apposed to hex then put s: in front of the key

---

### Post by hdanap on 2012-01-09
> **z3nhakr said:**
> ```

sudo service network-manager stop

iwconfig

sudo iwconfig **"your network device"** essid **&#8220;your essid(network name)&#8221;** key **"your router key(the password)"**


```BTW if your key is ASCII apposed to hex then put s: in front of the key
  
Thanks for the assistance guys, but I'm using one of those Internet sticks and really I have never used anything like essid, a router or anything of the sort, i always just inserted the broadband stick, then just connect.

Any thots, I have been on the phone with my isp for hour and those guys don't even know what the essid is.

I will try asking again, but if any other suggestions will be greatly depreciated.

Thanks 

PS. I use Huawei Mobile Broadband HSPA Rotate Usb Stick, and I'm in Canada. Hope that helps.

Thanks

---

