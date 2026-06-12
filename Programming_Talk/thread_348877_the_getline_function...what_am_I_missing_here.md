---
title: "the getline function...what am I missing here?"
date: 2007-01-29
forum: Programming Talk
---

### Post by indigoshift on 2007-01-29
Time for a little CompSci 101. ;)

I've been playing around with C++ again, and wrote this quick little program to see if I could remember how to do a "do/while" loop:

```

// do/while loop

#include <iostream>
#include <string>
using namespace std;

bool repeat = false;

int main()
{
	string x;
	

	do{
		cout << "enter text: ";
		getline(cin,x);

		cout << "you entered: " << x << endl;

		cin.clear();

		cout << "again (1/0)? ";
		cin >> repeat;

	}while(repeat);

return 0;
}

```

It'll work fine the first time through.  The second time, though, it'll ask for input, then it'll just run itself to death in an endless loop, like so:

> 
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
again (1/0)? enter text: you entered:
.
.
.
(and so on and so forth...forever)


I stuck a "cin.clear();" in there, and that lets it run right twice before the endless loop.

So am I screwing up the getline or the do/while?  I'm assuming the getline is where things are breaking, since I've changed to do/while to a while() loop, and even tried the dreaded goto as alternatives.  Both gave the same results.  It's very weird.

---

### Post by ghandi69_ on 2007-01-29
> #include<iostream>
using namespace std;

int main(){

	char buffer[10];
	int z = 0; 

do{
	cout << "Enter Text\n";
	cin >> buffer;

	cout << buffer;

	cout << "Keep going (1/0)\n>>";
	cin >> z;
	
}while(z == 0);

return 0;
}


This works.. so I'm guessing its something with getline.....

---

### Post by qpwoeiruty on 2007-01-30
The do/while is good, just try adding a cin.get() after the "cin >> repeat".

I think you were getting the infinite loop because of this: cin leaves the \n in the buffer. You then getline. The '\n' tells getline that it's all done and whatever you typed will be left in the buffer. x ends up just being an empty string...
So, if you typed in "Hello World", getline would see the '\n' and leave "Hello World\n" in the buffer and that's just not nice when your cin is expected to be grabbing a bool ;) As you noticed, fun stuff happens and you get that infinite loop :P


This is the code I used: ```
#include <string>
#include <iostream>

using namespace std;

int main()
{
    bool repeat = true;
	string x;

	while(repeat){
		cout << "enter text: ";

		getline(cin,x);

        cout << "you entered: " << x << endl;

		cout << "again (1/0)? ";
		
        cin >> repeat;
        [COLOR="red"]cin.get();[/COLOR]

	};

return 0;
}
```

---

### Post by indigoshift on 2007-01-30
Perfect!  Thanks, qpwoeiruty, for the assist, and for the informative bit on the \0 still in the buffer.  I would've never figured that out on my own. :D

---

