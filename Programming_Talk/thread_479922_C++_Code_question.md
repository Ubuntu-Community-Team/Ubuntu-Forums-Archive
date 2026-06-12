---
title: "C++ Code question?"
date: 2007-06-20
forum: Programming Talk
---

### Post by OhioYJ on 2007-06-20
Ok I cut out all the un-important stuff. I for some reason can not call a function in my program. Here is a sample of my code? I have to be overlooking something? 

> #include <iostream>
#include <iomanip>
#include <fstream>

using namespace std;

void lines();

int main()
{
	void lines();	
	return 0;
	
}

void lines()
{
	cout << "Hey you made it here" << endl;
}

---

### Post by cantormath on 2007-06-20
What error do you get when you try to run it?

---

### Post by Soybean on 2007-06-20
When you're calling the lines() function from within main (or from anywhere -- when you're calling a function), you don't need to list the return type.

So the relevant part becomes:
```
int main()
{
lines();
return 0;
}
```

And it ought to work, unless something else is also wrong. ;) (besides what you've shown here)

EDIT: Oh! And if it won't *compile*, make sure you're using "g++" instead of "gcc". I've spent a significant amount of time on *more than one occasion* trying to debug "undefined references" because I was using the wrong compiler. #-o

---

### Post by OhioYJ on 2007-06-20
I don't get any errors, it just never calls the function, just skips over it like its not there. 

The void lines() function is supposed to draw a horizontal line essentially, the code works if its in main(), but when I run the program, my menu shows up, but there is no line, it just skips it?

---

### Post by OhioYJ on 2007-06-20
> When you're calling the lines() function from within main (or from anywhere -- when you're calling a function), you don't need to list the return type.

Doh! I knew that... Thanks a ton, that took care of the problem. Still trying to brush up on my programming, been several years since I've done an coding.

---

### Post by gizmoarena on 2007-06-20
why you are using??
> #include <iomanip>
#include <fstream>

---

### Post by OhioYJ on 2007-06-20
> why you are using??

#include <iomanip>
#include <fstream>

Remember I cut out a bunch of code, the fstream is because I'm writing stuff to a file. The iomanip is for a bunch of formatting stuff I'm doing with the data?

Why, are those not necessary?

---

### Post by Golyadkin on 2007-06-21
Try putting the line function above the main function, so it can find it.
```

#include <iostream>
#include <iomanip>
#include <fstream>

using namespace std;

void lines();

void lines()
{
cout << "Hey you made it here" << endl;
}

int main()
{
void lines();
return 0;

}


```

---

### Post by hod139 on 2007-06-21
> **Golyadkin said:**
> Try putting the line function above the main function, so it can find it.
This is unnecessary because he place a function prototype at the top of the file.

---

