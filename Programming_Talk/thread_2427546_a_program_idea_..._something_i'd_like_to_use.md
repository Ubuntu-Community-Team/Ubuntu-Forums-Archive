---
title: "a program idea ... something i'd like to use"
date: 2019-09-23
forum: Programming Talk
---

### Post by Skaperen on 2019-09-23
for every process whose parent still exists, [COLOR=#0000cd][FONT=courier new]**ps**[/FONT][/COLOR] can list its parent process.  the program i'd like to see is one that shows a tree structure of running processes branch out from its parent.  parentheses processes that init inherits would just be loose branches laying on the ground.

---

### Post by TheFu on 2019-09-24
I assume you kow about pstree?```
       pstree shows running processes as a tree.  The tree is rooted at either
       pid  or  init  if  pid  is  omitted.   If a user name is specified, all
       process trees rooted at processes owned by that user are shown.

       pstree visually merges identical branches by  putting  them  in  square
       brackets and prefixing them with the repetition count, e.g.
```
Plenty of options.

---

### Post by Skaperen on 2019-09-24
no i didn't know of pstree.  it didn't come up in my google search but an unanswered question someone posted somewhere for such a thing did.  but, at least i know about it now.  i hope one of those options adds the user name for each process it shows.

---

### Post by #&amp;thj^% on 2019-09-24
```
Display a tree of processes.

  -a, --arguments     show command line arguments
  -A, --ascii         use ASCII line drawing characters
  -c, --compact       don't compact identical subtrees
  -h, --highlight-all highlight current process and its ancestors
  -H PID,
  --highlight-pid=PID highlight this process and its ancestors
  -g, --show-pgids    show process group ids; implies -c
  -G, --vt100         use VT100 line drawing characters
  -l, --long          don't truncate long lines
  -n, --numeric-sort  sort output by PID
  -N type,
  --ns-sort=type      sort by namespace type (cgroup, ipc, mnt, net, pid,
                                              user, uts)
  -p, --show-pids     show PIDs; implies -c
  -s, --show-parents  show parents of the selected process
  -S, --ns-changes    show namespace transitions
  -t, --thread-names  show full thread names
  -T, --hide-threads  hide threads, show only processes
  -u, --uid-changes   show uid transitions
  -U, --unicode       use UTF-8 (Unicode) line drawing characters
  -V, --version       display version information
  PID    start at this PID; default is 1 (init)
  USER   show only trees rooted at processes of this user

```

---

### Post by TheFu on 2019-09-24
> **Skaperen said:**
> no i didn't know of pstree.  it didn't come up in my google search but an unanswered question someone posted somewhere for such a thing did.  but, at least i know about it now.  i hope one of those options adds the user name for each process it shows.

We all have blind spots for some commands.  

I didn't know about ssh-copy-id for a long time and had been manually moving ssh-keys around.  What a pain.  Also remember when someone else pointed out that sort had added a *-h* switch to do smart sorting for things like 
```
du -sh * | sort -h
```
It knows that 1T is larger than 8G is larger than 999M.

The pstree on firefox is depressing. ;(

---

### Post by Skaperen on 2019-09-24
> **TheFu said:**
> We all have blind spots for some commands.  

i call it "gaps".  i'm sure i still have a lot.  one of the things that give me some big gaps is that i got used to just implementing a solution to many things.  so i end up not knowing about a possibly better thing, such as rclone (i still use the one i created).  it also makes me think more about how to implement what i need than how to find it.

---

