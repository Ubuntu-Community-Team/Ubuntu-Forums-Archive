---
title: "[SOLVED] Perl Scripting"
date: 2008-11-07
forum: Programming Talk
---

### Post by Jackp90 on 2008-11-07
Hi I am just learning Perl and I was trying to run the following script:


> #!/usr/bin/perl
# vars1
use warnings
$name = "Steve";
print "My name is ", $name, "\n";




But I get the following code:

> 
robert@laptop01:~/begperl$ perl vars1
Unknown warnings category 'Steve' at vars1 line 4
BEGIN failed--compilation aborted at vars1 line 4.



This script is just supposed to spit out 

> 
Hi my name is Steve 



Any help is much appreciated.

---

### Post by LaRoza on 2008-11-07
Semicolon missing ;)

```

#!/usr/bin/perl
# vars1
use warnings;
my $name = "Steve";
print "My name is ", $name, "\n";

```

---

### Post by slavik on 2008-11-07
you forgot a semi-colon after warnings

---

### Post by Gilabuugs on 2008-11-07
I have always liked this about perl,
```
#!/usr/bin/perl
use warning;
$name = "Steve";
print "My name is $name \n";
```

semicolons are sometimes hard to remember with a new language, usually a good place to start if you get an error.

---

### Post by Jackp90 on 2008-11-07
Thanks guys I feel really dumb but at least its working now.

Thanks Again.

---

