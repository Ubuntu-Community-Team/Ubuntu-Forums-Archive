---
title: "[C++] Custom ordering of map elements"
date: 2011-11-10
forum: Programming Talk
---

### Post by erotavlas on 2011-11-10
Hi,

I have a question about the map container. I would like to order the elements inside the map in custom way. I have tried with this
```

struct classcomp
{
    bool operator() (const std::string& lhs, const std::string& rhs) const
    {
        return lhs.length() <= rhs.length();
    }
};
map<string,int,classcomp> map;                 // class as Compare

```
It works well only if I access to the map with a for loop with iterator, but if I try the direct access like [] or at operator it doesn't work.  For example
```

  map["a"]=10;
  map["ab"]=30;
  map["b"]=50;
  map["c"]=70;
 
  std::cout << map["c"] << map.at("c") <<  std::endl;

```
Why?

Thank you

---

### Post by karlson on 2011-11-10
> **erotavlas said:**
> Hi,

I have a question about the map container. I would like to order the elements inside the map in custom way. I have tried with this
```

struct classcomp
{
    bool operator() (const std::string& lhs, const std::string& rhs) const
    {
        return lhs.length() <= rhs.length();
    }
};
map<string,int,classcomp> map;                 // class as Compare

```
It works well only if I access to the map with a for loop with iterator, but if I try the direct access like [] or at operator it doesn't work.  For example
```

  map["a"]=10;
  map["ab"]=30;
  map["b"]=50;
  map["c"]=70;
 
  std::cout << map["c"] << map.at("c") <<  std::endl;

```
Why?

Thank you

You might want to post the entire code and the explanation for "doesn't work".

There are multiple issues with this code which I am not gonna go into, but the biggest problem is actually logic.

When you do the comparison based on length the element returned for key "c" when you do a lookup would be the same as for key "a".  The only difference is that "a" != "c" for obvious reasons so the key doesn't match so you can't get the value of map["c"]

---

### Post by erotavlas on 2011-11-10
Ok, I'm sorry.
This is my code
```

// constructing maps
#include <iostream>
#include <map>
using namespace std;

struct ClassCompare
{
    bool operator() (const std::string& lhs, const std::string& rhs) const
    {
        return lhs <= rhs;
    }
};

bool FunctionCompare (std::string lhs, std::string rhs)
{
    return lhs <= rhs;
}

int main ()
{
  map<string,int,ClassCompare> Map;                 // class as Compare

  Map["a_0"]=10;
  Map["a_13"]=30;
  Map["a_1"]=50;
  Map["a_10"]=70;
  map<string,int,ClassCompare>::const_iterator it = Map.begin();

  std::cout << Map["a_10"] << std::endl;
  std::cout << Map[it->first] << std::endl;
  
for(map<string,int,ClassCompare>::const_iterator jt = fourth.begin(); jt != fourth.end(); ++jt)
  {
     std::cout << jt->first << " " << jt->second << std::endl;
  }
  return 0;
}

```How can I do to compare the key of the map?

---

### Post by karlson on 2011-11-11
> **erotavlas said:**
> How can I do to compare the key of the map?

First off why would you need a custom comparator for strings?
Second why are you comparing <=?

I still think that your comparator makes a map give you a different iterator from the one you are seeking.  I would suggest running it in the debugger and see what values it returns when you call []

---

### Post by ofnuts on 2011-11-11
If you want to iterate the map in key order, maintain a sorted list of keys on the side, and iterate that list to get the keys to access the map objects...

---

### Post by karlson on 2011-11-11
> **ofnuts said:**
> If you want to iterate the map in key order, maintain a sorted list of keys on the side, and iterate that list to get the keys to access the map objects...

I think the issue here is a actually random access using key.  The problem is that the search returns iterator that doesn't point to the key.

---

### Post by erotavlas on 2011-11-21
> **karlson said:**
> First off why would you need a custom comparator for strings?
Second why are you comparing <=?

