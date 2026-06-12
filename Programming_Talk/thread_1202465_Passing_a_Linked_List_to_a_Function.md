---
title: "Passing a Linked List to a Function"
date: 2009-07-02
forum: Programming Talk
---

### Post by shynthriir on 2009-07-02
Been playing with linked lists here and trying to clean up a small bit of code I have, the best way would be to break it up into a couple different functions, but this requires me to pass a linked list to a function. Here's some code bits and how I *think* I'm supposed to do it, but g++ gives me a compile error when I try to compile it.

This struct is in main().
```

  struct movie {
    string       name;     // movie name
    float        runtime;  // movie runtime (length) in minutes
    int          rating;   // user's person rating of movie (1/2/3/4/5)
    struct movie *next;    // pointer to the next struct in list
  };

```

For this example I want to have a function that prints the data from the list to the screen.

Function Protocall:
```

void printList(struct movie* firstInList, int listLength);

```

Function block:
```

void printList(struct movie* firstInList, int listLength);
  // loop priming
  struct movie* currentListItem = firstInList;
  cout << currentListItem -> name    <<               endl;
  cout << currentListItem -> runtime << " Minutes" << endl;
  cout << currentListItem -> rating  << " Stars"   << endl << endl;
  // end of loop priming
  for (int i = 1; i < listLength; i++) {
    currentListItem = currentListItem -> next;
    cout << currentListItem -> name    <<               endl;
    cout << currentListItem -> runtime << " Minutes" << endl;
    cout << currentListItem -> rating  << " Stars"   << endl << endl;
  }
}

```

It complains about the void type on the function, which I know I can change to int (not sure why it doesn't like void type-returning functions honestly). But even if I change that to, say, int, the problem that I don't quite get relates to the

currentListItem -> name

bits. Part of me says it has something to do with scope, but I really don't know. Any help?

---

### Post by jowilkin on 2009-07-02
Well I don't know if it's just a copy and paste error, but the first line of your function ```
void printList(struct movie* firstInList, int listLength);
```
Should be ```
void printList(struct movie* firstInList, int listLength) {

```

---

### Post by Nemooo on 2009-07-02
If the struct is declred in main, it only exists in that function. If you want other structs to acces the struct, you have to declare it globally (or at least that's how it is in C):

```
struct movie {
    string       name;     // movie name
    float        runtime;  // movie runtime (length) in minutes
    int          rating;   // user's person rating of movie (1/2/3/4/5)
    struct movie *next;    // pointer to the next struct in list
};

void function(struct movie *n)
{
    // do something
}

int main()
{
    struct movie *p;

    function(p);
}
```

What's the exact error message?

---

### Post by shynthriir on 2009-07-02
Yeah, that was just a total copy paste error.
Actual problem still exists though.

---

### Post by shynthriir on 2009-07-02
@Nemooo

Is there any way to do it without using global variables? I thought of that, but I seem to remember a couple people telling me I should always avoid global variables unless absolutely necessary.

Check back in a minute and I'll have error message, sorry, didn't see that request.

A2.cpp:104: error: invalid use of incomplete type &#8216;struct movie&#8217;
A2.cpp:16: error: forward declaration of &#8216;struct movie&#8217;

This happens for each instance of currentListItem -> (struct item)

---

### Post by Nemooo on 2009-07-02
You don't declare the variable to be global, it's still declared in main and then passed to another function. It's just the struct "prototype" you have to declare in a global scope.

[http://cplusplus.com/doc/tutorial/structures/](http://cplusplus.com/doc/tutorial/structures/)

---

### Post by shynthriir on 2009-07-02
Okay, that makes more sense, thank you. classes/structs/dynamic data are all things to me and I've having a lot of fun playing around with them.

My program actually already fits the requirement of the assignment, but I'm having a blast making the program better and more efficient.

Thanks.

---

### Post by Nemooo on 2009-07-02
And from what I gather from the error message, what I said should fix your problem, but post back when you've tried it.

---

### Post by shynthriir on 2009-07-02
Problem's Fixed! Thanks. Was able to apply the same concept for a couple different functions to help organise my code better. I appreciate the quick help.

---

