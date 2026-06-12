---
title: "geany problem"
date: 2009-01-29
forum: Programming Talk
---

### Post by cmay on 2009-01-29
hi.
i am learning perl and i use geany for all my programming and it works great other than perl where i get this error messsage. 
the perl programs i run by the terminal in geany so its valid code i try to run. i would like to have the simple click and compile option as i 
i am just learning so its a great advantage to be able to just click compile and run instead of using the terminal. 
how do i fix this. 

```
Can't locate B/Bytecode.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 1) line 18.

```thanks for your time.

---

### Post by Izziedee on 2009-12-18
This is a bit late but might help someone else.
This worked for me (on Mandriva Linux but it should be the same,Geany 0.14):

Under **Build** menu, choose "Set includes and arguments". A pop up window should appear.
At the Compile: line, I removed everything except:
[CENTER]**perl "%f"**[/CENTER]

The Execute item underneath is greyed out for me. Be sure to have **#!/usr/bin/perl -w** at the top of your file. 

**Compile** runs the code, NOT execute (I get a *Warning: Could not start program './geany_run_script.sh' with arguments './geany_run_script.sh'* error.)

Rose

---

