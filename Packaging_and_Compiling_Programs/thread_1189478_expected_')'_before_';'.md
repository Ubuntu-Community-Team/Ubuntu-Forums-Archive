---
title: "expected ')' before ';'"
date: 2009-06-16
forum: Packaging and Compiling Programs
---

### Post by kbo206 on 2009-06-16
I get the following error when using "make modules" on Anope 1.8.0. I'm using C.
```
bs_atn.c:16: error: expected ')' before ';' token
bs_atn.c:17: error: expected ')' before ';' token

```Here is a part of the code. (bs_atn.c)
```
int do_atn(int argc, char **argv);

int AnopeInit(int argc, char **argv)
{
    EvtMessage *msg = NULL;
    EvtHook    *hook = NULL;
    int status;
    hook = createEventHook(EVENT_BOT_FANTASY, do_atn);
    status = moduleAddEventHook(hook);
    alog("bs_atn: Module loaded.");
    moduleAddAuthor(AUTHOR);
    moduleAddVersion(VERSION);
    return MOD_CONT;
}

```Line 16 is:
```
moduleAddAuthor(AUTHOR);
```Line 17 is:
```
moduleAddVersion(VERSION);
```

Is there something I'm overlooking? I'm new to C.

---

### Post by doas777 on 2009-06-16
I don't do much C, but  somthing looks weird with your string on line 15. it may be treating the ';' on the end of the line as part of a string. are you certian that last doublequote is actually a doublequote? I've seen weirder things happen. even if thats not it the problem is prolly on 15.

good luck

---

### Post by kbo206 on 2009-06-16
Thanks for your quick response. Yup it's a double quote. And I agree that the code looks odd. I'll fool around with line 15 and see if that helps.

EDIT: I commented out Line 15 and it still gave me the same error. Hmm...

---

### Post by kbo206 on 2009-06-16
I found the problem. When I defined AUTHOR and VERSION I put I semicolon after each. That was the problem. Thanks!

---

