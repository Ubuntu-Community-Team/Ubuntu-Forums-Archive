---
title: "Logitech Quickcam Orbit/Sphere Webcam doesn't work properly on Gutsy"
date: 2008-01-25
forum: Philippine Team
---

### Post by wersdaluv on 2008-01-25
On Fiesty, my Logitech Quickcam Orbit/Sphere worked perfectly out of the box. Now on gutsy, the video is very choppy and it doesn't work in some apps like Gyachi and Skype. It works with Kopete and VLC but as I said, it's very choppy. Any idea?

Here are the details:

```
lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:08b5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

```
lsmod | grep videodev
videodev               29312  1 pwc
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

```

---

### Post by rjmdomingo2003 on 2008-01-25
Pareho tayo ng webcam pero di ko mapagana kahit sa kopete. Napagana ko pa lang 'to sa MeBeam.

---

### Post by Samhain13 on 2008-01-25
Wers: pinalitan mo na webcam mo pala. Ano nang nangyari dun sa Genius?

RJ: naglagay ka ba ng "jasper"? Tuwing kasi mag-iinstall ako ng OS at gagamitin ko yung Kopete for webcam chat, lagi akong pinag-iinstall ng libjasper-something, hindi ko maalala yung full name ng package.

---

### Post by rjmdomingo2003 on 2008-01-25
> **Samhain13 said:**
> Wers: pinalitan mo na webcam mo pala. Ano nang nangyari dun sa Genius?

RJ: naglagay ka ba ng "jasper"? Tuwing kasi mag-iinstall ako ng OS at gagamitin ko yung Kopete for webcam chat, lagi akong pinag-iinstall ng libjasper-something, hindi ko maalala yung full name ng package.
Check ko yun synaptic, and found out na di naka-install. libjasper-dev ata yun.

---

### Post by Samhain13 on 2008-01-25
Ang naka-install sakin, **libjasper1** at **libjasper-runtime**. Hindi ako sigurado kung parehong kailangan yun ng Kopete, pero yung libjasper-dev, hindi naka-install sakin.

Pero check mo na din muna sa Kopete kung kilala niya nga yung webcam mo. Makikita mo naman yun sa Settings > Configure > Devices. Kung makikita mo yung output nung cam mo, Jasper nga ang kailangan mo para magamit yung video chat.

---

### Post by rjmdomingo2003 on 2008-01-25
> **Samhain13 said:**
> Ang naka-install sakin, **libjasper1** at **libjasper-runtime**. Hindi ako sigurado kung parehong kailangan yun ng Kopete, pero yung libjasper-dev, hindi naka-install sakin.

Pero check mo na din muna sa Kopete kung kilala niya nga yung webcam mo. Makikita mo naman yun sa Settings > Configure > Devices. Kung makikita mo yung output nung cam mo, Jasper nga ang kailangan mo para magamit yung video chat.
K, will do. Tulog muna ko.:)

---

### Post by wersdaluv on 2008-01-25
> **rjmdomingo2003 said:**
> Pareho tayo ng webcam pero di ko mapagana kahit sa kopete. Napagana ko pa lang 'to sa MeBeam.

Pare, di ko mapagana sa MeBeam. Baka naman ibang version ng quickcam orbit sayo. Baka orbit MP o AP yan. Ano lsusb mo, tsiong?

---

### Post by wersdaluv on 2008-01-25
> **Samhain13 said:**
> Wers: pinalitan mo na webcam mo pala. Ano nang nangyari dun sa Genius?

RJ: naglagay ka ba ng "jasper"? Tuwing kasi mag-iinstall ako ng OS at gagamitin ko yung Kopete for webcam chat, lagi akong pinag-iinstall ng libjasper-something, hindi ko maalala yung full name ng package.

Parekoy, lumang webcam ko na to. Binili ko lang yung genius dahil di ko mapagana to. Di pa rin yun nagana. Yung bibigyan ko, may webcam na rin so naka-stock lang to.

Salamat pala sa lahat ng tulog. 

libjasper-runtime ata yon, btw.

---

### Post by wersdaluv on 2008-01-25
Mga tol! Okay na ang Quickcam Orbit ko sa mebeam! Di na ko magiinstall ng windows!!! Salamaaaaaaaaaaat!

Btw, may iba pa ba kayong alam na site like mebeam? :D baka may ibang okay :D

---

### Post by rjmdomingo2003 on 2008-01-26
> **wersdaluv said:**
> Pare, di ko mapagana sa MeBeam. Baka naman ibang version ng quickcam orbit sayo. Baka orbit MP o AP yan. Ano lsusb mo, tsiong?
```

