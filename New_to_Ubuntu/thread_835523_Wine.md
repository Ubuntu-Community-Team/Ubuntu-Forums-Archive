---
title: "Wine"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by sampioen on 2008-06-20
Hello all. Please advise. Thx.

I downloaded an decoder used to open online statements.
and installed Wine to run this windows decoder with the command as follows (I deleted some of the words to make it shorter):

root@sampi:/home/samuel# cd Desktop
root@sampi:/home/samuel/Desktop# wine striata-reader.exe
wine: creating configuration directory '/root/.wine'...
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set
correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 0
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set
correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error
1114
err:ole:apartment_createwindowifneeded CreateWindow failed with error
-536870654
Could not load Mozilla. HTML rendering will be disabled.
No protocol specified
err:wgl:process_attach X11DRV or GDI32 not loaded. Cannot create default
context                                                                                                   .
wine: '/root/.wine' created successfully.
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set
correctly.

:mad:

---

### Post by gr4nf on 2008-06-20
It's having trouble finding the display from the command line. Are you using a VT? Try just running it by double-clicking on the executable. It should run with wine automatically.

---

### Post by infoseeker on 2008-08-02
Check out this thread

[http://ubuntuforums.org/showthread.php?t=511759&highlight=striata](http://ubuntuforums.org/showthread.php?t=511759&highlight=striata)

You don't need wine to open your *.emc files.

---

