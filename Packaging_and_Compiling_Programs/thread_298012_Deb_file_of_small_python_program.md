---
title: "Deb file of small python program"
date: 2006-11-12
forum: Packaging and Compiling Programs
---

### Post by Osvaldo on 2006-11-12
Hi.

I'm doing a small program/script in Python and I would like to build a .deb package from it.

Can anyone point to tutorials on how to make a .deb package ?

Is there a graphic tool to do it?

Best regards

Osvaldo

---

### Post by ansi on 2006-11-12
> **Osvaldo said:**
> Hi.

I'm doing a small program/script in Python and I would like to build a .deb package from it.

Can anyone point to tutorials on how to make a .deb package ?



Very simple and straight method is to write Makefile file with "install" target and use ``checkinstall`` program for it.

---

### Post by Osvaldo on 2006-11-13
It seems there's no easier way to do this :( 


But I've found some help files:

[http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)

[http://users.actcom.co.il/~choo/lupg/tutorials/writing-makefiles/writing-makefiles.html](http://users.actcom.co.il/~choo/lupg/tutorials/writing-makefiles/writing-makefiles.html)

I did't quite understand how do you specify where you want the files to be installed, and how to require dependencies.

I may end up using tar command instead :( 

Thanks

Osvaldo

---

### Post by tseliot on 2006-11-13
Try this:
[http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html#Distributing+your+Python+applications](http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html#Distributing+your+Python+applications)

---

