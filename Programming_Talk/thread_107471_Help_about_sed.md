---
title: "Help about sed"
date: 2005-12-23
forum: Programming Talk
---

### Post by Gandalf on 2005-12-23
Hello,

I'm trying to change a file which has the below line in it, i want to comment it
```

30     3       * * *  /var/www/vhcs2/engine/tools/vhcs2-httpd-logs-mngr &>/var/log/vhcs2/vhcs2-httpd-logs-mngr.log

```

so i've tried to do
```

sed -i -e "s/\(.*vhcs2-httpd-logs-mngr.*\)/#\1/g"

```
it will succeed except that running it again will add another comment
can anyone tell me how can i Add # just before the 30 because i need it also to do the reverse operation, uncommenting it

Thanks

---

### Post by coredump on 2005-12-23
Sounds like you need to make 'sed' ignore the line when it's already commented out.  One way to do that would be to add something to the pattern that you're matching for, so that the initial hash will make the match fail.  How about:

```
sed -i -e "s/\([^#].*vhcs2-httpd-logs-mngr.*\)/#\1/g"
```

or even:

```
sed -i -e "s/\([^#]*vhcs2-httpd-logs-mngr.*\)/#\1/g"
```

The second one will fail to match if a hash occurs anywhere in the line before the string you're looking for.  I'm using the square brackets to specify a character class (i.e. any one character from the range specified will match) and then negating it with the up-arrow so that only the hash will fail to match.

Do let us know if that works!

---

### Post by Gandalf on 2005-12-23
Nope :(

both of them still add # again and over again whenever the process started again :(

---

### Post by coredump on 2005-12-23
Oh crap, I realised as soon as you said that why it won't work -- now why couldn't I have realised **before** I posted it!  All that the [^#] stuff does is make the pattern match one character later, after the '#'.  Try adding an uparrow to make it an anchored match:

```
sed -i -e "s/^\([^#].*vhcs2-httpd-logs-mngr.*\)/#\1/g"
```

The uparrow is special when it's the first character of a pattern, and it matches the beginning of a line.

Hope that's better...

---

### Post by jerome bettis on 2005-12-23
awk is way easier to use then sed if you know C syntax

awk :cool:

---

### Post by Gandalf on 2005-12-23
@coredump, Thank you that worked like a charm, how about removing it now?
this worked for me
```

sed -i -e "s/^#\([^#].*vhcs2-httpd-logs-mngr.*\)/\1/g"

``` but is it good one?

@jerome bettis: can you point me to a guide or tutorial please?

---

