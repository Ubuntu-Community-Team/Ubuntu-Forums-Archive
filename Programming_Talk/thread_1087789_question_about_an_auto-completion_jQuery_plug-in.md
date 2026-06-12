---
title: "question about an auto-completion jQuery plug-in"
date: 2009-03-05
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-05
Hi everyone

I am using this javascript code for auto-completion.
[http://nodstrum.com/2007/09/19/autocompleter/](http://nodstrum.com/2007/09/19/autocompleter/)
Demo:  [http://res.nodstrum.com/autoComplete/index.htm](http://res.nodstrum.com/autoComplete/index.htm)

I am happy with it, except that when the auto-suggestion box shows, everything else underneath it is pushed downwards.

Is there a way to take the suggestion box out of the flow and make it overlay on top of everything else?

I can change postition property to absolute which solves the problem, but then position of suggestbox is changing depending on the browser window size...


Thanks,

Tom

---

### Post by CptPicard on 2009-03-05
I am not a CSS guru, but CSS certainly supports layering. Look at the "z-index" property and how to use it, IIRC.

---

