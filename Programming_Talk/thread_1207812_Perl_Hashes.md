---
title: "Perl Hashes"
date: 2009-07-08
forum: Programming Talk
---

### Post by dellwood on 2009-07-08
Hi, 

I have recently been tasked with taking some Perl scripts (used to test drivers) and make them more accessible from the command line.  To do this, I have to be able to change a hash so that two of its variables can easily be changes (the 'host' and 'tree' ). Currently, I have it set up something like this:

```


my $var = ARGV[2];

---other code here---

if( $var eq 'arg-1')
{
    $conf{'ldap'}{'host'} = <someipadress>;
    $conf{'ldap'}{'tree'} = <sometree>;
}
if( $var eq 'arg-2')
{
    (same as above)
}
else
{
    (default)
}

```

(The ldap hash is nested inside the conf hash)

Also, I currently have those two variables ('host' and 'tree') set as undefined.  

So, I was wondering if this is their was a **clearer** or **better** way do accomplish this (notice the bold -- I know it can be done to the *same* profiency a zillion different ways -- its perl :D )

All help is greatly appreciated :).

-Josh

---

### Post by indigest on 2009-07-08
You might want to try the Getopt package for extracting flags and arguments from the command line.  There doesn't seem to be anything confusing or unusual about what you're doing with the hashes, so I don't see how it could be improved.

---

