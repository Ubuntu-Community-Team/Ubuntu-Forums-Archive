---
title: "Redirect/capture &quot;special&quot; output on shell"
date: 2008-11-17
forum: Programming Talk
---

### Post by Mango@TUG on 2008-11-17
Hi all!

I want to capture output of for example "segmentation fault" and write it to a logfile.

I've tried something like this:

```
michael@forseti:/home/michael# ./stacksmash 1> a.stdout 2> a.stderr
*** stack smashing detected ***: <unknown> terminated
Aborted
michael@forseti:/home/michael#
```

After execution, a.stdout and a.stderr are empty. So how do I catch this output instead of getting it on terminal?

It's the same with sigsegv, and crashes due to a libc error (doublefree for example)

My environment: executables compiled from C with gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) on dapper server, for above example with --fstack-protector-all

Hope someone can help me,
regards
Michael

---

### Post by geirha on 2008-11-17
That's because it is not the application that prints those messages, it's the c library. You should be able to catch those messages by using grouping though.

```
{ ./stacksmash ; } 2> logfile
```

---

### Post by Mango@TUG on 2008-11-17
Thank's geirha!

That's a first step, now it looks like this:

```
michael@forseti:/home/michael# { ./stacksmash ; } 1> a.stdout 2> a.stderr
*** stack smashing detected ***: <unknown> terminated
michael@forseti:/home/michael# cat a.stderr
Aborted
michael@forseti:/home/michael#
```

Now at least the message "Aborted" is in my logfile...

So if anybody has got further hints...

---

