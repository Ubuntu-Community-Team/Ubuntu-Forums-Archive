---
title: "Purple screen after login"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-08-05
After this latest round of updates, when I try to login to a gnome-session I get a purple screen.  I tried to wait ten minutes with no change.  Unity boots ok.  I was wondering if anyone had any ideas.  Thanks.

---

### Post by Quackers on 2011-08-05
Same here, except Unity doesn't even boot :-(
After logging in the login box disappears and the purple background just sits there. No HDD activity at all, just sits there.

---

### Post by mdhollis on 2011-08-05
My mistake, I logged into unity before I shutdown my machine.  Now unity is broken as well.

---

### Post by pulpo69 on 2011-08-05
Same here, with the only difference that i've permanent hdd-activity.

---

### Post by meborc on 2011-08-05
I have no issues with my ACER aspire one netbook 532h-2588

---

### Post by Richard on 2011-08-05
Same issue with Unity or Gnome-shell on Nvidia card only, seems related to the latest Nvidia driver 280.13.

---

### Post by mdhollis on 2011-08-05
> Same issue with Unity or Gnome-shell on Nvidia card only, seems related to the latest Nvidia driver 280.13.

Is there a workaround this issue?

---

### Post by Harry33 on 2011-08-05
> **mdhollis said:**
> Is there a workaround this issue?

You have to downgrade to the previous gnome-session (3.1.3-0ubuntu6).
There may also be something wrong with the nvidia-current 280.13-0ubuntu1.

---

### Post by pulpo69 on 2011-08-05
same issues, but i've an ati card.

---

### Post by Harry33 on 2011-08-05
It seems the newest gnome-session does not anymore allow login to gnome-shell.
It persistently tries to start ubuntu-session, but does not succeed.

There is a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477)

---

### Post by 3vi1 on 2011-08-05
Workaround:

[LIST=1]
[*]Ctrl-alt-F1
[*]Log in to terminal
[*]sudo killall -9 gnome-session
[*]Ctrl-alt-F7
[/LIST]

---

### Post by Quackers on 2011-08-05
> **3vi1 said:**
> Workaround:

[LIST=1]
[*]Ctrl-alt-F1
[*]Log in to terminal
[*]sudo killall -9 gnome-session
[*]Ctrl-alt-F7
[/LIST]

Yep, thanks.
That gets unity booting here. Still no gnome-shell, but in view of Harry33's comments that's not surprising.

EDIT
oops, synaptic now hangs (as Harry mentioned earlier) and the dash is unclickable.

---

### Post by Harry33 on 2011-08-05
> **Quackers said:**
> Yep, thanks.
That gets unity booting here. Still no gnome-shell, but in view of Harry33's comments that's not surprising.

EDIT
oops, synaptic now hangs (as Harry mentioned earlier) and the dash is unclickable.

Yes you did it Quackers.

So, for gnome-session just downgrade to the version 3.1.3-0ubuntu6
and for nvidia-current downgrade to the version 280.04
and you are back to business.

---

### Post by Quackers on 2011-08-05
Thanks Harry, but it was 3vi1 that did it :-)

On the other matter (synaptic) it will open and I can browse through it, but then if I try to close synaptic it will peg one processor at 100% and stay there.
Interestingly it will eventually close itself but still appears as running in top and if I start it again it will peg the other processor at 100%, which is somewhat limiting :-)

---

### Post by mdhollis on 2011-08-05
> **3vi1 said:**
> Workaround:

[LIST=1]
[*]Ctrl-alt-F1
[*]Log in to terminal
[*]sudo killall -9 gnome-session
[*]Ctrl-alt-F7
[/LIST]

This doesn't do it for me.  Should I log into either gnome-shell or unity before doing this?

---

### Post by Quackers on 2011-08-05
Yes, login to unity first (or I did) :-) but definitely not gnome-shell.

---

### Post by Harry33 on 2011-08-05
> **Quackers said:**
> Thanks Harry, but it was 3vi1 that did it :-)

On the other matter (synaptic) it will open and I can browse through it, but then if I try to close synaptic it will peg one processor at 100% and stay there.
Interestingly it will eventually close itself but still appears as running in top and if I start it again it will peg the other processor at 100%, which is somewhat limiting :-)

Yes Quackers, that is exactly the issue I have with 280.11 and 280.13.
There must be something wrong with these drivers or more likely they must be unsuitable for the current Oneiric system (mesa or something like that).

---

### Post by mdhollis on 2011-08-05
> **Quackers said:**
> Yes, login to unity first (or I did) :-) but definitely not gnome-shell.

Thanks. Now I'm getting somewhere.

---

