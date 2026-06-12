---
title: "How to calculate an expression in simple Script programming written in Emacs"
date: 2010-04-01
forum: Programming Talk
---

### Post by nir2000 on 2010-04-01
Hi everybody!
I have just started writing scripts. I am new to it, so excuse me for the silly question.
I wrote a Script that look like this in Emacs:
#!/bin/sh
echo "2*3=" $[2*3]
that's all, and I expected the output:2*3=6 when I run the Script.
Unfortunately the Script doesn't compute the expression in brackets [] and simply copies $[2*3] to the output.
When I simply write into the bash Shell: echo $[2*3] it prints out the result 6 as expected.
I have tried few configurations and I simply don't know how to make my Script compute expressions.
My Emacs doesn't Know the command expr.
Please if somebody know how to compute expressions in Scripts written in Emacs please let me know.
Thank you in advance.
Nir

---

### Post by swizman on 2010-04-01
echo $(( 2*3 )) 


Have fun

---

### Post by geirha on 2010-04-01
$[ ] is an old, obsolete, bash syntax for doing math, don't use it. If you found that in some bash "tutorial", then that "tutorial" is junk, don't read it.

Furthermore /bin/sh is not the same as /bin/bash. /bin/sh is a POSIX shell (dash) and has less features than bash, which is why it wasn't working in your script with #!/bin/sh as she-bang.

The $(( )) syntax is POSIX, so it will work with both /bin/sh and /bin/bash.

I recommend [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) for learning shell scripting.

---

### Post by nir2000 on 2010-04-01
Thank you very much for your replies they were very helpful and correct.
have a nice day.
Nir

---

