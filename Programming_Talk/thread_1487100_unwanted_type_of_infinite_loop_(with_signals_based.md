---
title: "unwanted type of infinite loop (with signals based talk - in c)"
date: 2010-05-18
forum: Programming Talk
---

### Post by h3lloWorld on 2010-05-18
I wrote a little program that's supposed to be opened from 2 terminals, and each instance chats/talks through signals with the one from the other terminal. 

here's part of the code 

```

for (;;)
   {
    do 
       gets(chstr);
    while ( !strlen(chstr) );
    for (i = 0; i < strlen(chstr); ++i)
       {
        charToSignal(talkdest, chstr[i]);
        sigsuspend(&mask);
       }
   }

```this is supposed to be an infinite loop , but somehow I get the side effect that the other process starts printing the line I send it again and again and again...

this is the function that sends the signals:
```

void charToSignal (pid_t ID, char ch)
{
   switch (ch)
    {
       case 'A' : kill(ID, 1); break;
       case 'B' : kill(ID, 2); break;
       case 'C' : kill(ID, 3); break;
       case 'D' : kill(ID, 4); break;
       case 'E' : kill(ID, 5); break;
       case 'F' : kill(ID, 6); break;
       case 'G' : kill(ID, 8); break;
       case 'H' : kill(ID, 10); break;
       case 'I' : kill(ID, 11); break;
 /*............................. blah , blah, blah...... the same......
through */
       case 'x' : kill(ID, 55); break;
       case 'y' : kill(ID, 56); break;
       case 'z' : kill(ID, 57); break;
       case ' ' : kill(ID, 58); break;
       case '\n' : kill(ID, 59); break;
       case '.' : kill(ID, 60); break;
       case ',' : kill(ID, 61); break;
       case '?' : kill(ID, 62); break;
       case '!' : kill(ID, 63); break;
    }
}

```then I set a handler function that converts the signals to chars and prints them... but it seems that it prints all the lines I give it forever... 

I tried to google stuff up, but my mistake must be so specific and probably trivially stupid that google refuses to help me... 

do any of you guys see what I'm doing wrong here?

---

### Post by yaaarrrgg on 2010-05-20
Kill signals might work, but seems like it's stretching the purpose of them to me.  Plus, they will have meaning to the terminals (like killing it) which could affect the application.

I'd recommend IPC, like pipes or sockets instead.

---

