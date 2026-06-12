---
title: "Doubt with hash_map in C++ STL"
date: 2008-11-04
forum: Programming Talk
---

### Post by darthshak on 2008-11-04
Hi.

I was using a hash table of characters for this codec that I was programming. However, this is my first brush with the hash_map structure defined in the STL.

Here's the code I'm using : 
```

#include <iostream>
#include <fstream>
#include <string>
#include <ctype.h>
#include <utility>
#include <ext/hash_map>
using namespace std;
using namespace __gnu_cxx;

struct eqchar {
	bool operator()(char c1, char c2)	{
		return c1 == c2;
	}
};

typedef hash_map<char,int,hash<char>,eqchar> table;
typedef pair<char,int> entry;

void findFrequency()	{
	table T; entry E;
	string str; table::iterator itr;
	ifstream file("sample.txt");
	for (int i = 0; i < 255; i++) {
		E.first = char(i);
		T.insert(E);
	}
	while (!file.eof())	{
		getline(file,str);
		for (int i = 0; i < str.size(); i++) {
			itr = T.find(str[i]); 
			(*itr).second += 1;
		}
	}
	file.close();
}

int main()	{
	findFrequency();
	return 0;
}

```

Well, the deal is in the line which says E.first = char(i). Now, the hash_map is a pair associative container of the form pair<key,data>. The problem is, by default, E.second assumes the value of 0. 

Now, if all the keys are associated with the value 0, the worst-case complexity of searching becomes O(n), which defeats the purpose of hashing. Or is there some internal mechanism of hash_map which prevents this from happening?

Would adding the line E.second = i make a difference?

---

### Post by kknd on 2008-11-04
The value of E.second doesn't matters, because the hash is calculed only with the key (E.first).

You will only have performance penalties when you have keys with the same hash.

---

### Post by alternatealias on 2008-11-04
Being that you are hashing based on a char and you populate the hash_map with all 256 entries, why not simply use an array and use the char as an index?

```

#include <iostream>
#include <fstream>
#include <string>
#include <ctype.h>
#include <utility>
using namespace std;
using namespace __gnu_cxx;

int entries[256];

void findFrequency()	{
	string str;
	ifstream file("sample.txt");
	for (int i = 0; i < 256; i++)
		entries[i] = 0;

	while (!file.eof())	{
		getline(file,str);
		for (int i = 0; i < str.size(); i++)
			entries[(unsigned char) str[i]]++;
	}
	file.close();
}

int main()	{
	findFrequency();
	return 0;
}

```

Note: you need to cast the str[i] to 'unsigned char' because chars, by default, are signed on most systems (except mac ppc iirc).

As I was re-implementing your code, I also noticed that you didn't account for all possible char values, you only accounted for 0-254, and missed 255.

---

### Post by darthshak on 2008-11-04
> Being that you are hashing based on a char and you populate the hash_map with all 256 entries, why not simply use an array and use the char as an index?

Well, thanks, that's a mistake in my code actually. I just wanted to hash the characters that were already present, so I should remove the for loop that stores 'em.

---

### Post by alternatealias on 2008-11-04
> **darthshak said:**
> Well, thanks, that's a mistake in my code actually. I just wanted to hash the characters that were already present, so I should remove the for loop that stores 'em.

Fair enough, but I think you'll find using a table lookup will not only be faster but use less memory than a hash_map for this particular purpose (not to mention far easier to write).

Also, as someone else previously mentioned, the value of each entry (E.second) plays no part in the hash insert/lookup logic.

---

### Post by dribeas on 2008-11-04
> **darthshak said:**
> Hi.

I was using a hash table of characters for this codec that I was programming. However, this is my first brush with the hash_map structure defined in the STL.

Well, the deal is in the line which says E.first = char(i). Now, the hash_map is a pair associative container of the form pair<key,data>. The problem is, by default, E.second assumes the value of 0. 

Now, if all the keys are associated with the value 0, the worst-case complexity of searching becomes O(n), which defeats the purpose of hashing. Or is there some internal mechanism of hash_map which prevents this from happening?

Would adding the line E.second = i make a difference?

First, hash_map is not (yet) part of the STL and there is no warranty that it will be implemented with the same interface by any other compiler/library provider.

Now, the data stored inside the associative container is a std:: pair<key_type, value_type>, first represents the key and second the stored value. Stored values (in your case 0) are not used for searching, only as the stored result.

You can store any value associated with the key with the .second element in the pair. If you don't need to store a value, you can fall back to a hash_set. For any of the requirements you can use the standard defined containers std::map and std::set (no data associated). Theoretical analysis will tell you that hash_maps (unordered_map in C++0x jargon) are faster (on average) than balanced-tree solutions as std::map, but in most cases there won't be a difference (unless you have a tailored hash function that warrants the spreading of the keys). While hash tables have O(1) access with no colisions, the worst case complexity turns linear O(n). Balanced trees have a warranted O(log n) insertion and extraction time.

---

