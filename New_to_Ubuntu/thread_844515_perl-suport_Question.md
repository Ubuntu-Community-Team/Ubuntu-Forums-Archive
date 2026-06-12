---
title: "perl-suport Question"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by perlsyntax on 2008-06-29
What does this error mean?



Can't stat /usr/local/share/perl/5.8.8: No such file or directory
 at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't stat /usr/local/lib/perl/5.8.8: No such file or directory
 at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't stat /usr/local/lib/site_perl: No such file or directory
 at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't cd to (./) .dbus: Permission denied
 at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Apache::RPC::Server                  (1.29)    A subclass of RPC::XML::Server tuned for mod_perl
:confused:

---

### Post by Xerp on 2008-06-29
> 
Can't stat /usr/local/share/perl/5.8.8: No such file or directory


Sounds like /usr/local/share/perl/5.8.8 doesn't exist. Have a look with:

```
ls -la /usr/local/share/perl
```

---

### Post by perlsyntax on 2008-06-29
How do i fix it?

---

### Post by Xerp on 2008-06-29
What exactly is it that you are trying to achieve? Install Apache with mod_perl?

---

### Post by perlsyntax on 2008-06-29
i try to install perl-support.zip for my gvim.

---

### Post by Xerp on 2008-06-29
try:

```
sudo apt-get install vim-perl
```

---

### Post by perlsyntax on 2008-06-29
[http://www.vim.org/scripts/script.php?script_id=556](http://www.vim.org/scripts/script.php?script_id=556)

---

### Post by perlsyntax on 2008-06-30
can anyone help m and does anyone have prob with perl?



:(

---

### Post by Xerp on 2008-06-30
[http://packages.ubuntu.com/hardy/editors/vim-perl](http://packages.ubuntu.com/hardy/editors/vim-perl)

---

### Post by perlsyntax on 2008-07-01
that not what i looking for.

---