melski@lapdanz:~$ lsusb
Bus 005 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:08b5 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
```

---

### Post by rjmdomingo2003 on 2008-01-26
> **wersdaluv said:**
> Mga tol! Okay na ang Quickcam Orbit ko sa mebeam! Di na ko magiinstall ng windows!!! Salamaaaaaaaaaaat!

Btw, may iba pa ba kayong alam na site like mebeam? :D baka may ibang okay :D
Cheers 'dre! Check mo post #4: [http://ubuntuforums.org/showthread.php?t=589305](http://ubuntuforums.org/showthread.php?t=589305)
I settled for mebeam kasi dun lang nag-work yung orbit ko.

---

### Post by wersdaluv on 2008-01-26
> **rjmdomingo2003 said:**
> ```

melski@lapdanz:~$ lsusb
Bus 005 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:08b5 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
```

Wow. Dala-dalawa pa ang webcam. Lol. Pare, pareho nga tayo ng quickcam orbit. Ok na siguro ang mebeam. Mabagal sa kopete yan e. Sinubukan ko rin ang tokbox.com kaso mabagal at pangit reso. Kailangan pa magregister.

---

### Post by wersdaluv on 2008-01-26
> **rjmdomingo2003 said:**
> Cheers 'dre! Check mo post #4: [http://ubuntuforums.org/showthread.php?t=589305](http://ubuntuforums.org/showthread.php?t=589305)
I settled for mebeam kasi dun lang nag-work yung orbit ko.

Salamat. :D

Sana lang, napapalaki ang webcam sa mebeam eh noh? Isa pa palang problema ko, pag lumipat ako sa ibang tab (sa firefox), nag-minimize ako, o lumipat ng desktop, nagfrefreeze ang webcam ko sa mebeam. Ganon din ba sa'yo, pre?

---

### Post by rjmdomingo2003 on 2008-01-26
> **wersdaluv said:**
> Wow. Dala-dalawa pa ang webcam. Lol.
Yung isang cam built-in sa laptop ko na di gumagana kahit sang app. Kaya gamit ko yung orbit na lang.

---

### Post by rjmdomingo2003 on 2008-01-26
> **wersdaluv said:**
> Salamat. :D

Sana lang, napapalaki ang webcam sa mebeam eh noh? Isa pa palang problema ko, pag lumipat ako sa ibang tab (sa firefox), nag-minimize ako, o lumipat ng desktop, nagfrefreeze ang webcam ko sa mebeam. Ganon din ba sa'yo, pre?
Sa totoo lang, yung asawa ko ang nagvi-video chat.. I usually don't. Tinanong ko sya't wala naman cyang na-encounter na nagfrefreeze ang cam pag nagsusurf pa sa PEP :) habang nagvi-video chat.

---

### Post by Samhain13 on 2008-01-26
Oi Wers, congratulations! Yey, may cam ka na na gumagana, hindi ka na papagalitan. :D

---

### Post by wersdaluv on 2008-01-26
Salamat sa tulong ninyo. Pinasaya ninyo ang aking buhay. 

:KS

---

### Post by wersdaluv on 2008-01-26
Guys! More good news!

Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=106558&highlight=setpwc"), I discovered something to improve the video quality of my pwc cam.  You can use setpwc and dov4l to adjust your cam's settings.

I haven't played much with the two apps yet. So far, the most useful thing that I have ever done is to ```
setpwc -f 30
``` which will improve the framerate so much that you would think that you bought a more expensive webcam!

:guitar:

---

### Post by rjmdomingo2003 on 2008-01-26
> **wersdaluv said:**
> Guys! More good news!

Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=106558&highlight=setpwc"), I discovered something to improve the video quality of my pwc cam.  You can use setpwc and dov4l to adjust your cam's settings.

I haven't played much with the two apps yet. So far, the most useful thing that I have ever done is to ```
setpwc -f 30
``` which will improve the framerate so much that you would think that you bought a more expensive webcam!

:guitar:
Nasubukan mo na rin ba 'to sa Orbit cam mo?

---

### Post by wersdaluv on 2008-01-26
> **rjmdomingo2003 said:**
> Nasubukan mo na rin ba 'to sa Orbit cam mo?

Oo, pare! Gumana! Sobrang laki ng epekto!

:KS

---

### Post by rjmdomingo2003 on 2008-01-27
> **wersdaluv said:**
> Oo, pare! Gumana! Sobrang laki ng epekto!

:KS
That's good news then! Try ko rin later. :popcorn:

---

### Post by rjmdomingo2003 on 2008-04-01
Mga pre, papaano nyo nakikita ang ka-chat nyo sa mebeam? Kita ko lang kasi is a blue square. Pag-invite ko sila, kita nila ako, pero di ko sila kita. Did I miss something?

---

