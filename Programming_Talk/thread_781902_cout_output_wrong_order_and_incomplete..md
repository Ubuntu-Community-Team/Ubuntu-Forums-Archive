---
title: "cout output wrong order and incomplete."
date: 2008-05-04
forum: Programming Talk
---

### Post by rnodal on 2008-05-04
Hello all:

My little c++ program is having a weird issue.
```
cout << "Searching SID's for " << airport_name << " ..." << "\n";
```

That line is supposed to output something that looks like this:
```
Searching SID's for MADEIRA ...
```

Instead I get:
```
...ching SID's for MADEIRA
```
As you can see it is replacing the first letters of the word Searching with the "...". Any clues why that is the case? Thanks a lot for your time.

-r

---

### Post by LaRoza on 2008-05-04
> **rnodal said:**
> Hello all:

My little c++ program is having a weird issue.
```
cout << "Searching SID's for " << airport_name << " ..." << "\n";
```


I am guessing:

```

cout << "Searching SID's for " << airport_name << " ..." << endl;

```
Maybe that will work?

---

### Post by rnodal on 2008-05-04
Thanks for your replay :). I have tried that and also putting flush(cout) before that line but nothing seems to work. The line works like this:
```
cout << "Searching SID's for " << airport_name << "\n" << endl;
```
But that is not the output that I want.:confused: I don't know what could be causing the problem.


-r

---

### Post by tseliot on 2008-05-04
This code works well here:
[PHP]
#include <iostream>
#include <string>
int main(int argc, char** argv)
{
    using namespace std;
	string airport_name = "MADEIRA";
	cout << "Searching SID's for " << airport_name << " ..." << "\n";
	return 0;
}
[/PHP]
A [screenshot]("http://albertomilone.com/madeira.png").

---

### Post by stroyan on 2008-05-04
I expect that airport_name contains a carriage return character.
that makes the terminal move the cursor to the start of the line.
Then the "..." overwrites the front.
You should filter your airport_name value to remove control characters.

---

### Post by rnodal on 2008-05-04
That was it! I forgot to clean the string since it came from a file. Thanks a lot all for your help.

-r

---

