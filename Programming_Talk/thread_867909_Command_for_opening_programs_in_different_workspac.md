---
title: "Command for opening programs in different workspaces?"
date: 2008-07-23
forum: Programming Talk
---

### Post by ConMan318 on 2008-07-23
I would like a command line open on all 4 workspaces all the time, as well as opening some other programs in specific places, so I want to write a simple startup script to open things up on each workspace.  How can I specify which workspace to open a program on?

I searched and found some old threads saying it can't be done, and saying a "Devil's Pie" add-on was needed, but I'd prefer a command, hoping there is one by now :p.  If not, though, can anyone link me to a site showing how to emulate button-presses in Bash or Perl?  I could do something like this pseudo:
```

open terminal
emulate Alt+Ctrl+Right
open another terminal
emulate Alt+Ctrl+Right
et cetera...

```

but I don't know how to mimic a button-press.

I am using compiz-fusion, and have the cube enabled.  Don't think that should matter, but letting you know just in case.

Thank you.

---

### Post by mssever on 2008-07-23
I'm guessing Devil's Pie would be your easiest option. Any Bash or Perl approach would depend on some library to do the work--and I'm quite sure that such a library, if it even exists, isn't installed by default. So you'll have to install something either way, and Devil's Pie is probably much easier to use. Disclaimer: I haven't actually used Devil's Pie.

---

