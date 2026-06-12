---
title: "[python] List Printers"
date: 2008-06-02
forum: Programming Talk
---

### Post by themusicwave on 2008-06-02
Hey everyone,

I was wondering if Python has an easy way to list printers on the system.  I need this to work on both Linux and Windows.

I don't need to actually send anything to them, I just need their names.  Basically, this is part of a configuration app that allows the user to pick the default printer for the application.  All I need to do is put the printer name into a config file.

I have been googling for quite awhile now and have turned up nothing...

Thanks,

Jon

---

### Post by geirha on 2008-06-02
Does this give you the needed information?
[php]
import cups
con= cups.Connection()
con.getPrinters()
[/php]

EDIT: Though of course this will only work if you have cups installed (which you usually don't on windows :/ )

---

### Post by themusicwave on 2008-06-02
That would probably work on Linux.

On Windows I am not sure how to do it...

Probably the Win32 API I guess.

---

