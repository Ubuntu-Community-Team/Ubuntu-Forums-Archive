---
title: "Can anyone good with C++ tell me how to tweak this Xfce panel?"
date: 2009-10-18
forum: Programming Talk
---

### Post by rob86 on 2009-10-18
There's this Xfce panel app called mailwatch that I like, but there's one thing about it that bugs me, and it's that when there's a connection error, a red error icon comes up in the bottom left corner of the main icon. Since I use dial-up, I frequently have connection errors, but they are temporary, something the programmer of mailwatch probably didn't think of. When my bandwidth becomes free again, and the email can connect, the error icon should go away, but it doesn't.

I'd prefer if this icon would disappear when the connection doesn't fail (it tries every 10 minutes, and the previous connection error doesn't prevent it from trying again). 

If that's too difficult, I just wish to get rid of the error icon permanently.

I tried to do this myself, but I don't know enough about C++ programming or how difficult it is for someone who knows what they're doing. It looks like a simple thing to fix but I couldn't figure it out. I couldn't find what made the error icon come up or if it's a standard Xfce thing or what.

If anyone is interested in looking at the source code, it's available here.

[http://spuriousinterrupt.org/projects/mailwatch](http://spuriousinterrupt.org/projects/mailwatch)

---

### Post by SSTwinrova on 2009-10-18
I'd suggest either emailing the program's mailing list or even filing a bug since that seems like undesired behavior (if I just got done checking my mail, why do I care if a check an hour ago failed?). If the creators want the existing behavior for whatever reason, they might be willing to implement an option that does what you want.

---

