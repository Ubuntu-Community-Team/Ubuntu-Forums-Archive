---
title: "System Program Problem Detected"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-04
I keep getting this message. If I press cancel or report the window closes then pops up over and over. I can't get rid of it. Any way to suppress the window?

---

### Post by lucazade on 2011-09-04
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport
```

---

### Post by sonicb00m on 2011-09-04
Heh saved my life again! Thanks.

---

### Post by lucazade on 2011-09-04
lol.. at the end of the day i'll ask you some money for all this support! ;)

---

### Post by arpanaut on 2011-09-05
> sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apportMr, lucazade, if you would please, explain what this command does?
I have filed a bug report:  [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/839810](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/839810)

Is there is anything you could add to offer insight into that report?

Thanks

---

### Post by lucazade on 2011-09-06
> **arpanaut said:**
> Mr, lucazade, if you would please, explain what this command does?
I have filed a bug report:  [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/839810](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/839810)

Is there is anything you could add to offer insight into that report?

Thanks

Arpanaut that command only disable apport (the error reporting tool you see popping up now and then). 
During the dev cycle of ubuntu, apport is usually enabled (set to 1), when Ubuntu is released is disabled (set to 0).

---

### Post by Quackers on 2011-09-06
Thanks lucazade :-)
That command has stopped my cpu bouncing every few seconds because of apport-gtk.
Gone now :-)

---

### Post by WorfSOM on 2011-09-06
Thanks for this it was really bugging me.:cool:

---

### Post by VinDSL on 2011-09-06
> **lucazade said:**
> ```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport
```

> **arpanaut said:**
> Mr, lucazade, if you would please, explain what this command does?
If I may... I love sed (and awk and cut)  :D

[LIST]
[*]sudo = allows local user to have elevated privileges. Think "root".
[*]sed = is a stream editor proggie (not normally used for stuff like this)
[*]-i = invocation mode.  It allows you to clobber protected files, e.g. allows forbidden commands.
[*]'s/enabled=1/enabled=0/g' = replaces the first instance of "enabled=1" with "enabled=0"
[*]/etc/default/apport = the path and name of the affected input file.
[/LIST]

Essentially...

It edits /etc/default/apport and replaces enabled=1 with enabled=0.

Pretty slick, lucazade!  I didn't know you speak fluent sed...  ;)

---

### Post by lucazade on 2011-09-06
> **VinDSL said:**
> If I may... I love sed (and awk and cut)  :D

[LIST]
[*]sudo = local user elevated privileges. Think "root".
[*]sed = is a stream editor proggie (not normally used for stuff like this)
[*]-i = invocation mode.  It allows you to clobber protected files, e.g. allows forbidden commands.
[*]'s/enabled=1/enabled=0/g' = replaces enabled=1 with enabled=0
[*]/etc/default/apport = is the affected input file.
[/LIST]

Essentially...

It edits /etc/default/apport and replaces enabled=1 with enabled=0.

Pretty slick, lucazade!  I didn't know you spoke fluent sed...  ;)

lol :)
Started to use sed because I had to manage a lot of files at work on a hp-ux machine and vi (the only available tool) was a pain to remember and use.

---

### Post by VinDSL on 2011-09-06
> **lucazade said:**
> lol :)
Started to use sed because I had to manage a lot of files at work on a hp-ux machine and vi (the only available tool) was a pain to remember and use.
That's a GREAT idea!

I use sed all the time, for stream editing, in Conky.

Never thought about using it to edit files.

Sure would save a lot of typing in these forums...  :)

---

