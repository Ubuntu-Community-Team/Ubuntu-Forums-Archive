---
title: "Could not download repository indexes"
date: 2008-07-01
forum: Philippine Team
---

### Post by unit_731 on 2008-07-01
guys! need your suggestion about this!!!


eto lang laging lumalabas pag nag update ako thru..

apt-get install or syaptic package manager

[IMG]http://i39.photobucket.com/albums/e187/gore_pinas/Screenshot.png[/IMG]

i try changing diffent server pero ganito lagi nalabas!??


any suggestions guys!??


TIA!

---

### Post by loell on 2008-07-01
hi,  comment out mo lang ang cdrom repo sa'yong  **sources.list**

lagyan mo nang **[COLOR="Blue"]#[/COLOR]**, ie

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080319)]/ hardy main restricted
```

---

### Post by loell on 2008-07-01
eheh, may simpleng paraan pala.. :D


pumunta ka sa **System Menu** --> **Software Sources** -->  uncheck mo ang **Cdrom with Ubuntu**

[ATTACH]75918[/ATTACH]

---

### Post by unit_731 on 2008-07-01
ok lang ba kung yun ang gagawin ko!??


para san yung repository na yun!?? 


TIA

---

### Post by loell on 2008-07-01
ok lang,

cd repo lang yun..

---

### Post by wersdaluv on 2008-07-01
> **unit_731 said:**
> ok lang ba kung yun ang gagawin ko!??


para san yung repository na yun!?? 


TIA

Ibig sabihin non, ginagamit niya yung Ubuntu CD mo as a software source. Di niya madownload kasi hindi nakalagay yung cd mo. Para wala nang ganong notification, gawin mo na lang yung sabi ni loell. 

Kung maayos naman ang internet connection mo, hindi mo naman kakailanganin ang Ubuntu cd mo as a software source kasi pwede mo naman download yung software online :)

---

### Post by unit_731 on 2008-07-03
Thanks Guys sa mga Reply!!! :KS

---

