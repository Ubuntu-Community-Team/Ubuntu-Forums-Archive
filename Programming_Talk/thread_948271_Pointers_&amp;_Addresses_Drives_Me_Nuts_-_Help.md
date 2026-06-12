---
title: "Pointers &amp; Addresses Drives Me Nuts - Help"
date: 2008-10-15
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-10-15
Just answer one, you do not have to answer them all.....Plz do a favor:
I can not learn anything new until i fully understand whats going on
what i'm doing now.

**************************************...
FIRST:

I have struct addrinfo *res;

cout<<res;
cout<<&res;

these two above produces two different addresses, why?

**************************************...
SECOND:

Based on the first question.

doing this:

cout<<*res;

Compiler throws an error! why this wouldn't work? *res! does not have an address? It does not exist?!

**************************************...
THIRD:

struct addrinfo hints;
struct addrinfo *res;
struct addrinfo *p;

hints.ai_family = AF_UNSPEC;
hints.ai_socktype = SOCK_STREAM;

//when status is success, a linked list of addrinfo structures is //returned in "res" parameter.

status = getaddrinfo(argv[1], NULL, &hints, &res);

So what i understand is:

res will be pointing to hints, because hints got all data, but res
have nothing. So upon success, res will be pointing to hints. In
other words, res will have an address of hints. But when i output addresses for a check, res address does not appear to be changed:

//after statues returns 0

cout<<&hints<<endl; //holds same address it had
cout<<&res<<endl; //holds same address it had

of course both have different addresses.

My question is: whats the point of returning linked list of
"res" when it actually does not have anything!

Remember: we only filled "hints", res is not filled with anything,
so "res" remained the same it has its same old address, and
its empty as we did not fill anything to it. Where is the effect
of the return then?!!
**************************************...

Please help, i teach myself, so i got no tutor.

Here is the complete code which you may find it useful to give the proper advice:

[http://beej.us/guide/bgnet/examples/showip.c](http://beej.us/guide/bgnet/examples/showip.c)

I hope to get some response :(

---

### Post by dribeas on 2008-10-15
> **f.ben.isaac@gmail.com said:**
> 
I have struct addrinfo *res;

cout<<res;
cout<<&res;
[QUOTE]

Assuming that you have acquired memory (with new):

[addrinfo] <--- [res] <--- &res

res is a pointer to addrinfo, &res is a pointer to the memory location where res resides.

[QUOTE=f.ben.isaac@gmail.com;5968305]
doing this:

cout<<*res;
[QUOTE]

Having the error would help. First assumption is that operator<< is not defined for addrinfo struct. You must provide the operator:

```

std::ostream& operator<< ( std::ostream& o, addrinfo const & a );

```

Also note that the pointer does not have memory by itself, you must have a pointer to a valid memory region (allocated with new or pointing to an existing addrinfo struct or you will get a segmentation fault.

[QUOTE=f.ben.isaac@gmail.com;5968305]
status = getaddrinfo(argv[1], NULL, &hints, &res);

So what i understand is:

res will be pointing to hints, because hints got all data, but res
have nothing. So upon success, res will be pointing to hints. In
other words, res will have an address of hints. But when i output addresses for a check, res address does not appear to be changed:


No. Internally getaddrinfo will malloc and initialize memory, creating a linked list, whose first element address is written into the last argument. Hints is a input only parameter, res is output only.

> **f.ben.isaac@gmail.com said:**
> 
My question is: whats the point of returning linked list of
"res" when it actually does not have anything!


If you initialize res to 0 before the function call and then you output the contents after the call you will see that res has changed.

> **f.ben.isaac@gmail.com said:**
> 
Remember: we only filled "hints", res is not filled with anything,
so "res" remained the same it has its same old address, and
its empty as we did not fill anything to it. Where is the effect
of the return then?!!


The address of res does not change, its contents do change. You have a base misconception: if you want to know where a pointer points, you don't use the address of operator (&), you use the address of operator to get a pointer into one element that already exists. If you use & over a pointer you will get the address of the pointer, not the address of the pointed element.

---

### Post by f.ben.isaac@gmail.com on 2008-10-15
Awesome, i get it now.

> if you want to know where a pointer points, you don't use the address of operator (&), you use the address of operator to get a pointer into one element that already exists. If you use & over a pointer you will get the address of the pointer, not the address of the pointed element.

Do you mean like that: cout<<res;? Can you show me an example on how to "use the address of operator to get a pointer into one element that already exists"?

---

### Post by f.ben.isaac@gmail.com on 2008-10-15
Can you explain to me why first output is 0 and second one is 2

status = getaddrinfo(argv[1], NULL, &hints, &res);
cout<<hints.ai_family<<endl;
cout<<res->ai_family<<endl;

output:

0
2

What i know is, linkedlist does not point to indexes such as 0, 1, 2 like array.

Sorry for the overloaded questions, but i must take it to the next step.

Thanks in advance

---

### Post by dwhitney67 on 2008-10-15
If you do not already have it, please install the man-pages:
```
sudo apt-get install manpages-devel
```

The read about getaddrinfo():
```
man getaddrinfo
```

Now, it seems that you question is specific as to why getaddrinfo() returns a value other than what you are expecting (for ai_family).  Read the man-page to deduce why, because unless you happen to tap somebody who is intimate with that library call and the results it produces, you probably will be shooting blanks.

Do you have a question about pointers?  You seemed to be confused earlier.

[PHP]
struct addrinfo   hints;
struct addrinfo * results = 0;

// fill in the hints...

if (getaddrinfo( ..., &hints, &results ) == 0)
{
  ...
  freeaddrinfo( results );
}
else
{
  // error
}
[/PHP]

The address of 'hints', which is a locally declared object is required.  The *address of a pointer*, for 'results' is required, because data needs to be returned to you.

When you deallocate 'results', you merely need to pass it by value (hence _not_ the address of the pointer).

With respect to your question, it is very possible that the 'ai_family' of the 'hints' you provided will be different from the value contained within 'results'.  But without direct experience with the getaddrinfo() call, much less with the values you are setting within 'hints', it is difficult to comment on why the values (0 and 2) are not what you expected.

---

### Post by f.ben.isaac@gmail.com on 2008-10-15
Solved .... Awesome members :)

---

### Post by nvteighen on 2008-10-16
> **dwhitney67 said:**
> If you do not already have it, please install the man-pages:
```
sudo apt-get install manpages-devel
```


Little correction: the package is actually called **manpages-dev** (at least in Hardy)

---

### Post by dwhitney67 on 2008-10-16
> **nvteighen said:**
> Little correction: the package is actually called **manpages-dev** (at least in Hardy)

Thank you.  I only womder WTFlock is this package not included in 'build-essentials'?

---

