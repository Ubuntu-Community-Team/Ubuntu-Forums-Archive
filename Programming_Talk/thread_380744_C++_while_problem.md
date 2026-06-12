---
title: "C++ while problem"
date: 2007-03-10
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-10
Hi, I decided to have a little play in c++ today for fun, and have started off making a Rock, Paper, Scissors game.

Now, making that was pretty darn easy. I only had one or two problems doing it, one of which I can't quite figure out.

Now, I just decided to add in some error checking for the user input just to make my code a little cooler and give me some extra experience. So, I have this
```

	while (choice != rock && choice != scissors && choice != paper ){
		cout<<"Enter 1 for Rock, 2 for Paper, 3 for Scissors: \n";
		cin >> choice;
		}

```

However, when the user enters anything other then a number it just prints out "enter 1 for...." for ever... well, I have tried running it for ever, i got bored after 20 seconds but you get know what I mean. So, what am I doing wrong? I think it's got something to do wih me using a while loop and not an if loop... but I want it to continue print "enter 1 for..." until the user has entered a valid choice so an 'if' won't cut it.

So, if someone could possibly point out my mistake in the code above, I'd be very happy.

EDIT: If anyone is interesting in seeing my program, here's it is:

```
#include <iostream>
#include <cstdlib> 
#include <ctime> 
using namespace std;

int main()

{
	srand((unsigned)time(0)); 
 	int compchoice = ((rand()%3)+1); 
	int choice;
	int rock = 1;
	int paper = 2;
	int scissors = 3;
	char error;
	cout<<"Enter 1 for Rock, 2 for Paper, 3 for Scissors: ";
	cin >> choice;	
	cin.ignore(); 
	if (choice != rock && choice != scissors && choice != paper){
		cout<<"Enter 1 for Rock, 2 for Paper, 3 for Scissors:	";
		cin >> choice;
		}


	if (choice == rock ){
		if (compchoice  == rock){
		cout<<"Rock doesn't beat rock, DRAW!\n"; 
			}
		else if (compchoice == paper){
		cout<<"Paper beats rocks, you loose!\n";
		}
		else{
		cout<<"Rock beats scissors, you win!\n";
		}
		
	
	}

	if (choice == paper ){
		if (compchoice  == paper){
		 cout<<"Paper doesn't beat Paper, DRAW!\n "; 
			}
		else if (compchoice == rock){
		cout<<"Paper beats rocks, you WIN!\n";
		}
		else{
		cout<<"Scissors beats paper, you LOOSE!\n";
		}
		
	
	}

	if (choice == scissors){
		if (compchoice  == scissors){
		cout<<"Scissors doesn't beat scissors, DRAW!\n"; 
			}
		else if (compchoice == paper){
		cout<<"Scissors beats paper, you WIN!\n";
		}
		else{
		cout<<"Rock beats scissors, you LOOSE!\n";
		}
		
	
	}
}


```

---

### Post by lnostdal on 2007-03-10
```

#define M_inline

	template<typename T>
	M_inline void readStdin(T& t, const std::string& msg, const std::string& on_wrong_input)
	{	
		std::cout << msg << std::flush;
		while(!(std::cin >> t)) {
			std::cout << on_wrong_input << std::flush;
			std::cin.clear();
			std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
			std::cout << msg << std::flush;
		}
	}	

```

..note the `clear' and `ignore'-methods. You can use the same when checking actual content.

---

### Post by Darkness3477 on 2007-03-10
So, how exactly am I supposed to use that? I have very limited c++ knowledge, here. Other than being able to make an atrocious program like the one I made above, I know jack all. Lol

---

### Post by lnostdal on 2007-03-10
here is an example: [http://nostdal.org/~lars/programming/c/read-stdin.cpp](http://nostdal.org/~lars/programming/c/read-stdin.cpp) 

```

lars@ibmr52:~/programming/c$ g++ -o read-stdin -g -Wall read-stdin.cpp 
lars@ibmr52:~/programming/c$ ./read-stdin 
Enter 1 for Rock, 2 for Paper, 3 for Scissors: a
That wasn't a correct input. Try again!
Enter 1 for Rock, 2 for Paper, 3 for Scissors: b
That wasn't a correct input. Try again!
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 0
Number not within range
Enter 1 for Rock, 2 for Paper, 3 for Scissors: -1
Number not within range
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 4
Number not within range
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 2
i: 2
lars@ibmr52:~/programming/c$ ./read-stdin 
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 1
i: 1
lars@ibmr52:~/programming/c$ ./read-stdin 
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 3
i: 3

```


edit: i splitted out the `clear' and `ignore'-stuff into a separate function so i can re-use it in the outher while-loop also

---

### Post by Darkness3477 on 2007-03-10
Ah, thank you very much! I get it now :D

If you have time, could you possibly have a look through the rest of my program and tell me if it's coded reasonably well, and what things (if any) I should change around and why? If not, that's cool.

EDIT: Because it's a do ... while, it gets evalutated once, right? 'Cause it's making me enter the input twice (When it's correct) which is kind of a problem. And, well, I don't know how to fix it so perhaps you could tell me how.

---

### Post by lnostdal on 2007-03-10
you should return an integer from main since it is declared as a function that returns `int' .. return 0 to indicate that everything is ok

consider using `switch' instead of `if'

always compile with -Wall and -g as i do above; it might give you some more hints

---

