---
title: "Upgrading issues"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Stikky on 2008-07-17
Hey everyone,

I havent been on here for a while cuz I have pretty much been trying to learn linux by myself but something seems to have gone wrong. Today I decided to take the plunge and upgrade to the latest version from 7.10 which I have been running for almost a year. It all seemed to be going great and now it appears to be stuck. It's been saying there's "about 8 minutes remaining" for the past hour or so and I dont know what to do. The last couple of lines say:

```
Setting up belocs-locales-bin (2.4.2ubuntu7) ...
Setting up locales (2.7.9-4) ...
Installing new version of config file /etc/belocs/iso-639.def ...
Generating locales...
  en_AU.UTF-8...
```

And none of that means ANYTHING to me. Now it's just stopped, it hasnt asked me to do anything, there's no cancel button, the computer is still working but it's not doing anything, the HDD is not making noise, nothing, I have no idea what to do :-(

Any help would be much appreciated.

Thanks,
Ollie

---

### Post by meindian523 on 2008-07-17
Did you try to update from a CD or from the Update Manager?

---

### Post by Stikky on 2008-07-17
Hi there,

I did the upgrade from the upgrade manager, yeah, it had a little box that said I didnt have the latest version so I just clicked update..

---

### Post by meindian523 on 2008-07-17
Well,usually upgrading through the Update Manager is not recommended since it's not quite finished quality.Usually a clean install from CD is recommended.
The message you posted looks like it's hung while configuring the Australian English UTF,but I'm no expert at that,and neither on updates done through Update Manager.
I'm sorry to say I can't really help you here,you will have to wait for other people to come along who can help with this situation.

---

### Post by Stikky on 2008-07-17
OK, well, thanks for trying anyway.

Hypothetically, if I just turn the damn computer off, will that break everything? Should I take all my important data off it so it doesnt get lost?

---

### Post by meindian523 on 2008-07-17
I dunno,I was about to recommend the Raising Skinny Elephants Is Utterly Boring,but I recalled having read something somewhere in ubuntuforums about broken packages which wouldn't allow you to do anything with Synaptic thereafter.the solution was simple,just to remove the offending packages.Also depends on whether you have a separate /home partition.

---

### Post by kansasnoob on 2008-07-17
"Hypothetically, if I just turn the damn computer off, will that break everything? Should I take all my important data off it so it doesnt get lost?"

Try every stupid thing first!

Move the mouse around!
Push the eject button on every drive your puter has!

But, yes, if you can still access your data "save it"!

---

### Post by kansasnoob on 2008-07-17
I'd even try an Alt > F-2 before I powered off but that's extreme!

Wait for better advice.

---

### Post by Stikky on 2008-07-17
OK, not entirely sure what you mean there.. Should I just turn the computer off? It's ridiculous, it's been saying about 8 mins remaining for hours now!!

---

### Post by meindian523 on 2008-07-17
@Stikky
The only good advice kansasnoob gave,by his own admission,is
[QUOTE='kansasnoob']Wait for better advice[/QUOTE]

---

### Post by Stikky on 2008-07-17
The computer is still working ok, I can use the internet (like I am now) and look at all my photosand documents and stuff. The upgrader has just stopped working :-(

---

### Post by Stikky on 2008-07-17
Haha, ok, ok, I get your point, I'll wait for some better advice :-P

Thanks to all of you for trying to help anyway!

---

### Post by kansasnoob on 2008-07-17
> **meindian523 said:**
> @Stikky
The only good advice kansasnoob gave,by his own admission,is

Gee, thanks a lot. What do you suppose the op meant by, "OK, not entirely sure what you mean there"?

I'll bet the op knows how to move the mouse around, or click a drive button, or wait for better advice. Do you suppose the op understands the "skinny elephant" command?

Maybe try to be actually helpful instead of snotty and hateful, eh?

---

### Post by meindian523 on 2008-07-17
I thought he didn't understand what you meant,that's what that comment sounds like to me.Of course,the OP knows all those things,but only,the actions you suggested IMHO wouldn't help the situation one bit.I'm trying to be helpful all right,IMHO,what would be best for the OP is wait for advice from people who know about this stuff,because I've had many situations with my own puter where turning it off and rebooting only worsened the problem.
But you have a point about the skinny elephants command.Here's a clarification:
@Stikky
The skinny elephants command is a way of remembering the Magic SysRQ keys which help you recover a system which has hung.The advice is to press
Alt+SysRQ+R
Alt+SysRQ+S
Alt+SysRQ+E
Alt+SysRQ+I
Alt+SysRQ+U
Alt+SysRQ+B
with a few seconds between each step.Look here for more info:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

---

### Post by kansasnoob on 2008-07-17
> **meindian523 said:**
> I thought he didn't understand what you meant,that's what that comment sounds like to me.Of course,the OP knows all those things,but only,the actions you suggested IMHO wouldn't help the situation one bit.I'm trying to be helpful all right,IMHO,what would be best for the OP is wait for advice from people who know about this stuff,because I've had many situations with my own puter where turning it off and rebooting only worsened the problem.
But you have a point about the skinny elephants command.Here's a clarification:
@Stikky
The skinny elephants command is a way of remembering the Magic SysRQ keys which help you recover a system which has hung.The advice is to press
Alt+SysRQ+R
Alt+SysRQ+S
Alt+SysRQ+E
Alt+SysRQ+I
Alt+SysRQ+U
Alt+SysRQ+B
with a few seconds between each step.Look here for more info:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

Look at post #7 again. I quoted the op and suggested that he or she do anything other than just shut down. At no point did I criticize you or your advice. When the op asked for further instruction you decided it was more important to make me look bad.

That's just being a jerk! I admitted my shortcomings by suggesting the op waqit for better advice. I never denigrated your advice.

---

### Post by meindian523 on 2008-07-17
I'm taking this to PM.No need to hijack the thread.

---

### Post by Stikky on 2008-07-17
Sorry, just to clarify, when I said I didnt know what you meant, I was talking about the skinny elephants thing, at that point, meindia523 and myself were the only two people who had posted when I clicked reply, I didnt realize there were new posts.

Thanks for clearing that up, by the way, the elephants thing, it did seem like a very strange comment to me! :-P

Still stuck at the same point, nothing new happening, might have to do your little elephant trick cuz this is just ridiculous, nothing is happening :-(

---

