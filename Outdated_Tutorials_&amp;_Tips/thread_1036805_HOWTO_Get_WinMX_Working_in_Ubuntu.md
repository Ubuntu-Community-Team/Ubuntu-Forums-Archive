---
title: "HOWTO: Get WinMX Working in Ubuntu"
date: 2009-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Bungo Pony on 2009-01-11
Ever since I left Windows, I've been quite unhappy with Frostwire and GTK-Gnutella and longed to get WinMX running again which I've had problems with. I finally figured it out, and here's how to do it:

First, if you don't already have it, install WINE:
```
sudo apt-get install wine
```

Second, go download WinMX from here:
[http://www.mxpie.com/downloads.html](http://www.mxpie.com/downloads.html)

* Please note that v3.54 is Beta

After the .exe has downloaded, you should be able to run it by right-clicking on it and selecting "Open with Wine Windows Program Loader".

Let the install do its thing

Note: Wine may ask you to install Gecko, which you should.

After WinMX has installed and is trying to connect to the network, close it.

Open up a terminal and enter the following: 
```
sudo gedit /etc/hosts
```

After the last line in the hosts file, paste the following into it and then save it:
```

# From here down, all lines with .winmx.com, winmxgroup.com, or winmxgroup.net were added by the MXpie patch v3.6  
65.75.216.6	www.winmx.com err.winmx.com 
205.238.40.54	www.winmx.com err.winmx.com 
65.75.216.6	cache0.winmx.com test3201.winmx.com test3206.winmx.com 
65.75.216.7	cache1.winmx.com test3202.winmx.com test3207.winmx.com 
82.43.229.238	cache2.winmx.com test3203.winmx.com test3208.winmx.com 
205.238.40.1	cache3.winmx.com test3204.winmx.com 
205.238.40.2	cache4.winmx.com test3205.winmx.com 
65.75.216.6	c3310.z1301.winmx.com c3310.z1302.winmx.com c3310.z1303.winmx.com c3310.z1304.winmx.com c3310.z1305.winmx.com c3310.z1306.winmx.com 
65.75.216.6	c3311.z1301.winmx.com c3311.z1302.winmx.com c3311.z1303.winmx.com c3311.z1304.winmx.com c3311.z1305.winmx.com c3311.z1306.winmx.com 
65.75.216.6	c3312.z1301.winmx.com c3312.z1302.winmx.com c3312.z1303.winmx.com c3312.z1304.winmx.com c3312.z1305.winmx.com c3312.z1306.winmx.com 
65.75.216.7	c3313.z1301.winmx.com c3313.z1302.winmx.com c3313.z1303.winmx.com c3313.z1304.winmx.com c3313.z1305.winmx.com c3313.z1306.winmx.com 
65.75.216.7	c3314.z1301.winmx.com c3314.z1302.winmx.com c3314.z1303.winmx.com c3314.z1304.winmx.com c3314.z1305.winmx.com c3314.z1306.winmx.com 
65.75.216.7	c3315.z1301.winmx.com c3315.z1302.winmx.com c3315.z1303.winmx.com c3315.z1304.winmx.com c3315.z1305.winmx.com c3315.z1306.winmx.com 
82.43.229.238	c3316.z1301.winmx.com c3316.z1302.winmx.com c3316.z1303.winmx.com c3316.z1304.winmx.com c3316.z1305.winmx.com c3316.z1306.winmx.com 
82.43.229.238	c3317.z1301.winmx.com c3317.z1302.winmx.com c3317.z1303.winmx.com c3317.z1304.winmx.com c3317.z1305.winmx.com c3317.z1306.winmx.com 
205.238.40.1	c3318.z1301.winmx.com c3318.z1302.winmx.com c3318.z1303.winmx.com c3318.z1304.winmx.com c3318.z1305.winmx.com c3318.z1306.winmx.com 
205.238.40.2	c3319.z1301.winmx.com c3319.z1302.winmx.com c3319.z1303.winmx.com c3319.z1304.winmx.com c3319.z1305.winmx.com c3319.z1306.winmx.com 
65.75.216.6	c3520.z1301.winmx.com c3520.z1302.winmx.com c3520.z1303.winmx.com c3520.z1304.winmx.com c3520.z1305.winmx.com c3520.z1306.winmx.com 
65.75.216.6	c3521.z1301.winmx.com c3521.z1302.winmx.com c3521.z1303.winmx.com c3521.z1304.winmx.com c3521.z1305.winmx.com c3521.z1306.winmx.com 
65.75.216.6	c3522.z1301.winmx.com c3522.z1302.winmx.com c3522.z1303.winmx.com c3522.z1304.winmx.com c3522.z1305.winmx.com c3522.z1306.winmx.com 
65.75.216.7	c3523.z1301.winmx.com c3523.z1302.winmx.com c3523.z1303.winmx.com c3523.z1304.winmx.com c3523.z1305.winmx.com c3523.z1306.winmx.com 
65.75.216.7	c3524.z1301.winmx.com c3524.z1302.winmx.com c3524.z1303.winmx.com c3524.z1304.winmx.com c3524.z1305.winmx.com c3524.z1306.winmx.com 
65.75.216.7	c3525.z1301.winmx.com c3525.z1302.winmx.com c3525.z1303.winmx.com c3525.z1304.winmx.com c3525.z1305.winmx.com c3525.z1306.winmx.com 
82.43.229.238	c3526.z1301.winmx.com c3526.z1302.winmx.com c3526.z1303.winmx.com c3526.z1304.winmx.com c3526.z1305.winmx.com c3526.z1306.winmx.com 
82.43.229.238	c3527.z1301.winmx.com c3527.z1302.winmx.com c3527.z1303.winmx.com c3527.z1304.winmx.com c3527.z1305.winmx.com c3527.z1306.winmx.com 
205.238.40.1	c3528.z1301.winmx.com c3528.z1302.winmx.com c3528.z1303.winmx.com c3528.z1304.winmx.com c3528.z1305.winmx.com c3528.z1306.winmx.com 
205.238.40.2	c3529.z1301.winmx.com c3529.z1302.winmx.com c3529.z1303.winmx.com c3529.z1304.winmx.com c3529.z1305.winmx.com c3529.z1306.winmx.com 
65.75.216.6	winmx-com.winmxgroup.com winmx-com-v30.winmxgroup.com 
205.238.40.54	winmx-com.winmxgroup.com winmx-com-v30.winmxgroup.com 
65.75.216.6	test0.winmxgroup.net test5.winmxgroup.net 
65.75.216.7	test1.winmxgroup.net test6.winmxgroup.net 
82.43.229.238	test2.winmxgroup.net 
205.238.40.1	test3.winmxgroup.net 
205.238.40.2	test4.winmxgroup.net 
65.75.216.6	cache0.winmxgroup.com cache5.winmxgroup.com cache0.winmxgroup.net cache5.winmxgroup.net cache10.winmxgroup.net cache15.winmxgroup.net 
65.75.216.7	cache1.winmxgroup.com cache6.winmxgroup.com cache1.winmxgroup.net cache6.winmxgroup.net cache11.winmxgroup.net cache16.winmxgroup.net 
82.43.229.238	cache2.winmxgroup.com cache7.winmxgroup.com cache2.winmxgroup.net cache7.winmxgroup.net cache12.winmxgroup.net cache17.winmxgroup.net 
205.238.40.1	cache3.winmxgroup.com cache8.winmxgroup.com cache3.winmxgroup.net cache8.winmxgroup.net cache13.winmxgroup.net cache18.winmxgroup.net 
205.238.40.2	cache4.winmxgroup.com cache9.winmxgroup.com cache4.winmxgroup.net cache9.winmxgroup.net cache14.winmxgroup.net cache19.winmxgroup.net 
```

After you have saved your updated hosts file, restart WinMX, and it should connect!

---

