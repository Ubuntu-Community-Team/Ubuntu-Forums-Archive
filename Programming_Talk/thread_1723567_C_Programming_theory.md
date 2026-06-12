---
title: "C Programming theory"
date: 2011-04-07
forum: Programming Talk
---

### Post by chaoprokia on 2011-04-07
Thanks

---

### Post by simeon87 on 2011-04-07
What do you think the answers are to the given questions and why? This sounds like homework or exams questions.

---

### Post by chaoprokia on 2011-04-07
> **simeon87 said:**
> What do you think the answers are to the given questions and why? This sounds like homework or exams questions.
 Yeah part of my homework to discover the fact. which i am trying to understand how is it being derive. well if no one can help me i try other ways.

---

### Post by simeon87 on 2011-04-07
> **chaoprokia said:**
> Yeah part of my homework to discover the fact. which i am trying to understand how is it being derive. well if no one can help me i try other ways.

My answers would be:

Q1: "Conditional compilation is provided by C compiler" is false because it is provided by the preprocessor, not the compiler.

Q2: The content of the struct is being printed but it's rather meaningless because you didn't initialize it. It's only a logic error if the printed content is important for the executing of the program (i.e., showing meaningful information to the user). Otherwise, it's not really a logic error as nobody really cares about the printed values.

---

### Post by chaoprokia on 2011-04-07
> **simeon87 said:**
> My answers would be:
 
Q1: "Conditional compilation is provided by C compiler" is false because it is provided by the preprocessor, not the compiler.
 
Q2: The content of the struct is being printed but it's rather meaningless because you didn't initialize it. It's only a logic error if the printed content is important for the executing of the program (i.e., showing meaningful information to the user). Otherwise, it's not really a logic error as nobody really cares about the printed values.
 
Q2.let say my Struct has 2 value Student Name and Student ID. The Program main functionally is to print Student Name and Student ID.
But i declare it and didn't initialize it and print it. so this is an logic error. It is not an logic error if the struct doesn't do stuff?

---

### Post by simeon87 on 2011-04-07
> **chaoprokia said:**
> Q2.let say my Struct has 2 value Student Name and Student ID. The Program main functionally is to print Student Name and Student ID.
But i declare it and didn't initialize it and print it. so this is an logic error. It is not an logic error if the struct doesn't do stuff?

What is or is not a logic error isn't rigidly defined. I'm just saying that I personally don't think it's a logic error when the printed value plays no meaningful role in the program. But if the main purpose is to show a student name and ID and it would print a meaningless value then it's indeed a logic error.

---

### Post by MadCow108 on 2011-04-07
> **chaoprokia said:**
> Q2.let say my Struct has 2 value Student Name and Student ID. The Program main functionally is to print Student Name and Student ID.
But i declare it and didn't initialize it and print it. so this is an logic error. It is not an logic error if the struct doesn't do stuff?

if the point of the program is to print nonsensical garbage (or zeros depending on where the struct is allocated), then no its no logic error.
In any other case yes.

---

### Post by chaoprokia on 2011-04-07
> **simeon87 said:**
> What is or is not a logic error isn't rigidly defined. I'm just saying that I personally don't think it's a logic error when the printed value plays no meaningful role in the program. But if the main purpose is to show a student name and ID and it would print a meaningless value then it's indeed a logic error.
 
> **MadCow108 said:**
> if the point of the program is to print nonsensical garbage (or zeros depending on where the struct is allocated), then no its no logic error.
In any other case yes.
 
ok thanks i understand more clearly on what is an logic error and what not.

---

