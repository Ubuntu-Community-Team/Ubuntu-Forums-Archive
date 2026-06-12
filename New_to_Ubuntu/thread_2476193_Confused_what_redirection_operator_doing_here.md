---
title: "Confused what redirection operator doing here"
date: 2022-06-19
forum: New to Ubuntu
---

### Post by abdul1337 on 2022-06-19
Following tutorial on linux journey. I am newbie to linux btw. 

```
$ echo Hello World > rm #is this removing a file called Hello World? 

$ > somefile.txt #I tried this command nothing really happens
```

---

### Post by deadflowr on 2022-06-19
You created a text file called rm.
The contents of which are Hello World.

---

### Post by Impavidus on 2022-06-19
```
echo Hello World > rm
```
The shell breaks this apart in three parts: "echo Hello World", ">" and "rm". The first part is a command, the second an operator to redirect standard output to a file and the third the filename where the output must be redirected too. Then the first part is again broken into three parts: "echo", "Hello" and "World". The first is the actual command, the others are the arguments to the command. The echo commands just writes its arguments to standard output, with spaces between the arguments, so it writes "Hello World". This is redirected to a file named "rm".

The thing after an >, which is an output redirect to file, or <, which is an input redirect from file, is handled as a filename. You can also redirect input and output to processes, tying standard output (and/or standard error) of one process to standard input of another, using pipes. You can also put the output of one command into the arguments of another. rm reads the files it has to remove from its arguments. To remove the file "Hello World", use the command```
rm "$(echo Hello World)"
```which is a needlessly complicated way of writing```
rm "Hello World"
```Watch the quote characters. Without those, rm would attempt to remove two files, named "Hello" and "World".
 
```
> somefile.txt
```This redirects the output of nothing at all to a file named somefile.txt. I wouldn't be surprised if this gave an error message, but as it happens, this creates (at least on Bash 5.1.8) an empty file named "somefile.txt".

All quote characters in this post, except those in code blocks, are just for clarity; the quote characters are not in the actual strings.

---

### Post by Holger_Gehrke on 2022-06-19
Since Impavidus gave a very complete explanation of what's going on in the shell when those commands are executed, here's a little something I happened upon:
```

echo Hello World > Hello World.txt

```
Obviously the result of a forgotten pair of quotes around 'Hello World.txt', but what file is generated and written to and what does it contain ?
The answer is in white text on white background between the dashes. Mark it to see it.
---
 [color=#ebece4]The file is named Hello and contains 'Hello World World.txt'. The shell does redirection quite early in the parsing process. It takes the redirection operator and one 'word' for the file name out of the input and then processes the rest.[/COLOR]
---

Holger

---

### Post by mIk3_08 on 2022-06-20
I prefer the way of Impavidus because it emphasizes the content
```
"content"
```
with the double quote while giving it directly to the
```
content
```
This will shambles you in the future specially when your codes reaches up to 2000 lines. Maybe this will mess you up. Regards and cheers.

---

### Post by abdul1337 on 2022-06-20
Thanks a lot.

---

