---
title: "Ubuntu 12.04 LTS with ATT Uverse Wireless"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by ThunderFuz275 on 2013-05-04
How do I set up my wireless connection? I've put in my SSID code, Device MAC Address and set my security to WPA & WPA2 Personal and entered my password.  I am obviously missing something very important because I cannot see an option to enable a wireless network.  Please help me.  I am a very new user to the LINUX and Ubuntu worlds.

---

### Post by carl4926 on 2013-05-04
You should post for us the result of

```
[COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]

```

---

### Post by alhefner on 2013-05-04
Yes, post the output of that command that you run in a terminal window (ctrl+alt+t). Also, have you clicked the ico just to the right of the battery icon at the upper right part of your screen? It should drop down a list of available networks and connections and you should choose yours. For wireless connections, the list should include all the wireless networks within range... yours should be in that list.

---

