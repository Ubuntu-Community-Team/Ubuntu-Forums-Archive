---
title: "how to search for a string  in a file inside a directory reccursively and replace"
date: 2013-08-11
forum: Programming Talk
---

### Post by Rahul04789 on 2013-08-11
Hi all,


I want to search a string    **printf("Line**      and replace it with the string    **printf("\nLine**

I have used the following code but oit gives error.

rahul@rahul-VPCEG28FN:~$ grep -rl 'printf("Line' qqqqq/ | xargs sed -i 's/printf("Line/printf("/nLine/g'
sed: -e expression #1, char 24: unknown option to `s'


please tell me how to do it?


Regards

---

### Post by bsamim on 2013-08-11
/usr/bin/perl -pi -e 's#printf\("Line#printf\("\\nLine#g' *.C

where *.C expression is the file or expression matching the file(s) you are interested in

---

### Post by SeijiSensei on 2013-08-11
Rather than sending the OP off to using perl, let's answer the original question.

If you want to insert a return, you need to use the "\n" alias.  However if that is entered into a string enclosed in single quotes, bash will interpret it as a literal \n, and not the return character.  To have bash replace \n with a return, you need to enclose the sed string in double quotes.

In your example, try this instead:

"s/printf(\"Line/printf(\n\"Line/g"

Notice that I also had to escape the " with the backslash since the entire expression in enclosed in double quotes.

---

### Post by Vaphell on 2013-08-11
OP said he wants [COLOR="#0000FF"]\[/COLOR]nLine but botched the expression and put [COLOR="#FF0000"]/[/COLOR]n instead. He got s//[COLOR="#FF0000"]/[/COLOR]/ while he should have s///

---

### Post by SeijiSensei on 2013-08-11
My recollection was that using single or double quotes with sed affected the interpretation of the command string the same way it does when bash interprets a string in quotes.  *I was wrong.*  I've tried a number of experiments and find *no difference* between

```
sed 's/\t/,/g' < file
```

and 

```
sed "s/\t/,/g" < file
```

(\t is the alias for the tab character; this command converts tabs to commas.)  

I also checked whether the quotes mattered if the special character was in the initial regular expression in the substitute command or in the substitution itself.  That also made no difference.  "s/,/\t/g" and 's/,/\t/g' return the same result.

Chalk it up to my declining memory, I guess.  Perhaps I was recalling a case where I was using an environment variable in the string.  Then the choice of quotes definitely matters, as in "s/,/$CHAR/g".

---

### Post by DarkAmbient on 2013-08-12
sed -i "s/printf(/printf\(\\\n/g" /path/to/file.txt

It's untested but would this suffice? Remove 2 \ in \\\n to insert a newline-character rather than adding \n as a string.

---

### Post by Vaphell on 2013-08-12
```
$ echo 'printf("abc") printf("def")' | sed 's/printf("/&\\n/g'
printf("\nabc") printf("\ndef")
```

that said, OP, why are you starting printfs with newlines? That's somewhat counterintuitive. When you type you don't go ENTER then CONTENT, you go CONTENT, then confirm with ENTER.

---

