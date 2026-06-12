---
title: "How to Run an OpenOffice Macro from the Command Line"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by FredJones on 2008-05-08
I ran in Windows this:

"C:\Program Files\OpenOffice.org 2.3\program\soffice" -invisible macro:///Standard.Module1.SaveAsXHTML("E:\ApacheRoot\RTF Tests\somefile.rtf")

and it worked fine.

Now on Gutsy 7.1 I am trying the same:
```

fred@ubuntu-hp:/var/www/apache2-default/RTFTests$ ooffice -invisible "macro:///Standard.Module1.SaveAsXHTML(/var/wwww/apache2-default/RTFTests/somefile.rtf)"
fred@ubuntu-hp:/var/www/apache2-default/RTFTests$ sudo find / -name 'somefile*'
/var/www/apache2-default/RTFTests/somefile.rtf
fred@ubuntu-hp:/var/www/apache2-default/RTFTests$ 

```

and as you can see, it fails, yet the file is there. I tried using soffice instead of ooffice. I tried running JUST the command 'soffice' or 'ooffice' and both bring up an OO window, so they work and are in the path. I tried the above without the invisible switch:

```

ooffice "macro:///Standard.Module1.SaveAsXHTML(/var/wwww/apache2-default/RTFTests/somefile.rtf)"

```

and OO 2.3 opens, but still nothing happens. 

Any ideas?

---

### Post by FredJones on 2008-05-08
Ooops, I see I never made the macro on OO on Gutsy.

Sub SaveAsXHTML( cFile ) 

Now that step is working at least.

An error message would have been helpful however.

OK, ignore me. SOrry.

---

