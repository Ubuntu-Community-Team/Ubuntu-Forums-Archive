---
title: "[SOLVED] Unusual Runtime Termination"
date: 2008-10-07
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-10-07
This program works as expected, save for one tiny flaw. On my Windows machine, after the user stops the program by entering the number 42, the command prompt spits this error at me:

"This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information."

Here's the code, written in C++:
```
[color=#408080][i]/* http://www.spoj.pl/problems/TEST/
 * 
 * This program lets the user input a series of numbers, and doesn't stop
 * until the user inputs the number 42. Afterward, all the numbers that the
 * user input are displayed back (except for 42).
*/[/i][/color]
[color=#BC7A00]#include <iostream>
#include <vector>
[/color]
[color=#B00040]int[/color] main(){
	std[color=#666666]::[/color]vector [color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>[/color] guesses([color=#666666]0[/color]);
	
	[color=#008000]**while**[/color] ([color=#008000]**true**[/color]){
		[color=#B00040]int[/color] guess;
		
		std[color=#666666]::[/color]cout [color=#666666]<<[/color] [color=#BA2121]"Guess: "[/color];
		std[color=#666666]::[/color]cin [color=#666666]>>[/color] guess;
		
		[color=#008000]**if**[/color] (guess [color=#666666]==[/color] [color=#666666]42[/color]){
			[color=#008000]**break**[/color];
		}
		
		guesses.push_back(guess);
	}
	
	[color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] index [color=#666666]=[/color] [color=#666666]0[/color]; index [color=#666666]<=[/color] guesses.size(); index[color=#666666]++[/color]){
		std[color=#666666]::[/color]cout [color=#666666]<<[/color] guesses.at(index) [color=#666666]<<[/color] std[color=#666666]::[/color]endl;
	}
	
	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

Any ideas?

---

### Post by LaRoza on 2008-10-07
Not sure about the error, but maybe:

```
while (true){
		int guess;
		
		std::cout << "Guess: ";
		std::cin >> guess;
		
		if (guess == 42){
			break;
		}
		
		guesses.push_back(guess);
	}

```

could be written better.

[php]
int guess;
do{		
    std::cout << "Guess: ";
    std::cin >> guess;			
    guesses.push_back(guess);
} while (guess != 42)
[/php]

---

### Post by Sinkingships7 on 2008-10-07
Nah, 'cause if guess == 42, then 42 is added to the end of my vector, and I don't want that. I could write it your way and just add a simple 

guesses.pop_back();

after the loop, but meh.

---

### Post by LaRoza on 2008-10-07
> **Sinkingships7 said:**
> Nah, 'cause if guess == 42, then 42 is added to the end of my vector, and I don't want that. I could write it your way and just add a simple 

guesses.pop_back();

after the loop, but meh.

How about:
[php]
#include <iostream>
#include <vector>

int main(){
    std::vector <int> guesses(0);
	

    int guess;
    while (true)
    {		
        std::cout << "Guess: ";
        std::cin >> guess;
        guess != 42  guesses.push_back(guess) ? break ;
    }

	
    for (unsigned int index = 0; index <= guesses.size(); index++){
        std::cout << guesses.at(index) << std::endl;
    }
    return 0;
}
[/php]

---

### Post by rogersce on 2008-10-07
looks like the last loop should be

    for (unsigned int index = 0; index < guesses.size(); index++){
        std::cout << guesses.at(index) << std::endl;
    }

---

### Post by rogersce on 2008-10-07
in other words, if guesses.size() = 10, then guesses is indexed on [0,9].

if you do a for(i<=guesses.size()) then you'll index guesses.at(10), which is outside the bounds of guesses.

if you do for(i<guesses.size()) then you're indexing i=0 to 9 and staying within the bounds.

---

### Post by Sinkingships7 on 2008-10-07
> **rogersce said:**
> looks like the last loop should be

    for (unsigned int index = 0; index < guesses.size(); index++){
        std::cout << guesses.at(index) << std::endl;
    }

!!!

You, sir or ma'am, seem to be correct!

Such a primitive mistake, too...

---

