---
title: "How do Time conversions ?"
date: 2009-11-15
forum: Programming Talk
---

### Post by adalmiina on 2009-11-15
How to converts time variables, when I get it from vector?
 
Errors: invalid conversion from time_t to char* 
 
initializing argument 1 of int puts (const char*) 
 
error: strftime and puts 
 
```

 
//Item.cpp file
**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]void [/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]**Item::print**()[/SIZE]
[SIZE=2]{[/SIZE]
[LEFT]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]  int [/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]size = [/SIZE][SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]NH[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2].size();[/SIZE][/LEFT]
 
[LEFT][SIZE=2][COLOR=#3f7f5f][SIZE=2][COLOR=#3f7f5f]//Loop trough all items in vector[/COLOR][/SIZE][/COLOR][/SIZE][/LEFT]
 
[LEFT]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]for[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]( [/SIZE]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]int[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2] i = 0; i < size; i++ )[/SIZE]

[SIZE=2]{[/SIZE]
[LEFT]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]     if[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2]([/SIZE][SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]NH[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2].at(i)->getItemStatusInt() == [/SIZE][SIZE=2][COLOR=#1069ef][SIZE=2][COLOR=#1069ef]Item[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]::[/SIZE]*[SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]LOAN[/COLOR][/SIZE][/COLOR][/SIZE]*[SIZE=2])[/SIZE]
[SIZE=2]  {[/SIZE][SIZE=2]  //cout << [/SIZE][SIZE=2][COLOR=#2a00ff][SIZE=2][COLOR=#2a00ff]"LoanDate: "[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] << [/SIZE][SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]NH[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2].at(i)->getLoanDate() << endl;[/SIZE][/LEFT]
[/LEFT]
 
  [SIZE=2][COLOR=#1069ef][SIZE=2][COLOR=#1069ef]       time_t[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] now;[/SIZE]
 [SIZE=2][COLOR=#1069ef][SIZE=2][COLOR=#1069ef]        time_t[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] buffer;[/SIZE]
[LEFT][SIZE=2]      //NH is vector[/SIZE]
[SIZE=2]       now = [/SIZE][SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]NH[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2].at(i)->getLoanDate();[/SIZE][/LEFT]
 
[LEFT]**[SIZE=2][COLOR=#646464][SIZE=2][COLOR=#646464]        strftime[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2] (buffer,[/SIZE][SIZE=2][COLOR=#2a00ff][SIZE=2][COLOR=#2a00ff]"%d.%m.%Y"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2],now); //error: strftime and puts[/SIZE]
**[SIZE=2][COLOR=#642880][SIZE=2][COLOR=#642880]        puts[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2](buffer);[/SIZE][/LEFT]
 
 [SIZE=2]// Item.h class declares[/SIZE]
 
[LEFT][SIZE=2]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]void [/COLOR][/SIZE][/COLOR][/SIZE]**[/SIZE][SIZE=2][SIZE=2]**setLoanDate**([/SIZE][SIZE=2][COLOR=#1069ef][SIZE=2][COLOR=#1069ef]time_t[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] p_now) {[/SIZE][SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]now[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] = p_now;};[/SIZE][/SIZE]
[SIZE=2][SIZE=2][COLOR=#1069ef][SIZE=2][COLOR=#1069ef]time_t[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] **getLoanDate**(){[/SIZE]**[SIZE=2][COLOR=#7f0055][SIZE=2][COLOR=#7f0055]return[/COLOR][/SIZE][/COLOR][/SIZE]**[SIZE=2][COLOR=#0000c0][SIZE=2][COLOR=#0000c0]now[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2];}; [/SIZE][/SIZE][SIZE=2][/LEFT]
[/SIZE]
```

---

### Post by dwhitney67 on 2009-11-15
Since it appears that you are attempting to display the date, the easiest function to use is ctime().
```

#include <ctime>

...

time_t theTime = NH.at(i)->getLoanDate();
cout << ctime(&theTime) << endl;

...

```

If you need to perform manipulations on the time, then consider using gmtime() or localtime().  Both of these functions, and the aforementioned ctime(), are documented in the manpages.

As for strftime(), you are not passing the correct parameters; it should be something like:
```

char       buffer[30] = {0};
time_t     theTime = NH.at(i)->getLoanDate();
struct tm* locTime = localtime(&theTime);

strftime(buffer, sizeof(buffer) - 1, "%d.%m.%Y, locTime);
cout << buffer << endl;

```
Btw, I have not tested the code above; I merely coded it using the manpage as a reference.

---

