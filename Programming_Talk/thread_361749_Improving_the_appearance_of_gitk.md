---
title: "Improving the appearance of gitk"
date: 2007-02-14
forum: Programming Talk
---

### Post by WebDrake on 2007-02-14
Hello all,

I've installed the latest version of git from [http://git.or.cz/](http://git.or.cz/) and there's one problem: gitk (the graphical display of the version history) looks appalling.  I'm guessing it's using the original GTK+, rather than v2.0.  The fonts in the interface are almost illegible.

Can anyone advise about something I can do with Ubuntu to improve matters, or is this something I should take direct to the git developers?

Thanks,

    -- Joe

---

### Post by louis_nichols on 2007-02-15
This should be an option you can set when you run ./configure

Try ./configure --help and it should tell you available switches for compiling. One of them should be for changing the GTK toolkit.

---

### Post by WebDrake on 2007-02-15
> **louis_nichols said:**
> This should be an option you can set when you run ./configure

Try ./configure --help and it should tell you available switches for compiling. One of them should be for changing the GTK toolkit.
Nope, no such luck.  In fact I was wrong about GTK+ as git apparently uses Tcl/Tk.

However, according to a friendly person on the git mailing list, it's possible to edit the .gitk config file and alter the font sizes .... e.g.
```

set mainfont {Helvetica 9}
set textfont {Courier 9}
set uifont {Helvetica 9 bold}

```
.... can be altered to 12, or 15, or whatever, which dramatically improves things.

---

### Post by Rusky on 2011-10-06
Found this on Google; despite its age I thought I'd post a solution in case anyone else finds it that way.

Tcl/tk 8.4 is the default, but 8.5 introduces better font behavior. Run ```
sudo update-alternatives --config wish
``` and choose version 8.5.

This may cause problems with other tcl/tk apps- I assume there's a reason 8.4 is the default.

---

