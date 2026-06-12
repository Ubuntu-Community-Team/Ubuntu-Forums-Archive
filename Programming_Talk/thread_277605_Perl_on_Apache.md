---
title: "Perl on Apache"
date: 2006-10-14
forum: Programming Talk
---

### Post by Naralas on 2006-10-14
I feel dumb because whenever i try run a .cgi file it just shows the source code...

Here is just an example of how INCREDIBLY simple my program is:
```

#!/usr/bin/perl -wT
print "Content-type: text/html\n\n";
print "Hello, world!\n";

```

it just... shows up.

I dont have any refrence to perl at all in my apache2.conf file..

---

### Post by coastdweller on 2006-10-14
> **Naralas said:**
> I feel dumb because whenever i try run a .cgi file it just shows the source code...

Here is just an example of how INCREDIBLY simple my program is:
```

#!/usr/bin/perl -wT
print "Content-type: text/html\n\n";
print "Hello, world!\n";

```

it just... shows up.

I dont have any refrence to perl at all in my apache2.conf file..

Where is perl?

> whereis perl

list what it says.

---

### Post by Naralas on 2006-10-15
perl:
/usr/bin/perl
/etc/perl
/usr/lib/perl
/usr/bin/X11/perl
/usr/share/perl
/usr/share/man/man1/perl.1.gz

---

### Post by coastdweller on 2006-10-15
Is this a lamp server?

---

### Post by Naralas on 2006-10-15
Forgive me but,.. what?

Oh oh sorry, yes Linux, Yes Apache, Yes(well its next on my todo list) mySQL, as of yet: No PHP

---

### Post by nereid on 2006-10-15
Is your CGI script executable and in the CGI folder? Without some tweaking CGI script aren't executable everywhere.

---

### Post by Naralas on 2006-10-15
I know about the cgi_bin but I always thought it was just proper coding not necesarily "needed". Heh if thats my problem I'm gonna slap myself.

And the directory is CHMOD 755

---

### Post by nereid on 2006-10-15
The problem is the apache configuration. Without changing the default config you can only use the cgi_bin to execute CGI scripts.

---

### Post by Naralas on 2006-10-15
even when i use cgi-bin it fails. :(

---

### Post by nereid on 2006-10-16
This seems to be an apache config problem. It would be nice if you could post your error.log from /var/log/apache/ and maybe your apache2.conf from /etc/apache2/.

---

