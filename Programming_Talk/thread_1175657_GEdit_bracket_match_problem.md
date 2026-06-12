---
title: "GEdit bracket match problem"
date: 2009-06-01
forum: Programming Talk
---

### Post by jounihat on 2009-06-01
Hi all!

I have a problem with GEdit that if a bracket and its match are too far away from each other (about 500 lines), the bracket match highlighting doesn't work anymore. I had the same problem with Emacs too. It's a bit irritating since that's the case where you really want the highlighting to work more than ever. Is there a fix to this problem? I have GEdit version 2.24.0.

---

### Post by crdlb on 2009-06-01
With gedit 2.26.1, it does seem to be limited, though it's apparently limited by the number of characters it searches, not the number of lines. This is undoubtedly done for performance reasons.

In my opinion, the only time you shoud have that much code between brackets is for class and namespace definitons, and you don't really need bracket matching there, so why is this an issue? If you've got some 1000-line functions, maybe it's time to refactor.

---

### Post by jounihat on 2009-06-01
> **crdlb said:**
> With gedit 2.26.1, it does seem to be limited, though it's apparently limited by the number of characters it searches, not the number of lines. This is undoubtedly done for performance reasons.

In my opinion, the only time you shoud have that much code between brackets is for class and namespace definitons, and you don't really need bracket matching there, so why is this an issue? If you've got some 1000-line functions, maybe it's time to refactor.

One example of a 1000-line function would be "printview" function of a PHP view object. However, it's not about 1000-line functions, it's already a problem with 300-500-line functions, which is not very much. Second case where you need long bracket matching would be finding missing bracket for "Unexcepted end of file" error. In my case, I'm trying to reorganize code that uses different tab length than I do. The code looks messy with my tab length, so long bracket matching would be nice.

And referring to your refactoring; how do I easily refactor a code made by someone else, if long bracket match is not working? Please don't be like a Gnome developer. "Why you need that? Why? Why? Why?" :-P

Is there a configuration file where I could fix this somehow?

---

### Post by ibuclaw on 2009-06-01
> **jounihat said:**
> One example of a 1000-line function would be "printview" function of a PHP view object. However, it's not about 1000-line functions, it's already a problem with 300-500-line functions, which is not very much. Second case where you need long bracket matching would be finding missing bracket for "Unexcepted end of file" error. In my case, I'm trying to reorganize code that uses different tab length than I do. The code looks messy with my tab length, so long bracket matching would be nice.

And referring to your refactoring; how do I easily refactor a code made by someone else, if long bracket match is not working? Please don't be like a Gnome developer. "Why you need that? Why? Why? Why?" :-P

Is there a configuration file where I could fix this somehow?

Just had a small peek around the gedit sourcecode, and it looks like you are limited to a buffer macro defined in the GTK library, so there is not really much you can do to tweak this, sorry.

[EDIT]
FYI, this is the function that determines whether or not bracket highlighting is turned on/off in gedit.
```
gtk_source_buffer_set_highlight_matching_brackets (GTK_SOURCE_BUFFER (doc),
                               gedit_prefs_manager_get_bracket_matching ());

```


To suggest a better program, I think you should try **geany**, I've just tested it, and bracket highlighting appears to work as expected in the application (tested it with a 447 line function), and bonus points, you can expand/collapse functions and scopes in the source code. :)

Regards
Iain

---

### Post by jounihat on 2009-06-01
> **tinivole said:**
> To suggest a better program, I think you should try **geany**, I've just tested it, and bracket highlighting appears to work as expected in the application (tested it with a 447 line function), and bonus points, you can expand/collapse functions and scopes in the source code. :)

Thanks! Geany seems like a really cool program. I still have to figure out how to make my own colour scheme though, but it shouldn't be too difficult :-)

Case solved.

---

### Post by crdlb on 2009-06-01
FWIW, the limit in gtksourceview is hardcoded to 10000 characters. To make it support much more, it would probably need a restructuring to keep track of the code structure internally to avoid doing that search.

---

