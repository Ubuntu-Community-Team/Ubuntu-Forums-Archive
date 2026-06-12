---
title: "Compiling with g++ is ugly any way to make it look better?"
date: 2008-05-29
forum: Programming Talk
---

### Post by CoffeeBreath on 2008-05-29
I'm compiling with g++. When I run my program, it runs properly but, when it ends the comp name is smashed onto the end of the program.

programmer@comp:~/me$ ./temp
enter Celsius temp:20
Fahrenheit temp is: 68programmer@comp:~/me$

is there any way to make this easier on my eyes? Any way to have the comp name start on a new line? Maybe another program

---

### Post by issih on 2008-05-29
Um...add a new line at the end of your programs output.....

Assuming you are doing c++ (as you are using g++) just tack "cout<<endl;" as the last line in your program. That ought to do you (assuming you have included iostream and are using the std namespace)

Hope that helps..sorry if I'm being massively over simplistic

---

### Post by LaRoza on 2008-05-29
> **CoffeeBreath said:**
> I'm compiling with g++. When I run my program, it runs properly but, when it ends the comp name is smashed onto the end of the program.

programmer@comp:~/me$ ./temp
enter Celsius temp:20
Fahrenheit temp is: 68programmer@comp:~/me$

is there any way to make this easier on my eyes? Any way to have the comp name start on a new line? Maybe another program

Yes...print newlines.

---

### Post by jonface on 2008-05-29
Just add a cout << "\n" as the last thing , no?

Edit: I swear two seconds ago these replies were not here. Heh.

---

### Post by CoffeeBreath on 2008-05-29
thanks folks

---

### Post by Joeb454 on 2008-05-29
> **jonface said:**
> Just add a cout << "\n" as the last thing , no?

Edit: I swear two seconds ago these replies were not here. Heh.

That'd actually be a combination of C++ and C

C++ - ```
cout << endl;
```

C - ```
printf("\n");
```

You can of course use the C code in a C++ application :)

---

### Post by LaRoza on 2008-05-29
> **Joeb454 said:**
> That'd actually be a combination of C++ and C

C++ - ```
cout << endl;
```

C - ```
printf("\n");
```

You can of course use the C code in a C++ application :)

std::endl does print a newline, but it does more than that (I think it flushes the buffer as well).

"\n" and the other characters are used in C++ as well.

---

### Post by Joeb454 on 2008-05-29
I thought flushing the buffer was cin.ignore()

That could just be the input buffer though

---

### Post by amingv on 2008-05-29
Actually, you'd flush like this:
[PHP]std::cout<< "Mmm, peppers\n" <<std::flush;[/PHP]
if you don't need the newline, cin.ignore() will just discard characters from the (input) stream.

---

### Post by LaRoza on 2008-05-29
> **Joeb454 said:**
> I thought flushing the buffer was cin.ignore()

That could just be the input buffer though

endl flushes the output buffer as well.

[http://www.cplusplus.com/reference/iostream/manipulators/endl.html](http://www.cplusplus.com/reference/iostream/manipulators/endl.html)

---

