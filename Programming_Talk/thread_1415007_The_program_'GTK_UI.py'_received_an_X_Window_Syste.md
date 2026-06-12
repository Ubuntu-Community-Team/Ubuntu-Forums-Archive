---
title: "The program 'GTK UI.py' received an X Window System error ???"
date: 2010-02-24
forum: Programming Talk
---

### Post by baskar007 on 2010-02-24
[PHP]
The program 'GTK UI.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 13812 error_code 9 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/PHP]


I got these errors on my python application on some time. This will crash my application. How do i solve this error.

Note: that my application have some thread for updating GUI. and i am using gdk.threads_enter for threading issue on GTk.

Any idea???????  Please help me.

---

