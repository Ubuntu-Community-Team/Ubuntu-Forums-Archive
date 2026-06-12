---
title: "javascript IE / Firefox /Chrome diagnostics"
date: 2011-09-07
forum: Programming Talk
---

### Post by bcz on 2011-09-07
Recently I had a webpage failing on IE8, but fine on Firefox and Chrome.

I assumed it was fine on IE6 and blamed "non-standards compliant" issues with IE8.

I found it was not MS, but my own coding error.  Javascript clientside validation was using unitialised data.

Firefox and Chrome ignored the problem...  (Standards say ignore errors and make best effort to display webpage) and loaded action page as expected.

IE6 and IE8 left the current page displayed (appearing to be hung).  In the circumstances it would have been nice to have a useful diagnostic on all three browsers.  (Credit to IE here;  at least it showed there was a problem).

So what is the best way to get error diagnostics displayed from javascript clientside code.

Thanks in advance

Bill

---

### Post by aura7 on 2011-09-07
JavaScript tools are also available in Firefox. Try ScratchPad in Firefox by pressing Shift + F4. 

You can also install advanced Javascript debugging plugins like Firebug.

---

### Post by bcz on 2011-09-07
A reply within 2 minutes.  Impressive.

I forgot about firebug.  Used to have it installed, but looks like its not there anymore.  Running FF 6.0.1 and looks like I lost Firbug sometime since FF3 days

Rgds Bill

---