### Post by Darkness3477 on 2007-03-10
Righteo, thanks. I changed it so it returns 0, and I understand why. However, what does the -Wall and -g do? Set the compiler to strict or something, or more intuitive error messages?

And I'll look into switch statements instead of if's.

Thankyou very much for your help.

---

### Post by lnostdal on 2007-03-10
-Wall makes GCC generate warnings for all stuff mentioned from the top of the page until -Wall (about half the page): [http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html) ..it generally gives you hints about potential problems in your code .. it is very useful

for -g see: [http://gcc.gnu.org/onlinedocs/gcc/Debugging-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Debugging-Options.html) .. this makes GCC generate binaries that you can use with a debugger when something goes wrong at runtime

glad to help ... :)

---

### Post by Darkness3477 on 2007-03-10
Thanks, although I'm still having to type my choice twice. Would change it to a normal while loop fix it? I'll give it a try.

---

### Post by lnostdal on 2007-03-10
not sure i understand, but if you have further problems paste the updated code again

---

### Post by Darkness3477 on 2007-03-10
```
#include <iostream>
#include <cstdlib> 
#include <ctime> 
using namespace std;

#define M_inline


template<typename T>
M_inline void readStdin(T& t, std::string msg, std::string on_wrong_input){
  std::cout << msg << std::flush;
  while(!(std::cin >> t)) {
    std::cout << on_wrong_input << std::flush;
    std::cin.clear();
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
    std::cout << msg << std::flush;
  }
}

int main()

{

	srand((unsigned)time(0)); 
 	int compchoice = ((rand()%3)+1); 
	int choice;
	int rock = 1;
	int paper = 2;
	int scissors = 3;
	cout<<"Enter 1 for Rock, 2 for Paper, 3 for Scissors: ";
	cin >> choice;	
	cin.ignore(); 
	int i = 0;


		do{
    readStdin(i, "Enter 1 for Rock, 2 for Paper, 3 for Scissors: ",
                 "That wasn't a correct input. Try again!\n");
  } while((i < 1 || i > 3) && (cout << "Number not within range" << endl));



	switch (choice){
	case 1:
		if (compchoice  == rock){
		cout<<"Rock doesn't beat rock, DRAW!\n"; 
			}
		else if (compchoice == paper){
		cout<<"Paper beats rocks, you loose!\n";
		}
		else{
		cout<<"Rock beats scissors, you win!\n";
		}
	break;
		
	
	

	case 2: 
		if (compchoice  == paper){
		 cout<<"Paper doesn't beat Paper, DRAW!\n "; 
			}
		else if (compchoice == rock){
		cout<<"Paper beats rocks, you WIN!\n";
		}
		else{
		cout<<"Scissors beats paper, you LOOSE!\n";
		}
		break;
	
	

	case 3:
		if (compchoice  == scissors){
		cout<<"Scissors doesn't beat scissors, DRAW!\n"; 
			}
		else if (compchoice == paper){
		cout<<"Scissors beats paper, you WIN!\n";
		}
		else{
		cout<<"Rock beats scissors, you LOOSE!\n";
		break;
		
	
	}

	
}
return 0;
cin.get();
}




```

I compile how you said too, then run and get this happening each time. 

```
maver@maver-laptop:~$ ./rps
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 3
Enter 1 for Rock, 2 for Paper, 3 for Scissors: 3
Scissors beats paper, you WIN!

```
It's fine when the I enter something wrong first, though. it might be where I have the do.. while position, but I though a do... while always gets evalutated once. Of course I could be wrong here...

---

### Post by lnostdal on 2007-03-10
remove these lines:
```

        cout<<"Enter 1 for Rock, 2 for Paper, 3 for Scissors: ";
	cin >> choice;	
	cin.ignore(); 

```

heh .. i mean; if you do a cin first .. then the readStdin-thing afterwards .. of course it will ask twice

see the example again .. no cin >> i; before the readStdin-stuff

---

### Post by Darkness3477 on 2007-03-10
It all makes sense now. I looked from where I stuck your code in to the bottom, but not up the top. Lol. Thanks for dealing with my nooby questions.

I think, possibly, I might find one or two more things to code (Might try to convert my Palindrome check from python to c++) and then try coding a GUI. I think I might make a cross platform webbrowser or something nifty like that.

Again, thanks.

---

### Post by WW on 2007-03-10
lnostdal's approach is interesting, but you could also try something like this:
```

#include <iostream>
#include <string>
#include <cstdlib>

using namespace std;

int main()
    {
    int choice;

    choice = 0;
    while (choice < 1 || choice > 3)
        {
        string s;
        cout << "Enter choice (1, 2, or 3): ";
        cin >> s;
        choice = atoi(s.c_str());
        }
    cout << "choice is " << choice << endl;
    return 0;
    }

```
The key difference between this code and your version is that the user's input is read into a string, and then converted to an integer with atoi.

---

### Post by Darkness3477 on 2007-03-10
Thanks. It's always interesting to see two (or more) different approaches to a problem. 

Last night, I decided to open up my c++ book and skip some parts (I'll look over them later) and go straight to the OOP section. Something I've had problems with in all languages I've tried. And, for once, the idea of OOP just clicked. The book I'm using is c++ for dummies 5th addidtion. The writer introduced OOP using an analogy of cooking Nacho's. 

So, hopefully, I'll be spitting out a slightly larger project in c++ soon. I'll just need to work on porting some of my knowledge into c++, learning a little bit more and then yeah! 

Thanks for showing another way to solve my problem.

---