I still think that your comparator makes a map give you a different iterator from the one you are seeking.  I would suggest running it in the debugger and see what values it returns when you call []

Hi,
I have ran my code in the debug and when I try to access to an element by the key, it gives 0;

```

struct ClassCompare
{
    bool operator() (const std::string& lhs, const std::string& rhs) const
    {
	return lhs <= rhs;
    }
};
 map<string,int,ClassCompare> fourth;                 // class as Compare

  fourth["name_0"]=10;

  std::cout << fourth["name_0"] << std::endl; // 0 value


```
I can only access by using the iterator. So my question, is there a way to order the key elements of the map even if they are string? 

Thank you

---

### Post by karlson on 2011-11-21
> **erotavlas said:**
> 
I can only access by using the iterator. So my question, is there a way to order the key elements of the map even if they are string? 

Thank you

Use the default comparator which is std::less<>.  That will order the std::string's for you.

---

### Post by erotavlas on 2011-11-24
> **karlson said:**
> Use the default comparator which is std::less<>.  That will order the std::string's for you.


Thank you very much, simple and clever.

---

### Post by erotavlas on 2011-12-19
Hi,

I have reopened this thread because the problem is not solved. I cannot use the default comparator less. For instance the following strings are compared in wrong way: "Name_12" and "Name_2". The first one is considered smaller than the second one. How can I do?

Thank you

---

### Post by ofnuts on 2011-12-19
> **erotavlas said:**
> Hi,

I have reopened this thread because the problem is not solved. I cannot use the default comparator less. For instance the following strings are compared in wrong way: "Name_12" and "Name_2". The first one is considered smaller than the second one. How can I do?

Thank youIn dictionary order, which is how strings are compared, "Name_12" is indeed smaller than "Name_2" (but would be bigger than "Name_02"). Either you change your string specifications, or write your own comparator.

---

### Post by erotavlas on 2011-12-20
Hi,
I have written this snippet of code that tries to realize what I want...

```

struct ClassCompare
{
    bool operator() (const std::string& lhs, const std::string& rhs) const
    {
        unsigned pos = lhs.find_first_of("_");             
        int left = 0;
	if (pos == static_cast<unsigned int> (std::string::npos))
	std::cout << "Check the name" << std::endl;
	else         
	{
	std::string lValue = lhs.substr(pos + 1, lhs.length());
	unsigned new_pos = lValue.find_first_of("_");
	if (new_pos != static_cast<unsigned int> (std::string::npos))
           lValue = lValue.substr(0, new_pos); 

        left = FromString<int>(lValue);
        }
        pos = rhs.find_first_of("_"); 
        int right = 0;
	if (pos == static_cast<unsigned int> (std::string::npos))
        std::cout << "Check the name" << std::endl;
	else 
        {
        std::string rValue = rhs.substr(pos + 1, rhs.length());
	unsigned new_pos = rValue.find_first_of("_");
	if (new_pos != static_cast<unsigned int> (std::string::npos))
           rValue = rValue.substr(0, new_pos); 
   
        right = FromString<int>(rValue);
        }        
	return (left < right);

    }
};

```
It works well for the words "Name_number" and now the two words of the example ("Name_12" and "Name_2") are correctly split. But if I have a new word a little bit more complicated like "Name_number_number" it does not work. Indeed the word "Name_12" and "Name_1" are recognized as the same word.
How can I do?

Thank you

---

### Post by ofnuts on 2011-12-20
> **erotavlas said:**
> Hi,
I have written this snippet of code that tries to realize what I want...

]It works well for the words "Name_number" and now the two words of the example ("Name_12" and "Name_2") are correctly split. But if I have a new word a little bit more complicated like "Name_number_number" it does not work. Indeed the word "Name_12" and "Name_1" are recognized as the same word.
How can I do?

Thank you

Write a workable spec first(*)... what kind of numbers are you going to accept? Is "Something2.012" smaller than "Something2.11"? In other words,  do you handle decimal numbers, or only integers? How do you handle 0-padded numbers? 

