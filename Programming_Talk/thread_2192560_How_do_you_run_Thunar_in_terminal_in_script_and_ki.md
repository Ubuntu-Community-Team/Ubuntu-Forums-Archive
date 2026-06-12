---
title: "How do you run Thunar in terminal in script and kill the terminal?"
date: 2013-12-08
forum: Programming Talk
---

### Post by sam_baker2 on 2013-12-08
hi,

How do you call Thunar up in a script and have the terminal to exit?

I have this script:
```

#!/bin/bash
Thunar ~/Documents/Temp 
exit

```

that must be run in the terminal, but after Thunar
runs, the terminal hangs around.

How can I get kill the terminal after Thunar runs?
I can manually click on it and make it go away, but I want it to
automatically disappear.


Thanks

---

### Post by hakermania on 2013-12-08
Hm, when you run the above script from terminal, you can do the following:

```
./that_script_you_posted.sh& exit
```

That will cause  the script you posted to start and then the terminal will exit without killing Thunar.

On the other hand, if you've made a .deskop file for Thunar, then I think that adding a & at the end of "[COLOR=#000000][FONT=Ubuntu Mono]Thunar ~/Documents/Temp[/FONT][/COLOR]" will do the trick.

---

### Post by Lars Noodén on 2013-12-08
If you use exec, then the terminal will go away after thunar is finished.

```

exec /usr/bin/thunar ~/Documents/Temp/

```

---

### Post by sam_baker2 on 2013-12-08
I want to run the script from the file browser its self by right-clicking on 
the script and selecting "run in terminal".
Another thunar file browser pops up with ~/Documents/Temp ,
but the terminal hangs around unless I manually click on it to go away.
.

---

### Post by sam_baker2 on 2013-12-08
here is the customized command in Thunar that lets me "run in terminal"
```

xfce4-terminal -e %f --hold

```

---

### Post by Lars Noodén on 2013-12-08
What happens when you run it without --hold ?

---

### Post by sam_baker2 on 2013-12-08
hmmm, taking --hold allowed the terminal to exit. I wonder why "--hold" is even in the command?

---

### Post by Lars Noodén on 2013-12-08
Having --hold would be there to [keep the terminal around](http://manpages.ubuntu.com/manpages/saucy/en/man1/xfce4-terminal.1.html) after the command it has run is finished.  ;)  Someone must have thought it useful, though for most cases I would go with your method.

---

### Post by sam_baker2 on 2013-12-08
I made aanother command , now have one with the "--hold"
and another without.

Thanks

---

