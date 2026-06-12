---
title: "Setting zenity's general options"
date: 2010-04-26
forum: Programming Talk
---

### Post by carandraug on 2010-04-26
Hi

I've been playing around with zenity lately. However, there's two things that I can't get to work with zenity. These are:

[LIST]
[*]set window height and width with file selection
[*]set the window icon (only works with notification)
[/LIST]

Here's some code
```

zenity --calendar                     # works fine
zenity --calendar --width=1000        # works fine
zenity --file-selection               # works fine
zenity --file-selection --width=1000  # does not enlarge the window

```

I also have a problem with setting the window icon.

```

zenity --notification --window-icon=question     # works fine
zenity --file-selection --window-icon=question   # there's no windowicon

```

I've read that the icon should appear in the window bar but nothing is there at all. Can it be related to the ubuntu theme that is blocking it? I also noticed that the zenity windows do not appear in the window list.

Any help is appreciated.

---

### Post by carandraug on 2010-04-26
Anyone?

---

### Post by fmiceli24 on 2011-08-10
Same issue here (Ubuntu 10.04).

Icon only changes when it is related to a notification.

---

