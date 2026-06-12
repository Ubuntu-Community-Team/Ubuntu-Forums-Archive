---
title: "Copy Files with the Command Line - Error Using Parentheses"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by famulusmercury on 2012-10-07
How do you copy files with () in the name using the command line?

eg. = cp my (file) name.txt /home/user/Documents

result = -sh: syntax error: "(" unexpected

I know you have to put "\" before a space in the file name, but what do you do about [B]parentheses in the file name?
[/B]

---

### Post by Vaphell on 2012-10-07
you can try using \ to escape () too, but it would be easier to put the name in quotes "" or '' (now you wont have to manage spaces either)

besides try autocompletion - type first few chars, press tab and the name should be expanded to its full form, with all the necessary escaping done for you, as long as there is no ambiguosity.

---

### Post by papibe on 2012-10-07
> **famulusmercury said:**
> what do you do about parentheses in the file name?
Hi famulusmercury.

You can do the same, and escape them:
```
mv myfile\(2012\).txt /tmp
```
or you can use quotes:
```
mv "myfile(2012).txt" /tmp
```
Let us know how it goes.
Regards.

---

### Post by famulusmercury on 2012-10-07
That got it. Thanks!

---

