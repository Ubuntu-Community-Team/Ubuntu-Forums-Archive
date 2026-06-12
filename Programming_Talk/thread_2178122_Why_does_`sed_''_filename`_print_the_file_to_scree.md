---
title: "Why does `sed '' filename` print the file to screen?"
date: 2013-10-02
forum: Programming Talk
---

### Post by vasa1 on 2013-10-02
If I have a file called "filename" and run [FONT=Courier New]sed '' filename[/FONT], the contents of "filename" appear on the screen. Why is that?

---

### Post by Vaphell on 2013-10-02
sed streams file but modifies it on the fly using these programs/expressions you usually provide. If you provide empty program, no change happens and the file is printed to the screen verbatim.

---

### Post by vasa1 on 2013-10-02
> **Vaphell said:**
> sed streams file but modifies it on the fly using these programs/expressions you usually provide. If you provide empty program, no change happens and the file is printed to the screen verbatim.

In other words, in something like
```
sed OPTIONS SCRIPT/COMMANDS INPUTFILE
``` the **SCRIPT/COMMANDS** would be within **'** and **'** but just an empty **''** tells sed to print INPUTFILE to screen verbatim and that is because "print" is the default when nothing else is specified or when "print" is not specifically excluded from being default by use of **-n**.

Would my understanding be correct?

---

### Post by Vaphell on 2013-10-02
yes.
Technically the script/commands part doesn't have to be within '' or "", all you have to make sure is that shell passes that part as a single parameter. Quotes are merely the most convenient way to do that but you can escape all chars related to shell syntax eg whitespace, semicolons etc. 

```
$ sed -n p\;s/\ /=/g\;p <( echo a b c )
a b c
a=b=c
```

---

### Post by vasa1 on 2013-10-02
Thank you! Marked "Solved"

---

