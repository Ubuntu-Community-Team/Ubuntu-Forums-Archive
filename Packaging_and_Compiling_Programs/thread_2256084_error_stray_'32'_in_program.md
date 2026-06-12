---
title: "error: stray '\32' in program"
date: 2014-12-09
forum: Packaging and Compiling Programs
---

### Post by mitmag on 2014-12-09
When compiling my program using gcc I ended up with the following error:

              error: stray '\32' in program

Does anyone know what this error means and how to correct it?

This is the only error generated.

Thanks ahead of time!

---

### Post by schragge on 2014-12-10
There is an ASCII 26 aka [SUB](http://en.wikipedia.org/wiki/Substitute character) aka [^Z](http://en.wikipedia.org/wiki/Control-Z) somewhere in your source code. Most probably, the last character of a file. You can just edit the offending line by hand or do something like```
[color=green]$ [/color]sed -i 's/\o32//g' [color=blue]your_program.c[/color]
```

---

### Post by mitmag on 2014-12-10
schragge: Thanks a great deal for your reply!
              This solved my problem!
              The code you requested returned  an error,
              but the ^Z in your reply was the tip off!
              My program was trying to load a file saved
              from DOS and I remembered DOS uses this
              for EOF. Heads up on your part!
              Thanks again for your time and knowledge!
              I may have to call on you again.

---

### Post by schragge on 2014-12-10
> The code you requested returned  an errorOops, wrong command. It should have been *sed*, not *sudo*. Corrected. Thank you for your kind words. Could you please change the topic name by adding [SOLVED] before it?

---

### Post by mitmag on 2014-12-10
How is this done?

---

