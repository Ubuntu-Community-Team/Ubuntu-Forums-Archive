---
title: "bash: trying to background commands  in a for loop"
date: 2017-07-13
forum: Programming Talk
---

### Post by stlu on 2017-07-13
Hello,

I am trying to run three scripts in the background.  I tried:

```

for i in `seq 1 3`; do ./script$i.sh &; done

```

It does not like that I put the ampersand there.  Is there another way to background each script that will work in a for loop?

---

### Post by sisco311 on 2017-07-13
It's because of the semicolon. You can't use both & and ; to terminate your command. 

```
for i in {1..3}; do ./script$i.sh & done
```

NOTE: seq is non-standard you should use a brace expansion. ;)

See:
 [http://mywiki.wooledge.org/ProcessManagement?highlight=%28background%29#How_do_I_run_a_job_in_the_background.3F](http://mywiki.wooledge.org/ProcessManagement?highlight=%28background%29#How_do_I_run_a_job_in_the_background.3F)
 [http://mywiki.wooledge.org/BadUtils?highlight=%28seq%29#seq](http://mywiki.wooledge.org/BadUtils?highlight=%28seq%29#seq)

---

### Post by stlu on 2017-10-02
Thank you very much!  In the month or two since this post I have managed to get a better understanding of this topic.  I was wrong to think that only the semicolon ended a command.  Now I get that there are several ways to end a command, which includes the semicolon and the ampersand (&).

---

