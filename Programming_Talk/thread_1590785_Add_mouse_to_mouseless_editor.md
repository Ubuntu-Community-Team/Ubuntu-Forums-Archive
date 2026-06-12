---
title: "Add mouse to mouseless editor"
date: 2010-10-08
forum: Programming Talk
---

### Post by macropanther on 2010-10-08
I choose to use the [X2 Programmer's Edito]("http://www.tangbu.com")r mostly because of its superior macroing environment ([Regina Rexx]("http://regina-rexx.sourceforge.net/") or [ooRexx based]("http://www.oorexx.org/")).  When started, X2 open a text window.  On Windows, X2 has some limited mouse capabilities and the newer XWinG has full mouse support, but on Linux X2 has virtually no mouse support.  No clicks.  No scroll wheel. nada.  But it still supports Rexx and rexx can talk to anything the shell can talk to.

So, what I'd like to explore is an application that runs from the command line that:
Gets the current text window dimensions,
Overlays an invisible GUI window over it
Captures all mouse motions and clicks and any and keyboard input. And,
send a string to stdout or the RexxSubcom and returns a helpful rc.

The goal here is to let the Rexx macro launch this app, the app watches for mouse clicks, wheel clicks and stripe and paste typeoperations.  When it knows what the user wanted, it returns a string to tell the editor what happened and an rc to validate the returned information.  The macro would turn the info into appropriate editor commands and then reinvoke the mouse watcher.

Any suggestions on where to start.  I have zero X programming experience so some well documented examples would be great.

And, of course, something that already does similar things would be happily used :)

Wes Miller

---

