---
title: "Will not remember WEP code for network connection"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by mrag on 2012-04-07
Dual boot with XP. When starting Ubuntu 11.10 I put in password then also have to put in WEP to get network connection. Need to do this every time. Using Roswell Wireless N 1T1R USB adapter. Works fine with Windows, works fine with Ubuntu other than with Ubuntu I have the extra step to enter WEP each time. Did not have this issue with older USB adapter and 11.04. More annoying than trouble.

---

### Post by xedi on 2012-04-07
I had the same issue before but it was fixed easily.

Try the following: click the wireless symbol, click edit connections.

There go to wireless and look for the Wi-Fi you want to log into. Click edit.

Go to Wireless Security. When I had the bug, the password section was blank, even though I put in the password and clicked that it should remember it. However, after putting the password there and clicking save the problems were gone and it remembered the password from then on.

I don't know why this happened in the first place, especially in my case after working fine for months.

---

### Post by alphacrucis2 on 2012-04-07
> **mrag said:**
> Dual boot with XP. When starting Ubuntu 11.10 I put in password then also have to put in WEP to get network connection. Need to do this every time. Using Roswell Wireless N 1T1R USB adapter. Works fine with Windows, works fine with Ubuntu other than with Ubuntu I have the extra step to enter WEP each time. Did not have this issue with older USB adapter and 11.04. More annoying than trouble.


Note the WEP is not a secure protocol. It is very easily cracked using readily available software. You should configure your wireless access point to require WPA2 with a strong pre shared secret key. That said, network manager does remember my WPA2 psk, so what you are seeing may be a bug related specifically to WEP.

---

### Post by mrag on 2012-04-08
@xedi...that seems to have fixed  it. Thanks! No idea why I didn't try that before.

@alpha...will look into moving beyond WEP. Appreciate suggestion. Is there a tutorial you recommend, been a while since I set up the network. I'd have to allow for XP, Vista, iPad, Win7, Ubuntu

---

### Post by xedi on 2012-04-08
Not 100% sure about the Ipod, but I think all of them should support WPA on the software side.

Your Wi-Fi card and router have to support WPA, too, though. Unless they're ancienct (in computer time) this should be the case. You need to look up how to setup your router so it uses WPA (the procedure differs depending on what model you have) everything else should work similar to WEP.

In case your hardware does not support WPA but only WEP, I would consider buying a new router/card, because as Alpha says, WEP has been cracked for some years now.

Edit: Just looked up your adapter, WPA should work. Now you just have to check whether your router does and how to configure it.

---

