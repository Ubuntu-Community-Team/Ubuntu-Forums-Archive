---
title: "Wireless Wont Connect"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by bongani13 on 2013-08-19
Hi I'm very new ubuntu. Just installed today. Everything works great, but when i try to connect to the wireless, it refuses to do so. It takes a few seconds to authenticate my password, then the wireless authentication windows keeps coming back up, its an endless cycle, no matter what i try. The wep im entering is definitely correct so i don't know what the problem is. My desktop doesn't have an internal wireless, so I'm using a tp link wireless adapter.

---

### Post by carl4926 on 2013-08-19
IMO you should switch to WPA 
WEP is not secure.

IIRC you need the complete HEX key for WEP, not the passphrase, but I could be wrong. I don't see WEP used at all now, must be 5yrs since I came across it.

---

### Post by eric-c-arellano on 2013-08-19
which version have you installed, also do you have any interent access and it just keeps dropping or can you not get on at all?

---

### Post by bongani13 on 2013-08-19
ive installed 13.04. no internet access at all. It shows all the wireless networks but when i try to connect to the one here, it just keeps bouncing me back to the authentication screen.

---

### Post by bongani13 on 2013-08-19
the network security is not really up to me.

---

### Post by carl4926 on 2013-08-19
> **bongani13 said:**
> the network security is not really up to me.
Then request the HEX key
It's probably 128 characters. Only the router admin will have access to that.
Though I do seem to recall connecting to a WEP AP about a year ago on my travels, with just a passphrase. I'm not sure.

---

### Post by bongani13 on 2013-08-19
Will give that a try. I stay on a student rezsidence, so theres a chance that they may not give that to me. DO i have any other options?

---

### Post by bongani13 on 2013-08-19
Correction not a wep key. wpa2 or something like that.

---

### Post by xarlin2 on 2013-08-19
same problem with me I use [proxy servers]("http://hideipaddresswhendownloading.com/hide-the-ip-address-of-your-computer-browser-settings-proxy-servers-and-vpns/") still stuck Password..

---

### Post by carl4926 on 2013-08-19
> **bongani13 said:**
> Correction not a wep key. wpa2 or something like that.

So it's WPA not WEP?!

WPA just requires a password

Universities are notorious for being silly bluggers with their AP's

Have you confirmed that your wireless works elsewhere, say at a coffee shop?

---

### Post by grahammechanical on 2013-08-19
> It shows all the wireless networks

Therefore, the wireless adapter is switched on and it is recognised by Ubuntu. It is an authentication issue. The password is not our log in password but the password to the wireless access point. It is also called the wireless key or the WPA-PSK key. It might be a 10 alpha-numeric character string.

Would would happen if you tried to access some else's wireless network and it was secured by a password? You would get the result that you are getting now. You are in effect trying to access a secured wireless access point without having the authenication code.

Regards.

---

### Post by bongani13 on 2013-08-20
I enter the password, and it just keeps bouncing back to the authentication box.
Ive got a desktop so its rather unlikely to get that chance. But my girl friend installed the same version on her laptop and she can connect to the wireless at her rez. It seems to be just mine having issues connecting here.

---

### Post by bongani13 on 2013-08-20
The password is correct. It hasnt changed at all. It worked fine when i was using windows, its only now with ubuntu that its giving me hassles.

---

### Post by Vladlenin5000 on 2013-08-20
Hint: Mark the case "show password" and confirm once and for all whether or not you're entering the correct password. The usual culprits are Caps Lock and or Num Lock (in a laptop's keyboard and some character happens to be in the part of the keyboard that is changed to the numeric keyboard).
Another hypotheses: The network you're trying to connect to has been configured for "n only" and you have a b/g WiFi device -> The network is still visible, allows authentication but it won't connect because the hardware isn't supported.

(EDIT)

Even if it worked before with Windows XP in the same machine and considering the second hypotheses it could be that the driver you're using in Ubuntu doesn't support "n". It usually happens with certain Ralink chipsets for which Ubuntu installs a generic open source driver that only supports b/g.

---

