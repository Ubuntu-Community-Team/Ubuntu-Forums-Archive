---
title: "Question on strings in C++"
date: 2008-02-22
forum: Programming Talk
---

### Post by mahy on 2008-02-22
Hi y'all, this should be quite simple:

i need to check if a given string ends with a sequence ".P". What's the simplest way to do it in C++?

TIA for any advice...

---

### Post by lnostdal on 2008-02-22
maybe you can figure it out on your own based on this [http://www.cppreference.com/cppstring/index.html](http://www.cppreference.com/cppstring/index.html)

---

### Post by pedro_orange on 2008-02-22
Somethin' like:

```

bool end_in_dotp(const string& somestring)
{
typdef string::size_type e = somestring.end()-2;
return (find(somestring.begin(), somestring.end(), ".p"))==e)
}

```

? :)

Or you could just use indices to check the last 2 parts of the string.

---

### Post by Zugzwang on 2008-02-22
> **pedro_orange said:**
> Somethin' like:

```

bool end_in_dotp(const string& somestring)
{
typdef string::size_type e = somestring.end()-2;
return (find(somestring.begin(), somestring.end(), ".p"))==e)
}

```

? :)

No! This (BTW: does it compile?) will check if the first occurrence of ".p" in a string is at the end. So ".p.p" wouldn't be matched. 

> **pedro_orange said:**
> 
Or you could just use indices to check the last 2 parts of the string.

That's far better (and normally faster as well).

---

### Post by pedro_orange on 2008-02-22
Probably not, I just did it from memory.

You're correct about it not matching ".p.p" I did not think of that. Suppose you could start at the end, and iterate backwards.
I post on here during downtimes at work, so I don't really think things through.

---

### Post by mahy on 2008-02-23
I tried several approaches, none of them is perfect. Moreover, i don't have a C++ string, but a char[] (zero-terminated)

This always works, but isn't very neat:

```
if ((mystring[strlen(mystring)-1] == 'P') && (mystring[strlen(mystring)-2] == '.'))
```

This is very neat, but also succeeds if ".P" only occurs in the middle of the string:

```
if (strstr(mystring, ".P") != NULL)
```

On the other hand, the following fails if it finds ".P" anywhere else than at the end:

```
if (((token = strstr(mystring, ".P")) != NULL) && (strlen(token) == 2))
```

The following works in most cases, but doesn't work on strings referenced by a pointer to a structure (mystructure->mystring):

```
if  (strcmp(mystring + strlen(mystring) - 2, ".P") == 0)
```

The following doesn't work on my Tru64 Unix where i need it (substr() is not implemented there):

```
if (strcmp(substr(mystring, strlen(mystring)-2), ".P") == 0)
```

Next, rfind() isn't applicable for type char[], rindex() only searches for a single character, not a substring... It seems there's no easy and working way... :(

---

### Post by lnostdal on 2008-02-23
> 
The following doesn't work on strings referenced by a pointer to a structure (structure->mystring):

```
if (strcmp(mystring + strlen(mystring) - 2, ".P") == 0)
```


this works here .. why does it not work on your end? .. can paste some code?

---

### Post by stratavarious on 2008-02-23
.

---

### Post by laxmanb on 2008-02-23
you can use the function strstr() in string.h if you're allowed to use the standard functions.

---

### Post by mahy on 2008-02-23
> **lnostdal said:**
> this works here .. why does it not work on your end? .. can paste some code?

Dunno, i'll research it later... THX for the moment

---

### Post by mahy on 2008-02-23
> **stratavarious said:**
> ```


  if(  test.compare(TestFor) != 0 )
  cout<< "string does not contain .p"<< "\n";
  else
  cout<< "string contains .p" << "\n";

```

Sadly, this is not what i need. First, i have a char[] not a C++ string. Second, the string must END WITH ".P", not just contain it...

---

### Post by stratavarious on 2008-02-23
.

---

### Post by stratavarious on 2008-02-23
.

---

### Post by dempl_dempl on 2008-02-23
If you're already using C++ , convert **char***  to **string** temporary , and then return it back to char* ;


anyway, the method   ***find_last_of***  in std::string  class does your job.

---

### Post by stratavarious on 2008-02-24
.

---

### Post by dempl_dempl on 2008-02-24
Yeap.. sorry my bad :-)

here's something I usually use [ It's my utils library ]

```

#include <string>

using namespace std;
//Extracts file extension
string extractFileExt ( const string& fileName )
{
        string ext;
	for ( size_t i = fileName.find_last_of ( "." );i < fileName.length();i++ )
		ext.push_back ( fileName[i] );

	return ext;
}



```

having this,  you just say :

```


bool endsWithDotP(string fileName)
{
if( extractFileExt(fileName) == ".P")
  return true;
else
 return false;
}

```


Of course  in real code, you would use , uppercase/lowercase stuff.


Anyway,  if you pass an array of chars to this function (char*) , it will  work too,  because C++ string can automatically overload C strings ,as long as that C string is null-terminated, of course.

Example of  using my function:
```

if( endsWithDotP( "/home/beatle/my_fie.P") )
 cout << "Ends with .P ";

```

---

