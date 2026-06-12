---
title: "Amaya is installed but will not start"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Costas100 on 2008-08-25
I am working with Ubuntu Studio and I installed here and there various programs using the add remove or Synaptic Package Manager, I am still a beginner maybe because of my age but I am getting better. I have two questions:

1. How can I find out what is the version of the present Ubuntu system I have installed?

2. A few months ago I tried Amaya and was working fine. Recently it stopped, it tries to start but nothing happens. I used the suggestion from one of the forums and entered in Terminal [SIZE="4"]**amaya**[/SIZE] and received the following reply:

> amaya
03:49:09 PM: Deleted stale lock file '/home/costas/.amaya-costas'.

(amaya:15329): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7700 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
costas@ 

I am not sure what to do now, I searched for the sync command and I am not sure how to apply for amaya, any suggestion will be greatly appreciated.
Costas

---

### Post by Michael.Godawski on 2008-08-25
For finding your current ubuntu version have a look at this tutorial:

[http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)


I am no expert in debugging but perhaps the command
```

amaya --sync
```

will give some more info

---

### Post by Costas100 on 2008-08-25
> **Michael.Godawski said:**
> For finding your current ubuntu version have a look at this tutorial:

[http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)


I am no expert in debugging but perhaps the command
```

amaya --sync
```

will give some more info
Thank you Michael, I found the version. Unforunately the amaya --sync did not work, same error message was produced. I think I will try removing amaya and then reinstall it. I also tried amaya sync without the -- but same results.
Many thanks
Costas

---

