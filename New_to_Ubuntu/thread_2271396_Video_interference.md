---
title: "Video interference"
date: 2015-03-29
forum: New to Ubuntu
---

### Post by geoff20 on 2015-03-29
Not sure whether this should be a Kodi problem.
When playing videos through Ubuntu with a Intel NUC Celeron Baytrail ( all drivers updated),the video plays perfectly.However when played through Kodi Helex 14.1 I have a line of interference, that comes and goes.
Tried playing with the acceleration controls in Kodi but nothing makes any difference.
Can't understand why it works in one and not the other.

---

### Post by DuckHook on 2015-03-29
Man... you've just made me feel so old.

Didn't know what Kodi was until Googling it and discovering that it's the new name for XBMC. These days, it's like I blink and miss most everything.

Would suggest that you ask in the Kodi forum, which should be a well established one (it was back in the XBMC days). They may be able to give you better insights especially if others have experienced the same issues.

---

### Post by gordintoronto on 2015-03-30
What player did you use in Ubuntu? A Celeron might be marginal for what you want to do.

---

### Post by mc4man on 2015-03-30
Your "a line of interference" may be video tearing. Ubuntu enables vsync thru compiz & other means, maybe your Kodi  session doesn't.

---

### Post by Vladlenin5000 on 2015-03-30
@mc4man - It would be the first time: [http://forum.kodi.tv/showthread.php?tid=100898](http://forum.kodi.tv/showthread.php?tid=100898), but usually affects nvidia only. Unlike what was hinted in post #3, your celeron is more than capable for any multimedia content no matter how high the resolution. It's not an hardware limitation. I wonder if the fix (workaround actually) for a recent tearing with certain nvidia cards running a certain driver, can be used here? No harm in trying, I guess... Install *ccsm* (CompizConfig Settings Manager) then open it, go to Solutions and select "Force full redraw...".

---

### Post by geoff20 on 2015-03-30
Thanks for the link. Have been trying to work through a Kodi link involving Baytrail NUC's and have tried everything suggested with no luck. 
This appears to be exactly what I'm experiencing, will give it a go when I'm home.

---

### Post by Vladlenin5000 on 2015-03-30
If it doesn't work better to change it back to the default (uncheck).

What's weird is your most certainly on-die graphics Intel HD are usually the less troublesome for video.

---

### Post by geoff20 on 2015-03-30
Have installed ccsm but can't see solutions. Have followed the Kodi thread and tried changing Composite.
Not sure what the refresh rate is for my TV, will investigate.

---

### Post by geoff20 on 2015-03-31
Success, now have video without the tearing.Took a while, so thank you 

[[COLOR=#000000]Vladlenin5000[/COLOR]]("http://ubuntuforums.org/member.php?u=1468732")[COLOR=#000000] [/COLOR]

---

