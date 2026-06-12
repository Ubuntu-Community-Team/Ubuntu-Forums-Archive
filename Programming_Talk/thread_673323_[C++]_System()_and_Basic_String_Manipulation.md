---
title: "[C++] System() and Basic String Manipulation"
date: 2008-01-20
forum: Programming Talk
---

### Post by family on 2008-01-20
In Python, I am used to doing, let's just say, this;
```

from os import system
# [...]
var = '/usr/bin/conky'; system("%s" % var);

```
How do I emulate such '%s' in C++?
EDIT>>> AFTER GETTING A NEW GUTSY SOURCES.LIST, I FOUND THIS EXTREMELY USEFUL. At least try it, the code is complete.
```

#include <iostream>
using std::cout; using std::cin; using std::system; using std::string; int c; string lino; string entry;
int words (void) {
	cout << "\nGPG HAS FINISHED THIS OPERATION TO ITS BEST ABILITIES.";
	cout << "\nPRESS ANY KEY BUTTON TO REPEAT THE SELECTION PROCESS.\n";
	cin.get();
}
int main (void) {
	while (1)
	{
	cout << "\nSelect a number/operation and enter it in.\n";
	cout << "1. GPG NUMMBER\n";
	cout << "2. URL\n";
	cout << "3. GPG FILE\n";
	cout << "0. FULL QUIT\n" << "-1. FAST QUIT\n";
	cout << "Enter your choice; "; cin >> c;
	if (c>=4 || c<=-2) {c=1;}
		if (c == 1) {
			cout << "GPG STRING: "; cin >> entry;
			lino = "gpg --keyserver subkeys.pgp.net --recv "+entry;
			string lint = "gpg --export --armor "+entry+" | sudo apt-key add -";
			system(lino.c_str()); system(lint.c_str()); words ();
		}
		else if (c == 2) {
			cout << "URL: "; cin >> entry;
			lino = "wget "+entry+" --quiet -O - | sudo apt-key add -";
			system(lino.c_str()); words ();
		}
		else if (c == 3) {
			cout << "GPG FILE: "; cin >> entry;
			lino = "sudo apt-key add "+entry;
			system(lino.c_str()); system("sudo apt-key update"); words ();
		}
		else if (c == 0) {
			cout << "\n"; system("sudo apt-get update"); exit(0);
		}
		else if (c == -1) {exit(0);}
	}
	return 1;
}
```

---

### Post by family on 2008-01-20
I'm sorry to bump, but this seems like a simple question...

---

### Post by LaRoza on 2008-01-20
[php]
#include <stdio.h>
#include <stdlib.h>

int main(int args,char ** argv)
{
    char *conky = "/usr/bin/conky";
    system(conky);
    return 0;
}
[/php]

---

### Post by Wybiral on 2008-01-20
There is no string formatting in C++. I believe the correct C++ method would be to use a stringstream, stream the values in, and convert that back to a string. In C, there is sprintf which provides similar functionality to Pythons string formatting. You could also simply concatenate the strings in either language.

---

### Post by LaRoza on 2008-01-20
@OP My example was in C, not C++.

---

### Post by family on 2008-01-21
Thanks guys, I'll look into that.
system() looks pretty straightforward.

---

### Post by family on 2008-01-22
Ok, here is my issue, I haven't really looked into sprintf yet (but I will, right now), but I fused the strings and the C example LaRoza gave me isn't working;
```

cin >> entry;
char *lino = "gpg --keyserver subkeys.pgp.net --recv "+entry;
system(lino);
char *lint = "gpg --export --armor "+entry+" | sudo apt-key add -";
system(lint);

```

---

### Post by family on 2008-01-22
Now what am I doing wrong?
```

cin >> entry;
string lino = sprintf("gpg --keyserver subkeys.pgp.net --recv %s",entry);
system(lino);
string lint = sprintf("gpg --export --armor %s | sudo apt-key add -",entry);
system(lint);

```
GPG.cpp: In function &#8216;int main()&#8217;:
Compilation failed.
GPG.cpp:29: error: cannot convert &#8216;std::string&#8217; to &#8216;const char*&#8217; for argument &#8216;2&#8217; to &#8216;int sprintf(char*, const char*, ...)&#8217;
GPG.cpp:30: error: cannot convert &#8216;std::string&#8217; to &#8216;const char*&#8217; for argument &#8216;1&#8217; to &#8216;int system(const char*)&#8217;
GPG.cpp:32: error: &#8216;lint&#8217; was not declared in this scope

---

### Post by supirman on 2008-01-22
For starters, you don't appear to be passing the correct parameters to sprintf.

From the man page for sprintf, we find:
```
int sprintf(char *str, const char *format, ...);

```

See [this page]("http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html") for an example of using sprintf.

In addition, you're trying to mix c++ strings with char* types, Also, note that sprintf doesn't return a string like you're trying to do. 

Finally, when you do get a valid string into your variable lint, you'd call system() as follows:
```
 system(lint.c_str());
```

system() takes a char*, so to get a char* from a c++ string, you call the c_str() method on the string.

---

### Post by family on 2008-01-23
I have several questions. I understand what the char variable type is, but what is 'char*''s purpose (or 'char ** argv''s)?
If I want to use sprintf, do I need to define it in my own program? If so, why? Isn't that what libraries are for?
In BASH, * is a wildcard, so for now I will assume that '*format' means 'any format'. I am sure I am wrong, but it's my only theory. :(

Please just look at my first post with the example of Python code; can anyone reproduce that in C++?

---

### Post by LaRoza on 2008-01-23
> **family said:**
> I have several questions. I understand what the char variable type is, but what is 'char*''s purpose (or 'char ** argv''s)?
If I want to use sprintf, do I need to define it in my own program? If so, why? Isn't that what libraries are for?


"char *" is a pointer to a char. "char ** argv" is a pointer to a pointer of char. Understanding this requires one to know the relationship between arrays and pointers.

You don't have to define sprintf, just include the header it is defined in.

---

### Post by supirman on 2008-01-23
Just as a really simple example, like your first python snippet, consider the following.  In this case, you don't really need sprintf.  

I skipped the menu entry stuff b/c it's irrelevant to the example.
```

#include <iostream>
#include <string>

using namespace std;

int main (void)
{
	string entry;

	cout << "Enter GPG NUMBER: ";
	cin >> entry;

	// you can do concatenation like this, that's fine.
	string lino = "gpg --keyserver subkeys.pgp.net --recv "+entry;
	string lint = "gpg --export --armor "+entry+" | sudo apt-key add -";

	// system takes a char* parameter, so from the c++ string,
	// we need its c string representation (which is a char *)
	system(lino.c_str());
	system(lint.c_str());

}

```

---

### Post by family on 2008-01-23
I love this forum so much.
Thank-you!!!

(And if anybody has gpg issues with a new sources.list, the fully functional source-code is on the first page of this thread :D)

---

