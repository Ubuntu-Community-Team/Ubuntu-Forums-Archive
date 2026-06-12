---
title: "pointers in c are confusing me."
date: 2007-10-23
forum: Programming Talk
---

### Post by jordanmthomas on 2007-10-23
[PHP]Person *temp = head;
printf("what is wrong with head id %s\n",head -> id);[/PHP]

I'm hoping there is a simple explanation for this:
If I remove the first line in this snippet of code, the next line prints what I'd expect
```
what is wrong with head id 111222333
```
If I have the first line there, however, it's like it wipes out what's in what head points to:
```
what is wrong with head id
```

Is there anything obvious I should check?  I am banging my head on tables at the moment (haven't programmed in c for a while so I hope it's something I am missing)

---

### Post by yabbadabbadont on 2007-10-23
I'm assuming that id is a field in the Person struct.  Also assuming that there are no lines of code between the two you have provided, the id field is never initialized with any value.  You are probably just lucky that it has NULL in it, otherwise you would most likely get either a memory access violation or a segmentation fault.  ;)

Edit: just re-read your post.  If it works when you remove the first line that declares the head pointer, then that must mean that head is already defined and initialized in an outer scope and your declaration is overriding it with a local variable (which is uninitialized).

---

### Post by Compyx on 2007-10-23
You need to post your code. The problem lies somewhere else, not in the snippet you've posted.

---

### Post by jordanmthomas on 2007-10-23
Yes, id is a field in the Person struct, and there's no lines here.
What I don't get, though, is why it works as long as I don't add a new pointer to head (which I need to do so I can go through a linked list).

I guess what I'm asking now is this:  if whatever head is pointing to has a value for id, why does it not after a pointer is made to head?  Forgive me if I'm being stupid.  :)

**edit** didn't see compyx's post:  I'll try to gather up the relevant sections and be right back.

---

### Post by jordanmthomas on 2007-10-23
First off, head is a global variable, as is numPeople
[PHP]
struct Person
{
	char* firstName;
	char* lastName;
	char* id;	//ssn
	char* houseNum;
	char* streetName;
	char* cityName;
	char* stateName;
	char* zip;
	struct Person* next;
};
typedef struct Person Person;
Person* head;
int numPeople = 0;[/PHP]

Ok, here's where I am putting together a Person struct named addMe and pointing head to it:
[PHP]Person* addMe = (Person*)malloc(sizeof(Person));
addMe -> lastName = lastName;
addMe -> id = id;
addMe -> houseNum = houseNum;
addMe -> streetName = streetName;
addMe -> cityName = cityName;
addMe -> stateName = stateName;
addMe -> zip = zip;
addMe -> next = NULL;
[/PHP]
and then, I set head to point to addMe:
[PHP]
if(numPeople == 0)
{
	//case of first item
	head = addMe;
	tail = addMe;
	numPeople++;
	return "Add_Person_Ack | First person added successfully";
}
else
{
	//not first person
	tail -> next = addMe;
	tail = addMe;
	numPeople++;
	return "Add_Person_Ack | Subsequent person added successfully";
}
[/PHP]

After setting head above, I can reference any field I need with
```
head -> whatever
```

This and the snippet I posted earlier are the only place I do anything with head.

---

### Post by jordanmthomas on 2007-10-23
I have fixed the problem.  (Not 100% sure what was wrong, but it's working for now)
Thanks for the consideration.  If I ever find out what I did to fix it, I'll post back.

---

### Post by dwhitney67 on 2007-10-23
> **jordanmthomas said:**
> 
[PHP]Person* addMe = (Person*)malloc(sizeof(Person));
addMe -> lastName = lastName;
addMe -> id = id;
addMe -> houseNum = houseNum;
addMe -> streetName = streetName;
addMe -> cityName = cityName;
addMe -> stateName = stateName;
addMe -> zip = zip;
addMe -> next = NULL;
[/PHP]

What's "confusing" to me is how you were able to pull off the assignments above for the char pointer strings without using a strdup() or strndup().

Is this the area of your code that you fixed?

---

### Post by mjwood0 on 2007-10-23
> **dwhitney67 said:**
> What's "confusing" to me is how you were able to pull off the assignments above for the char pointer strings without using a strdup() or strndup().

Is this the area of your code that you fixed?

I'm guessing it's working because he hasn't overwritten the stack with anything else.

From what I can tell, he's setting the pointers to addresses of local variables.  Not going to work correctly.

The other thing that's confusing to me is this:
```
typedef struct Person Person;
```

What exactly are you trying to do with this?

I've said it before and I'll say it again -- there needs to be consistent naming throughout your code, especially in a language such as C.  Defining all your types as PERSON_TYPE or something will help to make things much less confusing as then you'll know exactly what it is.

Glad to hear you got it working.

---

### Post by jordanmthomas on 2007-10-23
> From what I can tell, he's setting the pointers to addresses of local variables. Not going to work correctly.
After sleeping on it, that's the conclusion I came to as well.

> **dwhitney67 said:**
> Is this the area of your code that you fixed?
It is, I think that I wasn't allocating any space to the parts of addMe and I just got lucky that it even worked once.  

> ```
typedef struct Person Person;
```What exactly are you trying to do with this?
With that line, I can type something like this
```
Person* someone
```
instead of ```
struct Person* someone
```

> I've said it before and I'll say it again -- there needs to be consistent naming throughout your code,
Well, my naming is consistent for my own code, but I suppose it could be problematic if there was more than one person working on it.  What's inconsistent about my naming (or is it just that it's not how other people would name things)?

Anyway, I really appreciate the help.  (me <-- not the biggest fan of c, which is why I haven't used it in a while)

---

