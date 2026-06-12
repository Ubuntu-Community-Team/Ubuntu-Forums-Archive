---
title: "Please help setting up my wifi"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by ggiorelli on 2015-08-10
Hello,

I am totally lost here. I am using Ubuntu 14 on my toshiba U505.

lspci -vnn | grep -i realtek
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. **RTL8191SEvB** Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]



I downloaded  /rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 but make command throws errors such as:

rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:319:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
      IEEE80211_HW_BEACON_FILTER |
      ^
rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:319:6: note: each undeclared identifier is reported only once for each function it appears in
rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.c:349:4: error: ‘struct ieee80211_hw’ has no member named ‘channel_change_time’
  hw->channel_change_time = 100;


Can I get some help here pls? I want to use the system with WIFI enabled. I tried all possible solved threads without luck.

Thank you
GG

---

### Post by jim_deadlock on 2015-08-10
The first thing to check is whether the wifi switch/button on your laptop is properly enabled. I often accidentally switch mine off.

Next, describe the symptoms - do you see a wifi (network manager) icon on your top panel? What does it show when you click on it?

---

### Post by ggiorelli on 2015-08-10
Wifi button is Fn+F8 on toshiba U505. It has no effect in my case.
When I go to "network connection", I see the wired connection.
When I click on the top right of the screen, the "enable Wifi" and "Wifi Networks" are  disabled (greyed out)

Thx
GG

---

### Post by ggiorelli on 2015-08-10
> **jim_deadlock said:**
> The first thing to check is whether the wifi switch/button on your laptop is properly enabled. I often accidentally switch mine off.

Next, describe the symptoms - do you see a wifi (network manager) icon on your top panel? What does it show when you click on it?

You nailed it. The switch button lol.
Issue solved. Thanks

---

### Post by sandyd on 2015-08-10
Hi, if you have found a solution to your issue, please mark this thread as solved via Thread Tools -> Mark Thread As Solved.

This will help future visitors into finding a solution.

Thanks!

---

