---
title: "C++: Equivalent of system(&quot;pause&quot;); from Windows in Linux"
date: 2009-05-01
forum: Programming Talk
---

### Post by camper365 on 2009-05-01
What I want to do is pause program execution in the middle of a program and require the user to press a key to continue execution of the program.
Is there a way to do that with Linux?

---

### Post by cabalas on 2009-05-01
Something like this should do the trick:

[PHP]
#include <iostream>

int main(int argc, char *argv[])
{
	std::cout << "Press enter to continue ...";
	std::cin.get();
	
	return 0;
}
[/PHP]

---

### Post by Sinkingships7 on 2009-05-01
As a general rule, try not to use the system() function in production code. If it's for yourself, that's fine. But to the general public, it presents a security risk and generally makes the program OS-specific.

cabalas's suggestion is a sane one.

---

### Post by jimi_hendrix on 2009-05-02
i normally just throw getch() at the end of my main function

---

### Post by camper365 on 2009-05-02
The problem with that is that cin.get() isn't actually waiting for input.
It seemingly does nothing.

---

### Post by dwhitney67 on 2009-05-02
> **camper365 said:**
> The problem with that is that cin.get() isn't actually waiting for input.
It seemingly does nothing.

That's probably because you took in input at an earlier stage of your app, and a newline is still sitting in the input stream.  cin.get() is happy to gobble it, without actually waiting for you to enter anything.

To clear the input stream, try something like:
```

std::cin.ignore(1024, '\n');
std::cout << "Press enter to continue...";
std::cin.get();

```

---

### Post by Sinkingships7 on 2009-05-03
> **jimi_hendrix said:**
> i normally just throw getch() at the end of my main function

getch() is platform-dependent, and therefore a generally bad idea.

---

### Post by camper365 on 2009-05-04
> getch() is platform-dependent, and therefore a generally bad idea. 	
I figured that out.

---

### Post by robofish114 on 2012-06-24
as mentioned above, there is still a newline in the stream, so i usually use one of these two methods:

cin.get(); //the first get uses up the newline character
cin.get(); // with the stream now empty, this one actually waits for a character

OR

cin.ignore(); // ignores the newline
cin.get(); //waits for character

essentially the same thing, but the latter is more readeable, and logically makes more sense

---

### Post by dwhitney67 on 2012-06-24
> **robofish114 said:**
> as mentioned above, there is still a newline in the stream, so i usually use one of these two methods:

cin.get(); //the first get uses up the newline character
cin.get(); // with the stream now empty, this one actually waits for a character

OR

cin.ignore(); // ignores the newline
cin.get(); //waits for character

essentially the same thing, but the latter is more readeable, and logically makes more sense

**You brought a thread back to life that has been dormant for more than 3 years!**  And to boot, your suggestion above is incomplete.  There are cases where a user might input more than just a single character and a newline, regardless of what the prompt instructs them to do.

---

### Post by Simian Man on 2012-06-24
If your program is a terminal application, it should just be run in a terminal.  Then you don't have to bother with all of this foolishness.  Certainly you should never do this in any program that gets distributed.

---

### Post by robofish114 on 2012-06-25
well regardless of how old the thread is, i personally have found threads that have died and been revived two years later, died, revived a year later, died, and so on to be very helpful. no matter how old a thread is, other people will eventually find it when looking for the answer to their problem, and its no help to them if its not complete or correct. also by reviving, other people may intervene like you, and update it, correct it, etc. its much more helpful that way. honestly, forums would be much more helpful if reviving threads wasn't a bad thing. maybe info would be easier to find!

in terms of your suggestion, there's no doubt that there may be other things in the stream, and the ignore may not be enough. you could use cin.clear() but i've almost always had some errors (symantic and syntax) with it. of course ive issues with system("pause") too, so its about a draw.

---

### Post by trent.josephsen on 2012-06-25
> **simian man said:**
> if your program is a terminal application, it should just be run in a terminal.  Then you don't have to bother with all of this foolishness.  Certainly you should never do this in any program that gets distributed.
qft

---

