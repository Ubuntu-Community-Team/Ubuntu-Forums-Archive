---
title: "mit cookie monster program"
date: 2007-08-14
forum: Programming Talk
---

### Post by luckyd on 2007-08-14
Would it be possible to port the mit cookie monster to linux, using python. I am learning python, and I want to know how complex it would be to take this hilarious little program and be able to use it on linux. [http://www.multicians.org/cookie.html](http://www.multicians.org/cookie.html) 

PL/I source [ftp://ftp.stratus.com/pub/vos/multics/pg/cookie.pl1](ftp://ftp.stratus.com/pub/vos/multics/pg/cookie.pl1)

---

### Post by Wybiral on 2007-08-14
I'm sure, in one way or another, it can be.

But not only does that sound incredibly annoying, it sounds like a virus to me (and could be potentially abusable).

---

### Post by pmasiar on 2007-08-14
It reminds me a "give me a cookie" TSR virus from MS-DOS long time ago.

If you want to learn Python, wiki in my sig has many links and training tasks. Ask for more help as needed.

If you are cracker wannabe, you need to try harder, and not here :evil:

---

### Post by samjh on 2007-08-14
The name is Cookie Bear.

It's not really a virus, more like just an annoying program, or at worst a very primitive trojan.  If ported to Python, it would be nothing more than an annoying script that is very easily disposed of.

I've come across various forms of this program during my uni days, although none of them were damaging or even difficult to deal with.  It's a pretty harmless joke.  At high school, we even had it as a kind of classroom exercise.

Basic idea is:
1. Plant and execute the program.
2. Run a timer.
3. When timer runs out, demand the user for a "cookie"
4. When user enters "cookie", reset timer.
5. Restart from step 2.

---

### Post by Ramses de Norre on 2007-08-14
You mean something like this: (I'm not sure I understand the concept correctly)
```
package sandBox;

import java.util.Scanner;

public class CookieBear
{
    private static final int SLEEP_TIME=20;
	
    private Scanner scan;
	
    private CookieBear()
    {
        scan=new Scanner(System.in);
        askCookie(scan);
    }
	
    private void askCookie(Scanner scan)
    {
        while(true)
        {
            try{
                Thread.sleep(SLEEP_TIME*1000);
            }catch(InterruptedException e){
                e.printStackTrace();
            }
            System.out.print("Give me a cookie!");
            if(!("cookie".equals(scan.nextLine())))
            {
                System.out.println("A cookie I asked!");
            }
        }
    }
	
    public static void main(String[] args)
    {
        new CookieBear();
    }
}
```

---

### Post by Wybiral on 2007-08-14
> **samjh said:**
> ... It's not really a virus ...

It's a program capable of copying itself and spreading from computer to computer (unless I read incorrectly)... I classify that as a virus, whether it's damaging or just plain annoying.

---

### Post by Soybean on 2007-08-14
> **Wybiral said:**
> It's a program capable of copying itself and spreading from computer to computer (unless I read incorrectly)
No no, it was spread manually. The link describes installing it on someone's terminal when they left it logged on and unattended. "Mischevious people" aren't a valid transmission vector for a real virus. ;)

---

### Post by luckyd on 2007-08-14
No, I dont want to abuse it as I virus. Just a little annoying program to possibly get my friends off *their* myspaces on *my* computer. :) In my case I would just write a script with a timer, that could be easily stopped "cookie" and easily removed. My friends really dont know very much about computers so I wouldn't have to cover its presence at all :)

---

### Post by Wybiral on 2007-08-14
> **Soybean said:**
> No no, it was spread manually. The link describes installing it on someone's terminal when they left it logged on and unattended. "Mischevious people" aren't a valid transmission vector for a real virus. ;)

Oh OK... I misunderstood. It mentioned getting into a pentagon computer so I assumed it was capable of copying itself.

---

### Post by luckyd on 2007-08-14
nope, some mischevious defense departement guys cookie beared each other for fun :)

---

