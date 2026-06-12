---
title: "Variables!"
date: 2009-04-23
forum: Programming Talk
---

### Post by ayastona on 2009-04-23
hi. the title might be a little confusing.

c++

i am trying to set up variables that have multiple other variables within them..

so for instance i need to enter a persons name and then along with that name i need to specify the persons age and address and a few other demographic informations..

that information will then be written to a file. (which i know how to do... i think....) then i will move to the next person and enter their name and within that persons name i will repeat the process as before...

how do i go about doing this? do i need to create a class? please help!

---

### Post by Jiraiya_sama on 2009-04-23
Structs would do what you want to do.

---

### Post by apmcd47 on 2009-04-23
I'd use a class. Then you can put methods to print the information in the class.

As you are asking such a basic question, are you new to programming in C++? Have you any books to learn from?

Andrew

---

### Post by dwhitney67 on 2009-04-23
Definitely a struct (or a class).

Here's an example of a struct, which has a friend method to write the data to an output stream (e.g. an fstream).
```

struct Person
{
  std::string  name;
  unsigned int age;
  std::string  addr;
  ...

  friend std::ostream& operator<<(std::ostream& os, const Person& p)
  {
    os << name << '~'
       << age  << '~'
       << addr << '~'
       ...
       << std::endl;
    return os;
  }
};

```

---

### Post by Jiraiya_sama on 2009-04-23
> **apmcd47 said:**
> I'd use a class. Then you can put methods to print the information in the class.

As you are asking such a basic question, are you new to programming in C++? Have you any books to learn from?

Andrew

There's really no difference between structs and classes in C++ except that structs have the "public:" access label on by default, while the opposite is true for classes.

---

### Post by ayastona on 2009-04-23
> **apmcd47 said:**
> I'd use a class. Then you can put methods to print the information in the class.

As you are asking such a basic question, are you new to programming in C++? Have you any books to learn from?

Andrew

i was heavy into programming for a few years, but that was many years ago.. i kinda forgot how to do certain things.. what im trying to do is speed up a process at work and have a way to track information about some clients.. its a very bare bones thing that makes a printed report at the end...

i knew that i would have to use structs, i just forgot what they were called or if classes would be better.. i think ill stick with structs..

---

