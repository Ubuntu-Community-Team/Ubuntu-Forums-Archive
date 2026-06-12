---
title: "fgets() doesn't read string correctly"
date: 2007-12-08
forum: Programming Talk
---

### Post by dolgion1 on 2007-12-08
Hi people, i have a problem with the fgets() function, or rather actually scanf.
I want to read in an integer from the standard input stream, with scanf
then read a string with fgets(). here is the code:

        int n;
	scanf("%d",&n);
	fflush ( stdin );
	fgets(line,sizeof(line),stdin);

the problem is that after scanf fgets is skipped and line not read in correctly. what can the problem be?

thanks for any suggestions

---

### Post by yabbadabbadont on 2007-12-08
EDIT: See the reply in your other thread.  (and don't create duplicate threads, just edit your first post in the other one if you need to  ;))

---

