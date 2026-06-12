---
title: "[SOLVED] Dumb C++ Question"
date: 2008-03-02
forum: Programming Talk
---

### Post by t3hi3x on 2008-03-02
Ok. This is pissing me off. I am trying to read the arguments from an application and it isn't working. If I had a better explanation that I'd tell ya :)

Here's the exerpt:

[PHP]	//all the possible arguments
	string AdminName;
	string AdminPwd;
	string Username;
	string Password;
	string FullName;
	string Email;
	char* maxRows;
	char* adminYN;

	int j;
	
	cout << argc << endl; //debug

	for(j = 2; j < argc; j++)
	{
	cout << argv[j] << endl;  //debug

		if ( argv[j] == "-w" )
		{
			AdminName = argv[j + 1];
			cout << AdminName << endl;
			//continue;
		}
		if ( argv[j] == "-q" )
		{
			AdminPwd = argv[j + 1];
			cout << AdminPwd << endl << MD5(AdminPwd) << endl;
			//continue;
		}		
		if ( argv[j] == "-u" )
		{
			Username = argv[j + 1];
			cout << Username << endl;
			//continue;
		}
		if ( argv[j] == "-p" )
		{
			Password = argv[j + 1];
			cout << Password << endl << MD5(Password) << endl;
			//continue;
		}
		if ( argv[j] == "-n" )
		{
			FullName = argv[j + 1];
			cout << FullName << endl;
			//continue;
		}
		if ( argv[j] == "-m" )
		{
			Email = argv[j + 1];
			cout << Email << endl;
			//continue;
		}
		if ( argv[j] == "-r" )
		{
			maxRows = argv[j + 1];
			cout << maxRows << endl;
			//continue;
		}
		if ( argv[j] == "-b" )
		{
			adminYN = argv[j + 1];
			cout << endl << endl << "adminYN" << adminYN << endl;
			//continue;
		}[/PHP] 

When I run: ```
./ttuser --add -q alexb -w blynne -u bob -p wooo -m alexb@teraTunes.org -r 10000 -b y

```

I get:

```
16
-q
alexb
-w
blynne
-u
bob
-p
wooo
-m
alexb@teraTunes.org
-r
10000
-b
y

```

the -b argument should be showing me y here, but it isn't. Is there something I'm missing??

lol sorry I know this a dumb question.

---

### Post by jpeddicord on 2008-03-02
It's not really a dumb question; I'm stumped by it.

As another debugging measure, add
```
cout << "output -b value!" << endl;
```
just after ```
if ( argv[j] == "-b" )
        { 
```and see if you get anything. I see the Y after the -b, but what stumps me is why ```
 cout << endl << endl << "adminYN" << adminYN << endl; 
```isn't running.

Try cleaning out any .o files you may have and recompiling, just to be sure you aren't using stale files.

---

### Post by WW on 2008-03-02
The argv array is an array of C strings, not C++ strings, so you can't use ==.  Try using strcmp() instead.  E.g.   if (strcmp(argv[j],"-b") == 0) ...

---

### Post by t3hi3x on 2008-03-02
> **WW said:**
> The argv array is an array of C strings, not C++ strings, so you can't use ==.  Try using strcmp() instead.  E.g.   if (strcmp(argv[j],"-b") == 0) ...

Interesting. This does indeed make sense; however, I did not know you could not compare char* with "x" using ==.

Why is this? Sorry, I am just curious to why this is.

Thanks a lot, that sure did fix the thing. I cheated and made a function that streams the string so to_string(x) == "x" :)

That works.

---

### Post by WW on 2008-03-02
A "string" in C is just a character pointer.  Also, a string constant such as "-b" is effectively a pointer to a piece of memory that contains the characters '-', 'b', and a zero.  So when you say **if (argv[j] == "-b")**, you are really comparing two pointers, and these pointers point to different memory locations, so the test is never true.

> Thanks a lot, that sure did fix the thing. I cheated and made a function that streams the string so to_string(x) == "x"
Or you could do this:
```

for (j = 2; j < argc; j++)
{
    string arg(argv[j]);
    if (arg == "-w")
    {
    ...
    }
    else if (arg == "-q")
    {
    ...
    }
    else if ...
}
```

---

### Post by LaRoza on 2008-03-02
> **t3hi3x said:**
> Interesting. This does indeed make sense; however, I did not know you could not compare char* with "x" using ==.

Why is this? Sorry, I am just curious to why this is.


C strings are just character arrays that are terminated with the '\0' character. To compare them with the == operator, you use just comparing the pointer address, &name[0], assuming that char * name = "String". To compare the string itself, you have to loop over each character or address.

[php]
strcmp(char * string1, char * string2)
{
    for (;*string1 == *string2;string1++, string2++)
    {
        if (*string1 == '\0')
        {
            return 0;
        }
    }
    return *string1 - *string2
}
[/php]

---

### Post by t3hi3x on 2008-03-02
> **LaRoza said:**
> C strings are just character arrays that are terminated with the '\0' character. To compare them with the == operator, you use just comparing the pointer address, &name[0], assuming that char * name = "String". To compare the string itself, you have to loop over each character or address.

[php]
strcmp(char * string1, char * string2)
{
    for (;*string1 == *string2;string1++, string2++)
    {
        if (*string1 == '\0')
        {
            return 0;
        }
    }
    return *string1 - *string2
}
[/php]

Wow. That is an interesting way to tackle that problem. Oh well, I guess that's why they implemented the string.h class into C++ :)

Thanks for the C lesson.

---

### Post by nuggien on 2008-03-02
> **t3hi3x said:**
> Interesting. This does indeed make sense; however, I did not know you could not compare char* with "x" using ==.

Why is this? Sorry, I am just curious to why this is.

Thanks a lot, that sure did fix the thing. I cheated and made a function that streams the string so to_string(x) == "x" :)

That works.

in both C and C++, 'char* x' is simply a pointer to the beginning of a character buffer.  It is not the string itself.  Therefore when you do if (x == "foo")  you are really comparing the address of one variable with an anonymous buffer, instead of comparing two strings as desired.  strcmp() knows to look at each character at the specified buffers and will of course give you the correct results.  

Also, C++ strings have an overloaded == operator so if you did if (x == "foo") where x is a C++ string object, the compiler will probably turn "foo" into a C++ string (call it bar for example) and then call x.operator==(bar), which will do a strcmp() underneath.

Hope it helps.

---

### Post by nuggien on 2008-03-02
Looks like people beat me to my response.  Way too many people on this forum :)

---

### Post by t3hi3x on 2008-03-02
> **nuggien said:**
> ...Way too many people on this forum :)

That is NEVER a problem lol.

Actually having more than one explanation always helps. This is kinda neat though. It helps me to understand the classes in C++.

---

