---
title: "Issue with flex/bison or possible PEBKAC :("
date: 2009-12-27
forum: Programming Talk
---

### Post by bkoncomps@gmail.com on 2009-12-27
I'm having a issue which I'm sure exists between the keyboard and chair, but it's been confounding me for days now. 

I'm in the process of writing a mini-compiler using flex and bison, and am having issues when compiling. My compile file looks like this:

```

flex dj.l
bison -v dj.y
gcc dj.tab.c ast.c symtbl.c typecheck.c codegen.c -lfl -o dj2dism

```

I'm getting all sorts of errors which I'd normally associate with issues in my code, but I can compile this perfectly on my university's machines without changing anything in my code. These machines that I can remotely log into are running CentOS 

I've installed the latest versions of flex, and bison, and installed all the linux-headers-2.6.31-14-generic. Ubuntu seemed to come with the latest gcc, and I installed g++ as well just for kicks (and other programming projects).

Has anyone else experienced these issues, and if so how did you remedy this?

Thanks in advance for any help.

---

### Post by maximinus_uk on 2009-12-28
Could you at least post some of the errors as an example? Do you always get errors, or is ot only recently in development that problems occurred?

---

### Post by bkoncomps@gmail.com on 2009-12-28
I've always gotten errors, both on the current machine that I just installed Ubuntu onto, and on the old laptop that I had Ubuntu on.

To make clear, this is the first real project of this nature that I'm working on, but I've successfully compiled and executed my programs on the CentOS machines. That's what leading me to think there might be an issue with the way I have Ubuntu setup on my machine. Maybe I haven't installed everything that is necessary to use the -lfl command with gcc?

The errors claim that the TOKENS I've defined are all undefined in the yylex function. 

Here's an example of the error:

dj.l:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Token’
dj.l:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scanned’
In file included from dj.y:6:
dj.l: In function ‘yylex’:
dj.l:17: error: ‘MAIN’ undeclared (first use in this function)

This then continues for all the other tokens that I've declared in the .l file

Thank you for assisting in this issue.

---

