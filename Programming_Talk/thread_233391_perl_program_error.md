---
title: "perl program error"
date: 2006-08-10
forum: Programming Talk
---

### Post by FuzZy2006 on 2006-08-10
i'm trying to write one exercise from the perl llama book -- ex9-3 I guess. The code is so:
[HTML]#! /usr/bin/perl -w
$^I=".bak";
while(<>){if/^#!/{$_."##Copyrighted in 2006 by me;}}
[/HTML]. It is something similar. I wrote the exercise, i verified it at answers. saved it under ex9-3 name, but when i run [HTML]./ex9-3 fred[/HTML](where fred is a file that it'll edit, which is a perl program too). the program should ad that ##copyrighted line on the shebang line of the perl program, but it deletes what the file contains. the file is a perl program too. pls hlp.

---

### Post by yaaarrrgg on 2006-08-11
no print statement?
filtering on only the line that matches
syntax errors.

here is it cleaned up a bit:

```

#!/usr/bin/perl -w
while(<>){
    print $_;
    if (/^#!/) {
        print "##Copyrighted in 2006 by me; \n\n";
    }
}

```

you can write the output to another file.

---

