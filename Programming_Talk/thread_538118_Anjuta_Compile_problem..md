---
title: "Anjuta Compile problem."
date: 2007-08-29
forum: Programming Talk
---

### Post by climatewarrior on 2007-08-29
Hi, this is probably just a stuipidty of mine and not a real problem. Im taking a programming class and the professor gives us code in microsoft word so that we copy and paste it to the IDE and compile it. The problem is that when I copy and paste I get like 30 errors. But If I type the same exact code in Anjuta instead of copying and pasting it the program compiles perfectly.Is there anyway around this?

---

### Post by Paul820 on 2007-08-29
It sounds like he hasn't saved it as a normal ASCII text file. He might have saved it as a word document, anjuta will not be able to read it correctly. Try loading it into open office and resaving it as a normal text file.

---

### Post by climatewarrior on 2007-08-29
I tried that but Im still getting the same problem.

main.c:1: error: stray ¨\357¨ in program

This is what the compile errors look like. I get like 20 of these.

Im going to upload a screenshot of my anjuta with the compile errors + the .txt with 
the code that doesnt compile.

Thank you all!

---

### Post by fct on 2007-08-30
Copy this:

> #include <stdio.h>

int main (int argc, char **argv)
{
int i;
FILE *newoutput;
newoutput = fopen("result.txt", "w");
for (i=0; i<=9; i++)

{
if(i%2!=0)
fprintf(newoutput, "Hello there world\n");
else
fprintf(newoutput, "Smile life is short\n\n");
}

fclose(newoutput);
}


I had to delete the lines with the "stray" errors and rewrite them. Funnily enough, there was no way to convert from UTF-8 to another encoding in gedit, it displayed conversion errors and wouldn't let me save. Same thing with vim.

Looks like the editor of your teacher messes encoding.

---

### Post by fct on 2007-08-30
Read again your message. If he's using Word, you should save the code as a .txt file from Word itself, so that it gets rid of the weird hidden unicode characters it adds to documents.

---

### Post by Ticus on 2007-09-25
If u want to change the format you can copy the code to empty file without any extention, save it then open it with your editor  (I use Kdevelop) and then "save the file as" .cpp

---

### Post by Compyx on 2007-09-25
I think saving it with a .c extension would make more sense since the code is obviously C, not C++. ;)

---

