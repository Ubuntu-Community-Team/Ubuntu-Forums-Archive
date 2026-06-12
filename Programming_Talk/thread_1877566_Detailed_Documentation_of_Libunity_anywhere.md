---
title: "Detailed Documentation of Libunity anywhere?"
date: 2011-11-08
forum: Programming Talk
---

### Post by hakermania on 2011-11-08
I searched the net and the only thing I found was this:
[https://wiki.ubuntu.com/Unity/LauncherAPI](https://wiki.ubuntu.com/Unity/LauncherAPI)
I downloaded the source and has the same examples as on the link above. I need more detailed information in some aspects :)

Is Libunity's documentation available anywhere?:confused:

---

### Post by haqking on 2011-11-08
> **hakermania said:**
> I searched the net and the only thing I found was this:
[https://wiki.ubuntu.com/Unity/LauncherAPI](https://wiki.ubuntu.com/Unity/LauncherAPI)
I downloaded the source and has the same examples as on the link above. I need more detailed information in some aspects :)

Is Libunity's documentation available anywhere?:confused:

[https://launchpad.net/libunity](https://launchpad.net/libunity)

what do you wanna know about it ? look in the code, it contains all you need to know ;-)

---

### Post by hakermania on 2011-11-08
> **haqking said:**
> [https://launchpad.net/libunity](https://launchpad.net/libunity)

what do you wanna know about it ? look in the code, it contains all you need to know ;-)

Heh, I guess that looking the code would be an idea, a time consuming one, but we don't have infinite time and a list with the functions and what each one does would be a much better idea...

---

### Post by haqking on 2011-11-08
> **hakermania said:**
> Heh, I guess that looking the code would be an idea, a time consuming one, but we don't have infinite time and a list with the functions and what each one does would be a much better idea...

[http://packages.ubuntu.com/maverick/libunity-misc-doc](http://packages.ubuntu.com/maverick/libunity-misc-doc)

---

### Post by nvteighen on 2011-11-09
Libunity has documentation? 0_0

(just kidding)

---

### Post by hakermania on 2011-11-09
> **nvteighen said:**
> Libunity has documentation? 0_0

(just kidding)
Well, I knew that nautilus used dynamic quicklists when copying things so I inspected the code and things are clearer now to me!

I can have a working menu, enable/disable/hide/show items and have them do the actions I want, but I cannot seem to find a way to tackle the problem of editing the static quicklist.

I mean, if static quicklist has :

[LIST]
[*]Start
[*]Stop
[*]Capture
[/LIST]
When the program starts I'd like to have this and **only** dynamic quicklist:

[LIST]
[*]Hello
[*]World
[*]I
[*]am Alex
[/LIST]
I mean I want something completely different from the static quicklists defined inside the .desktop files, and then, when the program exits, the quicklist to return to the .desktop file's ruleZ... That would be perfect....

---