Something that can work is to create a sort key by replacing any group of digits by a fixed-length (but how long?),  group of digits  that is left-padded with spaces, 0's, or else (is "42" same as "042"? bigger? smaller?) and use that for comparisons. This may require using a regular expression library such as Boost. If you do many comparisons (sorting...) you may want to store the key with the rest of the data. 


(*) Yes, this is programming: see Robert Martin's stance on the subject:[ "We will never be rid of code, because code represents the details of the  requirements. At some level those details cannot be ignored or  abstracted; they have to be specified. And specifying requirements in  such detail that a machine can execute them *is programming*."]("http://www.informit.com/articles/article.aspx?p=1235624") (click for full article, or find his "Clean code" book)

---

### Post by erotavlas on 2011-12-20
> **ofnuts said:**
> Write a workable spec first(*)... what kind of numbers are you going to accept? Is "Something2.012" smaller than "Something2.11"? In other words,  do you handle decimal numbers, or only integers? How do you handle 0-padded numbers? 

Something that can work is to create a sort key by replacing any group of digits by a fixed-length (but how long?),  group of digits  that is left-padded with spaces, 0's, or else (is "42" same as "042"? bigger? smaller?) and use that for comparisons. This may require using a regular expression library such as Boost. If you do many comparisons (sorting...) you may want to store the key with the rest of the data. 


(*) Yes, this is programming: see Robert Martin's stance on the subject:[ "We will never be rid of code, because code represents the details of the  requirements. At some level those details cannot be ignored or  abstracted; they have to be specified. And specifying requirements in  such detail that a machine can execute them *is programming*."]("http://www.informit.com/articles/article.aspx?p=1235624") (click for full article, or find his "Clean code" book)

I'm sorry if I don't explained well. I need to build a sorted map where the key element are as the following type:
1) string composed by a fixed keyword "Name" and a chaining of numbers separated by the underscore char "_number_number_..._number". The numbers are all integer. For instance "Name_number_number" -> "Name_2", "Name_1", "Name_12", "Name_2_12"
2) I want to sort the map in such way the smaller numbers are in top positions. The problem are the chained numbers as "Name_2_34" and "Name_2". How can I compare them?

Thank you

---

### Post by karlson on 2011-12-20
> **erotavlas said:**
> I'm sorry if I don't explained well. I need to build a sorted map where the key element are as the following type:
1) string composed by a fixed keyword "Name" and a chaining of numbers separated by the underscore char "_number_number_..._number". The numbers are all integer. For instance "Name_number_number" -> "Name_2", "Name_1", "Name_12", "Name_2_12"
2) I want to sort the map in such way the smaller numbers are in top positions. The problem are the chained numbers as "Name_2_34" and "Name_2". How can I compare them?

Thank you

How deep does chaining go?  Can the strings be of the form <string>_number_<string>_number?

The simplest way I can think of is to tokenize the string into a struct and then compare the structs elementwise to determine the lesser.

On top of this why would you want to sort the map in this fashion?

---

### Post by ofnuts on 2011-12-20
> **erotavlas said:**
> I'm sorry if I don't explained well. I need to build a sorted map where the key element are as the following type:
1) string composed by a fixed keyword "Name" and a chaining of numbers separated by the underscore char "_number_number_..._number". The numbers are all integer. For instance "Name_number_number" -> "Name_2", "Name_1", "Name_12", "Name_2_12"
2) I want to sort the map in such way the smaller numbers are in top positions. The problem are the chained numbers as "Name_2_34" and "Name_2". How can I compare them?

Thank youOK, so we are dealing with integers only and a fixed separator, and my technique still holds... 

Another solution is to cut the name string on the underscores and generate a composite key made of the root string and a vector of ints. Then to compare items you first compare the root strings and if they are equal you walk down the vectors of ints comparing each with the one at the same index in the other item.

---

