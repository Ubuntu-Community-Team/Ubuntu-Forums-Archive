---
title: "More of a question than a cry for help."
date: 2009-02-12
forum: Programming Talk
---

### Post by Tek-E on 2009-02-12
I have an odd question...Im not sure this is where this belongs or not.  But are ANSI bombs still in use today?  I ask this because I have a friend ( Who I sadly cant convince to join ubuntu forums ) lol who is studying the C language with me.  And every time he write a program that contains
```

system( "cls" );

```
His computer restarts whenever the program reaches that command.  Could this be the result of an ANSI bomb that when the cls command is issued the computer instead issues the shutdown command?  I recommended that instead of using the system function he use the 
clrscr() function.  Any body have an idea though?

---

### Post by cmay on 2009-02-12
that is strange. i use this exact piece of code myself and even made a clrscr() dummy function so i can use it in examples that uses the borland c++  function to clear the screen. its what it does and its what happens here on my machine. 
i cant help any with the question other than this.

---

### Post by geirha on 2009-02-12
Won't happen in Ubuntu at any rate. Is he programming in windows or ubuntu? There's no command called cls in a default ubuntu install at least, so the program will just print
```
$ gcc -x c - <<< 'main(){system("cls");}'  && ./a.out
sh: cls: not found

```

---

### Post by Tek-E on 2009-02-12
> **geirha said:**
> Won't happen in Ubuntu at any rate. Is he programming in windows or ubuntu? There's no command called cls in a default ubuntu install at least, so the program will just print
```
$ gcc -x c - <<< 'main(){system("cls");}'  && ./a.out
sh: cls: not found

```

Sorry. I should have noted that yes he is programming in windows.  idk I just thought it was really weird that whenever he either a. Issued the cls command in his command prompt his computer would automatically shutdown ( which made me think ANSI bomb ) or b.  Whenever a program he wrote reaches the system( "cls" ); command it also shuts down.  Since I told him to instead use clrscr(); he hasnt had a problem....idk its kinda weird.

---

### Post by geirha on 2009-02-12
I'm guessing he has another command called cls in his path or something. Maybe he should search his computer for "cls.*" and see if there is any .bat, .com, .exe or similar with that name in PATH.

---

### Post by Tek-E on 2009-02-12
> **geirha said:**
> I'm guessing he has another command called cls in his path or something. Maybe he should search his computer for "cls.*" and see if there is any .bat, .com, .exe or similar with that name in PATH.

Thats kinda what I figured I would do. It doesn't sound like a tough fix.  But oh well.  Thanks everyone. :P

---

