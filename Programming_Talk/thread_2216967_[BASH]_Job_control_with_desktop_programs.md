---
title: "[BASH] Job control with desktop programs?"
date: 2014-04-14
forum: Programming Talk
---

### Post by rocket13 on 2014-04-14
I've never figured out how to make one desktop program wait for another to finish before starting itself. For example, in a bash script:

gedit somefile.txt
zenity --info --title="Status:" --text="Done!"

What happens is that the zenity box appears as soon as the gedit window is loaded, but I want it to wait until the gedit window is closed.  I haven't been able to make the usual bash script commands like:

<somecommand> &
waitvar=$!
wait $waitvar

work with desktop programs like gedit and zenity.  There must be a simple answer, but how is it done?  Many thanks in advance!

---

### Post by papibe on 2014-04-14
Hi rocket13. Welcome to the forum ):P

In a regular bash script, zenity should be executed only after gedit have closed,  so you're experiencing something unique.

Could you post your script so we can take a look?

Regards.

---

### Post by steeldriver on 2014-04-14
I suspect the issue is that if the user already has a running instance of gedit, then when it's invoked in the script it just does some dbus sorcery behind the scenes to open 'somefile' in the running instance (and then returns control to the script). A possible workaround may be to force standalone mode:

```

gedit **-s** somefile.txt
zenity --info --title='Status:' --text='Done!'

```
or
```

gedit **-s** somefile.txt && zenity --info --title='Status:' --text='Done!'

```

---

### Post by rocket13 on 2014-04-14
Well, I've discovered something interesting.  Here's a sample script:

#!/bin/bash
echo "Some text" > Testfile.txt
gedit Testfile.txt
zenity --info --title="Status:" --text="Done!"
exit

This works in sequence, i.e. zenity waits for gedit to finish-- but only if there is no other gedit window already open.  If there is already a gedit window open, then the zenity box appears instantly, without waiting, even if I add the --new-window switch to the gedit command, forcing a new instance of gedit.  Can you confirm this behavior?

---

### Post by rocket13 on 2014-04-14
You guys are amazing!  While I was replying to Papibe, steeldriver posted his suggestion, to try using the -s, or "standalone" switch... which works!  I didn't even know about the -s switch in gedit.  Many thanks!  So, I'm thinking I should mark it solved, right?  Much appreciated, you guys!

---

