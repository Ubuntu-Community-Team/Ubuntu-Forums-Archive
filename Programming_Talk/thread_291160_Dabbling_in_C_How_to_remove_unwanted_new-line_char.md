---
title: "Dabbling in C: How to remove unwanted new-line characters?"
date: 2006-11-02
forum: Programming Talk
---

### Post by robenroute on 2006-11-02
Hi there,

I'm dabbling in C at the moment and I'm confronted with a simple problem; hopefully, someone out there has an equally simple solution....

I'm reading prompted user input (in console) using the scanf function and after reading (user input) I want to print some intermediate result on the same line. However, scanf reads the user input, including the "Enter"/new line character and therefore (?) the intermediate result gets printed on the next line, which is exactly what I don't want.

Example output (how it should be):
```

Enter number:  28.6          Intermediate sum:  28.6
Enter number:  31.1          Intermediate sum:  59.7
...

```


This is what happens (again, console output):
```

Enter number:  28.6
          Intermediate sum:  28.6
Enter number:  31.1
          Intermediate sum:  59.7
...

```


My C code:
```

    .
    .
    printf ("Enter as many numbers as you like.\n");
    printf ("Enter 0 to finish the input.\n\n");
    
    printf ("Enter number %2d: ", counter);
    scanf  ("%f", &number);
    
    while (number != 0)
    {
        sum = sum + number;
        printf ("      Intermediate sum: %4.1f\n", sum);
        printf ("Enter number %2d: ", counter + 1);
        scanf  ("%f", &number);
        counter = counter + 1;
    }
    .
    .

```


Anyone? Thanks a bunch!

Rob

---

### Post by Arndt on 2006-11-02
> **robenroute said:**
> Hi there,

I'm dabbling in C at the moment and I'm confronted with a simple problem; hopefully, someone out there has an equally simple solution....

I'm reading prompted user input (in console) using the scanf function and after reading (user input) I want to print some intermediate result on the same line. However, scanf reads the user input, including the "Enter"/new line character and therefore (?) the intermediate result gets printed on the next line, which is exactly what I don't want.

Example output (how it should be):
```

Enter number:  28.6          Intermediate sum:  28.6
Enter number:  31.1          Intermediate sum:  59.7
...

```


This is what happens (again, console output):
```

Enter number:  28.6
          Intermediate sum:  28.6
Enter number:  31.1
          Intermediate sum:  59.7
...

```


My C code:
```

    .
    .
    printf ("Enter as many numbers as you like.\n");
    printf ("Enter 0 to finish the input.\n\n");
    
    printf ("Enter number %2d: ", counter);
    scanf  ("%f", &number);
    
    while (number != 0)
    {
        sum = sum + number;
        printf ("      Intermediate sum: %4.1f\n", sum);
        printf ("Enter number %2d: ", counter + 1);
        scanf  ("%f", &number);
        counter = counter + 1;
    }
    .
    .

```


Anyone? Thanks a bunch!

Rob

Do you mean the user will see the prompt

```
Enter number: 
``` 

enter a number, press Return and then see the line look like

```
Enter number:  28.6          Intermediate sum:  28.6
```

? The normal mode of terminal I/O in Unix is that all characters are echoed. So when the user presses Return (which sends the character '\n'), a '\n' will be echoed to the terminal and start a new line. It's the terminal driver that does this, not your program.

You can tell the terminal driver to not echo. It can be as easy as doing

```
stty -echo
```

in the shell before you start the program, but then the shell too probably won't echo anything after that, which can be confusing.
You can let the program turn off echoing, by using system calls like 'ioctl'. If you do that, it's best to also trap interrupts, so the program  is guaranteed to turn echoing back on when it's done. Editors like 'vi' work like that.

My suggestion is that a simple line-oriented program which yours seems to be doesn't do any such complicated actions, but adapts to the usual Unix I/O model.

---

### Post by robenroute on 2006-11-02
Thanks Arndt, your explanation is crisp & clear. I'll take your advice and live with the normal I/O behaviour. Thanks again.

Rob

---

### Post by rplantz on 2006-11-02
If you continue on with C programming under Linux, you may wish to get "Beginning Linux Programming" by Stones and Matthew. They have a section on terminal I/O which shows how to turn of echo in your program. I have the 2nd edition and assume this material is still in the 3rd. I found the book to be pretty good. It's fairly practical and most of their code seems to work.

---

