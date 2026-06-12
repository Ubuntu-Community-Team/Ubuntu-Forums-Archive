---
title: "Broken keymap due do compiz (i think)"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by durban on 2008-12-01
Hello,

I recently installed compiz desktop effects and was toying around with different options via the compizconfig Settings Manager... this included changing some of the default key bindings. BIG MISTAKE!!! I can no longer type <Shift> <c> to get a capital letter <c> in any application! Instead, nothing happens. In compizconfig Settings Manager I've tried to change everything back to defaults but no luck. Is there an easy way to force <Shift> <c> to give me a capital letter c?

---

### Post by ncanna1 on 2008-12-01
edit: sorry, just noticed that you tried that already.

If you open ccsm and go to preferences, there should be an option to reset to defaults.  That will get rid of your custom keybindings.

Is <shift>-c the only thing that's not working?  If so, you could try editing the file by hand.
```

gedit /home/username/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml
```

---

### Post by durban on 2008-12-01
> **ncanna1 said:**
> 
If you open ccsm and go to preferences, there should be an option to reset to defaults.  That will get rid of your custom keybindings.


I did this and it did not work. Typing <Shift>-c Still will not produce a capital letter c

> **ncanna1 said:**
> 
Is <shift>-c the only thing that's not working?  If so, you could try editing the file by hand.
```

gedit /home/username/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml
```

<shift>-c is the only thing not working. I tried opening the gconf.xml file you referenced and it is blank. SHould I be typing something in there?

---

### Post by jenkinbr on 2008-12-01
After making said changes, dod you try to restart compiz?

Try running ```

sudo pkill compiz*

``` and then run ```
 compiz
```

Alternatively, you could restart the X server: save any work, close applications, then press <ctrl>+<alt>+<backspace> to restart X.

Let us know if this does/does not help.

---

### Post by durban on 2008-12-01
[SOLVED]

I killed compiz ```

sudo pkill compiz*

```

and then restarted the X server. Everything works fine now.

It appears (to me) that if you change the default action bindings in the CompizConfig Settings Manager, you can run into trouble. Thanks for all your help.

---

### Post by jenkinbr on 2008-12-02
It's not changing the keybindings themselves, it's changing them to something that can produce undisired effects, like what you had with your <shift>+<c> issue.  A rule of thumb is to never use <shift>,<ctrl>, or <alt> by themselves as a key combination, because it may interfere with another app.  If I want something to have a two-key shortcut, I use the <super> key (aka winkey), as most programs can get by without using it.

Be sure to mark the entire thread as solved by clicking 'thread tools' and selecting 'mark thread as solved' at the top of the page to help others find a solution should they have the same problem.

---

