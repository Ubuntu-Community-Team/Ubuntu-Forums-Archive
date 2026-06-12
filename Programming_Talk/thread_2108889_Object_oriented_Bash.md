---
title: "Object oriented Bash"
date: 2013-01-25
forum: Programming Talk
---

### Post by gabriellhrn on 2013-01-25
Hello there!

I just had a thought of an Object Oriented Bash and I wanted some advice in it.

Sometimes Bash scripts grow larger and an object oriented approach could ease the development and make the code more reusable, but would it be better to write the application with a more powerful and easier language, like Python, or an OO Bash would worth it? I think something like that could slowdown the application.... 

Well, I just had this idea and I thought of developing it just for fun and for knowledge. What I can't think of is whether it would be useful or if it would worth the effort and that's why I share this idea and ask for tips :)

Thanks!

P.S.: I've already found some people doing this, but a bit different from what I thought.

---

### Post by trent.josephsen on 2013-01-25
Ok, I'll bite.

I can't think of any kind of problem that is both complex enough to merit an OO-ish solution and something I'd otherwise do in shell. That's not saying much, though, because I don't really use bash or any shell (except interactively). So... what kind of script were you thinking of?

Another question, just to provoke thought: if OO features were added to bash, how would you refactor old code to be "more reusable", as you put it? Seems to me that in most cases it would be just as much work as rewriting the whole thing in Perl, but again, I'm not much of a shell programmer.

---

### Post by satsujinka on 2013-01-26
If you really are worried about complexity then you'll want a better language. Your example of Python would be fine.

Perhaps, though your intent is that you want just 1 language for both the shell and your scripts. There are shells that use Python for instance, but maybe you'd prefer something a little closer to shell syntax (considering your first idea was to extend the shell.) In which case, you may want to check out Tcl. It's a full programming language with a library for objects, but it's a little closer to the shell in syntax (considering it, like a shell, is designed to be used to glue programs together.)

---

### Post by gabriellhrn on 2013-01-26
> Ok, I'll bite.

I can't think of any kind of problem that is both complex enough to  merit an OO-ish solution and something I'd otherwise do in shell. That's  not saying much, though, because I don't really use bash or any shell  (except interactively). So... what kind of script were you thinking of?

Another question, just to provoke thought: if OO features were added to  bash, how would you refactor old code to be "more reusable", as you put  it? Seems to me that in most cases it would be just as much work as  rewriting the whole thing in Perl, but again, I'm not much of a shell  programmer.     There are some scripts that become very big, but if it is known that the script will be big, maybe the idea of using another language instead of an OO bash would be better. The "more reusable" I said was for new code, written in OO-ish style.


> If you really are worried about complexity then you'll want a better language. Your example of Python would be fine.

Perhaps, though your intent is that you want just 1 language for both  the shell and your scripts. There are shells that use Python for  instance, but maybe you'd prefer something a little closer to shell  syntax (considering your first idea was to extend the shell.) In which  case, you may want to check out Tcl. It's a full programming language  with a library for objects, but it's a little closer to the shell in  syntax (considering it, like a shell, is designed to be used to glue  programs together.)     

Thanks for the tip. I'll give Tcl a try. My first intent of doing an OO bash was just for fun (and it would be cool to ease the development in bash). But maybe it won't worth it, considering the difficult and the usefulness of it.

---

