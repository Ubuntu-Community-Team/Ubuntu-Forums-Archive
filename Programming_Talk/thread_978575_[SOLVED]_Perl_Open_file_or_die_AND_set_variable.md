---
title: "[SOLVED] Perl: Open file or die AND set variable"
date: 2008-11-11
forum: Programming Talk
---

### Post by Rocket2DMn on 2008-11-11
Hey guys and gals, I'm posting this as a regular user, I need some help!  I don't know a lot about perl, so here goes:

I am opening a file as follows:
```
open(CONFIG , $filename) ||
   die "$filename is not available.\n";
```
I would like to also be able to set my return value variable ($RETVAL) to 1 in the case that die is executed, but I don't know how to combine the two commands.

Perhaps I need to run the open function with an eval expression (which I know nothing about)?  Or can I just do something like
```
if (!CONFIG) {
   $RETVAL=1;
}
```
Thanks in advance!

---

### Post by loell on 2008-11-11
maybe put $RETVAL=1; before die?

---

### Post by Rocket2DMn on 2008-11-11
> **loell said:**
> maybe put $RETVAL=1; before die?

You mean like this?
```
open(CONFIG , $filename) ||
   $RETVAL=1; die "$filename is not available.\n";
```

I get
```
Can't modify logical or (||) in scalar assignment at *(./scriptname)* line 148, near "1;"
Execution of *(./scriptname)* aborted due to compilation errors.
```

If there isn't a way to combine two commands after the or (||) statement, what is the best way to capture the fact that the file open failed before the next part of the code executes?  If I can do that, I can set the return value and break out of the subroutine.  That's why I asked about eval as well, I just don't know how to use it effectively.

---

### Post by loell on 2008-11-11
```

sub die_me {
$retval = 1;
die "$filename is not available.\n"
}

open(CONFIG , $filename) || die_me();
```

---

### Post by brunovecchi on 2008-11-11
I think there is no need to set $RETVAL manually, there are lots of environment variables that perl handles automatically, check out [**This page**]("http://www.sarand.com/td/ref_perl_reserve.html").

I think you are looking for the $! variable, but I'm not sure, you can check the list to see which one you should look for.

EDIT: **[This list ]("http://www.kichwa.com/quik_ref/spec_variables.html")**is shorter and friendlier

---

### Post by Rocket2DMn on 2008-11-11
OK, it would appear that using die() is not allowing me to set return codes in my program since I guess it sets its own the returns up the function stack until it exits.  I was able to achieve my goal with:
```
open(CONFIG , $filename) || do {
   print "$filename is not available.\n";
   $RETVAL=1;
}
```
Using the two lines above in a separate function also worked (which is what gave me the idea to use a do {} statement.  A separate function didn't help either with trying to combine my own return values with die().

I will attempt to capture die() further up in the stack so that I can still use proper error handling.  Thank you for the help!

---

