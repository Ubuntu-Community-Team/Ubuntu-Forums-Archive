---
title: "problem importing pgp key"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by soufiane.android on 2014-10-08
when i want to import pgp-key i have this problem 

[IMG]http://4.bp.blogspot.com/-MQiPdca0cG8/VDUdvAqvDaI/AAAAAAAAGFs/uZX8_MFnqzk/s1600/Screenshot%2Bfrom%2B2014-10-08%2B12%3A17%3A20.png[/IMG]

---

### Post by Lars Noodén on 2014-10-08
What method did you use to acquire the key?

---

### Post by soufiane.android on 2014-10-08
in the termimal 
=>
nano pgp-key 
i past this =>
[COLOR=#333333][FONT=arial]-----BEGIN PGP PUBLIC KEY BLOCK-----[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Version: SKS 1.1.4[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Comment: Hostname: keyserver.ubuntu.com[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]mI0ET324YwEEANbSlISrOlAGjxgFRxiN6jk0JIl/[/FONT][/COLOR][COLOR=#333333][FONT=arial]*vxQ8lapRdxZ4DHDAQdXbX4AuigMBkP5e[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sOxhMpDnkgMRtEVpaBMdQheA0/431pPQYqkr3jde[/FONT][/COLOR][COLOR=#333333][FONT=arial]*Zw5JS5opiyJ4qr/QrcoSFHSluEkWkbZ6[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]RYOkA25vW31KK2FB2LQVRYk580llXAVgIUznm2AT[/FONT][/COLOR][COLOR=#333333][FONT=arial]*ABEBAAG0GExhdW5jaHBhZCBQUEEgZm9y[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]IHdhZ3VuZ4i4BBMBAgAiBQJPfbhjAhsDBgsJCAcD[/FONT][/COLOR][COLOR=#333333][FONT=arial]*AgYVCAIJCgsEFgIDAQIeAQIXgAAKCRAb[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]IuuNj9/bVxabBADSGN8cp+hqkdZqwq263wdz/UGs[/FONT][/COLOR][COLOR=#333333][FONT=arial]*iuB1bCrH06/HznC/ZC5rjfH3aQ1Dwwag[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]zYCrSD3c0cKNAqD10009N76RMlzZBH8kKL9khH3z[/FONT][/COLOR][COLOR=#333333][FONT=arial]*PL/k4/lYuVP7y6NKFbBsnawEUc0mWcCa[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]mH4ScTdWWPXP/mOQiUUjnQ1bZhzpcbQOb+hEUAqE[/FONT][/COLOR][COLOR=#333333][FONT=arial]*xg==[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]=fJ+8[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]-----END PGP PUBLIC KEY BLOCK-----
and i save it[/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-10-08
There seem to be some invalid characters repeated in it.  Where did you get it from?  There might be a problem with the key itself or else a more reliable way to get the key in the first place.

---

### Post by soufiane.android on 2014-10-08
here => [http://pastebin.com/XFdcrrvS](http://pastebin.com/XFdcrrvS)

 i want to install kali linux tools

---

### Post by Lars Noodén on 2014-10-08
Paste bin is not a reputable source of keys.  :( 

I would look elsewhere for the Kali linux key.   I see the PPA here:

[https://launchpad.net/~wagungs/+archive/ubuntu/kali-linux](https://launchpad.net/~wagungs/+archive/ubuntu/kali-linux)

So the key would be here (by following the above link)

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0xEC48840B131FCB4F9BCB82431B22EB8D8FDFDB57&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0xEC48840B131FCB4F9BCB82431B22EB8D8FDFDB57&op=index)

Try that one instead.

---

### Post by soufiane.android on 2014-10-08
thank you so much 
the problem is solved

---

