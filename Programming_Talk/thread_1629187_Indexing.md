---
title: "Indexing"
date: 2010-11-23
forum: Programming Talk
---

### Post by denarced on 2010-11-23
Hei,

anyone know any library or something like that with which I could achieve fast searching. In other words binary search, indexing and so on..

Ideas ?

---

### Post by denarced on 2010-11-23
Language could be c, c++ or python

---

### Post by worksofcraft on 2010-11-23
> **denarced said:**
> Language could be c, c++ or python

The C++ standard template library transparently incorporates search algorithms in containers like "map" and "set".

p.s.: "An expert is a person who has made all the mistakes that can be made in a very narrow field" -Nils Bohr

:shock: I always thought a "spurt" was a drip under preasure and ex meant "has been", so now you shed new light on the meaning expurt for me ;)

---

### Post by denarced on 2010-11-23
> **worksofcraft said:**
> The C++ standard template library transparently incorporates search algorithms in containers like "map" and "set".

Hmm, I checked map and set. Both have a method called find:
[LIST]
[*] [http://www.cplusplus.com/reference/stl/set/find/]("http://www.cplusplus.com/reference/stl/set/find/")
[*] [http://www.cplusplus.com/reference/stl/map/find/]("http://www.cplusplus.com/reference/stl/map/find/")
[/LIST]
Both in complexity are equal to size. Maybe I could go around that somehow?

---

### Post by worksofcraft on 2010-11-23
> **denarced said:**
> Hmm, I checked map and set. Both have a method called find:
[LIST]
[*] [http://www.cplusplus.com/reference/stl/set/find/]("http://www.cplusplus.com/reference/stl/set/find/")
[*] [http://www.cplusplus.com/reference/stl/map/find/]("http://www.cplusplus.com/reference/stl/map/find/")
[/LIST]
Both in complexity are equal to size. Maybe I could go around that somehow?

It depends what you are trying to find.
When you create a map you specify what kind of value to use as the key. Like typically you might use a text string as the key to a map.
You can then simply use one of those values (e.g. text string) to find the entry in the map and it does all your searching for you in a most efficient way e.g.

[php]

// g++ stlmap.cpp
// ./a.out spider
#include <cstdio>
#include <cstring>
#include <map>

using namespace std;

// A class for comparing char strings this is used by STL map classes
struct lt_charptr {
	bool operator()(const char *s1, const char *s2) const { return strcmp(s1, s2) < 0; }
};

int main(int argc, char *argv[], char *envp[]) {
	map<const char *, const char *, lt_charptr> aMap;
	aMap.insert(pair<const char *, const char *>("aardvark", "comes early in the dictionary"));
	aMap.insert(pair<const char *, const char *>("elephant", "is big"));
	aMap.insert(pair<const char *, const char *>("spider", "is creepy"));
	aMap.insert(pair<const char *, const char *>("snake", "is poisonous"));
	aMap.insert(pair<const char *, const char *>("frog", "says ribbet"));

	const char *pFindMe = "elephant";
	if (argc > 1) pFindMe = *++argv;

	return !printf("%s %s\n", pFindMe, aMap[pFindMe]); 
}
[/php]

see on that last line I just index it by it's key then it looks it up and returns the associated value from the map.

p.s. My understanding is that** std::map uses a "self balancing tree" while std:hash_map uses a hash table** to "find" the index, but I haven't done any metrics to see how efficient it is.

---

### Post by DanielWaterworth on 2010-11-24
I recently came across Tokyo Cabinet which describes itself as the new DBM. If you ever want to work from disk then I'd recommend it. [http://fallabs.com/tokyocabinet/](http://fallabs.com/tokyocabinet/)

---

### Post by nasul on 2010-11-24
C++ I think is better.

---

### Post by denarced on 2010-11-24
> **DanielWaterworth said:**
> I recently came across Tokyo Cabinet which describes itself as the new DBM. If you ever want to work from disk then I'd recommend it. [http://fallabs.com/tokyocabinet/](http://fallabs.com/tokyocabinet/)

Interesting. Not exactly what I was looking for but I didn't know about DBM before.

This is a prime example why people should reply even if they don't have the exact answer that's needed.

Thanks.

---

### Post by denarced on 2010-11-24
> **nasul said:**
> C++ I think is better.

Better than what ?

---

