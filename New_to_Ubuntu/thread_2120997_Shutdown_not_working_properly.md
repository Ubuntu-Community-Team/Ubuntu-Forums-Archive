---
title: "Shutdown not working properly"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by cheatos on 2013-02-28
Hi all,

nice to see the forum is up again :)
I have a problem with my lubuntu on my laptop. When I press shutdown it doesn't really shut down.
When I disconnect it from power source its only a few hours until the battery is completely empty. Besides of this which is altredy pretty enerving, the computer also gets very warm even when shut off.
Is this a known problem and will be fixed in a upcoming kernel?
Bzw i'm running lubuntu 12.04

Thanks for your advice!

---

### Post by Rex Bouwense on 2013-02-28
What type of laptop are you using?  
Can you shut it down from the terminal?  
How do you know that it isn't shutting down? 
I am using Lubuntu 12.04 on my very old Dell Inspiron 1000 and yes it runs hot but it does shut down.  Can't tell you anything about the battery though since it is pretty old as well so I use it with the plug in.

---

### Post by ajgreeny on 2013-02-28
It sounds as if your machine is set to suspend rather than power-off when you press shutdown, though it depends what you mean by "press shutdown".

If I simply press the shutdown (power) button on both my old laptop and newer netbook, each running Lubuntu 12.04, they both go into suspension and do not fully shutdown.  To fully shutdown and totally power-off I have to use the **logout->Shutdown** item in the menu.

Neither of my two machines get very warm when doing normal things, but if I try encoding video or using a cpu intensive application they warm up a bit more, but still not hot.  What hardware do you have?

---

### Post by cheatos on 2013-02-28
hi,

sorry for the confusion.
I press the shutdown button in lubuntus desktop, so by using this "start" thing and then logout -> shotdown
Nothing with suspend or hibernate or something like this.
The laptop is not running very hot during usual work, it's just when I shut it down and then pack it away to carry the laptop, it can't get so much air and becomes warm. By saying this I just wanted to make clear, that the laptop really is not shutting down.
The excessive power usage must be from this, because usually i can work with my laptop without a cord for about 2hours (in lubuntu) and then the display is running all the time.
I haven't tried shutting down via terminal, I'll give this a try.

Thanks for the help!

---

### Post by cheatos on 2013-03-03
bump

---

### Post by Rulius on 2013-03-03
Hi,

What about a hard shutdown (press and hold the power button on your laptop).

Besides the laptop being warm, are there any other indications that make you think it hasn't shutdown?

---

### Post by cheatos on 2013-03-03
hi,

well i have done that already but it's not a satisfiying solution for me...

Sometimes the laptop shuts down properly, then all indicators are off (except if i have a power cord, then the dc-indicator and the battery-loading-indicator are lit) but when it doesn't shut down properly there's also the snooze indicator which stays lit. So I guess the laptop goes in some suspended state.

---

### Post by Rulius on 2013-03-03
Yeah, hard shutdown is definately not a solution!

I was just wondering if the syptoms remain even after a hard shutdown.

If it doesn't happen every time, try to notice why that is....For example does it happen after you have used a specific software.

Regards

---

### Post by pfeiffep on 2013-03-03
possibly try to shutdown from a terminal with this command
> sudo shutdown -H

---

### Post by cheatos on 2013-03-05
ok, Ill try that.
> sudo shutdown -H
Also with the software, dont think that matters, i mainly use firefox and thunderbird in all my sessions, not more not less...
maybe its my latex editor, i only use that every once and a while, ill have an eye on that as well

---

### Post by Hadaka on 2013-03-05
Hi, here is a script to shut down.

open a termnal ctrl/alt/t and do..

```
gedit off 
```

in gedit editor enter..
```
# ** Removes Power and shuts down computer **

#!/bin/bash
echo 'your_password' | sudo -S shutdown -P now
 
```
*Note: 'your_password'  is YOUR password...and must be in single quotes.*
save and close.   then..back to terminal  ctrl/alt/t
and do..
```
chmod +x
```
then simply enter..
```
./off 
```
and your computer will shutdown.
once saved and tested...you can do the  ./off
in a terminal at any time.
hope this helps.

---

### Post by cheatos on 2013-03-06
hey, thanks for this script hadaka!
Is it also possible to link this script to the GUI-shutdown button?

---

### Post by cheatos on 2013-03-06
btw, is it still possible to mark a thread as solved?
because with this "off" it works just fine.
Copied it to /usr/bin so now i can just type off in anywhere of the terminal :)
Still it would be nice to make a link to the gui-button.
If theres some xml-file that regulates this i can probably figure it out b myself, just would need to know where to search for it

---

