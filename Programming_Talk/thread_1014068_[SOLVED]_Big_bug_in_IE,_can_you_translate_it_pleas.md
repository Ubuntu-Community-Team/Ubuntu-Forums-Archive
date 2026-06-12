---
title: "[SOLVED] Big bug in IE, can you translate it please?"
date: 2008-12-17
forum: Programming Talk
---

### Post by L-mental on 2008-12-17
I bumped into this:
[http://edition.cnn.com/video/#/video/tech/2008/12/16/finighan.internet.explorer.cnn](http://edition.cnn.com/video/#/video/tech/2008/12/16/finighan.internet.explorer.cnn)

Can you please explain what is he talking about? I would be really grateful.
I fear not to descend into details or reading so much material and/or pages. So be as detailed as you're able. Thx.:p

PS: Why does he think that if it's not windows, it has to be Mac? Why are they, with such an important position, so illiterate?

PS2: I guess Microsoft stakeholders are not happy :popcorn:

---

### Post by nvteighen on 2008-12-17
Ok, it's about an "invalid pointer reference". Very basically put, at some point of code, IE is trying to access (possibly write) a place in memory that might not be guarranteed to be its own. So, an attacker could eventually inject some code at that memory place and IE would execute it.

But, it's quite interesting to see a reporter saying that this is too complicated to him... Why don't they get a better informed one for these kind of stuff? ("Mozilla's" Firefox, Safari and Google Chrome are "Internet Explorers from other manufacturers"? I guess he wants to keep it simple, but why doesn't he just say "web browser"??)

---

### Post by Reiger on 2008-12-17
Suppose you had a fairly computer-illiterate grandma... What's going to ring a bell: "[Internet] Explorer" or "web browser" ?

I know mine would stare at me "web browser? what's that?".

---

### Post by Gilabuugs on 2008-12-17
> **L-mental said:**
> 
PS: Why does he think that if it's not windows, it has to be Mac? 


He doesn't say that he says that safari the mac default browser is available on windows.

> Why are they, with such an important position, so illiterate?

The average person knows little about how computers work and would not understand any details, he gave a situation in which it was being used (grabbing passwords) and what the target was (IE7) and then gave plenty of alternatives (Firefox, Chrome, Safari) that is sufficient for news of this type.

And he just misspoke when he said internet explorers he said browser in the beginning, he was probably just a bit antsy.

---

### Post by mssever on 2008-12-17
I hate CNN. Their video never works on my machine. Another offender is Fox News. Why can't these idiots write software that works wherever Flash is installed?

---

### Post by L-mental on 2008-12-17
Thanks, nvteighen.
One more question: doesn't AVG and similar products defends you against those attacks, or by the way they're done those antivirus can't "see" what's going on? 
I'm ignorant on how anti-virus work on the web attacks.

---

### Post by slavik on 2008-12-17
> **mssever said:**
> I hate CNN. Their video never works on my machine. Another offender is Fox News. Why can't these idiots write software that works wherever Flash is installed?
That would make sense and we can't have non of that.

---

### Post by nvteighen on 2008-12-18
> **L-mental said:**
> Thanks, nvteighen.
One more question: doesn't AVG and similar products defends you against those attacks, or by the way they're done those antivirus can't "see" what's going on? 
I'm ignorant on how anti-virus work on the web attacks.
I'm not sure... but I fear such attacks are rather network-based, e.g. a site that executes code taking advantage from this vulnerability... an antivirus won't be able to detect that, as it is IE's code which is being run. The best protection would be to use a more decent browser (anything not called IE :)) or disabling any possible plugin and Javascript at IE (maybe even images) and wait for the patch to be delivered.

---

### Post by L-mental on 2008-12-18
:D
Never used IE in my whole life. IE it's something that uses to happen in some other people computers, but living in this world of market shares and blah blah blah, I better understand what's going on, right?
However, after the first answer I reasoned about not letting Explorer run anything... and did not know about the pictures though. That's why I asked, in these strange and dangerous domains (IE and friends) better double check for the right information. Thanks!
;-)

---

