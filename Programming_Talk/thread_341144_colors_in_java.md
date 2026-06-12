---
title: "colors in java?"
date: 2007-01-18
forum: Programming Talk
---

### Post by Arppa on 2007-01-18
i need to get somehow colors in System.out -output stream. how could i do that? :-k

---

### Post by Tomosaur on 2007-01-18
Not sure if that's possible. Standard output is basically just characters, the shell controls the colour formatting. Maybe there are certain control characters which allow the shell to do this, but as far as Java goes - there's no support for coloured text anywhere other than GUI programs (as far as I'm aware).

---

### Post by pmasiar on 2007-01-18
There are terminal escape sequences to change colors (and do other neat tricks in terminal) - you need to learn them and output them. depends on terminal type. I did something like that years ago for VT100 :-)

---

### Post by Ramses de Norre on 2007-01-18
[This](http://www.debian-administration.org/users/uroboros/weblog/9) might help you getting to understand how it works.

---

### Post by BatteryCell on 2007-01-18
All that you have to do is output certain escape sequences to the terminal and it will change either background or foreground, note that this stays in that color untill you reset it or change 
the colors again. All that you have to do is put the sequences in the string that you are outputting an it will change the colors.  I wrote a program a while back that needed colors as well and I just defined a bunch so here you go :-) (B is background and F is foreground):
REDB "\033[1;41m"
REDF "\033[31m"
GREENB "\033[1;42m"
GREENF "\033[1;32m"
YELLOWB "\033[1;43m"
YELLOWF "\033[1;33m"
BLUEB "\033[1;44m"
BLUEF "\033[1;34m"
MAGENTAB "\033[1;45m"
MAGENTAF "\033[1;35m"
CYANB "\033[1;46m"
CYANF "\033[1;36m"
WHITEB "\033[1;47m"
WHITEF "\033[1;37m"
RESET "\033[0m"

An example java program to output Hello World in Red would be:
```

public class Colors
{
        public static void main(String[] args)
        {
        //The \033[31m part is what turns this red
        System.out.println("\033[31m Hello World");
        //And then just clear the colors so that your terminal doesn't still have the red
        System.out.print("\033[0m");
        }
}

```

---

### Post by steve.horsley on 2007-01-20
Excellent answer from BatteryCell. But remember that this depends on the terminal that you are viewing hte output on. Not all terminals implement these colour escape codes. Frinstance, a VT100 monochrome terminal doesn't.

---

