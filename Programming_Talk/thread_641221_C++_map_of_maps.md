---
title: "C++ map of maps"
date: 2007-12-15
forum: Programming Talk
---

### Post by EricDallal on 2007-12-15
Hello,
I am trying to create a map of maps in c++. I normally wouldn't do this, but there is a need for incredible flexibility in my program. I have data types Observation and Action which are both structs and I want a map as follows:

map< Observation, map< Action, double, actCmp >, obsCmp > Qvalue;

the problem is that whenever I do:

map< Action, double, actCmp > obsMap;
Qvalue.insert(make_pair(*o, obsMap));

the thing continually inserts the same map for every Observation *o (o is a pointer to an Observation). This is useless since I want different maps for different Observations. In principle, I could declare Qvalue to be a map from Observations to pointers to maps and create as many new maps as I need, but I don't know how to use the new operator with maps.

Can anybody help me with this?

---

### Post by pedro_orange on 2007-12-15
I have an app I made for a uni project a few years ago that uses a Vector inside a map structure - but it's too big for me to send as a private msg. If u send me a msg with my ur e-mail I'll send it to you.

---

### Post by duff on 2007-12-15
I'm not sure what your problem is.  If I'm understanding your post correctly, you basically want something like this:

```
#include <iostream>
#include <string>
#include <map>

using namespace std;

template <typename K, typename V, class C, class A>
ostream &operator<< (ostream &os, map<K,V,C,A> const& m)
{
	os << "{ ";
	typename map<K,V,C,A>::const_iterator p;
	for (p = m.begin(); p != m.end(); ++p) {
		os << p->first << ":" << p->second << ", ";
	}
	return os << "}";
}

int main (int argc, char *argv[])
{
	typedef map<int, string> Map1;
	typedef map<double, Map1> Map2;

	Map2 m;
	m.insert (make_pair (1.2, Map1 ()));
	m[1.2].insert (make_pair (3, "three"));
	m[1.2].insert (make_pair (5, "five"));

	m.insert (make_pair (.5, Map1 ()));
	m[.5].insert (make_pair (5, "five"));
	m[.5].insert (make_pair (1, "one"));
	m[.5].insert (make_pair (9, "nine"));

	cout << m << endl;
}
```

When I run the above, I get :
```
 # ./a.out
{ 0.5:{ 1:one, 5:five, 9:nine, }, 1.2:{ 3:three, 5:five, }, }
```

---

### Post by EricDallal on 2007-12-15
Yes, I did a test of my own and it seemed to work fine when I had a map of maps where all the types were ints. I think the problem is with the structs, not with the maps. I'm going to try to do a bit more testing to try to pinpoint the problem. If you can get working code where the keys are structs, that would certainly convince me that what It's just a bug in my code and not something that I can't do.

---

### Post by EricDallal on 2007-12-15
Ok, I have found that a map of maps of the form:

map<int, map< int, int > > themap

works fine.

I have also found that a map with structs as keys works fine:

typedef struct {
int x;
} IntWrap;

struct IntWrapCmp {
	bool operator()( IntWrap i1, IntWrap i2 ) const {
		return i1.x < i2.x;
	}
};

map< IntWrap, int, IntWrapCmp > themap

However, I have found that a map of maps where the keys are both structs doesn't work:

typedef map< IntWrap, int, IntWrapCmp > IntMap;
typedef map< IntWrap, IntMap, IntWrapCmp > IntMapMap;

void PrintIntWrap(IntWrap I) {
	cout << I.x << "\n";
}

IntMapMap themapmap

I ran the following code:

main() {
        IntMapMap themapmap;
	IntWrap I1, I2;
	for (int i = 0; i < 10; i++) {
		I1.x = i;
		themapmap.insert(make_pair(I1, IntMap()));
		for (int j = 0; j < 10; j++) {
			I2.x = j;
			themapmap[I].insert(make_pair(I2, i + j));
		}
	}
	IntMapMap::iterator mapmapiter;
        IntMap::iterator iter;
	for (mapmapiter = themapmap.begin(); mapmapiter != themapmap.end(); mapmapiter++) {
		cout << "Outer\n";
		PrintIntWrap(mapmapiter->first);
		for (iter = (mapmapiter->second).begin(); iter != (mapmapiter->second).end(); iter++) {
			cout << "Inner\n";
			PrintIntWrap(iter->first);
			cout << iter->second << "\n";
		}
	}
}

and obtained the following output:

Outer
0
Outer
1
Outer
2
Outer
3
Outer
4
Outer
5
Outer
6
Outer
7
Outer
8
Outer
9
Inner
0
0
Inner
1
1
Inner
2
2
Inner
3
3
Inner
4
4
Inner
5
5
Inner
6
6
Inner
7
7
Inner
8
8
Inner
9
9

Can anybody suggest a solution (or even figure out what is happening)?

---

### Post by EricDallal on 2007-12-15
I've now determined that the above code can work if I get rid of the line:

themapmap.insert(make_pair(I1, IntMap()));

However, my program still doesn't work, since the structures have more than basic components.

---

### Post by hod139 on 2007-12-16
I'm not sure what your trouble is.  The following code works for me.  I chose to overload the operator< instead of writing a comparison struct, but you get the idea. 

```

#include <map>

using std::map;

struct Observation{
  Observation() : foo(0) {}

  int foo;
};

bool operator<(const Observation &lhs, const Observation &rhs){
   return lhs.foo < rhs.foo;
}

struct Action{
  Action() : foo(0) {}

  int foo;
};

bool operator<(const Action &lhs, const Action &rhs){
   return lhs.foo < rhs.foo;
 }

int main (void)
{
   map< Observation, map< Action, double > > Qvalue;

   map< Action, double > obsMap;
   Observation o;
   
   Qvalue.insert(make_pair(o, obsMap));

   return 0;
}

```

Looking back at your first example, at the line causing you trouble
```

Qvalue.insert(make_pair(*o, obsMap));

```
the pointer o is not NULL is it?

---

