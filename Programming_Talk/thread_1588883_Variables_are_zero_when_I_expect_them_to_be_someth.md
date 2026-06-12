---
title: "Variables are zero when I expect them to be something else"
date: 2010-10-05
forum: Programming Talk
---

### Post by SoftwareExplorer on 2010-10-05
In the Murrine Gtk theme engine, the opacity of widgets was set with #define s in support.h, which makes it so you have to recompile the whole thing if you want to change the opacity. I decided I wanted try to make it so that you can change it in the gtkrc. After a few tries and 2 days, I seemingly successfully made the change (everything compiles without errors), however, the variables are always zero when I would expect them to be almost 1 (like .90 or something like that).

To try to debug this, I added printf s to tell me what the variable is where it is used, and it comes out to being zero, even though I set it to .90 for debugging purposes right after it should have been read from the gtkrc . This makes me wonder if the part of the code the reads the setting from the gtkrc (murrine_rc_style.c around line 701) is not running? Also confusing is that I thought I initialised the variables (in murrine_rc_style.c around line 204+) to settings that were in the range of .88 to .94, so if the gtkrc reading code isn't running, shouldn't the variables be at what I initialised them to?

You look at can the code I am experimenting on at [[COLOR="DeepSkyBlue"]launchpad[/COLOR]]("http://bazaar.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity/files"), and you can see what I've changed at [[COLOR="DeepSkyBlue"]this launchpad page[/COLOR]]("http://bazaar.launchpad.net/~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity/revision/28?remember=22&compare_revid=22"). You can download it by running ```
bzr branch lp:~erik-b-andersen/gtk2-engines-murrine/MurrineGtkrcOpacity
```

The new variables I added are double s called entryopacity, gradientopacity, menubarglossyopacity, menubaropacity, menubarstripedopacity, menuopacity, notebookopacity, toolbaropacity, toolbarglossyopacity, tooltipopacity, and windowopacity, and are part of the _MurrineRcStyle structure. I also added them to the WidgetParameters structure, they are copied from a _MurrineRcStyle to a WidgetParameters in murrine_set_widget_parameters (which is in murrine_style.c around line 149).

Help would be greatly appreciated, I've tried and tried to fix this on my own, but I don't think I'll figure it out myself. I feel like I'm at this point ](*,) . Let me know if you need any more information.

---

### Post by Zugzwang on 2010-10-06
Hardly related, but many debuggers have a function that allow you to watch a variable in a way such that your program is interrupted right after the variable content has changed. Perhaps yours has this function as well?

See, e.g., here: [http://www.gammon.com.au/forum/?id=9123](http://www.gammon.com.au/forum/?id=9123)

---

### Post by SoftwareExplorer on 2010-10-06
> **Zugzwang said:**
> Hardly related, but many debuggers have a function that allow you to watch a variable in a way such that your program is interrupted right after the variable content has changed. Perhaps yours has this function as well?

See, e.g., here: [http://www.gammon.com.au/forum/?id=9123](http://www.gammon.com.au/forum/?id=9123)

I think I would use gdb and I'm pretty sure it can watch a variable. But how would I do that for something that you don't run directly (ie you don't type murrine a a command prompt, instead, it runs when something else runs, like a Gtk application)?

---

### Post by dwhitney67 on 2010-10-06
Good question!

What I do in such circumstances is intentionally insert the following code within the app you want to debug:
```

#include <unistd.h>
...

int flag = 1;

while (flag == 1)
{
   sleep(2);
}

```

After recompiling this library (or module or whatever it is), launch the main app as you normally would.

Then, when *murrine* is running, lookup it's process ID.  Then with GDB:
```

gdb murrine <pid>

```
You should find the *murrine* endlessly looping at the while-loop created above.  To get out of the while loop, invoke this command from within GDB:
```

set flag=0

```
Then continue debugging as you normally would.


P.S.  ddd is a lot friendlier than gdb alone.

---

### Post by endotherm on 2010-10-06
@dwhitney67: what an interesting approach. thank you!

---

### Post by SoftwareExplorer on 2010-10-09
I got the gdb thing to work, but it wasn't very useful because I can't figure out how to make pbuilder build the package with debugging symbols. 

However, I tried putting in some more printfs and found out that the gscanner that is scanning the gtkrc is picking up the values. However, in murrine_style.c around line 140, params and murrine_style have zero values. If I change the code to assign a reasonable value to the opacity variables in params instead of copying them from the murrine_style variables (which are zero) the highlights on buttons and menubars draw properly, otherwise, everything else is completely transparent, as if the variables are still zero.

---

### Post by dwhitney67 on 2010-10-09
Somehow you need to figure out how to pass the -g compiler option to the compiler when building the source files.

Make sure that if you are using a Makefile that it does not conclude by stripping out the debugging symbols using the command "strip".

---

