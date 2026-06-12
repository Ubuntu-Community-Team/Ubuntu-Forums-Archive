---
title: "visual control center"
date: 2009-04-04
forum: Philippine Team
---

### Post by Script Warlock on 2009-04-04
meron ba tayong ganito para sa ubuntu/linux? very useful sana para sa inet pero remote desktop viewer can only display one at a time.

---

### Post by loell on 2009-04-04
setup ka lang ng script for multiple instances of vnc viewer via a script (python or bash) , assuming lahat ng clients mo ay na setup mo na para ma view sa vnc.

parang ganito
```

vncviewer  192.168.0.2 & vncviewer 192.168.0.3 ....

```

---

### Post by Script Warlock on 2009-04-04
kailangan ko install vnc?

---

### Post by loell on 2009-04-04
di na siguro, vncviewer lang sa control center mo.

---

### Post by Script Warlock on 2009-04-04
yesss got it, ty boss....meron nga akong nakita na multivnc pero japanese ang language kaya di ko mapatakbo ng maayos...but this one is nice:guitar:

---

### Post by Script Warlock on 2009-04-05
eto pala link ng ibig ko sabihin 
[http://thetechnologyteacher.wordpress.com/vncthumbnailviewer/](http://thetechnologyteacher.wordpress.com/vncthumbnailviewer/) 

dami nga lang kulang pero ok din....solve!.. ty uli boss loell

---

### Post by loell on 2009-04-05
nice software. :)

---

### Post by raxso on 2009-04-05
Open-Source Classroom Management With iTALC 


[http://raxso.net/2008/04/open-source-classroom-management-with-italc/](http://raxso.net/2008/04/open-source-classroom-management-with-italc/)

---

### Post by Script Warlock on 2009-04-06
italc is nice but para sa akin overkill kc i only want to monitor/control client pc and it almost broke my server after i uninstall italc. it almost broke my server(desktop edition) dahil sa conf na to at pina-login lang ako sa cli. 

$sudo gedit /etc/X11/xorg.conf  add>>>> Load "record"
$sudo gedit /etc/gdm/Init/Default /etc/gdm/PreSession/Default add the following at the very top of both of them (just below the introductory block of comments):
       killall ica
       /usr/bin/ica &

buti na lang natandaan ko pa last kong ginawa kaya...i still prfer the vncviewer script or the vnc thumbnail viewer para sa inet shop ko..

---

