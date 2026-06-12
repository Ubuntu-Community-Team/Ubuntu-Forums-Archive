---
title: "Character Counting - What's wrong?"
date: 2005-06-12
forum: Programming Talk
---

### Post by Gtaylor on 2005-06-12
```
include <stdio.h>

// Count characters in input; 1st version

main()
{
    long nc;

    nc = 0;

    while (getchar() != EOF)
        ++nc;
    printf("%1d\n", nc);
}

```
This program is supposed to count the number of characters from input until an EOF is reached. When I compile/run it, I recieve no output from it with the value of nc which means EOF isn't being reached. I thought each time I hit 'enter' when being prompted for input, an EOF is sent. Am I doing something wrong here or do I have to specify a special character to equal EOF?

---

### Post by LordHunter317 on 2005-06-12
Enter doesn't send end-of-file, it sends newline.

To send EOF on a console, use Ctrl-D.

Also, in the UTF-8 locale, then won't give an accurate count of number of characters.

---

### Post by Gtaylor on 2005-06-12
Ahh, I was wondering what the character was :) Good deal, I tried a bunch of other key combos to no avail.

---

### Post by trivialpackets on 2005-06-13
[QUOTE=Gtaylor]Ahh, I was wondering what the character was :) Good deal, I tried a bunch of other key combos to no avail.[/QUOTE]
 Also of note, instead of referring to EOL, you can refer to an unnamed variable value char 12.  ie.  char termcount = 12;  as that is equal to carriage return in ascii values, if I'm not mistaken.  It's been a while since I've thought of this, but it comes in handy to have that ascii chart around.

---

### Post by thumper on 2005-06-14
[QUOTE=eric.proctor]Also of note, instead of referring to EOL, you can refer to an unnamed variable value char 12.  ie.  char termcount = 12;  as that is equal to carriage return in ascii values, if I'm not mistaken.  It's been a while since I've thought of this, but it comes in handy to have that ascii chart around.[/QUOTE]
Normally I use '\n' rather than hard coding values.

char newline = '\n';

---

### Post by LordHunter317 on 2005-06-14
[QUOTE=thumper]Normally I use '\n' rather than hard coding values.

char newline = '\n';[/QUOTE]
 That's hardcoding the same value.

---

### Post by poster_nutbag on 2005-06-14
[QUOTE=LordHunter317]That's hardcoding the same value.[/QUOTE]

No, they just happen to have the same byte value. Try the same thing with unicode and it'll be different.

---

### Post by thumper on 2005-06-15
[QUOTE=LordHunter317]That's hardcoding the same value.[/QUOTE]
It is actually platform dependant as well.

'\n' is different on *nix / windows platforms.

---

### Post by jdong on 2005-06-15
so, if I try:

```

./charcount < /dev/zero

```

Your program will consume all of the system's resources counting.... ;)

---

