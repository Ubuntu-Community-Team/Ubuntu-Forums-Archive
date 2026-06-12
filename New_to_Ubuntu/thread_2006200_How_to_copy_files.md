---
title: "How to copy files"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by mayagrafix on 2012-06-18
OK, I want to copy contents from one HD (80 gig) to another so I can make room to install Precise Pangolyn (who comes up with these names BTW?) on an external HD.

Is there some kind of file copy management program I can use? working from the cd here (internal HD just went down) so downloading and installing may not be possible, but on the bright side, I have enough RAM.

Tried to do a straight copy and paste from HD to HD but the OS (12.04) became very slow and started to produce a lot of errors. 

If File Manager (Nautilius?) were able to show contents in a alfa list instead of icons I could copy and paste manually by alfabetatizing (first the a's, then the b's, etc) a littlea t a time so the system won't bog down. So I think there must be some kind of a program that makes it easier to do this. 

Thanks for your help, 
A borne again Ubuntu fan. (Unity is so cool!)

---

### Post by Arand on 2012-06-18
> **mayagrafix said:**
> OK, I want to copy contents from one HD (80 gig) to another so I can make room to install Precise Pangolyn (who comes up with these names BTW?) on an external HD.

Is there some kind of file copy management program I can use? working from the cd here (internal HD just went down) so downloading and installing may not be possible, but on the bright side, I have enough RAM.

Tried to do a straight copy and paste from HD to HD but the OS (12.04) became very slow and started to produce a lot of errors.
That I would guess means the hard disk is in a bad state...

> **mayagrafix said:**
> 
If File Manager (Nautilius?) were able to show contents in a alfa list instead of icons I could copy and paste manually by alfabetatizing (first the a's, then the b's, etc) a littlea t a time so the system won't bog down. So I think there must be some kind of a program that makes it easier to do this.
(...)
You can always Use [View]->[List] (Ctrl+1) to get an alphabetically sorted list in the normal file manager.

---

### Post by Kopkins on 2012-06-18
> **mayagrafix said:**
> OK, I want to copy contents from one HD (80 gig) to another so I can make room to install Precise Pangolyn (who comes up with these names BTW?) on an external HD.

[COLOR="Red"]What do you want to copy? Everything? Or just your important files? Is the destination HD empty?[/COLOR]

Is there some kind of file copy management program I can use? working from the cd here (internal HD just went down) so downloading and installing may not be possible, but on the bright side, I have enough RAM.

[COLOR="red"]Is your internal drive the one you want to copy from? What does going down mean? Broken?[/COLOR]

Tried to do a straight copy and paste from HD to HD but the OS (12.04) became very slow and started to produce a lot of errors. 

[COLOR="red"]From the live CD, using nautilus to copy your root directory will not work normally. Several directories require root privileges and cannot be accessed as a normal user. You are a normal user. You could try pressing alt+f2 and entering the command : ```
gksudo nautilus
``` and that should open nautilus as root user giving you the privileges you need.[/COLOR]

If File Manager (Nautilius?)[COLOR="red"]Nautilus :)[/COLOR] were able to show contents in a alfa list instead of icons I could copy and paste manually by alfabetatizing (first the a's, then the b's, etc) a littlea t a time so the system won't bog down. So I think there must be some kind of a program that makes it easier to do this. 

[COLOR="red"]If you want to see it as a list, go to view, list. Or if in 12.04, open nautilus, tap alt then type **list** and press enter.[/COLOR]

Thanks for your help, 
A borne again Ubuntu fan. (Unity is so cool!)

[COLOR="Red"]Glad you think so.[/COLOR]



Kopkins

---

