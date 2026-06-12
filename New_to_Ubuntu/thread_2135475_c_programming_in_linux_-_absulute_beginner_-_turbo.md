---
title: "c programming in linux - absulute beginner - turboc to gcc"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by kgandhi on 2013-04-14
greetings to everyone
I am pretty new to ubuntu (linux in general) and need pretty BIG help - possibly from a lot of people:p
i need to create a brick breaker game - pretty simple one - in C
and searching on the net - I found one for TurboC
so turboc supports some additional header files such as process.h dos.h graphics.h which are used in the game
but i need it to function in ubuntu - and I probably dont want an IDE or any app which can compile and run c in ubuntu/linux
the program will need to be run on a hardware kit - so it needs to be proper C (I guess)
what are the options??
can i add these header files that are used in the game??
or must I convert the complete code for linux?
can some part of the code be used with change in other code?

[http://www.mycplus.com/source-code/c-source-code/brick-game/](http://www.mycplus.com/source-code/c-source-code/brick-game/)

i got the code from here

all help appreciated
thanks in advance
(and I hope i posted it in the correct place)

---

### Post by wickedpuppy on 2013-04-14
I am not going to ask why a newbie wants to do C programming in a completely unfamiliar environment , instead of installing TurboC on Windows and be done with it ,  so lets go straight to the answers.

First , it has dos.h , and you are on Linux. I am not sure it would be able to compile. Check this out , its old so might have been changed then. [http://www.computing.net/answers/linux/library-dosh/6421.html]("http://www.computing.net/answers/linux/library-dosh/6421.html")

It has to run on a hardware kit , embedded you mean? Again , you are going to have to spell out everything. 

Finally , it sounds like a school project.

---

### Post by kgandhi on 2013-04-14
wickedpuppy - you are right about everything
it is an arm7 kit - which quite frankly noone knows anything about

[http://www.mission10x.com/mission-10x/Pages/UnifiedLearningKit.aspx](http://www.mission10x.com/mission-10x/Pages/UnifiedLearningKit.aspx)
[http://www.iwavesystems.com/unified-learning-kit.html](http://www.iwavesystems.com/unified-learning-kit.html)

its in my college - and i m working under a teacher - who is not helping much
from what i know - 
1. there are additional header files which are present to provide support for all the hardware
2. there are only incomplete material/manual for these header files
3. the teacher doesnt know much about the hardware

all the teacher wants is, me to run a program in C in linux
now I dont know whether even if i make a working game, it would work in that hardware??
I saw the link you posted

so i guess i need to completely startover with the game??
any tutorials on some standard replacement for graphics.h??
and thank you once more

---

### Post by wickedpuppy on 2013-04-14
No. You don't need to start all over. The hardest part is done, the algorithm. The rest is nothing. 

First, write a helloworld. 

Install this package - build-essential

```
sudo apt-get install build-essential
```

Actually someone already written a tutorial --> [http://www.blog.highub.com/linux/ubuntu-c/]("http://www.blog.highub.com/linux/ubuntu-c/")

Try it and play with it first. Then move on from there.

---

### Post by kgandhi on 2013-04-14
> **wickedpuppy said:**
> No. You don't need to start all over. The hardest part is done, the algorithm. The rest is nothing. 



thank you very much buddy
had a bad day today:P
your 1 line made me really really happy TY
appreciate you and all helpful people here
i guess i will be coming here more often :)

Edit: Its night here now, will come back tomorrow, thank you again

---

