---
title: "C++ question..."
date: 2009-02-18
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-18
Ok, just when I think I am doing good and sailing right along I get errors that I think shouldn't be there but what do I know this is only my second day of this.

Here is the deal. Below is the lesson from: [http://www.cprogramming.com/tutorial/lesson6.html](http://www.cprogramming.com/tutorial/lesson6.html). The first one is the lesson, the second is my code, the third is the errors I get when I go to run it. ( And I can do that in my sleep now I think...;-) ) What am I missing and why won't this run if it is even suppose to. It looks to me like it should but like I said what do I know...;-).

**Lesson on pointers:**

```

#include <iostream>

using namespace std;

int main()
{ 
  int x;            // A normal integer
  int *p;           // A pointer to an integer

  p = &x;           // Read it, "assign the address of x to p"
  cin>> x;          // Put a value in x, we could also use *p here
  cin.ignore();
  cout<< *p <<"\n"; // Note the use of the * to get the value
  cin.get();
}

```

**Now my code:**

```

#include <iostream>

using namespace std;

int main()
{
	int x;		    // A normal interger
	int *p;		    // A pointer to an integrer

	p = &x;		   // Read it, "assign the address of x to p"
	cin>> x;	   // Put a value in x, we could also use *p here
	cin.ignore();
	cout<< *p <<"\n";  // Note the use of the * to get a value
	cin.get();
}

```

**and now the error report:**

```

leo@Illuzionz:~/Practice Folder$ g++ -Wall "pointers.cpp" -o executable
pointers.cpp:3: error: expected constructor, destructor, or type conversion before &#8216;namespace&#8217;
pointers.cpp: In function &#8216;int main()&#8217;:
pointers.cpp:12: error: &#8216;cin&#8217; was not declared in this scope
pointers.cpp:14: error: &#8216;cout&#8217; was not declared in this scope
leo@Illuzionz:~/Practice Folder$ 
 

```

Please tell why I have a headache...lol

---

### Post by jimi_hendrix on 2009-02-18
you have build-essential installed right?

---

### Post by Leo Dragonheart on 2009-02-18
> **jimi_hendrix said:**
> you have build-essential installed right?

Yes I do and I have compiled and ran about 6 other lessons so far...

---

### Post by jimi_hendrix on 2009-02-18
ok...i am kinda sleepy so i wont be of much assistence, but the error is in the using line, the other two errors seem to be a result of the first error...try this:

comment out like 3.

add std:: infront of every usage of cin or cout

---

### Post by Reiger on 2009-02-18
With build-essential, I don't see any errors...

---

### Post by Leo Dragonheart on 2009-02-18
> **jimi_hendrix said:**
> ok...i am kinda sleepy so i wont be of much assistence, but the error is in the using line, the other two errors seem to be a result of the first error...try this:

comment out like 3.

add std:: infront of every usage of cin or cout

ok I will give it a try thanx...

---

### Post by TVTrukChik on 2009-02-18
I have encountered some things like that, mostly when using gedit as my editor.  Every now and then there would be some error that made no sense at all when trying to compile the program.  It was like there were some invisible control codes or something that the compiler could see that were invisible to the human eye.  

I finally got desperate, and commented out the line that was giving the error, then re-typed it exactly the same way, and it worked.  It's happened more than once.  What editor are you using?

I copied and pasted both those code blocks onto my system, and they both compiled without errors.

---

### Post by Can+~ on 2009-02-18
Compiled, no problems here (copied and pasted directly into gedit and geany).

---

### Post by Leo Dragonheart on 2009-02-18
> **TVTrukChik said:**
> I have encountered some things like that, mostly when using gedit as my editor.  Every now and then there would be some error that made no sense at all when trying to compile the program.  It was like there were some invisible control codes or something that the compiler could see that were invisible to the human eye.  

I finally got desperate, and commented out the line that was giving the error, then re-typed it exactly the same way, and it worked.  It's happened more than once.  What editor are you using?

I copied and pasted both those code blocks onto my system, and they both compiled without errors.

I am using gedit. What is comment out? I haven't got that far yet...

---

### Post by jimi_hendrix on 2009-02-18
i assume its the gedit bug that TV mentioned...i can see no error

---

### Post by Can+~ on 2009-02-18
> **Leo Dragonheart said:**
> I am using gedit. What is comment out? I haven't got that far yet...

Commenting is just adding information to code for other humans. Or removing an offending piece of code.

[PHP]
// Here I do someting useful
a = 2 + 2;

// I am in ur codez, messin' ur dataz.
b = a;

/* Multi line comment!
 w00t
       w000t!!
      Here the comment ends -> */[/PHP]

---

### Post by Leo Dragonheart on 2009-02-18
I have tried deleting the lines and retyping, then saving and retrying but it still does not work I get same errors...Hmmmmm

---

### Post by Leo Dragonheart on 2009-02-18
I added comments to the 2 lines in question: I still get same errors.

```
#include <iostream>

using namespace std;

int main()
{
	int x;				// A normal interger
	int *p;				// A pointer to an integrer

	p = &x;				// Read it, "assign the address of x to p"
	cin>> x;			// Put a value in x, we could also use *p here
	cin.ignore();                   [COLOR="RoyalBlue"]// This is very strange[/COLOR]
	cout<< *p <<"\n";	       // Note the use of the * to get a value
	cin.get();                     [COLOR="RoyalBlue"]// I am confused...[/COLOR]
}

```

---

### Post by Leo Dragonheart on 2009-02-18
I don't know it is crazy... I deleted all of the files then redid it again from scratch and it worked fine. Hmmmmmm... Oh well it worked this time. On to the next lesson!!!

---

### Post by run1206 on 2009-02-19
are you using the command gcc instead of g++?  i'm using g++ and it worked for me (both with terminal and Anjuta) :?

oh well, as long as it works someway somehow...

---

### Post by Leo Dragonheart on 2009-02-19
> **run1206 said:**
> are you using the command gcc instead of g++?  i'm using g++ and it worked for me (both with terminal and Anjuta) :?

oh well, as long as it works someway somehow...

I was using g++ and I can do that in my sleep because for the last two days every time I had an error I would retype the whole thing from scratch. In the last two days I must have typed g++ -Wall "mycode.cpp" -o executable, chmod u+x executable, ./ executable, well over 500 times. I got that part down pat. 

The only thing I can think is that when I originaly saved the file it was saved in home so I moved it to my practice file where I wanted it and maybe that is why it was not reading it correctly. I really don't know but thanx to everyone who assisted me and checked to make sure my code was correct. Glad to know it wasn't my code this time...lol.

---

