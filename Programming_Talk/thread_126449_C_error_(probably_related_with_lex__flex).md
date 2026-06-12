---
title: "C error (probably related with lex / flex)"
date: 2006-02-06
forum: Programming Talk
---

### Post by draenor on 2006-02-06
Hey, I've tried google and irc, but it seems impossible to find any resources concerning this problem, so I figuered I might give theese forums a shot. 

I'm trying to install this 'no-name' language for concurrent programming called MPD. 

It's based on C librarys during the installation and I've downloaded all repositories I could think of that seemed necessary. During the installation I find a problem, this problem was covered on a small readme coming with the language (no, there's no forums or any better resource for the language...). 

The sugestion was to replace a line
          lex tokens.l , with
          flex -l tokens.l
          which should supposedly seem ok as I'm using flex and flex -l means setting
          lex with maximum compatibilty. 

However despite the changes I still get the same problem, so I wondered if this would have to do with never version of flex not being compatible with lex or something .. 

Output of error:
  >   tokens.l: In function ‘chrlit’:
  >   tokens.l:311: error: ‘yytext_ptr’ undeclared (first use in this function)

Thanks for your interest ..

---

### Post by snoman on 2006-02-08
Sounds like a problem in you lex code.  Would it be posible to post it, or at least the chrlit function that is causing the error?

---

