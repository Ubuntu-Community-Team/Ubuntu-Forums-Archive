---
title: "Why is this doing this?"
date: 2009-02-26
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-26
I was going to enter this in one of LaRoza's  beginer challanges but I can't get this bug out... I won't enter it now since I am asking for help!

The program compiles and runs great except that when it couts the bottom line in place of name I get like 8 #'s instead of a name Why?


```
#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main()
{
     string mystr;
     int name;
     int age;
     int ID;
{
	cout << "Please enter your forum name: ";
	getline(cin,mystr);
	stringstream(mystr) >> name;

	cout << "Please enter your age: ";
	getline (cin,mystr);
	stringstream(mystr) >> age;

	cout << "Please enter your user ID #: ";
	getline (cin,mystr);
	stringstream(mystr) >> ID;
					
	if (age < 1 || age > 100) {
	     cout << "This can't be true, Please try again!" << endl;
					}
	else {
	     cout << "You are " << name << ", You are " << age << ", next year you will be " << age + 1 << ", Your user ID # is " << ID << ", and the next users ID # is " << ID + 1 << endl; }
	}						

	return 0;
}

```

P.S. How do you qoute a single line from a post is it [qoute][/qoute]?

---

### Post by dwhitney67 on 2009-02-26
The problem is with the declaration of 'name'; I believe you wanted it to be a string, not an int.

Btw, if you change the declaration of 'name' to be an std::string, the code below will not compile!
```

stringstream(mystr) >> name;

```
P.S.  You won't need to use the statement above anyway, if you change the declaration for 'name'.

---

### Post by Leo Dragonheart on 2009-02-26
I changed it to below but now I get a blank...nothing for the name.


```


#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main()
{
	
        string name;
	string mystr;	
	int age;
	int ID;
      {
	cout << "Please enter your forum name: ";
	getline(cin,mystr);

	cout << "Please enter your age: ";
	getline (cin,mystr);
	stringstream(mystr) >> age;

	cout << "Please enter your user ID #: ";
	getline (cin,mystr);
	stringstream(mystr) >> ID;

	if (age < 1 || age > 100) {
	   cout << "This can't be true, Please try again!" << endl;
					}
        else {
	   cout << "You're forum name is:" << name << ", You are:" << age << ", next year you will be:" << age + 1 << ", Your user ID # is:" << ID << ", and the next users ID # is " << ID + 1 << endl;
             }
	}						

	return 0;
}
			 
```

---

### Post by issih on 2009-02-26
As it stands you load the entered name into the mystr variable, but do nothing with it, until you replace the value in mystr with the next entered value. just drop in a line like:

```
name = mystr;
```

after the first getline statement.

Alternatively just use name in place of mystr in that getline statement.

Hope that helps

---

### Post by dwhitney67 on 2009-02-26
> **issih said:**
> As it stands you load the entered name into the mystr variable, but do nothing with it, until you replace the value in mystr with the next entered value. just drop in a line like:

```
name = mystr;
```

after the first getline statement.

Alternatively just use name in place of mystr in that getline statement.

Hope that helps

+1.

It's funny how the OP missed that.  LOL.

---

### Post by Leo Dragonheart on 2009-02-26
> **issih said:**
> As it stands you load the entered name into the mystr variable, but do nothing with it, until you replace the value in mystr with the next entered value. just drop in a line like:

```
name = mystr;
```

after the first getline statement.

Alternatively just use name in place of mystr in that getline statement.

Hope that helps

Thanx for the info... I replaced the first getline(cin,mystring); with getline(cin,name); like I thought you instructed but it would not cout the last line it just ended program. Then I droped in a name = mystr; right below the first getline, like I thought you instructed and it worked perfectly thanx again... could you give a little explanation on why that works like that for me? It doesn't have to be a long winded explanation, I am just wondering why it would not return the name when it returned the rest of the string fine? Thanx again for the help...:p

---

### Post by dwhitney67 on 2009-02-26
[comment deleted]... nevermind I see the closing bracket.

This code works for me:
```

#include <iostream>
#include <string>
#include <sstream>

int main()
{
  std::string name;
  std::string mystr;
  int         age;
  int         ID;

  {
    std::cout << "Please enter your forum name: ";
    getline(std::cin, name);

    std::cout << "Please enter your age: ";
    getline(std::cin, mystr);
    std::stringstream(mystr) >> age;

    std::cout << "Please enter your user ID #: ";
    getline(std::cin, mystr);
    std::stringstream(mystr) >> ID;

    if (age < 1 || age > 100) {
      std::cout << "This can't be true, Please try again!" << std::endl;
    }
    else {
      std::cout << "You're forum name is:" << name
                << ", You are:" << age
                << ", next year you will be:" << age + 1
                << ", Your user ID # is:" << ID
                << ", and the next users ID # is " << ID + 1
                << std::endl;
    }
  }
}

```

---

### Post by issih on 2009-02-26
Hmmn an explanation. tricky as its fairly fundamental.

Ok lets say you have someone behind a screen so you can't see him, and every time you hand him a bucket he empties whatever is currently in the bucket on the floor, fills it with a new randomly coloured liquid, and hands it back.

Your basic program flow now equates to handing him one specific bucket lets call it bucket1. Once you have bucket1 back you then pour the contents into a second bucket (bucket2), which you never pass to the man behind the screen, for safe keeping.

You then pass bucket1 back to the man behind the screen and get it returned with a new, differently coloured liquid in it. This time you pour it into a jamjar, as you only wanted some of that liquid, but the basic idea is the same.

At each step you pass bucket1 over and when you get it back you pour the contents into some other container to keep hold of it and pass bucket1 back to get the next item.

Your original code was the equivalent of pouring bucket1 into a jamjar when really you wanted to keep it in a bucket. In your second attempt you passed bucket1 back without ever storing its contents in bucket2, consequently the man behind the screen threw the original contents away, and later when you went to see what was in bucket2 it was empty.


My other suggestion was that for the first case, where you just wanted to keep the whole bucket, not just pour some of it into a jam jar, that you could send over bucket 2 directly and let the man fill that, then just keep that from then on. As to why it didn't work, I don't know, I suspect there was another little error in your code somewhere.

Sorry if that seems patronising, its hard to explain coding concepts without using coding concepts.

Hope that helps

---

### Post by Leo Dragonheart on 2009-02-26
> **dwhitney67 said:**
> [comment deleted]... nevermind I see the closing bracket.

This code works for me:
```

#include <iostream>
#include <string>
#include <sstream>

int main()
{
  std::string name;
  std::string mystr;
  int         age;
  int         ID;

  {
    std::cout << "Please enter your forum name: ";
    getline(std::cin, name);

    std::cout << "Please enter your age: ";
    getline(std::cin, mystr);
    std::stringstream(mystr) >> age;

    std::cout << "Please enter your user ID #: ";
    getline(std::cin, mystr);
    std::stringstream(mystr) >> ID;

    if (age < 1 || age > 100) {
      std::cout << "This can't be true, Please try again!" << std::endl;
    }
    else {
      std::cout << "You're forum name is:" << name
                << ", You are:" << age
                << ", next year you will be:" << age + 1
                << ", Your user ID # is:" << ID
                << ", and the next users ID # is " << ID + 1
                << std::endl;
    }
  }
}

```

I havn't got that far yet. I did not know about the std::cout << thingy.. Thanx for the example though I will study it...

---

