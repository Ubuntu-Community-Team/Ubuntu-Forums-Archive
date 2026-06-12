---
title: "path alias in tcsh"
date: 2009-01-31
forum: Programming Talk
---

### Post by cybo on 2009-01-31
i want to setup a path aliases in my tcsh to several of my dirs. so if i want to go to mydox dir i would type 
cd mydox
instead of cd /usr/share/usr_name/dir1/dir2/dir3/mydox

i have a variable for mydox,

set mydox=/usr/share/usr_name/dir1/dir2/dir3/mydox

but it is annoying to type a '$' sign every time i do a cd

cd $mydox


can anyone give any suggestions about how i can setup an alias, so i could do the following

cd mydox

---

### Post by snova on 2009-01-31
I've never heard of such a feature, in any shell. It would probably be very ambiguous...

I would suggest creating a function, or an alias.

```
alias mydox='cd /usr/share/usr_name/dir1/dir2/dir3/mydox'
```

Adapt as necessary to fit the proper syntax, I never learned much about CSH and its derivatives.

---

### Post by zpzpzp on 2009-01-31
Type this line in the terminal, or create a shell script of this:
PATH=:/your_folder_path:$PATH

This adds the folder you are interested in to the PATH variable.
And this should allow you to access any files in that folder w/o typing in the full path.

Don't know if this solves your problem.

Paul

---

### Post by snova on 2009-01-31
> **zpzpzp said:**
> And this should allow you to access any files in that folder w/o typing in the full path.

PATH doesn't do that; it changes the list of directories the shell searches for executables in. Unless all the files in that directory are programs, changing it wouldn't do much good.

---

### Post by dwhitney67 on 2009-01-31
> **snova said:**
> I've never heard of such a feature, in any shell. It would probably be very ambiguous...

I would suggest creating a function, or an alias.

```
alias mydox='cd /usr/share/usr_name/dir1/dir2/dir3/mydox'
```

Adapt as necessary to fit the proper syntax, I never learned much about CSH and its derivatives.

+1.

I believe the proper (t)csh syntax does not require the '=' symbol in the statement.

So something like:
```

alias mydox 'cd /usr/share/usr_name/dir1/dir2/dir3/mydox'

```

---

### Post by cybo on 2009-02-01
thank you everyone. i got it.

---

