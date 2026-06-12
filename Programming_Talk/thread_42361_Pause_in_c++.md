---
title: "Pause in c++"
date: 2005-06-17
forum: Programming Talk
---

### Post by karmah on 2005-06-17
Hello.
I'm a bit of a noob at c++ and right now im making a little test text-based rpg. I want to use a "slowcout" function that im making so the text appear letter by letter...But there's no real pause function as there was back when I used Borland. If someone knows a good way (not like a meanless loop) to make a pause, i would be thankful :).

---

### Post by MoneyCat on 2005-06-17
Try using the sleep() function.

#include <unistd.h>
unsigned int sleep(unsigned int seconds);


Example:
```

      1 #include <unistd.h>
      2 #include <stdio.h>
      3
      4 int main()
      5 {
      6
      7     int array[10] = { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 } ;
      8
      9     int i;
     10     for(i=0; i < 10; i++)
     11     {
     12         printf("%i \n", array[i]);
     13         sleep(1);                   // sleep for 1 second
     14     }
     15     printf("Blastoff!\n");
     16
     17     return 0;
     18 }

``` 
If you're in Windows then you must include windows.h and use Sleep()


Good luck  :grin:

---

### Post by karmah on 2005-06-17
Thank you very much! :) highly appreciated

---

### Post by karmah on 2005-06-17
Hmmm...is that really c**_++_** ? I'm having some trouble when running my own program when including those headers and using sleep...nothing happens..

---

### Post by MoneyCat on 2005-06-17
> 
Hmmm...is that really c++ ?
 
Whoops, I completely overlooked that requirement. Nevertheless, g++ will compile & run that same code. 

If you're doing this on Windows look at this working example:

```

#include <iostream>
#include <windows.h>

using namespace std;

int main()
{
     int array[10] = { 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 } ;
     int i;
     for(i=0; i < 10; i++)
     {
         cout <<  array[i] << endl;
         Sleep(1000);                   // sleep for 1 second
     }
     cout << "Blastoff!" << endl;

 return 0;   
}

``` 



MoneyCat

---

### Post by karmah on 2005-06-17
Ok, well im not doing it in windows, cuz i dont have it :P... So i need a  working pause kindof function in c_++_ in linux ;o....

---

### Post by LordHunter317 on 2005-06-17
The function he provided you is standard POSIX, and will work just fine in C and C++.

Did you even try it?

---

### Post by karmah on 2005-06-17
Yep. It didn't work for me.

---

### Post by karmah on 2005-06-17
Actually, compiling it works fine. But when I try to run it, NOTHING happens :S

---

### Post by karmah on 2005-06-17
It DID work!! You were right, but not as expected! I'll be figuring some more on this and see if I can get this working now, otherwise I'll post more questions :D, thx guys :)

---

### Post by Kimm on 2005-06-17
another simple way of pausing (in secunds) would be to define something like this:

```

#include <ctime>
#include <iostream>

void pause(int dur);

int main()
{
       std::cout<<"Pausing for 2 secund... ";
       pause(2);
       std::cout<<"DONE\n";

return 0;
}

void pause(int dur)
{
       int temp = time(NULL) + dur;

       while(temp > time(NULL));
}

```

I've been using that in a couple of programs and it works fine :)

---

### Post by LordHunter317 on 2005-06-17
Except that it spins the CPU and wastes cycles.

Also, it doesn't ensure you'll actually delay for that long: if the process is yielded for another to run, it may be forever until you come back.  While sleep() doesn't ensure you'll return exactly in time, it at least makes sure the scheduler does the right thing.

---

### Post by Kimm on 2005-06-17
well, yes, it does spin the CPU, but in a game (that runs in the console) that shouldnt matter, should it?

I was under the impression Linux went by the rule: "All processes are of equal importance" and therefore didnt care what comes first or not, did I get it wrong?

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=Kimm]well, yes, it does spin the CPU, but in a game (that runs in the console) that shouldnt matter, should it?[/quote]Yes, it does, as it denies other processes resources unnecessarily.  

> I was under the impression Linux went by the rule: "All processes are of equal importance" and therefore didnt care what comes first or not, did I get it wrong?You got it wrong.  There are priority levels for starters.  Under 2.6, the default scheduler gives temporary higher priority to processes performing I/O.


Also, I believe sleep() will do the right thing if the RTC is changed,  while your code will not.

---

### Post by Kimm on 2005-06-17
well, In that case I confess to being wrong and bow before you!

---

