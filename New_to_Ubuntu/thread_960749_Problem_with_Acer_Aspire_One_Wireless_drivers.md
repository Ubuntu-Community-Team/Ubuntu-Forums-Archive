---
title: "Problem with Acer Aspire One Wireless drivers"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by nairb101 on 2008-10-27
I just installed Ubuntu onto my netbook. I followed the instructions located at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) for installing the wireless card drivers. 

The first method using madwifi didnt work at all, so I switched to using ndiswrapper and downloading the drivers located on that site.

Now, I can log onto unencrypted Wifi just fine. The problem is, here at OSU (Ohio), the students wifi is encrypted. It uses a WPA enterprise key. When I enter in all the data correctly, it hangs up.

For example, I enter in my user name, encryption type, password, ect. I click connect, and the icon in the bar changes to two dots with some blue swirls. Neither dot lights up, and the mouse hover is "waiting for network key".

My question is this: Does WPA enterprise work using the drivers I installed? additionally, why is it stuck waiting for a key I just entered? many thanks.

---

### Post by miner49er on 2008-12-24
Just thought I would mention that I _think_ I have a work-around for the problem with using the madwifi drivers with the acer aspire one - after trying everything.

So, if your problem is intermittent or no connection at all - I found I could sometimes connect but if I checked the status of the connection using ifconfig ath0, it would sometimes say RUNNING and sometimes not - you can either disable WEP on the router, or, as I found disable WEP, then connect, then re-enable WEP then reconnect. It works for me every time I restart the router.

If this doesn't make sense then I can explain again if neccesary.

---

