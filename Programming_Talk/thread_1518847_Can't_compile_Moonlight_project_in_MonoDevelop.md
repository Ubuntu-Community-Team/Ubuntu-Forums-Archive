---
title: "Can't compile Moonlight project in MonoDevelop"
date: 2010-06-27
forum: Programming Talk
---

### Post by testalucida on 2010-06-27
Hi all,
when compiling a simple Moonlight project the following error occurs:

```
Error: Could not add reference 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' to 'moon5.xap': Assembly not available for Moonlight / Silverlight 2.0 (in Mono 2.4.4) (moon5)
```Here the result of dpkg -l | grep gtk-sharp:

```

ii  gtk-sharp2                        2.12.9-4                            GTK# 2.10 suite, CLI bindings for  GTK+
ii  gtk-sharp2-examples       2.12.9-4                            sample applications for the GTK# 2.10 toolki
ii  gtk-sharp2-gapi                2.12.9-4                            C source parser and C# code generator for GO

```I'm running Lucid and I've installed both MonoDevelop and Moonlight from repository (lucid/main).

What's going wrong here?
Thanks for any advice

Regards
testalucida

---

### Post by slavik on 2010-06-27
try installing the -dev library.

---

### Post by testalucida on 2010-06-27
Hi Slavik
which -dev library do you mean?

---

### Post by slavik on 2010-06-27
slava@dogbert:~$ apt-cache search gtk-sharp
gtk-sharp2-gapi - C source parser and C# code generator for GObject based APIs
libgtk2.0-cil - CLI binding for the GTK+ toolkit 2.12
libgtk2.0-cil-dev - CLI binding for the GTK+ toolkit 2.12
gtk-sharp2 - GTK# 2.10 suite, CLI bindings for GTK+
gtk-sharp2-examples - sample applications for the GTK# 2.10 toolkit
libanculus0.3-cil - utility library for CLI projects
monodoc-anculus-manual - compiled XML documentation for libanculus-sharp
slava@dogbert:~$ 

Looks like you need libgtk2.0-cil

---

### Post by testalucida on 2010-06-27
no :(
result of apt-cache search is exactly like yours

---

### Post by slavik on 2010-06-27
did you install the package?

---

### Post by testalucida on 2010-06-28
dpkg -l | grep libgtk2.0-cil shows:

```

ii  libgtk2.0-cil                               2.12.9-4                                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-cil-dev                           2.12.9-4                                        CLI binding for the GTK+ toolkit 2.12

```

---

