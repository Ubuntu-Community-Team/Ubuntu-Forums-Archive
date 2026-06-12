---
title: "cases in C sharp"
date: 2011-05-15
forum: Programming Talk
---

### Post by Drenriza on 2011-05-15
When you create cases in C# in a console / terminal. if you have the following options

press 1 for something
press 2 for something else
press 3 for something third.

If i press one how do i clear the console / terminal screen before the next set of cases are presented to the user?

Thanks on advance.
Kind regards.

---

### Post by NovaAesa on 2011-05-15
The easiest way would be to just print enough carriage returns to empty the screen. There are other ways though - you could use a system call to execute "clear" (or "cls" if you're running on Windows) or use something more sophisticated such as ncurses. I'm not sure if there are bindings for C# or not though.

EDIT: yes, ncurses does have C# bindings. [http://sourceforge.net/projects/curses-sharp/](http://sourceforge.net/projects/curses-sharp/)

---

### Post by simeon87 on 2011-05-15
I don't speak from experience but try [Console.Clear()]("http://msdn.microsoft.com/en-us/library/system.console.clear.aspx").

---

### Post by NovaAesa on 2011-05-15
> **simeon87 said:**
> I don't speak from experience but try [Console.Clear()]("http://msdn.microsoft.com/en-us/library/system.console.clear.aspx").

That's much better than my solution!

---

### Post by cgroza on 2011-05-15
If it is a serious program and you want a more than a "enter the number" interface, you should use ncurses.

---

