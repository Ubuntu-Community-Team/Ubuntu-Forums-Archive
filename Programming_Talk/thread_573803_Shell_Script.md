---
title: "Shell Script"
date: 2007-10-12
forum: Programming Talk
---

### Post by gswang on 2007-10-12
I am looking to create a shell script that interacts with a C program. Normally, I wish it were as simple as calling the name with a bunch of arguments. However, the arguments must be provided in the program itself. Luckily, the program runs from the terminal and is purely text based.

One solution I thought up would be to simulate keystrokes. I would like to know if its possible/easy to have the shell script basically input "keystrokes" or something to that effect in the C program. All I need it to do is hit <C><enter> <Y><enter>, which should be pretty simple...right?

If keystrokes won't work, is there a simpler way to do this than to edit the C source to allow for command line arguments?

---

### Post by PaulFr on 2007-10-12
Perhaps the script could write out all the input lines into a file, then call the C program with input redirected from the file.

---

### Post by Arndt on 2007-10-12
> **gswang said:**
> I am looking to create a shell script that interacts with a C program. Normally, I wish it were as simple as calling the name with a bunch of arguments. However, the arguments must be provided in the program itself. Luckily, the program runs from the terminal and is purely text based.

One solution I thought up would be to simulate keystrokes. I would like to know if its possible/easy to have the shell script basically input "keystrokes" or something to that effect in the C program. All I need it to do is hit <C><enter> <Y><enter>, which should be pretty simple...right?

If keystrokes won't work, is there a simpler way to do this than to edit the C source to allow for command line arguments?

There is a tool called "expect", which can do this.
[http://expect.nist.gov/](http://expect.nist.gov/)

---

