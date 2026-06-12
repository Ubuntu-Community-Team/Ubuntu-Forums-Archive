---
title: "Yacc and Lex"
date: 2010-03-19
forum: Programming Talk
---

### Post by Faulty_Engineer on 2010-03-19
I've written lexers for my data file and config file respectively, and I'm wondering how to generate different yyparse() function names so that we can call separate parsing algorithms from the same place. So far I have tried compiling with the -p (i.e. prefix) flag as well as manually changing the header in our lexer to redefine yylval. Niether of these methods worked. I checked the generated files to see if the various yy things had been replaced and they had. The errors I get are thrown by gcc and indicate that the replacement prefix is not being properly set. 

So, would it be better to write one large lexer to deal with all our program's parsing requirements, or is there a way to generate different yyparses? I don't see why there wouldn't be a simple way to do this. It makes sense to separate the parsers into modules. 

thanks.

---

### Post by Faulty_Engineer on 2010-03-19
I've written lexers for my data file and config file respectively, and I'm wondering how to generate different yyparse() function names so that we can call separate parsing algorithms from the same place. So far I have tried compiling with the -p (i.e. prefix) flag as well as manually changing the header in our lexer to redefine yylval. Niether of these methods worked. I checked the generated files to see if the various yy things had been replaced and they had. The errors I get are thrown by gcc and indicate that the replacement prefix is not being properly set.

So, would it be better to write one large lexer to deal with all our program's parsing requirements, or is there a way to generate different yyparses? I don't see why there wouldn't be a simple way to do this. It makes sense to separate the parsers into modules.

thanks.

---

### Post by cariboo on 2010-03-19
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by gmargo on 2010-03-19
> **Faulty_Engineer said:**
>  The errors I get are thrown by gcc and indicate that the replacement prefix is not being properly set. 
I don't know what that means.

Generating separate parsers is the whole point of the -p option on bison, so I'd guess you're overlooking something.

Can you post a very short example that you think should work but doesn't?

---

### Post by Faulty_Engineer on 2010-03-20
Can you give me a quick rundown of how to correctly compile it then? This is what I'm doing.

I have a "file1.lex" lex file and a "file2.y" yacc file

1) flex file1.lex 
          This gives me a lex.yy.c file

2) yacc -d -p cfg file2.y
          This gives me a y.tab.h and a y.tab.c file

Note: I have included y.tab.h in my lex file. (#include "y.tab.h")

3) gcc -c lex.yy.c y.tab.c -o parser
          This is where it screws up. I get an error saying that I have an unknown symbol. 

Is the above method the correct way to generate files so that I can call yyparse() (or in

this case cfgparse()) in some other C program and have it run? Do I need to do the gcc 

at all, or can I move my lex.yy.c, y.tab.c, and y.tab.h into the folder where I have my C 

program that calls cfgparse()?

PS: Sorry about the double threads.

---

### Post by gmargo on 2010-03-20
The -c in the compile line doesn't seem right; remove it.

But without you providing some usable example code, as well as the actual text of the error messages, there's little I can do.

---

### Post by Faulty_Engineer on 2010-03-20
I ended up fixing that problem. What I ended up doing was putting both parsers in the same yacc file and ths specific tokens in the same lex file and I compiled it. 

Thanks for your help, though.

Now, I wish to know how to call yyparse in my C program so that it parses some input in, say, a character array.

so if my code is:

```

int main()
{
    char line[500]; 
    yyparse()
    return 0;
}

```How do I call yyparse and pass in the character array for it to parse that?

Thanks for your help.

---

### Post by gmargo on 2010-03-20
There are functions for parsing in-memory strings instead of file contents.  See yy_scan_string etc in the flex documentation.
[http://flex.sourceforge.net/manual/Multiple-Input-Buffers.html#Multiple-Input-Buffers](http://flex.sourceforge.net/manual/Multiple-Input-Buffers.html#Multiple-Input-Buffers)

---

### Post by largedimples on 2010-07-14
What compiler can one run trivialC / YACC and Lex  programs

---

