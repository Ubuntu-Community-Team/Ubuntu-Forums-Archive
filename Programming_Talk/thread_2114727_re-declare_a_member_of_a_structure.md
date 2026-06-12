---
title: "re-declare a member of a structure"
date: 2013-02-10
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-10
Hello,
Is it possible in C to re-declare a member of a structure ?
As in, say I have a structure like,
```

typedef struct _TABLE
{
 int age;
 char* name;
}TABLE;

```

Can I do something like
```

if(entered_age is not a number)
{
 redeclare int age as char* age;
 printf("\nyou entered %s which is not a valid age. Please enter a number",age);
}

```

Thanks.
PS : The example in the scenario is not based on a requirement, I have just tried to create an example to explain my question.

---

### Post by lisati on 2013-02-11
It has been a while since I have seen an example, but I think "[union]("http://www.go4expert.com/articles/unions-c-powerful-feature-c-t15/")" might be similar to what you are after. It is possible that more experienced C programmers than myself might be able to offer alternatives.

---

### Post by dwhitney67 on 2013-02-11
> **IAMTubby said:**
> Hello,
Is it possible in C to re-declare a member of a structure ?

And the rationale/requirement for this is...?

If your program is accepting input from a user (or a file, or whatever) and it requires a certain type (say an unsigned int for an age value), then why accept any other type?  So unless you are on the Planet Hex, the string "abc" is not considered a valid number.  Any input that the user enters that does not conform to your expected range or type of value should be flagged as an error/warning to the user.

As for a union, it can be used as a "box" to hold various, overlapping, types of data, with the union being the size of the largest data member.  However that does not mean if you store the value 10, that this will magically be able to be interpreted as the string "10" or "ten".

---

### Post by Tony Flury on 2013-02-11
Bear in mind also that if you use a union it is up to you (the programmer) to keep track of what "type" of data that union now holds.

Although a union has a number of uses (for instance reading communication protocols can be done reaonably easily if you define unions), you should be really careful as relaying on a union could be a sign of poor design (especially in C as you are meant to know ahead of time what type your data is).

If you really need dynamic typing - then look at python, but even then mixing types can cause lots of unseen and un-announced logic errors, so it still needs handling with care.

---

### Post by muteXe on 2013-02-11
indeed.
my last company's coding standards forbade the use of unions for those reasons mentioned.

---

### Post by Warren Hill on 2013-02-11
You can use a union to do this sort of thing but you will need to keep track of what this is perhaps with a flag.

---

### Post by ofnuts on 2013-02-11
> **IAMTubby said:**
> Hello,
Is it possible in C to re-declare a member of a structure ?
As in, say I have a structure like,
```

typedef struct _TABLE
{
 int age;
 char* name;
}TABLE;

```Can I do something like
```

if(entered_age is not a number)
{
 redeclare int age as char* age;
 printf("\nyou entered %s which is not a valid age. Please enter a number",age);
}

```Thanks.
PS : The example in the scenario is not based on a requirement, I have just tried to create an example to explain my question.

There is no need to make the same variable play multiple roles. You can use several variables. This kind of scenario is normally handled by:

[LIST=1]
[*]having a short-lived char[] buffer to receive the user input
[*]convert the char[] into some int value, and store this in some long-lived int variable
[*]in case of errors, report the problem, showing the contents of the char[] variable
[/LIST]

---

