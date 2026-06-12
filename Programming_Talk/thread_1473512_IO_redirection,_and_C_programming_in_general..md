---
title: "I/O redirection, and C programming in general."
date: 2010-05-05
forum: Programming Talk
---

### Post by spaz886 on 2010-05-05
Hi people.
 
I just recently migrated from win7 to linux. LinuxMint to be precise.
The only reason i keep win7 on dual boot is because i'm not yet comfortable programming in linux.
I'm new to programming in general, and i take a C course now in the university.
The editor we use at uni is Visual Studio Express.
I'm using Geany on linux(because it's the only editor i managed to get my simple console programs to run with).
 
First of all, is there another editor you would think might be more friendly for a newbie?
and for a more specific question, how do i redirect input to a file? in visual studio i'd just use the properties gui of a project to do so, but i can't find something like this when using Geany.
 
Thanks for your help!

---

### Post by psusi on 2010-05-05
It isn't easy to learn, but emacs is a VERY powerful editor that works well with gcc and gdb.

To redirect input on the command line you just use '<' as in ./myprogram < somefile.

---

### Post by Portmanteaufu on 2010-05-05
> **psusi said:**
> It isn't easy to learn, but emacs is a VERY powerful editor that works well with gcc and gdb.

To redirect input on the command line you just use '<' as in ./myprogram < somefile.

+1.

All input comes from some_file.txt:
```
./my_program < some_file.txt
```

All output goes to some_file.txt:
```
./my_program > some_file.txt
```

All output is appended to the end of some_file.txt
```
./my_program >> some_file.txt
```

All output becomes the input for some_other_program
```
./my_program | ./some_other_program
```

I'm a big fan of vim because it's what I learned first and I'm most productive on the command line. If I'm going to use a GUI editor, I often go for gedit or Kate though from what I hear geany is a solid choice.

---

### Post by sprince09 on 2010-05-05
+1 for geany, definitely my favorite IDE for small projects. If you ever migrate to larger/GUI projects, take a look at anjuta/glade.

---

### Post by soltanis on 2010-05-06
What you're looking for are piping semantics from the shell, which are briefly covered in a previous post. Rest assured, it gets a lot more powerful than that alone.

---

### Post by spaz886 on 2010-05-09
Thanks for the replies peeps..
sorry for disappearing. been away for a couple of days.

I think i'll stick with Geany for now, for some reason it's most intuitive for me, and i'm not used to yet for all the shell commands.

---

