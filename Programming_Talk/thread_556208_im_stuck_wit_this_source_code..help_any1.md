---
title: "im stuck wit this source code..help any1"
date: 2007-09-21
forum: Programming Talk
---

### Post by azroule on 2007-09-21
ok here are my code, suppose this source code that im trying to do will make a copy the content from the input.txt and then write to output.txt..
=======================
the sourcecode is
=======================
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>

main()
{
int fdin, fdout, value,bytes_read;
char buffer[5000];
char c;
fdin = fopen ("input.txt", "r");
fdout = fopen ("output.txt", "wr");


while(1) { /* keep looping... */
c = fgetc(fdin);
if(c!=EOF) {
printf("%c", c);
//fprintf(fdout, buffer, value);
fprintf( fdout, "%c", c );



/* print the file one character at a time */
}
else {
break; /* ...break when EOF is reached */
}
}


//bytes_read = read (fdin, buffer, 5000);
//write(fdout, buffer, value);

close(fdin);
close(fdout);
}

==========================================================
the error is
==========================================================
azroule@ophidiophobia:~/azali$ ./mc.c
./mc.c: line 10: syntax error near unexpected token `('
./mc.c: line 10: `fdin = open ("input.txt", O_RDONLY);'
azroule@ophidiophobia:~/azali$ 
azroule@ophidiophobia:~/azali$ cc mc.c -o mc
mc.c: In function â€˜mainâ€™:
mc.c:15: warning: passing argument 1 of â€˜fgetcâ€™ makes pointer from integer without a cast
mc.c:19: warning: passing argument 1 of â€˜fprintfâ€™ makes pointer from integer without a cast
azroule@ophidiophobia:~/azali$

---

### Post by yabbadabbadont on 2007-09-21
Two things:

1) Do your own homework.  ;)
2) Read the fgetc man page for the correct syntax.  (same for fprintf)

---

### Post by slavik on 2007-09-21
1. declare many as returning an int.
2. return 0 from main at the end
3. don't put space between opening parenthesis and function name
4. you are reading character by character which is inefficient (especially if the input is not buffered)
5. try to use read() and write()
6. fdin and fsout should be FILE*, not int. fopen() returns FILE*, open returns int.
7. in future, please surround your code by code tags or by php tags.

---

### Post by azroule on 2007-09-21
ok thx for the info... i try again and do my homework.:)

i will post again if i hav sum problem wit this..

thx again

---

### Post by mortykun on 2007-09-22
You can probably do what you want to do in half that amount of code. ... less if you're not set on doing it one char at a time

{
   FILE *fin = 0;
   FILE *fout = 0;
   intr ch;

   /* fopen you files, you should put some error handling here in case that does not work */

   while ((ch = fget(fin)) != EOF) 
   {
      fput(ch, fout);
      printf("%c", ch);
    }

    /* flcose your file handles, */
}

---

### Post by slavik on 2007-09-22
I think read/write would be a better combination :)

---

