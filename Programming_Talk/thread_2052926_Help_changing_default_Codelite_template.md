---
title: "Help changing default Codelite template?"
date: 2012-09-04
forum: Programming Talk
---

### Post by willieterry on 2012-09-04
I'm running the latest build of the Codelite IDE in an attempt at learning some c++.
What I want to know is how to change the default main.cpp template from:

[INDENT][SIZE="2"][FONT="Courier New"]#include <stdio.h>

int main(int argc, char **argv)
{
	printf("hello world\n");
	return 0;
}[/FONT][/SIZE][/INDENT]

to

[INDENT][SIZE="2"][FONT="Courier New"]#include <iostream>
using namespace std;

int main()
{
	cout << "Hello World" << endl;
	return 0;
}[/FONT][/SIZE][/INDENT]

I've tried editing the main.cpp in ~/.codelite/templates/projects/executable
but that didn't keep the change for new projects.

I've searched Google, but it's been a real shitstorm since codelite likes to find pages on CoD Elite and "codelite" is practically only download pages.

Any help is appreciated.

---

### Post by eranif on 2012-09-04
Hello,

This looks like a bug to me in codelite

however, you can easily workaround it like this:

- Create the standard template 
- Change main.cpp to fit your needs
- Right click on the project -> Save As Template...
- Give it a name + description

From now on use this new template instead of the default one.

OR

Modify the template file from: /usr/share/codelite/templates/projects/executable

BTW, you might consider joining codelite's forum at:
[http://forums.codelite.org](http://forums.codelite.org)

---
Eran, author of codelite IDE
[http://codelite.org](http://codelite.org)

---

### Post by willieterry on 2012-09-04
Thank you. I actually went over the their forum right after posting that. Brain fart. -_-

But I've got it where I need it, so all's well. Thanks again.

---

### Post by durdenstationer on 2012-09-04
Just as a hint, using 'using namespace std;' is considered poor style since it loads everything in the global namespace. It's okay if you are just starting out, but even then it's better to get used to using the scope operator and prefixing with std:: instead. The 'using namespace std;' is even used by Bjarne in The C++ Programming Langauge but admits it's only to make the examples shorter not because it's good style.

---

