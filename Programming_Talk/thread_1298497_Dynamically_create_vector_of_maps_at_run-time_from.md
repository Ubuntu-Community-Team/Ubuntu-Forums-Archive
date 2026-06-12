---
title: "Dynamically create vector of maps at run-time from config file"
date: 2009-10-22
forum: Programming Talk
---

### Post by trparacyte on 2009-10-22
Hey Programming Talk,
 
EDIT:: Look to third post for revised question. This one was a mess. =]

---

### Post by dwhitney67 on 2009-10-23
Could you please rephrase what you are hoping to accomplish?  Perhaps if you posted your configuration file (w/o any comments) and less pseudo-code would help.

Btw, if all you are expecting from the configuration file that there exists a Key with multiple Values, then what you may want to consider any of the following:

1.  A multi-map  (std::multimap<KeyType, ValueType>)

or

2.  A map of vectors (std::map<KeyType, std::vector<ValueType> >)

---

### Post by trparacyte on 2009-10-23
Heh. Sorry for being so vague, after I posted that I sort of improved on my earlier idea. It was extremely ugly at first.
 
Essentially, I need to read values from a configuration file, seperated by line, whitespace, commas, etc. Haven't decided which. Those values go into a vector which I iterate over in order to get the variable names.
```

std::vector<std::string> ConfVariables;
// Read config file, store values in ConfVariables

```
 
To store the actual data, I create a map of <string, map<string, string>>. Would it be better to create the map as ```
map<string, map<string, string>>
``` or should I create a seperate map for each user and pass it as a pointer to the second map, like ```
map<string, *map<string,string>> RootMap//first map, holds users
map<string, string> User1Variables;
RootMap.insert(make_pair("User1", *User1Variables);

```
 
I guess that's what my question is now.

---

### Post by dwhitney67 on 2009-10-23
> 
Essentially, I need to read values from a configuration file, seperated by line, whitespace, commas, etc. Haven't decided which. Those values go into a vector which I iterate over in order to get the variable names.


You barely scratched the surface of what you _need_ to do, and immediately jumped in with what you think the solution should be.

Since I haven't a clue of what your data looks like, much less what you need to do with it, for now, I will give you a simple, yet complex answer...

42

---

### Post by trparacyte on 2009-10-23
Sorry, I tend to do that a lot.
My config file:
```

test1
test2
test3
test4

```
 
For right now, I'm just shooting data at the program through command-line arguments instead of a network. Such as
```

./testprogram hello world one two

```
 
I need to open the file, read each line, and for each word on the line, I need to pop it onto a vector<string>.
 
Next, I need to initialize a map of maps.
 
```

map<string, map<string,string>>;

```
 
For each value in the vector<string> of config variables, I need to use the value from the vector as the key in the second map.
 
```

Map Example:
User1 //string from map<**string**, map<string,string>>
  Map 2
    test1 // variable from vector<string> and config file map<string, map<**string**, string>>
       hello // value from CLI arg passing map<string, map<string, **string**>>
 

```
 
I'm just inquiring as to the efficiency of this now, if that makes any more sense.

---

### Post by dwhitney67 on 2009-10-23
The vector<string> sounds ok.

I still do not understand where the Keys for the map(s) are coming from.  You mentioned Users, but I do not know where/how these come into play.  How you obtain the key (eg. test1) for the second (internal) map also is not clear.

Are you attempting to collect user-names, process-names, and the command-line args that go with them??

As far as efficiency is concerned, you will get bitten if you pass your vector and/or map around by value to a function.  Make sure that you pass it by reference so that you avoid creating duplicate objects on the stack.  So far from what I have understood, I do not think you will need to allocate memory from the heap, unless you are dealing with large amounts of data (> 8 MB).

---

### Post by trparacyte on 2009-10-23
I'm gathering the keys for the root map by gleaning usernames from users. User1, User2, User3, etc., from a login process or just the request being sent to the server. The keys for the second, internal map are the variable names outlined in the config file. The config file defines the data the application wishes to store. Keep in mind it's part of a framework, and not an application itself.

---

### Post by dwhitney67 on 2009-10-23
I don't see an issues then.  Just be careful not to pass your containers by value, should you fling it around from one function to another.

---

### Post by trparacyte on 2009-10-23
Alright, thanks much. =]

---

### Post by Can+~ on 2009-10-23
> **dwhitney67 said:**
> Since I haven't a clue of what your data looks like, much less what you need to do with it, for now, I will give you a simple, yet complex answer...

42

[http://www.wolframalpha.com/input/?i=The+Answer+to+the+Ultimate+Question+of+Life,+the+Universe,+and+Everything](http://www.wolframalpha.com/input/?i=The+Answer+to+the+Ultimate+Question+of+Life,+the+Universe,+and+Everything)

---

