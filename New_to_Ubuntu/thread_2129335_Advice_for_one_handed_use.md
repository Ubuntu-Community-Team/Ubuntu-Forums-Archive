---
title: "Advice for one handed use"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-25
With OSI, I can basically only use one hand at the moment and will soon have an op that will put me into one hand mode for possibly six weeks.

I do a lot of stuff with keyboard shortcuts. esp 
ctrl-alt-'whatever key'

Can I configure a key I never use to mean:
ctrl-alt-'wait for input key', then do the input as ctrl-alt-'input key'

Hope this makes sense.

---

### Post by vasa1 on 2013-03-25
Makes perfect sense.

I think regular Ubuntu had a feature for one-handed operation. So instead of pressing alt and f simultaneously, you could first press alt and then f. IIRC, you didn't have to configure any keyboard setting for that. It was just a regular GUI option.

---

### Post by phillw on 2013-03-25
I'd normally suggest the accessibility area of this forum, but that seems real quiet of late. I can only suggest IRC freenode #ubuntu-accessibility or asking on their mailing list, details of which can be found at [https://wiki.ubuntu.com/Accessibility/Contacts](https://wiki.ubuntu.com/Accessibility/Contacts)

Sorry that I can not be of more help.

Regards,

Phill

---

### Post by stinkeye on 2013-03-25
I think sticky keys will do what you want.
> Turn on sticky keys
Sticky keys allows you to type keyboard shortcuts one key at a time rather than having to hold down all of the keys at once. For example, the Alt+Tab shortcut switches between windows. Without sticky keys turned on, you would have to hold down both keys at the same time; with sticky keys turned on, you would press Alt and then Tab to do the same.
You might want to turn on sticky keys if you find it difficult to hold down several keys at once.
Click your name on the top bar and select System Settings.
Open Universal Access and select the Typing tab.
Switch Sticky Keys on.

---

### Post by DuckHook on 2013-03-26
> **Kevin McCready said:**
> ...will soon have an op that will put me into one hand mode for possibly six weeks.

Others have replied with great suggestions as to sticky keys and accessibility options. Just wanted to wish you all the best on your upcoming procedure.

---

### Post by Kevin McCready on 2013-03-26
Thanks. I'm on Lubuntu which doesn't seem to have the ability to switch on stickykeys.

So I downloaded  xkbset which tells me:
xkbset <options>
where <options> may be all or any of (the '-' switches the feature off, 
otherwise it is switched on):
To switch AccessX on (so pressing shift five times starts sticky keys
and pressing the shift key down 8 seconds starts slow keys):
        [-]{accessx|a}
To switch sticky keys on or off, and optionally set or reset:
() two keys pressed at the same time stops sticky keys;
() a modifier pressed twice will be locked:
        [-]{sticky|st} [[-]twokey|[-]latchlock]...

But I still can't figure out how to turn on stickykeys with xkbset

---

### Post by vasa1 on 2013-03-26
> **stinkeye said:**
> I think **sticky keys** will do what you want.
Yes, that's what I remember. But I looked briefly for it in Lubuntu and didn't find any relevant.

---

### Post by vasa1 on 2013-03-26
For now, please look at bodhi.zazen's answer here: [http://askubuntu.com/a/120023/25656](http://askubuntu.com/a/120023/25656)

And here's wishing you a speedy recovery :)

---

### Post by Kevin McCready on 2013-03-26
Thanks. I'm on Lubuntu which doesn't seem to have the ability to switch on stickykeys.

So I downloaded  xkbset which tells me:
xkbset <options>
where <options> may be all or any of (the '-' switches the feature off, 
otherwise it is switched on):
To switch AccessX on (so pressing shift five times starts sticky keys
and pressing the shift key down 8 seconds starts slow keys):
        [-]{accessx|a}
To switch sticky keys on or off, and optionally set or reset:
() two keys pressed at the same time stops sticky keys;
() a modifier pressed twice will be locked:
        [-]{sticky|st} [[-]twokey|[-]latchlock]...

But I still can't figure out how to turn on stickykeys with xkbset

---

### Post by Kevin McCready on 2013-03-26
Thanks so much everyone! And thanks for the well wishes. They tell me the worst part is rehab for possibly six months or more or ... if it doesn't go well.
I issued 2 commands in the terminal and now I have stickykeys:
xkbset exp -bell -sticky -twokey -latchlock -accessx -feedback -stickybeep -led 9999
xkbset bell sticky -twokey -latchlock feedback led stickybeep

If it disappears when I switch off, I'll have to learn again how to put it in a script and make sure it boots when I turn on the machine.

---

