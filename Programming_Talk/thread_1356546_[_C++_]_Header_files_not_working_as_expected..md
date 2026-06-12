---
title: "[ C++ ] Header files not working as expected."
date: 2009-12-16
forum: Programming Talk
---

### Post by Physical Hook on 2009-12-16
[COLOR=Green]main.cpp[/COLOR]:
```
#include <iostream>

#include "engine.h"

using namespace std;

int main(int argc, char *argv[])
{
    Sample mc;
    
    mc.day = "Monday";
    mc.month = "January";
    mc.year = 2009;
    
    return 0;
}

```[COLOR=Green]engine.h[/COLOR]:
```
#ifndef ENGINE_H
#define ENGINE_H

#include <string>

struct Sample
{
    string day;
    string month;
    int year;
};

#endif
``````
[COLOR=Red]In file included from main.cpp:3:
engine.h:8: error: ‘string’ does not name a type
engine.h:9: error: ‘string’ does not name a type
main.cpp: In function ‘int main(int, char**)’:
main.cpp:11: error: ‘struct Sample’ has no member named ‘day’
main.cpp:12: error: ‘struct Sample’ has no member named ‘month’[/COLOR]
```[COLOR=Black]What I'm doing wrong ?[/COLOR]

---

### Post by dwhitney67 on 2009-12-16
You need to qualify the string data types in your header file with the std:: namespace.

Do NOT declare a 'using namespace std' in your header file... bad, bad, bad!

Btw, good programming practice dictates that you include your project header file(s) (eg. engine.h) before including system header file(s) (eg. iostream).  Please examine your main module.

---

### Post by Physical Hook on 2009-12-16
Oh, ok - works now :) Thanks for the suggestion about the header file inclusion order - I'm still learning.

---

### Post by Muffinabus on 2009-12-16
> **dwhitney67 said:**
> You need to qualify the string data types in your header file with the std:: namespace.

Do NOT declare a 'using namespace std' in your header file... bad, bad, bad!

Btw, good programming practice dictates that you include your project header file(s) (eg. engine.h) before including system header file(s) (eg. iostream).  Please examine your main module.

Just a quick question, why exactly would it be bad to declare 'using namespace std;' in the header?  Is it just bad practice or does it actually consume more memory or something of the sort?

---

### Post by Zugzwang on 2009-12-16
> **Muffinabus said:**
> Just a quick question, why exactly would it be bad to declare 'using namespace std;' in the header?  Is it just bad practice or does it actually consume more memory or something of the sort?

This is because your header file might be included by other source files. For example, consider the following source file:
```

#include <algorithm>
#include "yourheader.h"

std::string getline() {
 ...
}


```

This source file will not compile if you put "#using namespace std;" in your header file as then the "getline" function conflicts with the "getline" function from the algorithm header. So it introduces naming conflicts where the writer of the .cpp source file would not expect them.

I only had the pleasure to find out why I couldn't call the "fail()" method of an "istringstream". G++ was always giving some weird error message. The reason was that a third-party library header file I included defined a macro called "fail". So this is also something you shouldn't do! ;-)

---

### Post by Muffinabus on 2009-12-16
Gotcha, thanks for the info!

---

### Post by Arndt on 2009-12-18
> **dwhitney67 said:**
> 
Btw, good programming practice dictates that you include your project header file(s) (eg. engine.h) before including system header file(s) (eg. iostream). 

Why?

---

### Post by dwhitney67 on 2009-12-18
> **Arndt said:**
> Why?

Because we do not live in a perfect world full of perfect s/w developers.  There's always some moron who will neglect to include a necessary dependency in their header file, which is then satisfied by 'magic' when some other module includes that dependency.

It pisses me off to no end when I work on project, or support legacy s/w, and come across a header file similar to the following:
```

#ifndef HEADER_H
#define HEADER_H

class Foo
{
public
   Foo();

...

private:
   std::string myStr;
};
#endif

```
Then the test code and/or implementation module:
```

#include "headerFileFromLeftField.h"
#include "header.h"

int main()
{
...
}

```
Then the developer compiles, and goes geez, this crap works... I'm bitching programmer!... I should be payed more for my efforts.

Ten weeks later, someone else wants to use the header.h, and the damn thing won't compile.  Or better yet, someone determines that <string> is no longer needed in headerFromLeftField.h, and removes the include.  Then you are staring at perhaps one, perhaps a dozen or more files that depend upon header.h that won't compile.

The geezer that wrote header.h in the first place still thinks he's best thing since sliced bread was invented.  I, of course, can think of at least 10 ways I would like to insert a knife through his heart.

Now you may think this is an extreme example, but piss poor programming techniques are more prevalent than good ones; and I've worked on lots of projects where programmers ask the same question as you... "Why??".  Uhh... where's my knife!!!


P.S.  Sorry for the rant.  If you want to develop bad s/w, do so... it keeps me employed.

---

### Post by Arndt on 2009-12-19
> **dwhitney67 said:**
> Because we do not live in a perfect world full of perfect s/w developers.  There's always some moron who will neglect to include a necessary dependency in their header file, which is then satisfied by 'magic' when some other module includes that dependency.



P.S.  Sorry for the rant.  If you want to develop bad s/w, do so... it keeps me employed.

Thanks for the explanation. We're on the same side here. I've just not developed large C or C++ things for a long time, so I needed to ask "why".

---

### Post by LKjell on 2009-12-19
@dwhitney67 I am kinda confused. If you add system header file last and your project header needs one system header file. Where do you add it then?

In my opinion the geezer who wrote header.h should include the string header in it.

---

### Post by dwhitney67 on 2009-12-19
> **LKjell said:**
> @dwhitney67 I am kinda confused. If you add system header file last and your project header needs one system header file. Where do you add it then?

In my opinion the geezer who wrote header.h should include the string header in it.

Your second statement (paragraph) answers your question.

---

### Post by LKjell on 2009-12-19
> **dwhitney67 said:**
> Your second statement (paragraph) answers your question.

But then it should not matter in which order you include the project header since it has the system header it requires to compile. 

The only scenario I can think of is that your project header is suppose to overwrite some functionality that system headers have.

Though including the project header first gives a layer of protection to make sure you include the system header in the project header in the first place. But then if you do forget I can see your frustration.

---

### Post by MadCow108 on 2009-12-19
including the system header first masks missing system header dependencies in the following includes:
```

#include <string>
#include "header.h" // this now works even if header.h is lacking the string dependency

```

writing some module which does not need <string> explicitly now will require fixing header.h (or, less recommended, explicitly include <string> before header.h)

---

### Post by dwhitney67 on 2009-12-19
> **MadCow108 said:**
> including the system header first masks missing system header dependencies in the following includes:
```

#include <string>
#include "header.h" // this now works even if header.h is lacking the string dependency

```

writing some module which does not need <string> explicitly now will require fixing header.h (or, less recommended, explicitly include <string> before header.h)

Thank you; that sums up what I was trying to state earlier.

---

### Post by dribeas on 2009-12-20
That is all about rules of style: they don't fix problems, but they help you detect them early, or even avoid common problems altogether. 

At this point you should follow the advice of those that have more experience, learn from their mistakes and the mistakes they have seen, and you can find quite experienced people here.

---

