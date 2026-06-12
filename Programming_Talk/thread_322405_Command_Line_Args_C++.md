---
title: "Command Line Args: C++"
date: 2006-12-20
forum: Programming Talk
---

### Post by Ben Sprinkle on 2006-12-20
Why won't this work?
```

#include <iostream>

using namespace std;

int main(char args[]) {
	if(args == "--help" || args == "-help" || args == "-h" || args == "--h") {
		cout << "args 1.0.0" << endl;
		cout << "Created by Goat Spirit" << endl;
		cout << "http://goatcd.org" << endl;
	} else {
		cout << "Usage: args [args]" << endl;
		cout << "Help: (--help || -help || --h || -h)" << endl;
	}
}

```

---

### Post by Wybiral on 2006-12-21
Ok, first you aren't accessing the arguments properly, the arguments are sent to the main function as parameters in the order of:

1.) argument count
2.) array of the argument pointers

This allows for multiple arguments, and is the standard way of dealing with them. Also, the first argument passed is always the name of the program itself.

Secondly, you need a string class in order to compare an array of characters (such as a string)... string.h works wonderfully.

Here is an example where it will iterate through every argument and check it against the possible options you needed (note, if they enter the same arguments multiple times, this program does not catch and correct it)...

```

#include <string.h>
#include <iostream>

using namespace std;

int main(int argc, char* argv[]) {
	string myArg;
	for (int i=1; i<argc; i++){
		myArg = argv[i];
		if(myArg == "--help" || myArg == "-help" || myArg == "-h" || myArg == "--h") {
			cout << "args 1.0.0" << endl;
			cout << "Created by Goat Spirit" << endl;
			cout << "http://goatcd.org" << endl;
		} else {
			cout << "Usage: args [args]" << endl;
			cout << "Help: (--help || -help || --h || -h)" << endl;
		}
	}
}

```

Notice the use of argc (representing argument count) and then argv is an array that points to the individual arguments (pointers allow for easier access to the argument array as nothing needs to be copied). Also notice how the for-loop iteration starts at 1 instead of 0, thats because the first argument is the name of the program and we don't need it.

Then we created a string named myArg... Since simple character arrays can be passed into a string, we are able to pass the arguments from argv to a string so that we can use comparative operators such as "=="... We can't do this with normal character arrays unless we write our own operator overload for it.

Now... In a real program you may want to use a boolean to store whether or not that argument has already been used and prevent it from printing it multiple times in the event that the user enters the same argument more than once.

Hope this helps.

Btw, here's a link that might help elaborate it a little: [http://www.codepedia.com/1/CppMain](http://www.codepedia.com/1/CppMain)

---

### Post by slavik on 2006-12-21
there is also char *env[] (environment)

---

### Post by Ben Sprinkle on 2006-12-22
Thanks.

---

