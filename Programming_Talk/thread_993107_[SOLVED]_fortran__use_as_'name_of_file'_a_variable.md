---
title: "[SOLVED] fortran : use as 'name of file' a variable, in open statement"
date: 2008-11-25
forum: Programming Talk
---

### Post by Claus7 on 2008-11-25
Hello,

In a fortran program I want to open and close the same file multiple times. Every time I open it I have to use the command:

open(11, file = 'name of file', status = 'unknown')

What I would like to do is to be able the **'name of file'** to declare it somewhere as variable and use it whenever I like somehow. This will help me in the same program to open other files by just giving their names only at one place of the program.

Any proposal would be appreciated.

What I'm looking right now is the getarg and getenv commands in case they will solve my problem.

Regards!

---

### Post by Claus7 on 2008-11-25
Hello,

testing it with a program like:

        program test
        character namevar*40
        namevar = 'paizo.txt'

        open(11, file=namevar)
        write(11,*) 'Write to file'
        end

I saw that it is working. Maybe it was simpler than I thought...

Regards!

---

