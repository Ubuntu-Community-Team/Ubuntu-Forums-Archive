---
title: "declaration of obj with no type"
date: 2007-11-29
forum: Programming Talk
---

### Post by belikewater on 2007-11-29
i have an Email class:
and an EmailDB (database)

[COLOR="Blue"]EmailDB.h[/COLOR]

following changes doesn't help:

class EmailDB{

private:
 Email *Head;     changed to        ->             Email::Email *Head;
 Email *Tail;        changed to        ->             Email::Email *Tail;
}

[COLOR="Blue"]i compile using gcc  gcc -cc EmailDB.cpp 
 and link gcc EmailDB.cpp Email.cpp -o main[/COLOR]
tried to include file Email.h at EmailDB but it doesn't help:
[COLOR="Red"]
EmailDB.h:13: error: ‘Email’ has not been declared
EmailDB.h:13: error: ISO C++ forbids declaration of ‘Email’ with no type
[/COLOR]

---

### Post by geirha on 2007-11-29
> **belikewater said:**
> 
class EmailDB{

private:
 Email *Head;     changed to        ->             Email::Email *Head;
 Email *Tail;        changed to        ->             Email::Email *Tail;
}


;

---

### Post by smartbei on 2007-11-29
Ok, what is up with the colors? :D
I would add to what geirha pointed out - you probably need a semicolon after the email class.

Also, please us [ code ] tags for code - it makes it so much more readable.

---

### Post by evarlast on 2007-11-29
you will need to post more code to get real helpful answers.

Is this an exercise in learning about linked lists or are you writing a real application? If the latter, why not use an STL container instead of making your own linked list?

If the former:

email.hpp has an unimplemented factory method
```


class Email {
public:
	static Email* Email::NewMessage(char* from, char* to, char* subject, char* message)
	{
		return new Email();
	}

};

```

emaildb.hpp is defined as you wish. I added an "Add" method.
```

#include "Email.hpp"

class EmailDB
{
public:
	void Add(Email*);
private:
	Email *Head;
	Email *Tail;	
};

```

The implementation of each of these is empty.  Email.cpp is empty, emailDB.cpp contains an unimplenented add method:

```

#include "EmailDB.hpp"

void EmailDB::Add(Email *){
}

```

Example usage might look like this main.cpp:
```

#include "EmailDB.hpp"

int main(int argc, char* argv[])
{
	EmailDB emaildb;
	
	emaildb.Add(Email::NewMessage("bob", "alice", "hi there!", "spam!"));
      return 0;

```


The above code compiles. It is up to you to implement it and make it do something.

--
j

---

