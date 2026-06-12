---
title: "Showing Authentication Dialog"
date: 2010-08-30
forum: Packaging and Compiling Programs
---

### Post by vishvesh on 2010-08-30
Hi all,
   I have been using Ubuntu for few months now. I have used deb  files which doesn't ask user to Authenticate. So I am not sure whether  it's legal to show up an Authentication dialog. So my question is can I show up Authentication Dialog?

  Secondly I have an installer(Created using IZPack) jar file. Through which I intend to install java 1.5 jre, for which I would need administrative rights. Is there a way to access the admin rights from UI? 

Any suggestions on this issue are welcome.

Thanks and Regards,
Vishvesh

---

### Post by Bachstelze on 2010-08-30
A DEB package is always installed as root, an authentication dialog should not be needed.

---

### Post by vishvesh on 2010-09-01
Hi Bachstelze,
    I am using a deb installer for JRE 1.5. So as you said I don't have to worry about authentication. 

This question is for understanding things better on Ubuntu. Is there a way to show Authentication dialog similar to the one below on Linux.

[IMG]http://i55.tinypic.com/15na8v8.png[/IMG]
     The image is taken from a Macintosh Machine.

Is it the case with Ubuntu that the OS decides when to display the Authentication dialog.

---

### Post by surfer on 2010-09-01
by the way: you could install sun-java (ok, it's jre 1.6) from the partner repositories with apt-get (or synaptic).

there are many ways do display widgets. there is swing for java, wxwindows for c++, wxpython/glade for python, you can even write small guis in the bash (with zenity).

if you just want to start an application from the shell that needs root rights, use
```
$ gksudo application

```

---

### Post by vishvesh on 2010-09-06
Thank you very much for the suggestion.

---

