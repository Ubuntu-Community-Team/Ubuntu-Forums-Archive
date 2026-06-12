---
title: "firefox crashes"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by naoyuki on 2012-02-09
i am using ubuntu 11.10.
when i visited website of [epson usa]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.epson.com%2Fcgi-bin%2FStore%2Findex.jsp&ei=Pho0T7S0F-KKmQWturX4AQ&usg=AFQjCNFMOnYNMhv1-Rf7hLYrZP2ZsJjtoA&sig2=m5GhxhUL8k90Nyum0gL_vQ"),firefox 9.1.0 crashes everytime.
Does anybody tell me what does the crash report mean? 

all of the addons are off.
my pc is IBM x40.
> Add-ons: {972ce4c6-7e08-4474-a285-3208198ce6fd}:9.0.1
BuildID: 20111228084953
CrashTime: 1328814459
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1326011514
Notes: OpenGL: Tungsten Graphics, Inc -- Mesa DRI Intel(R) 852GM/855GM x86/MMX/SSE2 -- 1.3 Mesa 7.11 -- texture_from_pixmap
WebGL? libGL.so.1? libGL.so.1+
GL Context? GL Context+

ProductName: Firefox
SecondsSinceLastCrash: 71
StartupTime: 1328814425
Theme: classic/1.0
Throttleable: 1
URL: [http://ubuntuforums.org/showthread.php?t=1685798](http://ubuntuforums.org/showthread.php?t=1685798)
Vendor: Mozilla
Version: 9.0.1

This report also contains technical information about the state of the application when it crashed.

---

### Post by Cheesemill on 2012-02-09
Try launching Firefox from the terminal and then causing the crash, it may give some more descriptive errors.
```
firefox
```

---

### Post by naoyuki on 2012-02-09
i launched firefox from terminal.
and the terminal says like this...


> naoyuki@naoyuki:~$ firefox

(firefox:3987): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3987): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3987): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:3987): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


---

### Post by Cheesemill on 2012-02-09
I don't think those errors have anything to do with Firefox crashing, does it give you any different errors when it does crash or is that all of them?

---

### Post by winh8r on 2012-02-09
Give this a try

restart your browser

go to "Help"

click on "restart with add-ons disabled"

you should see a window that has a "continue in safe mode" button

click it

visit the site again and see if it crashes

if it does not crash then your issue is probably an add-on which needs updated.

No-Script is a common culprit.


If the above method does not work you can start firefox from the terminal with 

firefox --safe-mode

and do the same test.


Also make sure firefox is updated too.



******EDIT*****  Is this only happening on one site?

---

### Post by naoyuki on 2012-02-09
> **Cheesemill said:**
> I don't think those errors have anything to do with Firefox crashing, does it give you any different errors when it does crash or is that all of them?


that is all.......it doesn't give me any defferent errors..

---

### Post by naoyuki on 2012-02-09
i tried all the way you told me to do .
but,firefox crashed even when i launched firefox in safemode....

this is happening only when i visit epson usa site as for now....



> **winh8r said:**
> Give this a try

restart your browser

go to "Help"

click on "restart with add-ons disabled"

you should see a window that has a "continue in safe mode" button

click it

visit the site again and see if it crashes

if it does not crash then your issue is probably an add-on which needs updated.

No-Script is a common culprit.


If the above method does not work you can start firefox from the terminal with 

firefox --safe-mode

and do the same test.


Also make sure firefox is updated too.



******EDIT*****  Is this only happening on one site?

---

### Post by naoyuki on 2012-02-09
after i installed gtk2-engines-pixbuf, ''Unable to locate theme engine in module_path: "pixmap"'' disappeared.

but there  is still a problem.
the error below showed in the terminal when i visited epson usa site.

> naoyuki@naoyuki:~$ firefox
Mesa 7.11 implementation error: unexpected format in _mesa_choose_tex_format()
Please report at bugs.freedesktop.org
Mesa 7.11 implementation error: unexpected MESA_FORMAT for renderbuffer
Please report at bugs.freedesktop.org


---

### Post by winh8r on 2012-02-09
Cant come up with an answer right now but here is a sort of workaround to try:

go to [babelfish.yahoo.com]("babelfish.yahoo.com")


and in the webpage translation box type in

[www.epson.com/](www.epson.com/)

and select it to translate from german to english in the drop down menu

it will take a moment to load then select North america from the world map and it should allow you to visit the site, I think, maybe , possibly

try it anyway, and i will try to check it out more tomorrow

hope it helps.

---

### Post by winh8r on 2012-02-09
> **naoyuki said:**
> after i installed gtk2-engines-pixbuf, ''Unable to locate theme engine in module_path: "pixmap"'' disappeared.

but there  is still a problem.
the error below showed in the terminal when i visited epson usa site.
 There appear to be some known bugs concerning mesa drivers and firefox.
I see that you are using version 7.11 and according to the MESA homepage they have released quite a few updates and are now at version 8.

I would suggest typing lspci into the terminal and posting the result here.

If it is a graphics card/driver issue then I have to be honest and say that this is not an area I have any real experience in and I would rather step aside and let someone who knows about them help you.


Apologies for not being able to resolve the issue


Hope you get it sorted out soon though.

---

### Post by naoyuki on 2012-02-09
> **winh8r said:**
> Cant come up with an answer right now but here is a sort of workaround to try:

go to [babelfish.yahoo.com]("babelfish.yahoo.com")


and in the webpage translation box type in

[www.epson.com/](www.epson.com/)

and select it to translate from german to english in the drop down menu

it will take a moment to load then select North america from the world map and it should allow you to visit the site, I think, maybe , possibly

try it anyway, and i will try to check it out more tomorrow

hope it helps.
firefox crashed as well .....

---

### Post by naoyuki on 2012-02-09
> **winh8r said:**
> There appear to be some known bugs concerning mesa drivers and firefox.
I see that you are using version 7.11 and according to the MESA homepage they have released quite a few updates and are now at version 8.

I would suggest typing lspci into the terminal and posting the result here.

If it is a graphics card/driver issue then I have to be honest and say that this is not an area I have any real experience in and I would rather step aside and let someone who knows about them help you.


Apologies for not being able to resolve the issue


Hope you get it sorted out soon though.
this is the lspci result...

> naoyuki@naoyuki:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
02:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)


---

### Post by winh8r on 2012-02-10
Like I said in my last post, this is not an area I am greatly familiar with when it comes to all kinds of graphics cards and drivers. But I would suggest having a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1865295&highlight=Intel+Corporation+82852%2F855GM+Integrated+Graphics+Device]("http://ubuntuforums.org/showthread.php?t=1865295&highlight=Intel+Corporation+82852%2F855GM+Integrated+Graphics+Device")

This might help you out.

---

### Post by naoyuki on 2012-02-11
> **winh8r said:**
> Like I said in my last post, this is not an area I am greatly familiar with when it comes to all kinds of graphics cards and drivers. But I would suggest having a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1865295&highlight=Intel+Corporation+82852%2F855GM+Integrated+Graphics+Device](http://ubuntuforums.org/showthread.php?t=1865295&highlight=Intel+Corporation+82852%2F855GM+Integrated+Graphics+Device)

This might help you out.
the xorg-edgers did not help me, firefox still crashes....

---

