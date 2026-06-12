---
title: "help with my first try at a c++ program"
date: 2007-02-04
forum: Programming Talk
---

### Post by nite owl on 2007-02-04
Hi about a week ago I noticed a programming challenge about creating a program for a lottery draw, at the time I didnt think I could. But now after reading some more this is as far as I've got(this is written in c++):

#include <iostream>

using namespace std;

int storeUserInput();//prototype declaration

int main()
{
	storeUserInput();//call to storeUserInput function
}

int storeUserInput()
{
	int playerNumber[6];//declaring an array capable of hold the 6 users numbers
	
                for(int number = 0;number <= 6; number++)
	{
		cout << "Please select a number: " << endl;
		cin >> playerNumber[number];
	}
}

....Basically this just stores the users number choices in the array 'playerNumber'(Hopefully this is coded right??If not please tell me:)) Any helpful criticism would be greatly appreciated.

---

### Post by amohanty on 2007-02-04
Does it compile?
Looks good to me without compilation.

Also this looks more like a C program. Although C++ can be used in procedural manner and there are various arguments for and against that sort of usage in certain situations, the more interesting features of C++ are OO related, so you might want to look into that.

Of course (and I havent done C in a loooong time) you could do this in C too, if you know it better. I would suggest picking up a book and going through it and its exercises before trying a real problem. The reason I say that is because programming languages are (didnt you know it :)) are analogous to languages. Anybody can write in english but to write a decent book may require some sort of formal(ized) training.

HTH
AM

---

### Post by Lux Perpetua on 2007-02-04
It helps if you put your code in [code****] tags. (At least it preserves indentation.) Some criticism: ```
#include <iostream>

using namespace std;

int storeUserInput();//prototype declaration

[color=red]int[/color] main()
{
	storeUserInput();//call to storeUserInput function
}

[color=red]int[/color] storeUserInput()
{
	int playerNumber[[color=red]6[/color]];//declaring an array capable of hold the 6 users numbers
	
                for(int number = 0;number [color=red]<= 6[/color]; number++)
	{
		cout << "Please select a number: " << endl;
		cin >> playerNumber[number];
	}
}
```when you declare `int playerNumber[6];' you get playerNumber[0], ..., playerNumber[5], but not playerNumber[6]. Your loop takes input into a nonexistent array element. (**edit:** See the [fun with buffer overflow](http://www.ubuntuforums.org/showthread.php?t=348501) thread if you want to see the bad things that can result from this.) 

A function declared to return `int' should return something. If you don't want it to return anything, declare it as `void'. (But main() always returns int. If in doubt, have it return 0. It's a safe return value.)

---

### Post by amohanty on 2007-02-04
:oops: Thats a whooper for a programmer to miss :)

AM

---

### Post by finer recliner on 2007-02-04
Lux Perpetua makes a good point. its traditional in c++ to have main() return 0 when the program completes.

i will also make suggestion about your cin statement. you're assuming that the input that the user puts in will be an integer. if you want to take a few extra lines for caution i would replace your cin statement with this, so cin doesnt return false at any time (and thus have a runtime error):

```

      while(!(cin >> number)){
            cin.clear();
            cin.ignore(std::numeric_limits<streamsize>::max(),'\n');
            cout << "You entered an illegal value. Please try again." << endl;
      }

```

[http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3](http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3)

---

### Post by nite owl on 2007-02-04
Thankyou all for your quick reply:) and yes Lux Perpetua thanks for pointing that out, my bad. Yes I also did have it originally indented its just when I copied and pasted it ended up like that. Also finer recliner  I have to admit you have completely stumped me there because as of yet I have not read up about error checking yet.

---

### Post by amohanty on 2007-02-05
> std::numeric_limits

That is actually part of the Standard Template Library. The gcc related docs are at:
[http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/structstd_1_1numeric__limits.html](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/structstd_1_1numeric__limits.html)

HTH
AM

---

### Post by finer recliner on 2007-02-05
> **nite owl said:**
> Thankyou all for your quick reply:) and yes Lux Perpetua thanks for pointing that out, my bad. Yes I also did have it originally indented its just when I copied and pasted it ended up like that. Also finer recliner  I have to admit you have completely stumped me there because as of yet I have not read up about error checking yet.

i'll try to explain a little better:
you're defining 'number' as an integer (with no value yet). you're going to let the user decide what the value should be by using cin. this is fine if the user correctly inputs an acceptable integer. but what if someone dumb tries to type "HELLO WORLD!!"? well, cin will try to assign a string of characters to an integer type -- a clearly illegal operation. this means that the cin function will not be able to perform its operation and will return to a 'false' state. it will stay in this state until manually fixed. for the end user, all he/she will see is an endless loop of text printed out. try it yourself, you'll see what i mean. remember ^C (ctrl+c) is quit.

the code i added above is a workaround. while cin is false, clear the buffer and ignore any text currently stored (this will allow you to overwrite it when prompted for a new input). when cin finally returns true, it will break out of the while loop

---

### Post by GeneralZod on 2007-02-05
Edit: Oops - I didn't notice that this was a lottery program.  This negates a lot of what I said, and I can't be bothered to fix it, so I removed it :)

---

### Post by hod139 on 2007-02-05
> **finer recliner said:**
> Lux Perpetua makes a good point. its traditional in c++ to have main() return 0 when the program completes.


With C++ it's more than traditional, the standard requires main to return an int.  The value 0 is a return value that another program can use to decide if your program exited correctly.   You can use non-zero values to denote errors.

In C, main is not required to return int, but it is very good practice to always do so.

---

