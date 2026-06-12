---
title: "Run a PERL program turns error"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by nada2 on 2013-09-04
Hi everyone!

I'm new to linux environment and just was able to install and use Ubuntu 12.04 a month ago. Actually I need ubuntu mainly to work with linux-based bioinformatics tools. Few days ago I was able to compile the software (EIGENSOFT, downloaded from: [http://www.hsph.harvard.edu/alkes-price/software/](http://www.hsph.harvard.edu/alkes-price/software/)) into /usr/local/bin directory. My problem now that one of the program inside this software is PERL program and when I type the syntax for it in the terminal, it returns me with this error:
[COLOR=#a52a2a]**bash: ../bin/ploteig: /usr/local/bin/perl: bad interpreter: No such file or directory**[/COLOR]

The program is called ploteig, and is located inside bin of the software file. Would you please help me to overcome this error? :( I downloaded the software in the same path of PERL.

Thanks a lot in advance! O:)

---

### Post by Lars Noodén on 2013-09-04
The first line of a script has to point to the script's interpreter.  The one provided is for a different system than Ubuntu and it appears to have perl in a slightly different location:

```

#!/usr/local/bin/perl  -w 

```

That's the wrong location for a script on a Ubuntu system.  With Ubuntu (or any other), you can find perl with [which](http://manpages.ubuntu.com/manpages/raring/en/man1/which.1.html)

```

which perl

```

That gives us */usr/bin/perl*.  So you can edit the first line of the ploteig script to point to where perl really is.

---

### Post by nada2 on 2013-09-04
Your tip works well.

Thanks a million.. you saved my day:))

---

### Post by Lars Noodén on 2013-09-04
Have fun.  perl is a very flexible scripting language.

---

