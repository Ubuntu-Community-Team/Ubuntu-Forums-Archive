---
title: "selecting a certain number of lines with sed?"
date: 2005-11-26
forum: Programming Talk
---

### Post by nandasunu on 2005-11-26
I am writing a script that has to copy a user specified number of lines from a specified file to another starting from a particular line number.

I believe that the function I need to use is sed, but trying to understand how to do this simple task with it has confused me more than anything!

Does anyone know the correct syntax? I basically need to copy 'n' lines from 'f' file starting at line 'a' ending at line 'b'.

---

### Post by frodon on 2005-11-26
hi,

sed only handle the lines you give to him so you have to select lines you want to handle before using sed.
Ii would be easier to do a perl script for that.
This is a perl script i wrote which will do what you want if i understand well. Use it in a terminal like that : ```
./copy_lines.pl input_file_path output_file_path start_line end_line
```PS : remove the .txt extension

---

### Post by lcg on 2005-11-26
[QUOTE=nandasunu]Does anyone know the correct syntax? I basically need to copy 'n' lines from 'f' file starting at line 'a' ending at line 'b'.[/QUOTE]
Short answer according to the info given: ```
sed -n -e 'a,b p' f
```
You will have to substitute a, b and f with your actual values.

Longer explanation:
-n: suppresses sed's standard output
-e: execute the following script
'a,b p': select the lines between number **a** and **b** and **p**rint them.

With GNU sed, you could also use ```
sed -n -e 'a,+n p' f
```
which does the same as above, but selects and **p**rints **n** lines starting with line **a**.

There might be off-by-1 problems, but you should be able to figure out whether the last line is included or not.

HTH,
Lars

---

### Post by lcg on 2005-11-26
[QUOTE=frodon]
Ii would be easier to do a perl script for that.[/QUOTE]
I could never quite understand why people wanted to use perl (or any other script language, for that matter) for simple goals which can easily be achieved with standard GNU utils. ;)

It should be a lot faster to execute a simple sed script than it is to first load the perl interpreter, which then executes the perl script, which in turn is working on the file. I haven't tested that, so I might be wrong here (but I doubt it).

Lars

---

### Post by nandasunu on 2005-11-26
Thank you both for your help. I am using the solution given by lcg. One problem I am having is running it using variables. It works fine in the command line when I specify the numbers manually, but I need to include it in my script and have the details entered by the user. I would also like to save the results into a variable so that I can save them to a seperate file.

this is how it looks with the variables:

> sed -n -e "$start_line,+$numlines p" $source_file

It doesn't work, I get this error:

> sed: -e expression #1, char 24: unterminated `s' command

---

### Post by lcg on 2005-11-26
[QUOTE=nandasunu]One problem I am having is running it using variables.[/QUOTE]
The problem with your command is that bash interprets the , as part of start_line**,** which probably doesn't exist. Try this one:
```
sed -n -e "${start_line},+${numlines} p" ${source_file}
```

Usually, prefixing a variable with a $ is enough for bash. However, if there is another symbol immediately following the variable name, you have to surround the variable name with {} so bash knows what the variable name is and what isn't.

HTH,
Lars

---

### Post by nandasunu on 2005-11-26
Thank you so much for the help, I've got it working now! I must say that the syntax used in bash is really wierd to me.. I've used C, VB, PHP and a few others  and this has got to be the wierdest one yet... haha :)

---

### Post by lcg on 2005-11-26
[QUOTE=nandasunu]Thank you so much for the help, I've got it working now![/QUOTE]
You're welcome.

[QUOTE=nandasunu]I must say that the syntax used in bash is really wierd to me.. I've used C, VB, PHP and a few others  and this has got to be the wierdest one yet... haha :)[/QUOTE]
It may not be really intuitive, but I'm sure that **every** programming language does not recognize a variable name once you append a character at the end which isn't a word delimiter (in most if not all languages, the comma is; in bash syntax, it is only sometimes). But then again, if you want clean syntax, try Ada or Ruby. ;)

Regards,
Lars

---

### Post by frodon on 2005-11-27
[QUOTE=lcg]I could never quite understand why people wanted to use perl (or any other script language, for that matter) for simple goals which can easily be achieved with standard GNU utils. ;)[/QUOTE]Because i like perl ;)

---

### Post by lcg on 2005-11-27
[QUOTE=frodon]Because i like perl ;)[/QUOTE]
Liking perl is something else I could never really understand. ;)

---

