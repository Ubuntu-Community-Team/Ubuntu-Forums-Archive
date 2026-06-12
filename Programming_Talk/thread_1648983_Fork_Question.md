---
title: "Fork Question"
date: 2010-12-19
forum: Programming Talk
---

### Post by Mosabama on 2010-12-19
Why the output of this:

```

int main ()
{
pid_t child_pid;
printf ("the main program process ID is %d\n", (int) getpid ());
child_pid = fork ();
if (child_pid != 0) {
printf ("this is the parent process, with id %d\n", (int) getpid ());
sleep(10);
printf ("the child&#8217;s process ID is %d\n", (int) child_pid); 

}
else
sleep(10);
printf ("this is the child process, with id %d\n", (int) getpid ()); // twice ?? with diff pid ?
return 0;
}


```

is this:

```

the main program process ID is 2733
this is the parent process, with id 2733
the child&#8217;s process ID is 2734
this is the child process, with id 2733
this is the child process, with id 2734


```

---

### Post by Mosabama on 2010-12-19
ops sorry I got it ... there is no {} is else. the last line gets executed by both parent and child.

---

