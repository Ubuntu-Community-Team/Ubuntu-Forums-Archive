---
title: "I need help with my homework"
date: 2012-02-08
forum: Programming Talk
---

### Post by rafaelcbf on 2012-02-08
I know this is cheating... sort of, but out of the 5 programs I have to wright this one turned out to be the hardest, can some one please explain to me why I just can't get it right?

[PHP]#include "stdio.h"
#include <iostream>

int main ()
{
int name, edad;
printf("Pedir nombre");
scanf("%i", &name);
printf("Pedir edad");
scanf("%i", &edad);
printf("el nombre es %i y su edad es  %i \n", name, edad);
}[/PHP]

When I run it, it askes for name like it should, then it skips asking for age and prints out some numbers. I just don't get What I'm doing wrong.

---

### Post by muteXe on 2012-02-08
You are asking for someone's name and assigning it to an integer? I ain't done c in a while but what is %i? I thought integer was %d?

---

### Post by rafaelcbf on 2012-02-08
When I wright %s it gives me an error, so wrote it with %i. It's supposed to aske for your name and age, and then print it out in sentence: Your name is whatever and your age 666.

---

### Post by Bachstelze on 2012-02-08
You have some learning to do about how strings work in C. You certainly can't just read a name and store it in a variable of type int.

---

### Post by r-senior on 2012-02-08
> **muteXe said:**
> I ain't done c in a while but what is %i? I thought integer was %d?
You can use "%i" and "%d" interchangeably. They are the same.

@rafaelcbf

The %s was correct. You have declared 'name' as an int. You need a string.

---

### Post by rafaelcbf on 2012-02-08
Well, it's my second class. I did a whole bunch of other programs, but htey were all numbers. This one I just can't get to work. I guess homework will be incomplete this week. :S

---

### Post by lisati on 2012-02-08
Getting your head around different data types and how to handle them can be a bit daunting when you're new to programming or a particular language. 

Here's my hint that might help you get things moving again: [http://www.cprogramming.com/tutorial/lesson9.html](http://www.cprogramming.com/tutorial/lesson9.html)

---

### Post by rafaelcbf on 2012-02-08
> **lisati said:**
> Getting your head around different data types and how to handle them can be a bit daunting when you're new to programming or a particular language. 

Here's my hint that might help you get things moving again: [http://www.cprogramming.com/tutorial/lesson9.html](http://www.cprogramming.com/tutorial/lesson9.html)

Thank you so much, this will definitely help me with this little problem. SOLVED.

---

### Post by Bachstelze on 2012-02-08
> **r-senior said:**
> You can use "%i" and "%d" interchangeably. They are the same.

Actually no, %i allows integers to be input in octal or hex in addition to decimal, while %d as its name implies is decimal only.

---

### Post by Tony Flury on 2012-02-09
Also - I am no expert - but are you writing C or C++ ?

if you are using C then you don't need "#include <iostream>". 

If you are using C++ you don't need '#include "stdio.h"', and you should really use the C++ style input and output methods :
for example : 
```

cin >> name

```

---

