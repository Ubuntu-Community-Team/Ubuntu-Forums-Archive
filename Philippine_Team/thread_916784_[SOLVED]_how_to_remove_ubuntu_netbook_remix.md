---
title: "[SOLVED] how to remove ubuntu netbook remix"
date: 2008-09-11
forum: Philippine Team
---

### Post by ache109 on 2008-09-11
Guys,

Pede po bang i-uninstall ang ubuntu netbook remix. Ang bagal kasi ng interface sa pc ko dahil may metacity. Eh yung ubuntu hindi supported ang vidcard ko kaya walang visual effects... YAn tuloy ang bagal na.. hayyyyy buhay.

Or kung pede ma-remove ung metacity effects....


e2 ung pic...(Wala ung top panel dahil nga dun.)

---

### Post by wersdaluv on 2008-09-11
I think, you mean, compiz effects. Go to the "Appearance" dialog then to the "Effects Tab." Select "None."

---

### Post by loell on 2008-09-12
if you installed NBR like this

```
sudo apt-get install window-picker-applet maximus go-home-applet human-netbook-theme ume-launcher
```

just do the reverse to uninstall it. ;)

```
sudo apt-get remove window-picker-applet maximus go-home-applet human-netbook-theme ume-launcher
```

but i'm worried that you mentioned **metacity**, as it really doesn't use it.  

its using maximus. are you sure you're on netbook remix?

---

### Post by ache109 on 2008-09-12
> **loell said:**
> if you installed NBR like this

```
sudo apt-get install window-picker-applet maximus go-home-applet human-netbook-theme ume-launcher
```

just do the reverse to uninstall it. ;)

```
sudo apt-get remove window-picker-applet maximus go-home-applet human-netbook-theme ume-launcher
```

but i'm worried that you mentioned **metacity**, as it really doesn't use it.  

its using maximus. are you sure you're on netbook remix?

well, thanks i'll do the uninstall thing... Bythe way... pede ba tanggalin ang maximus if ever para nd ko na sya tanggalin

---

### Post by loell on 2008-09-12
> **ache109 said:**
> pede ba tanggalin ang maximus if ever para nd ko na sya tanggalin

 in theory, kahit anong window manager ang pwede mong ipalit dyan.  pwede tanggaling pero kailangan mong e-setup nang ibang window manager para gumana.

---

### Post by ache109 on 2008-09-12
pano???

---

### Post by loell on 2008-09-12
> **ache109 said:**
> pano???

if you're ready to edit the gdm session(s) , sakit lang nang ulo yan :D

kaya remove na lang. ;)

---

### Post by Malagas on 2010-01-14
I have One more issue...
After removing all stuff from Ubuntu Netbook remix, my desktop has gone !!!

Well after half an hour i did this:

[I]sudo apt-get install nautilus-wallpaper

 gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true
[/I]

And now i can put icons, scripts finally...

Im using a toshiba nb200 with jaunty...
:D

---

### Post by joostvdw on 2011-07-05
After removing ubuntu netbook remix, i lost all icons on desktop: 

After a week of googling, a fin your solution. It  works !! thanks a lot !

joost van der wulp from belgium

---

