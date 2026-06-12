---
title: "C++ optimization and benchmarking vs. Java"
date: 2008-12-31
forum: Programming Talk
---

### Post by CptPicard on 2008-12-31
**Note: There is a [[COLOR="Red"]Java version[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6482254&postcount=26") later on in the thread for benchmarks, and a [[COLOR="Red"]C version[/COLOR]]("http://www.voittoporukka.fi/~eero/c-analyzer/") too!**


Ok, so here is a little challenge for all you C++ gurus out there. ;)

Over the past week I have had occasional bouts of boredom during which I started wondering how much performance could be gained by porting my betting analysis toolkit (my secret weapon in life) from Java to C++. Java has been a good language for its crossplatformness, ease of exploratory algorithm development and threading... but I have never had a good idea of how I am losing in performance terms.

Check out the header

```
#ifndef __VAKIO_ANALYZER_H__
#define __VAKIO_ANALYZER_H__


#include <map>
#include <string>
#include <vector>
#include <functional>



using namespace std;


typedef struct {

  int winclass_size[4];
  double exp_components[4];

  double prob;
  double kelly;

} vakiodata;


typedef map<unsigned int, vakiodata, less<unsigned int> > data_map_type;


class StateHandlerCallback;

class VakioAnalyzer {
  
 private:
 
  data_map_type data;

  int row_length;

  void produce_combinations(int, unsigned int);
  string stateToString(unsigned int state);
  
  void neighbourSet(unsigned int state, int k,
		    StateHandlerCallback&);

  void neighbourRecursion(unsigned int, 
			  unsigned int,
			  StateHandlerCallback&,
			  int, 
			  int);

  unsigned int parseState(string);
  void computeWinSetSizes();

 public:
  VakioAnalyzer(int row_length);
  int rowlength();
  void init();
  void test();
};


#endif


```

and the implementation

```

#include "vakioanalyzer.h"
#include <iostream>



class StateHandlerCallback {
  
private:
  data_map_type &datamap;
  int winclass;
  vakiodata &orig;

public:
  StateHandlerCallback(data_map_type &m,
		       int w, vakiodata &o) :
    datamap(m), winclass(w), orig(o) {}

  void operator() (vakiodata &other) {
    orig.winclass_size[winclass] += 
      other.winclass_size[0];
  }

};



VakioAnalyzer::VakioAnalyzer(int row_length) {
  this->row_length = row_length;
  cout << "Created thingy of size " << row_length << endl;
}


int VakioAnalyzer::rowlength() {
  return row_length;
}



void VakioAnalyzer::produce_combinations(int pos, unsigned int state) {

  if (pos == rowlength()) {
    vakiodata &item = data[state];
    item.prob = 0;
  }
  else {
    for (int i = 0; i < 3; i++)
      produce_combinations(pos+1,
			   state | (i << (pos*2)));
	
  }
   
}



unsigned int set_bits(unsigned int orig,
		      unsigned int set_to,
		      unsigned int pos,
		      unsigned int width) {

  unsigned int mask = ((1 << width) - 1) << (pos*width);
  return (orig & (~mask)) | (set_to << (pos*width));

}

unsigned int get_bits(unsigned int i,
		      unsigned int pos,
		      unsigned int width) {
  
  unsigned int mask = ((1 << width) - 1) << (pos * width);
  return (i & mask) >> (pos * width);

}



void VakioAnalyzer::neighbourRecursion(unsigned int orig,
				       unsigned int neighbour,
				       StateHandlerCallback &cb,
				       int left,
				       int pos) {

  map<unsigned int, vakiodata>::iterator it;

  if (left == 0 && neighbour != orig &&
      (it = data.find(neighbour)) != data.end()) {
    cb(it->second);
  }
  else if (pos >= rowlength() ||
	   left > (rowlength()-pos)) {
    return;
  }
  else {

    // The case where it is not set to anything, just skipped
    neighbourRecursion(orig, neighbour, cb, left, pos+1);
    // The other cases
 
    for (unsigned int i = 0; i < 3; i++) {
      if (i != get_bits(orig, pos, 2)) {
	neighbourRecursion(orig,
			   set_bits(neighbour, i, pos, 2),
			   cb,
			   left-1,
			   pos+1);
      }
    }
  }
}



void VakioAnalyzer::neighbourSet(unsigned int state, int k,
				 StateHandlerCallback &cb) {

  neighbourRecursion(state, state, cb, k, 0);

}



void VakioAnalyzer::init() {

  produce_combinations(0,0);
    
}






string VakioAnalyzer::stateToString(unsigned int state) {

  string s;

  for (int i = 0; i < rowlength(); i++) {

    int state_item = get_bits(state, i, 2);

    if (state_item == 0)
      s = '1' + s;
    else if (state_item == 1)
      s = 'X' + s;
    else if (state_item == 2)
      s = '2' + s;
  }

  return s;

}


unsigned int VakioAnalyzer::parseState(string s) {

  unsigned int result = 0;
  int pos = 0;
  
  for (string::reverse_iterator iter = s.rbegin();
       iter != s.rend();
       iter++) {

    switch (*iter) {

    case 'X':
      result = set_bits(result, 1, pos, 2);
      break;
      
    case '2':
      result = set_bits(result, 2, pos, 2);
      break;
    }
    
    pos++;

  }

  return result;
}



void VakioAnalyzer::computeWinSetSizes() {

  for (data_map_type::iterator 
	 iter = data.begin();
       iter != data.end();
       iter++) {
  
    for (int i = 1; i < 4; i++) {
   
      StateHandlerCallback cb(data, i, iter->second);

      neighbourSet(iter->first, i, cb);
      
      /*
      cout << stateToString(iter->first) << " "
	   << i << endl;
      */
    }
  }

}


void VakioAnalyzer::test() {

  init();


  cout << "initing material..." << endl;
  init();
  cout << "Inited" << endl;

  cout << "Winset size computation.." << endl;

  computeWinSetSizes();

  cout << "Winset size computation done" << endl;
  
}

```


of class VakioAnalyzer. You can run the test case by doing

```

VakioAnalyzer a(13);
a.test();

```

Essentially, what this thing does is that it stores 13-item state vectors of three possible states (1, X, 2) in an unsigned int, 2 bits per item in the map "data" where the value in the map is the associated data struct "vakiodata". There are bit-fidding utility functions for extracting and setting state and parsing and printing strings.

The important part is the recursive "finding neighbours" part... a k-neighbour of some state s is another state where exactly k items differ from those found in state s.

The "winset sizes" part is essentially the first part of all the algorithms I run in my analysis, but it is very representative - most passes over the data take the same form (for each data item, find (1,2,...k)-neighbours, compute something). In Java it is convenient to implement stuff using anonymous inner classes as callbacks that fake closures ... it is easy to just say "forKNeighboursDo(k, new Callback() ...)". In C++ I took the easy way out for the time being and am just returning a vector of ints. It's possible that behind the scenes reallocations of the vector are making this thing slow...

Anyway, in Java on a few years old AMD64 3400+ this phase takes maybe 10-15 minutes or so if memory serves. On my Acer Aspire One the C++ version has been running for 45 minutes and it's still not done ;)

EDIT: Removed the usage of vector to return k-neighbour states and replaced it with a functor-style callback which approximates pretty well what I am able to do in Java (but C++ doesn't quite allow as far as I know). Performance is STILL unusable ...

EDIT2: Made less<unsigned int> explicit comparison object...

---

### Post by jespdj on 2008-12-31
Is your C++ version exactly the same as the Java version (I mean, exactly the same algorithm)? Did you properly use the compiler optimization flags?

Despite what many people still think, Java is not slow at all. Sun's HotSpot just-in-time compiler is very smart and efficient, and compiles your Java bytecode to optimized machine code for your specific hardware on the fly - which makes Java programs run quite fast.

In principe, a just-in-time compiler can produce more optimized code than an ahead-of-time compiler (i.e. most normal C/C++ compilers, including gcc), because the JIT compiler can take advantage of information about the program that's only available at runtime. (An AOT compiler runs before runtime, so it can't profile your program on the fly, as a JIT compiler can in principle do).

I haven't done any really careful and serious performance comparison between Java and C++ myself, but I once wrote a simple ray tracing program, first in Java and then in C++. It was not easy to make the C++ program run faster than the Java program...

---

### Post by CptPicard on 2008-12-31
> **jespdj said:**
> Is your C++ version exactly the same as the Java version (I mean, exactly the same algorithm)? Did you properly use the compiler optimization flags?

The *algorithm* is the same. There are two differences I did not mention -- Java version makes use of a sorted binary-searched array whereas C++ uses the STL map, and C++ makes use of ints as bitsets whereas Java just uses byte arrays to store data. The former change just makes a search of O(log n) key comparisons happen in an explicit tree structure, which should result in a comparable amount of operations, and the latter change should perhaps even give C++ an edge, as keys are just ints, not arrays of bytes, comparison of which is a loop over the array.

A future change into the Java version will mean making use of TreeMap so that I can make some mutations into the set more quickly, and because this adds to already rather humongous memory consumption, I will probably move over to the bitvector model in Java too.

In any case, I was expecting "comparable" performance. Instead, I get atrocious performance from C++. :) I'll tell more when I get stuff run on the same box.

Flags are -O3 -march=i686.

> 
Despite what many people still think, Java is not slow at all.

This is what I have been trying to tell people, too. ;) This stuff is a good comparison point because the algorithm is no longer a "microbenchmark", there is lots of number-crunching and memory-traversing. However, an important point to note that the Java version doesn't allocate anything after setting things up for computation, so there is also no garbage collection. The object graph stays the same, so the big issues are Java's greater memory consumption and the fact that on Java you're potentially traversing pointers more than in C++. It is conceivable that the C++ compiler could move more of the number-crunching parts properly into registers...

> It was not easy to make the C++ program run faster than the Java program...

Yeah... in particular if it turns out that relatively straightforward (yet intelligently written) Java beats straightforward (not über-handcrafted) C++, I'd be quite happy ;)

---

### Post by Bichromat on 2009-01-01
I profiled your code and it seems that the bottleneck is the std::map. About 35% of the time is spent in std::_RB_tree<>::find and another 15% in std::less<>::operator()

Maybe using the same data structure as in Java would make the code more efficient.

---

### Post by jmartrican on 2009-01-01
Bichromat,

How did you do the profiling?  How were you able to tell how much time was being spent on that particular section.  I been wanting to get into profiling since reading the optimization section of Code Complete 2.  


One weird thing worth mentioning is that it could be the case that people assume the c++ version of a piece of code must be faster than the java so they keep tweaking the c++ version until it is true.

---

### Post by CptPicard on 2009-01-01
Thanks bc. :)

> **Bichromat said:**
> I profiled your code and it seems that the bottleneck is the std::map. About 35% of the time is spent in std::_RB_tree<>::find and another 15% in std::less<>::operator()


It actually sounds rather reasonable that 50% of time is spent in lookup, because that's what the code mostly does, profiling of Java code gives me similar percentages for its lookup parts. The other 50% are probably spent recursing down the neighbour sets, generating them...

An interesting point is that 15% is spent in what is essentially "int < int". As there are the same number of these calls as there are nodes searched, the total time spent in each single node is not that bad :)

> 
Maybe using the same data structure as in Java would make the code more efficient.

I will see about it when I experiment the other way around, switching Java's data structure into the java.util.TreeMap. I have my doubts though, a binary search into sorted array visits the same number of same kind of nodes ... the only difference with a tree is that the nodes are explicit structures.

---

### Post by Bichromat on 2009-01-01
> **jmartrican said:**
> Bichromat,

How did you do the profiling?  How were you able to tell how much time was being spent on that particular section.

I used gprof. You first need to compile your code with the '-pg' option (assuming you use a GCC compiler). Then you run your code, and it produces a file named 'gmon.out' that contains profiling data. 
You can extract it with 'gprof ./executable_name > profiling.txt'.
Read gprof's manual if you want more info.

CptPicard: Given that I'm not well versed in trees, maps and search algorithms, I'll take you word for it. Still, I feel that something's not right about C++ being (more than) 3 times slower than Java...

---

### Post by Cracauer on 2009-01-01
In the profile, you spend almost all time in the map, but this is somewhat misleading. To profile effectively, you have to disable inlining, and that makes some things pop up in the time spent that shouldn't. Doing int <  int is very fast if you do it as a single instruction, but if you wrap a function call around it the time multiplies.

Changing your code from map to hash_map cuts off 30% right away. I can post the code if you want.

You spend a lot of time "breathing", that means allocating and freeing memory.  The major areas are the strings (did you say you use a real bitmap in java?) and computeWinSetSizes constructs a new vector in a loop that looks pretty tight.

These
```

s = '1' + s;

```

are absolutely deadly, they allocate entirely new memory for the result string every time.

---

### Post by CptPicard on 2009-01-01
> **Cracauer said:**
> 
Doing int <  int is very fast if you do it as a single instruction, but if you wrap a function call around it the time multiplies.

Changing your code from map to hash_map cuts off 30% right away. I can post the code if you want.

Interesting... no need to post though, I can swap it myself. :) As an aside, a binary tree of 3^13 items is about 20 levels deep... so hashing is going to have an effect, yes, with associated memory implications (which is why I have not gone the hashing route in Java..).

I really don't know how map internally compiles the comparator, but apparently it leaves it out in a function of its own.

Then again in Java I actually do function calls where I run down doing comparisons on a 13-item byte[] and return the resulting lexicographical ordering... I am giving C++ a substantial head start here ;)

> 
You spend a lot of time "breathing", that means allocating and freeing memory.  The major areas are the strings (did you say you use a real bitmap in java?)

The strings aren't used for anything except printing out state for debugging, so they are not present in the heavy-lift parts :) In benchmarking the cout in computeWinSets should be commented out, I am not sure if it was in the version you're looking at.

> 
 and computeWinSetSizes constructs a new vector in a loop that looks pretty tight.

Hmm, you found an old version of the code somewhere. The vector has been removed for a while now for exactly this reason. Although it didn't make much of a difference to be honest, the compiler was good at it -- currently I call a callback functor -- whose construction on stack could probably be moved out of the loops, now that I look at it... it is a very small object though.

But you're right that that is indeed the tight part -- 3^13 times about 3000 times recursing down to the point where the callback can actually be called...

---

### Post by Cracauer on 2009-01-01
[http://www.cons.org/tmp/java-stuff/v1/](http://www.cons.org/tmp/java-stuff/v1/)

This cuts the time (when run with 10, not 13) about in half.

This is mainly the hash_map instead of map, some inlining, some copy avoidance.

I didn't tackle any of the real problems yet, which is the memory breathing from string and vector allocation.

---

### Post by Cracauer on 2009-01-01
> **CptPicard said:**
> 
Hmm, you found an old version of the code somewhere. The vector has been removed for a while now for exactly this reason. Although it didn't make much of a difference to be honest, the compiler was good at it -- currently I call a callback functor -- whose construction on stack could probably be moved out of the loops, now that I look at it... it is a very small object though.


Hmm, I picked up code from a link in your post yesterday. It was MS-DOS line breaked code which made me puzzled.

Anyway, let me restart with the code you have posted.

---

### Post by CptPicard on 2009-01-01
> **Cracauer said:**
> Hmm, I picked up code from a link in your post yesterday. It was MS-DOS line breaked code which made me puzzled.

Yeah, those pastebin links were first version :) I wrote out the vector around noon today...

Interesting wrt line breaks, it comes from vanilla Emacs on Intrepid...

---

### Post by Cracauer on 2009-01-01
Using size 11, hash_map is still twice as fast as map in the new version. According to top(1) it's also smaller, res and virt.

I'll run it with full size, both versions. My gut feeling is it won't reverse the speed of the two.

I think the MS-DOS newlines probably came from a braindead website.

---

### Post by CptPicard on 2009-01-01
Hmmh, I may have to actually consider the possibility of hashmap instead of tree in general. The reason why I want to move away from the array even in the Java version is that in the general case the entire space is too big to fit totally in RAM (the 3^{13,11,12,10} 1X2 game is an exception) and I want some limited mutability. An important consideration though is that all these algorithms I run on the data can be parallelized trivially by just running threads on their respective parts of the data (it can be arranged such that there are never concurrent writes, just reads)... but, I suppose I can do that on hashes as well, as the structure itself is read-only during threading anyway.

---

### Post by Cracauer on 2009-01-01
I'm not sure the hash_map is that brilliant either.

The profile (for all the mess caused by not inlining stuff) is still all hyper about the find(neighbour).

What's the range of that unsigned int, typically?

---

### Post by CptPicard on 2009-01-01
Well the int is in the case of size 13, at max 4.4739242e7 (it's a base-three number of 13 digits so max is 13 binary '10's packed end to end)

---

### Post by Cracauer on 2009-01-01
One trick I use with maps from int to something else is this: if the small numbers are much more common than bigger ones, split up actual storage of the map into two parts, choosing some {limit} of integers that seems suitable:

1) an array for the first part, for indexes <= {limit}
2) for indexes > {limit}, fall back to a hashtable

{limit} would be chosen to cover a lot of cases and keep memory consumption low.

I just gave your program a spin by similating such a mechanism for the first quarter of the specified range, but I only get a hit rate of 33%.  So smaller numbers are more common, not not common enough to make good for the 680 MB memory that this would cost.  In addition you would also have to introduce a mechanism to mark "index not present".  It still might pay off as you get rid of 1/3rd of the hash lookups in exchange for memory that's probably available, but I wouldn't call this an efficient use of memory.

It might be possible look at the numbers that appear more closely and re-map them so that actually occuring numbers are concentrated in the low range.  But if this needs a couple more indirections you just re-implement a hashtable.

Binary trees I dunno about either since the 64 bit pointers can bite you.

I'm experimenting some more, but what I think needs to be done here is a custom hashtable.

%%

Question:

Can I use
  vakiodata.winclass_size[0] == -1

as a marker for "not set yet". I don't think it can have negative values naturally, can you confirm?

---

### Post by CptPicard on 2009-01-01
> **Cracauer said:**
> 
I just gave your program a spin by similating such a mechanism for the first quarter of the specified range, but I only get a hit rate of 33%.  So smaller numbers are more common, not not common enough to make good for the 680 MB memory that this would cost.

Actually, 3^13 = 1 594 323 and the entire range is pushed as keys into the map, and the encoding makes use of integers of up to 4.473..e7, and the ratio of these two is about 0.035. Distribution ought to be even IMO but I am not quite 100% sure :)

The reason why I am not just counting integers up to ~1.6 million is obviously that generation of the "off by k neighbours" is easier.

> It still might pay off as you get rid of 1/3rd of the hash lookups in exchange for memory that's probably available, but I wouldn't call this an efficient use of memory.

... and to think that this case is still relatively merciful, in other similarly behaving games I can fill up about as much RAM as I can get ;)


> 
Can I use
  vakiodata.winclass_size[0] == -1

as a marker for "not set yet". I don't think it can have negative values naturally, can you confirm?

Hmm... for a "not set yet" value yes, but it does have a meaning when it does get set. A more informative name for the array would probably be just "total_neighbour_count[i]", because the index 0 contains data that is loaded from outside (for sake of experiments it can be just random data) and says how many times a given result has been bet on... then, neighbour_count[1] contains the sum of neighbour_count[0] of all results that are wrong by one result digit, neighbour_count[2] is the total sum of [0] that is off by two.. so on.

EDIT: and let's not get carried away yet, I really need to see this thing running on the same machine with the Java version to have a good idea how much behind we actually are :) Gut feeling doesn't bode well for C++ so far...

---

### Post by Cracauer on 2009-01-01
Here's the version with some stats and using hash_map:
[http://www.cons.org/tmp/java-stuff/v2/](http://www.cons.org/tmp/java-stuff/v2/)

---

### Post by Cracauer on 2009-01-02
I hacked up a custom hastable and it seems to speed up the whole thing by a factor of more than two for the smaller sets. It doesn't finish the 13 set as-is, some bugs to sort out.

I don't have an extensive testsuite for it. Is there a way to verify that the results of your program are correct? Can you supply some code that e.g. walks the hashtable and yells at things that are obviously wrong?

---

### Post by CptPicard on 2009-01-02
LOL, thanks... you're going way beyond the call of duty here :)

No, there is no test suite unfortunately... I can personally just easily eyeball the results as needed and see when they are wrong. :) winclass[i], i > 0, ought to always be, for some item in our hashmap, sum over {k in neighbours(i)} winclass[0].

On the other hand if the hashtable data structure itself works correctly -- that it really does fetch the generated neighbour values right -- I see no reason why things would work wrong as my neighbour generator does work right  -- and if you suspect it there is issues, you can print out stuff to make sure things go right... namely, for say case 10:

```

First item of case 10, with some hypothetical winclass[0] values is

1111111111

neighbour set k = 1:     winclass[0]

111111111X               1
11111111X1               2
1111111X11               1 
111111X111               1
...                 ...  1  ... (assume, 6 results skipped)
1111111112               2
1111111121               2
...                 ...  1  .... (*8)
2111111111               2

total, for 
first item's 
winclass[1] =            25

```

---

### Post by Cracauer on 2009-01-02
I hacked up all custom hash code and I don't have an extensive test suite for it. Right now when using it with size 13 it doesn't finish, obviously it's not quite correct yet.

Let me just ask, do you plan to give Java another best shot using the same algorithm?

This program of yours looks like a much better language benchmark than anything else I have seen. It would be interesting to drive C++ and Java to the max using it. That's why I'm sticking with it.

It doesn't explore some points that would make Java weaker (no arrays of user-defined data types), but given the hash-or-tree problem I think I should be able to crush Java anyway.


Another question: I see none of the data fields being used except for ->prob and I get warnings about uninitialized use of data from it.  Is that intentional?

---

### Post by bobrocks on 2009-01-02
Is this data generated from your program at the top of this thread?

I have taken a quick look at it and I don't see where data is getting set.  It looks like the setting is getting done in the call back but that just does

```

orig.winclass_size[winclass] += other.winclass_size[0];

```

But I don't see where this value changes so winclass_size[0] is always 0, I am playing online poker at the same time so I may be missing something?

Like Cracauer mentions there is no test, if there was a test method that I could actually compare my result I would be happy to look at the algorithm.  Because I can't really see if my change has broken the algorithm so I'm cautious to try.

> **CptPicard said:**
> LOL, thanks... you're going way beyond the call of duty here :)

No, there is no test suite unfortunately... I can personally just easily eyeball the results as needed and see when they are wrong. :) winclass[i], i > 0, ought to always be, for some item in our hashmap, sum over {k in neighbours(i)} winclass[0].

On the other hand if the hashtable data structure itself works correctly -- that it really does fetch the generated neighbour values right -- I see no reason why things would work wrong as my neighbour generator does work right  -- and if you suspect it there is issues, you can print out stuff to make sure things go right... namely, for say case 10:

```

First item of case 10, with some hypothetical winclass[0] values is

1111111111

neighbour set k = 1:     winclass[0]

111111111X               1
11111111X1               2
1111111X11               1 
111111X111               1
...                 ...  1  ... (assume, 6 results skipped)
1111111112               2
1111111121               2
...                 ...  1  .... (*8)
2111111111               2

total, for 
first item's 
winclass[1] =            25

```

---

### Post by CptPicard on 2009-01-02
> 
I have taken a quick look at it and I don't see where data is getting set.  It looks like the setting is getting done in the call back but that just does

That's just an example.

In the real world values of winclass[0] are among the input data to the tool. As there is no input data, I didn't set it to anything, because the summing works just as well :)

A good way to provide at least some minimal test coverage would be to initialize all winclass[0] to 1, and then you will at least get the number of neighbours tallied to the other winclass-array items. That means that winclass[1] is, for case 13, 26 (ways to set one item differently) and analogously for k it is (13 k) * 2^k.


> **Cracauer said:**
> 
Let me just ask, do you plan to give Java another best shot using the same algorithm?

If there are obvious algorithmic improvements, yeah, so that it is comparable. I plan on testing with HashMap as soon as I get to my code from here -- until tomorrow I am at my parents' for year-end and just had my laptop to write the C++ mock-up. Even if I didn't end up rewriting in C++, anything that is transferable to the Java side is a huge plus ;)

> 
This program of yours looks like a much better language benchmark than anything else I have seen. It would be interesting to drive C++ and Java to the max using it. That's why I'm sticking with it.

Yeah, that's why I posted the thread. :) Microbenchmarks can be misleading, and a lot of big apps suffer from noise in benchmarking sense because in Java in particular the situation is polluted by bad object spamming all the time.

I am also willing to drive the Java side to the max for obvious reasons... 

> 
It doesn't explore some points that would make Java weaker (no arrays of user-defined data types), but given the hash-or-tree problem I think I should be able to crush Java anyway.

Well actually the main data structure in Java at the moment is a sorted ArrayList of data items. :) I wouldn't want to move the benchmarking to the array direction though as the long term design goal is to get some easier mutability to the main data structure, even at the cost of some lookup performance.

> 
Another question: I see none of the data fields being used except for ->prob and I get warnings about uninitialized use of data from it.  Is that intentional?

Even prob shouldn't be used? Or do I just initialize it for some reason somewhere? It's intentional... they do exist, but the mock-up doesn't use them. It's mostly just to get an idea of RAM consumption.

---

### Post by glok_twen on 2009-01-02
i'll pile on with my microbenchmarking result, not intending of course to stir the pot but i was obsessed with this for a while. this doesn't take the hashing item to any more depth. just gives another somewhat similar benchmarking where i worked to be as objective as possible in the well-worn path of java v. c++ benchmarking.

first an overview of the solution:

i have a stock trading program i've evolved since about 2001. (i am still broke :)). i've got a version that runs in java and a version that runs in c++. the main processing is many many different runs through an ArrayList in java and correspondingly through a std::vector<> in c++. i do not have the hash process you describe. the processing heavy parts are: pattern checking within the data structures, and also a lot of time aggregating the lists into aggregated lists, with still more pattern matching on those.

and now the results:

it's been pretty simple. in the straight java to c++ comparison it's pretty clear. the java version needs very consistently 55% more cpu time, and 65% more memory space. 

i also did a much simplified version on windows comparing java to c# (ms native). they were very close on both memory and cpu needs, with c# being a few percent less required on both counts.

i also ran the simplified version in python, which ran out of memory before it could reach the volumes of the previous test.

---

### Post by CptPicard on 2009-01-02
Here is a Java implementation for your reference... I fixed the bug that initially made this really, REALLY slow....

```
import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;
import java.util.Iterator;

public class Analyzer {

  private final int DIGIT_BASE = 3;

  private class DataItem {

    private int[] winclass_sizes = new int[4];
    private double prob;
    private double[] exp_components = new double[4];
    private double kelly;

  }
  
  private abstract class Callback {
    public abstract void call(int state, DataItem item);
  }

  private Map<Integer, DataItem> data;
  private int row_length;
  private byte mask_width;
  
  public Analyzer(int size) {
    data = new HashMap<Integer, DataItem>();
    row_length = size;
    mask_width = 2;
  }

  public int rowLength() {
    return row_length;
  }


  private void produceCombinations(int pos, int state) {
    if (pos == rowLength()) {
      DataItem item = new DataItem();
      item.winclass_sizes[0] = 1;
      data.put(state, item);
    }
    else {
      for (int i = 0; i < DIGIT_BASE; i++) {
	produceCombinations(pos+1, state | (i << (pos*mask_width)));
      }
    }
  }
  
  
  private int getBits(int i, int pos) {
  
    int k = pos * mask_width;
    int mask = ((1 << mask_width) - 1) << k;
    
    return (i & mask) >> k;
  }
  
  
  private int setBits(int i, int set_to, int pos) {
  
    int k = pos * mask_width;
    int mask = ((1 << mask_width) - 1) << k;
    
    return (i & (~mask)) | (set_to << k);
  }

  
  private void neighbourRecursion(int orig,
				  int neighbour,
				  Callback cb,
				  int left,
				  int pos) {

    // Sorry I'm messing with these conditions, I am just trying to
    // make them logically clear to avoid bugs
    if (left > pos+1 || neighbour < orig)
	return;
    else if (left == 0) {
      if (neighbour != orig) {
	DataItem item = data.get(neighbour);
	if (item != null) {
	  cb.call(neighbour, item);
	}
      }
      else
	return;
    }
    else if (pos >= 0) {
    
      neighbourRecursion(orig, neighbour, cb, left, pos-1);
      
      for (int i = 0; i < DIGIT_BASE; i++) {
	if (i != getBits(neighbour,pos))
	  neighbourRecursion(orig,
			    setBits(neighbour, i, pos),
			    cb,
			    left-1,
			    pos-1);
      }
    }
  }
  
  
  private void neighbourSet(int state, int k, Callback cb) {
    neighbourRecursion(state, state, cb, k, rowLength()-1);
  }
  
  
  private void init() {
    produceCombinations(0,0);
  }
  
  
  private String stateToString(int state) {
    
    // OK I am having cooler strings in Java.. these don't matter ;)
    StringBuffer result = new StringBuffer();
    
    for (int i = 0; i < rowLength(); i++) {
      int state_item = getBits(state,i);
      if (state_item == 0)
	result.append('1');
      else if (state_item == 1)
	result.append('X');
      else if (state_item == 2)
	result.append('2');
      else
	throw new RuntimeException("wtf?");
    }
    
    return result.reverse().toString();
  }
  
  
  private int parseState(String s) {
  
    int result = 0;
    
    for (int pos = 0; pos < s.length(); pos++) {
      if (s.charAt(pos) == 'X')
	result = setBits(result, 1, pos);
      else if (s.charAt(pos) == '2')
	result = setBits(result, 2, pos);
    }
    
    return result;
  }
  
  // Java forces a bit of trickery here, a helper method:
  private void winsetHelper(final int orig_state, final int winclass) {
    
    final DataItem di = data.get(orig_state);
  
    // Most of my Java version's code is built on this kind of
    // callback model. It's pretty important that they are just
    // interfaces that contain no data, so that compiler does not 
    // need to actually create any objects!
    neighbourSet(orig_state, winclass, new Callback() {
      public void call(int nb_state, DataItem nb_di) {
      
	//System.out.println("\t"+stateToString(nb_state)+"\t"+winclass);
      
	di.winclass_sizes[winclass] += nb_di.winclass_sizes[0];
	nb_di.winclass_sizes[winclass] += di.winclass_sizes[0];
      }
    });
    
  }
  
  
  private void computeWinSetSizes() {
    for (Integer key : data.keySet()) {
      for (int i = 1; i < 4; i++) {
      
//	System.out.println("Do class "+i+" for "+stateToString(key));
	
//	long begin = System.currentTimeMillis();
	
	winsetHelper(key, i);
	
//	long end = System.currentTimeMillis();
//	System.out.println("Did "+stateToString(key)+" class "+i+
//			   " in "+(end-begin)+" ms");
			   
      }
    }
  }
  
  
  private void dumpClasses() {
 
    for (Map.Entry<Integer,DataItem> e : data.entrySet()) {
	System.out.print(stateToString(e.getKey())+"\t");
	for (int i = 0; i < e.getValue().winclass_sizes.length; i++)
	    System.out.print(e.getValue().winclass_sizes[i]+"\t");
	System.out.println();
    }
  
  }
  
  
  public void test() {
  
    init();
    System.out.println("Initialized data... map has "+data.size()+" items");
    
    /*
    Integer k = data.entrySet().iterator().next().getKey();
    
    System.out.println("Nbset 2 for "+stateToString(k));
    
    neighbourSet(k, 3, new Callback() {
      public void call(int key, DataItem i) {
	System.out.println(stateToString(key));
      }
    });
    */
    

    long begin = System.currentTimeMillis();
    
    computeWinSetSizes();
    
    long end = System.currentTimeMillis();
    
    System.out.println("Computing winsets took "+(end-begin)+" ms");
    
    System.out.println();
    
    //dumpClasses();
   
  }
  
  
  public static void main(String[] args) {
    Analyzer a = new Analyzer(11);
    a.test();

  }
  
}
```

---

### Post by bobrocks on 2009-01-03
> **CptPicard said:**
> Here is a Java implementation for your reference... I fixed the bug that initially made this really, REALLY slow....

Note @Cracauer: I made a little change to the termination condition of neighbourRecursion (it now checks first whether there is anything left to place, and then goes down ... it should not make any difference but feels more logically correct)

Seems like Java's HashMaps and TreeMaps are comparable in size and take about 2x the RAM of the STL std::map. In case 10, HashMap takes (on this machine) 52 seconds to run, while TreeMap runs in 117 seconds. No contest between hashing and treeing, then as there is no memory difference.


I had a look at this earlier, because it is spending so much time in find I implemented googles fast access dense hash map.  Didn't really help, we are still talking 1 hour 6 minutes for the 13 set.

On this machine with sets of 10, the java and c++(with dense_hash_map) programs both run in 7 seconds.  Sets of 11 java moves ahead with 46 against c++ with 48.   After that it's game over, java just annihilates it on 12 with 2min13 against 4min15.  

Of that 4min15, non scientific analyses (disable find) would say roughly 11 seconds is spent doing everything bar the find.  The other 4min04 is spend inside find.  Which seems to say java's hashmap is very efficient at fetching compared to google's or gcc's C++ hashmaps.

It's intresting, but as I am a java developer and only started writing c++ for fun a few months back I don't have many more ideas on how to improve the c++ version.  Look forward to seeing Cracauer's custom hashmap solution though.

---

### Post by CptPicard on 2009-01-03
Hmmph, never mind if you saw this post before edit, I had forgotten a TreeMap in there in place of HashMap...

Anyway, on size 11, Cracauer's code from website ran at 42 secs, Java takes 1:59. Actually this starts to look more "expected"... bobrocks, are you sure you aren't just doing something wrong there ;)

---

### Post by bobrocks on 2009-01-03
> **CptPicard said:**
> Hmmph, never mind if you saw this post before edit, I had forgotten a TreeMap in there in place of HashMap...

Anyway, on size 11, Cracauer's code from website ran at 42 secs, Java takes 1:59. Actually this starts to look more "expected"... bobrocks, are you sure you aren't just doing something wrong there ;)

I hadn't actually seen that Cracauer had posted up code using hashmap, I just read his comment about the hashmap not being that brilliant either.  But anyway running the code with hashmap I get

11 :- 31sec
12 :- 1m59
13 :- 9m58

Which is pretty good, and considering he is mentioning performance increases of a factor of 2 from the custom implementation that's pretty impressive.


It appears, looking at their newsgroups, googles dense hashmap is not really good for big collections it is meant for smaller ie less that 100000 which is why it beats gcc's tr1 hashmap in retrieval benchmarks, and is also why I was getting times that progressivly fell back.

My java times are correct, I just ran them again, I do have a fairly fast computer which might explain why they are quite fast compared to yours.

---

### Post by CptPicard on 2009-01-03
Thanks for verification... I was getting weirded out. :)

But, it looks like Java is getting trounced anyway as I expected. On "the real thing" Java code I am also parallelizing this to make use of multiple cores (dividing up the keyspace for computations is of course trivial). I am still not completely 100% clear on why there was such awful performance on the originals... is the tree-based map really *that* bad?

Interestingly, this may just be justification enough to ask "boss" for money to reimplement in C++, the improvements are big enough... then... we could actually attack Quiniela in Spain which is size=15 game. Too bad even in Finland we're I/O bound -- I need to pull the winclass[0] numbers from a web app, parsing HTML for the 3^13 possible results, 100 results a page... saturates a fat ADSL line for a long time, unfortunately :p

> **bobrocks said:**
> My java times are correct, I just ran them again, I do have a fairly fast computer which might explain why they are quite fast compared to yours.

Still a bit odd that I manage to get the C++ version to run for 11 to run in 42 seconds and Java is that much slower while on yours it's still within "striking distance". What are your compiler flags? I was pretty heavy-handed, -O3 -fexpensive-optimizations

---

### Post by Cracauer on 2009-01-03
Looks like a gotta finish the custom hashtable.

If you take the hash_map code I put on the second url you have to take out a debug print statement, it prints out all keys for the hashtable.

---

### Post by Reiger on 2009-01-03
> **CptPicard said:**
> Still a bit odd that I manage to get the C++ version to run for 11 to run in 42 seconds and Java is that much slower while on yours it's still within "striking distance". What are your compiler flags? I was pretty heavy-handed, -O3 -fexpensive-optimizations

Is any swap taking place? You mentioned the memory consumption of the C++ being ~ 2 times less than that of Java, so if you're PC has half the RAM of his machine ... :)

---

### Post by CptPicard on 2009-01-03
Trust me, any swapping causes much more issues than a doubling-quadrupling of runtime ;)

Memory locality is also remarkably weak in this application btw, there is no good stable "working set" anywhere -- some item's neighbours are all over memory. With this stuff and oversized Java heap I've witnessed some remarkably pathological cases of hours-long thrashing until the OOM killer finally managed to step in :)

---

### Post by bobrocks on 2009-01-04
> **CptPicard said:**
> 
Still a bit odd that I manage to get the C++ version to run for 11 to run in 42 seconds and Java is that much slower while on yours it's still within "striking distance". What are your compiler flags? I was pretty heavy-handed, -O3 -fexpensive-optimizations

Argghh with the editing posts, it breaks my head.  Im sure I read that post before minus the question.

What I used:
GCC - 4.1: -O3 -march=nocona
Sun Java 64bit 1.6.0_10

---

### Post by Cracauer on 2009-01-04
Can you post the code so that I have a base to compare?

---

### Post by CptPicard on 2009-01-04
Who and which code? :) The Java version is a few pages back in the thread (there's a link in first post).

I started hacking up something in C for kicks...

---

### Post by Bichromat on 2009-01-04
I compared g++ and Intel's icpc for sizes 11 and 12:

code by Cracauer:
icpc -fast: 0m23.684s   1m42.024s
g++ -O3: 0m24.476s   1m48.400s

original code:
icpc -fast: 0m55.353s   4m32.198s
g++ -O3: 0m52.781s   4m22.613s

java: 0m52.255s   3m55.448s

On the kind of codes I play with (heavy double precision computation), icpc is usually at least 20% faster than g++. Here, there's no clear winner.

Now, where's the Lisp version, CptPicard ? :D

---

### Post by CptPicard on 2009-01-04
> **Bichromat said:**
> 
On the kind of codes I play with (heavy double precision computation), icpc is usually at least 20% faster than g++. Here, there's no clear winner.

Good to know. In the real thing, there actually is quite a lot of double precision math (it becomes a lot, the callbacks are tight spots).

> 
Now, where's the Lisp version, CptPicard ? :D

Right here on my hard drive ;)

I wrote one last spring out of curiosity and desire to get better at CL. I'm not showing though because it contains some details of what I do in those callbacks ... :)

Put short, if you do it the elegant way and map lists etc, all the consing totally kills performance. The faster way is much more imperative, and still conses quite a lot. In the end I couldn't get much difference between Lisp and Java, but it it also was one of my first real Lisp things I wrote...

I can really feel it that these other languages don't have closures, and even Java just barely manages to provide something with a similar feel. At least on Lisp you can trivially pass a lambda to your "iterateNeighbours" function, and most of the rest of the code just falls out as a consequence.

---

### Post by stroyan on 2009-01-04
You may be very interested in the "Judy" dynamic array library from Ubuntu package
libjudy-dev and [http://judy.sourceforge.net/](http://judy.sourceforge.net/).
The Judy library can be an extremely fast replacement for hash tables.
It has an advantage because it explicitly manages its use of memory locations to
place as many accesses as possible in common cache lines.  That makes memory access
much, much faster with modern processors.
Note that the Judy library does not include thread safe locking.
If you are trying to mix array inserts and reads from multiple threads
you will need to use explicit locking operations.

You note that your neighbor visiting operations don't tend to have
decent memory locality.  Some of that is within your control.  You visit
many records in rapid succession at the bottom of your recursion.  If you
allocate the data records accessed by those leaf functions close together
you will have less TLB fault pressure accessing them.  You might even be able
to get some cache line sharing between records.  To take that kind of control
you would need to explicitly locate such similar records near eachother instead
of relying on a map<> or hashmap<> to allocate the storage.  The judy library
could be used to rapidly map index values to addresses that you allocate out
of a buffer.   It looks like you tend to build the big data structure only once
and never free and reallocate memory from records.  That could make the allocation
task much easier to take on in your own code.

---

### Post by CptPicard on 2009-01-05
C version:

[http://www.voittoporukka.fi/~eero/c-analyzer/](http://www.voittoporukka.fi/~eero/c-analyzer/)

Runtime on case 11 is 37 seconds on my box. Essentially the same as C++ with STL hashmap. Admittedly my own hashmap is about as naive as they get :)

---

### Post by CptPicard on 2009-01-05
Wow, this this is *very**hash function sensitive already. Proof that in tight loops little things add up!!

So initially I had a naive hash function that just takes state % array_length. This has a really nasty hash performance -- buckets of 10 (I use load factor of optimal 2 keys per bucket) and then just ten buckets of zero. Yet, it performs best, at the numbers I gave.

Then I found a nicer function that really hashes pretty well:

```

inline unsigned int hash(unsigned int a) {
    a = (a ^ 61) ^ (a >> 16);
    a = a + (a << 3);
    a = a ^ (a >> 4);
    a = a * 0x27d4eb2d;
    a = a ^ (a >> 15);
    return a;
}

```

BUT... runtime is around 1 minute 30 seconds! Hashes fine but computing hash takes more time than actually iterating down lists in buckets.

Then I found Knuth's multiplicative hash for 32 bit ints, simply, multiply by 2654435761 (it's golden ratio of 2^32, it says there are no common factors between the two). Hashing is "ok", runtime around 1 minute... so totally crappy hashing is apparently tolerable.

Then again this suggests that when I actually run anything substantial in the callbacks, it's a whole different ballgame... I am consoled by the fact that our Java tool runs, parallelized over 4 cores, in usable time :)

I still need to give the Judy trees a go, but if a simple mult and mod are worse than using raw keys...

---

### Post by Cracauer on 2009-01-05
Is it possible that this algorithm is sensitive to the order in which the iterator returns keys in computeWinSetSizes?

I wrote a whole bunch of testing code and my hashtable seems to work fine. I even went as far as making a double-backed hashtable that stuffs things into both kinds of hashtable and compares both.

Still, with size 12 and 13 mine goes into an endless loop and I think the difference is order of iterations.

---

### Post by CptPicard on 2009-01-06
Then there is probably something wrong with the implementation... case 13 should not be any different from other cases except for generating 3 times more keys, which get returned in alphabetical order (and, well, the neighbourset sizes are bigger too). Also, it is pretty clear on the C code at least that hash function performance is already something that can throw off performance 2-3x so this is pretty narrowed down now.. :)

BTW it would be very interesting to see what, say, Haskell could do with this problem. The neighbour generation/handling problem is very functional in nature.. any Haskellers up to the challenge? :)

---

### Post by stroyan on 2009-01-06
Your c++ implementation has VakioAnalyzer::computeWinSetSizes loop through values of i from 1 to 3.
Your c implementation has test_node loop through values of i from 0 to 3.
That value of 0 looks very wrong.

The way that you generate neighbors makes it look like the order in which the neighbor nodes is visited is unimportant.
If you actually have the callbacks written such that they can be called in an arbitrary order, then you can potentially double the performance by making two callbacks with the two nodes swapping roles.  You already found a pair at a specific distance from each other.  Perform the callback twice with each of the pair once as the orig and once as the neighbor.  When you are walking through the neighbors in neighbour_recursion use only
higher values of the current digit.

Change ```

        for (i = 0; i < DIGIT_BASE; i++)
            if (i != get_bits(neighbour,pos))

```to```

        for (i = get_bits(neighbour,pos)+1; i < DIGIT_BASE; i++)

```
That way you will visit each pair once.  By making both callbacks at the same time you save half the effort of searching for nodes and get better memory locality since you don't revisit a node after it may have been evicted from cache or TLB.

---

### Post by CptPicard on 2009-01-06
> **stroyan said:**
> 
That value of 0 looks very wrong.

Oops, you are correct, it should be from 1. 0 doesn't actually do anything as it just results in visiting "same item" for which nothing is called, so it's a bug but of no consequence.

> 
If you actually have the callbacks written such that they can be called in an arbitrary order, then you can potentially double the performance by making two callbacks with the two nodes swapping roles.

Yes, I considered this a long time ago already when I was writing the first versions of the code. It would potentially be a big boost, but the issue is keeping track of which pairs were visited already so that the callbacks don't get called twice on some pair... it does not work as simply as you suggest, as adding one to the sub-bits is meaningless (IMO)...

Now, what you CAN do, because the keys have an order, is to always check that for found pair a, b, you only do stuff if (a < b) and then run both callbacks, otherwise quit. This does not save from having to generate, but saves on lookup time which is the bottleneck...

Thanks for the idea, I abandoned this a long time ago when it seemed like generation is the problem, not the data structure... if this were the case this would not be an optimization... looks like now it is :)

---

### Post by stroyan on 2009-01-06
> **CptPicard said:**
> Yes, I considered this a long time ago already when I was writing the first versions of the code. It would potentially be a big boost, but the issue is keeping track of which pairs were visited already so that the callbacks don't get called twice on some pair... it does not work as simply as you suggest, as adding one to the sub-bits is meaningless (IMO)...

Take a closer look at that loop.  By starting at get_bits(neighbour,pos)+1 it always visits each pair only once.

---

### Post by CptPicard on 2009-01-06
> **stroyan said:**
> Take a closer look at that loop.  By starting at get_bits(neighbour,pos)+1 it always visits each pair only once.

:shock: Yes you're right of course.

As the data structure is really the bottleneck here... assuming the algorithm is still correct... it runs at around 13 seconds for size 11 here now (with the Knuth hash) :)

13 minutes 5 secs for case 13. Not bad, considering that this scales easily over n cores...

---

### Post by Cracauer on 2009-01-07
I have something running and it looks like it's faster than STL's hash table. Sorry for the delay, I think I fooled around with Lisp too much lately. I'll post when I get home and had a chance to polish it up, I'm at work right now (home machine runs tests).

Did you change anything about the algorithm? I want to make sure the new stuff is still in sync with what it's doing, exactly.

Can we post the current reference C/C++/Java stuff?

---

### Post by CptPicard on 2009-01-07
This is the C version link, [http://www.voittoporukka.fi/~eero/c-analyzer/](http://www.voittoporukka.fi/~eero/c-analyzer/)

It's got stroyan's optimization (which is a Very Good Point), with the callback called both ways and the small change made to the starting of the loop (only loop through bigger digits). I just fixed the Java too, and runtime for 11 was 16 secs whereas C was 13... very very interesting!

EDIT: Java version case 13 ran at 4 min 12 secs... I am a bit suspicious of its correctness right now... ... and yes, it is buggy, it generates the latter two winclasses wrong... ... and seems like it happens when one just generates the higher keys.. :(

---

### Post by CptPicard on 2009-01-07
OK so Stroyan's original idea is buggy but basic idea seems sound, just need to implement it in a reasonable manner. The reason why the optimization does not work as suggested is this.. consider the very simple case of size 3 and 2-neighbours. Now take key 11X. Key 121 should be a 2-neighbour. This pair is never produced because when we get to 11X, we want to just increase digits, and X is the sticking point. Likewise, when we get to 121, we can't get 2 down to 1.

---

### Post by Cracauer on 2009-01-07
All right.

Original C++ code changed to hash_map on my machine:
503.62user 0.65system 8:27.26elapsed 99%CPU

New code with custom hashtable:
190.78user 0.48system 3:11.79elapsed

[http://www.cons.org/tmp/java-stuff/v3/](http://www.cons.org/tmp/java-stuff/v3/)

Call with size "13" as commandline argument.

It is not robust code, only intended to get the job done. If you have made algorithmic shortcuts in newer versions of your code it is not in here.

On the same machine, the C version from the link posted (with different algorithms with some shortcuts which might be incorrect):
470.66user 0.07system 7:51.13elapsed 99%CPU 

Any link to a current java version?

---

### Post by CptPicard on 2009-01-07
I've been hacking on the Java version to see if I could get stroyan's idea working. I'm not sure, it feels dodgy but numbers from most recent posted version did not seem "obviously wrong"... guess I need to sleep a little and then see this with new eyes, I'm sure the correct implementation is lurking there somewhere ;)

**Yeah I think I got it** :)

Two important changes to neighbourRecursion in the Java version: First, most significant bits get set first in the recursion. This is very important, as they dominate the size of the key of course.

Next: stroyan's per-digit model was changed to a top-level check that makes sure neighbour hasn't been pushed to be less than the original. The logic here is that if with changes to more significant digits we're smaller than original, even if you set all the rest of the bits to 1 you would still be less than the original!

---

### Post by Cracauer on 2009-01-07
> **CptPicard said:**
> I've been hacking on the Java version to see if I could get stroyan's idea working. I'm not sure, it feels dodgy but numbers from most recent posted version did not seem "obviously wrong"... guess I need to sleep a little and then see this with new eyes, I'm sure the correct implementation is lurking there somewhere ;)

Mumble.

If the goal is to compare languages we shouldn't improve the algorithm in one of the language's implementation :)

---

### Post by CptPicard on 2009-01-07
> **Cracauer said:**
> Mumble.

If the goal is to compare languages we shouldn't improve the algorithm in one of the language's implementation :)

Heheh.. true. This is just a rather substantial boost though, it cuts off 50% of data structure access for an essentially trivial change. :)

Well, hacking a flag into the Java version that runs either symmetric or asymmetric callbacks is easy. I'll see about that over weekend or something :)

---

### Post by Cracauer on 2009-01-07
> **CptPicard said:**
> Heheh.. true. This is just a rather substantial boost though, it cuts off 50% of data structure access for an essentially trivial change. :)

Well, hacking a flag into the Java version that runs either symmetric or asymmetric callbacks is easy. I'll see about that over weekend or something :)

Can you just keep track of the algorithm change in your original C++ file? Then I can retrofit my hash stuff.

So that means my version runs twice as fast doing twice as much work? Sweet :) - if it doesn't have a bug.

---

### Post by CptPicard on 2009-01-07
Ok, I'll see about that. Although I have a feeling that it may be easier to hack the relatively minor changes into your code unless it looks very weird/works fundamentally wrong :)

---

### Post by Cracauer on 2009-01-07
> **CptPicard said:**
> Ok, I'll see about that. Although I have a feeling that it may be easier to hack the relatively minor changes into your code unless it looks very weird/works fundamentally wrong :)

Yeah, but either way if I can just diff your old and new C++ code it should be obvious what to do.

---

### Post by CptPicard on 2009-01-08
Ok, so I changed the C++ to reflect what is in the Java code... I didn't test but as the Java and C++ are essentially 1:1 when it comes to the changes, this should work (at least it compiles...).

Nothing to change in the header, but in implementation... new vakioanalyzer.cpp:

```

#include "vakioanalyzer.h"
#include <iostream>



class StateHandlerCallback {
  
private:
  int winclass;
  vakiodata &orig;

public:
  StateHandlerCallback(int w, vakiodata &o) :
    winclass(w), orig(o) {}


  // Ok so this one is symmetric, does things both ways in one go
  void operator() (vakiodata &other) {
    orig.winclass_size[winclass] += 
      other.winclass_size[0];
    other.winclass_size[winclass] +=
      orig.winclass_size[0];
  }

};



VakioAnalyzer::VakioAnalyzer(int row_length) {
  this->row_length = row_length;
  cout << "Created thingy of size " << row_length << endl;
}


int VakioAnalyzer::rowlength() {
  return row_length;
}



void VakioAnalyzer::produce_combinations(int pos, unsigned int state) {

  if (pos == rowlength()) {
    vakiodata &item = data[state];
    item.prob = 0;
  }
  else {
    for (int i = 0; i < 3; i++)
      produce_combinations(pos+1,
			   state | (i << (pos*2)));
	
  }
   
}



unsigned int set_bits(unsigned int orig,
		      unsigned int set_to,
		      unsigned int pos,
		      unsigned int width) {

  unsigned int mask = ((1 << width) - 1) << (pos*width);
  return (orig & (~mask)) | (set_to << (pos*width));

}

unsigned int get_bits(unsigned int i,
		      unsigned int pos,
		      unsigned int width) {
  
  unsigned int mask = ((1 << width) - 1) << (pos * width);
  return (i & mask) >> (pos * width);

}



void VakioAnalyzer::neighbourRecursion(unsigned int orig,
				       unsigned int neighbour,
				       StateHandlerCallback &cb,
				       int left,
				       int pos) {

  map<unsigned int, vakiodata>::iterator it;

  if (left > pos + 1 || neighbour < orig)
    return;
  else if (left == 0) {
    if ((it = data.find(neighbour)) != data.end())
      cb(it->second);
    else
      return;
  }
  else if (pos >= 0) {
    // The case where it is not set to anything, just skipped
    neighbourRecursion(orig, neighbour, cb, left, pos-1);
    // The other cases
    for (unsigned int i = 0; i < 3; i++) {
      if (i != get_bits(orig, pos, 2)) {
	neighbourRecursion(orig,
			   set_bits(neighbour, i, pos, 2),
			   cb,
			   left-1,
			   pos-1);
      }
    }
  }
}



void VakioAnalyzer::neighbourSet(unsigned int state, int k,
				 StateHandlerCallback &cb) {

  neighbourRecursion(state, state, cb, k, row_length);

}



void VakioAnalyzer::init() {

  produce_combinations(0,0);
    
}



string VakioAnalyzer::stateToString(unsigned int state) {

  string s;

  for (int i = 0; i < rowlength(); i++) {

    int state_item = get_bits(state, i, 2);

    if (state_item == 0)
      s = '1' + s;
    else if (state_item == 1)
      s = 'X' + s;
    else if (state_item == 2)
      s = '2' + s;
  }

  return s;

}


unsigned int VakioAnalyzer::parseState(string s) {

  unsigned int result = 0;
  int pos = 0;
  
  for (string::reverse_iterator iter = s.rbegin();
       iter != s.rend();
       iter++) {

    switch (*iter) {

    case 'X':
      result = set_bits(result, 1, pos, 2);
      break;
      
    case '2':
      result = set_bits(result, 2, pos, 2);
      break;
    }
    
    pos++;

  }

  return result;
}



void VakioAnalyzer::computeWinSetSizes() {

  for (data_map_type::iterator 
	 iter = data.begin();
       iter != data.end();
       iter++) {
  
    for (int i = 1; i < 4; i++) {
   
      StateHandlerCallback cb(i, iter->second);

      neighbourSet(iter->first, i, cb);
      
      /*
      cout << stateToString(iter->first) << " "
	   << i << endl;
      */
    }
  }

}


void VakioAnalyzer::test() {

  init();


  cout << "initing material..." << endl;
  init();
  cout << "Inited" << endl;

  cout << "Winset size computation.." << endl;

  computeWinSetSizes();

  cout << "Winset size computation done" << endl;
  
}


```

---

### Post by Cracauer on 2009-01-09
All right.

Your new version with STL hash_map:
6:11.78 371.78 real 370.97 user 0.31 sys 99% CPU 0/49907 faults

Your new version with custom hashtable (useless for anything else):
2:10.80 130.80 real 130.27 user 0.38 sys 99% CPU 0/169084 faults

[http://www.cons.org/tmp/java-stuff/v4/](http://www.cons.org/tmp/java-stuff/v4/)

I made minimal changes to your C++ file to allow compilation both with new and old hash interface. Compile with -DOLD to get your code back. The header file is unchanged from my previous posting.

---

### Post by CptPicard on 2009-01-11
Hmm, problems

```

eneva@manticore:~/analyzertest/cracauerscode$ g++ -O3 -o vakioanalyzer vakioanalyzer4.cpp
In file included from /usr/include/c++/4.3/ext/hash_map:64,
                 from vakioanalyzer3.h:9,
                 from vakioanalyzer4.cpp:4:
/usr/include/c++/4.3/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
In file included from vakioanalyzer4.cpp:4:
vakioanalyzer3.h: In member function ‘void vakiodata::zero()’:
vakioanalyzer3.h:49: error: ‘bzero’ was not declared in this scope

```


The plot thickens, though, as standard C++ version is

```

eneva@manticore:~/analyzertest/cracauerscode$ time ./vakioanalyzer 11
Created thingy of size 11
initing material...
Inited
Winset size computation..
Winset size computation done

real    0m37.317s
user    0m36.942s
sys     0m0.036s

```

While Java is

```

eneva@manticore:~/analyzertest$ time java Analyzer
Initialized data... map has 177147 items
Computing winsets took 59616 ms


real    1m1.347s
user    0m54.867s
sys     0m0.248s

```

This difference is around what I have been expecting all along, but of course your hashing strategy potentially makes another algorithmic difference to the whole thing...

---

### Post by Kilon on 2009-01-11
So can we have a sum up of the whole process? What is your first conclusion , which is faster, when and why ?

---

### Post by CptPicard on 2009-01-11
Well first of all, the C++ treemap solution was very bad. Using normal hashmap vs. Java's standard library HashMap produces a fairly typical ~30-40% speed disadvantage for Java. Java's memory consumption is pretty atrocious in comparison though...

I still don't have a good opinion on Cracauer's hashmap because I couldn't compile it, but if the ratio of his runtimes hold true, it should be substantially the fastest approach. However, I am not sure how much of that improvement would translate to Java if I implemented his strategy over there...

Hey, as a fun point of comparison, is anyone up to doing a Python version or something? :D

---

### Post by Cracauer on 2009-01-11
Please add 
#include <strings.h>
to the header file to fix the error you get on gcc-4.3

That version should be much faster.

---

### Post by Cracauer on 2009-01-11
Oh and we need to find somebody with a Windoze system to run the Java version on the different JVMs with JITs that aren't available on Linux.

---

### Post by CptPicard on 2009-01-11
```

real    0m17.706s
user    0m16.993s
sys     0m0.440s

```

Yeah, your hash destroys anything else so far. Need to dig into it a little to see how much of it I could reproduce.. :)

---

### Post by Cracauer on 2009-01-11
All right. Just keep in mind it's really specialized for this task.

I used this style of hashtable in the past with good success, but for this problem I was struggling. The reason is that the possible number of elements is so vastly different. The highly exponential nature of the algorithm make brute-force hash lookup like mine fragile. Just activate the "shake_bits" option and see how the better distribution of hash values and less collisions destroy the performance advantage :)

Having said that this style works very well when the number of elements is knows within -say- an order of magnitude. I think I first used it on the nationwide identifier numbers of German towns. They don't add too many of those per year.

Anyway, if you want to get another speed boost out of this thing, the way to go is to seal the thing after you are finished consing up value pairs. The read/write hashtable gets converted once to something that optimizes based on the now known set of keys. It's definitely worth it here.

---

### Post by CptPicard on 2009-01-11
GCJ native-compilation (-O3 -fexpensive-optimizations) is 50% slower than normal Java... I wonder if the hashmap it links to is trash...

```

real    1m34.778s
user    1m33.814s
sys     0m0.156s

```

---

### Post by Cracauer on 2009-01-11
> **CptPicard said:**
> GCJ native-compilation (-O3 -fexpensive-optimizations) is 50% slower than normal Java... I wonder if the hashmap it links to is trash...

```

real    1m34.778s
user    1m33.814s
sys     0m0.156s

```

I'm not up-to-date with what Java JITs are doing, but the problem we are discussing here is actually a prime exactly of where it can be useful. If you discover that a very tight loop (or recursion) over few functions hammers lookups in a hashtable, you obviously want to recompile the thing to at least have inline hash lookup, if not unroll the loops. Tail recursion might be another factor here.

---

### Post by CptPicard on 2009-01-11
> **Cracauer said:**
> Tail recursion might be another factor here.

Actually, if the bottleneck were in the neighbour-generator-recursion, the current implementation is certainly stupid -- a smarter one probably would divide the vector in half, recurse down each half and then when it hits a case of "cycle under < 3 items" that could be implemented straight in nested loops. Actually, the whole thing could be done using nested loops already (as there is never a bigger one than the 3-neighbour set), but I like keeping some generality in this example for the sake of intellectual interest -- although in the "real thing" I'm certainly applying the KISS principle here ;)

I am going to try in Java a simple perfect hash where the keys are simply numbered according to the base-3 number they represent, and that is used as array index. The "powers of 3 * digit" are easy to precompute in lookup table, so for case-n, you get at most n adds (you can skip for the '00' digit) and RAM economy is as good as it can get for the case where the entire 3^n-space is in use.

---

### Post by Cracauer on 2009-01-11
I think that gcc is basically unable to do any kind of optimization on recursion. That is fine for C/C++ which have fast function calls. But I wonder whether the Java code compiled from gcc follows a more elaborate calling convention.

---

### Post by Kilon on 2009-01-11
> **CptPicard said:**
> Well first of all, the C++ treemap solution was very bad. Using normal hashmap vs. Java's standard library HashMap produces a fairly typical ~30-40% speed disadvantage for Java. Java's memory consumption is pretty atrocious in comparison though...

I still don't have a good opinion on Cracauer's hashmap because I couldn't compile it, but if the ratio of his runtimes hold true, it should be substantially the fastest approach. However, I am not sure how much of that improvement would translate to Java if I implemented his strategy over there...

Hey, as a fun point of comparison, is anyone up to doing a Python version or something? :D

Thanks for the clarification. Python comparison will surely be interesting. Too bad I do not understand what the hell your are doing ! LOL

---

### Post by Branimir on 2009-01-29
Perhaps Im stupid but this executes:

bmaxa@maxa:~$ g++ -Wall -O3 vakio.cpp -o vakio
bmaxa@maxa:~$ time ./vakio
Created thingy of size 13
initing material...
Inited
Winset size computation..
elements:1594323
Winset size computation done

real	0m1.432s
user	0m1.048s
sys	0m0.344s
bmaxa@maxa:~$ 

e8400 overclocked to 3.6 ghz

```

//#include <map>
#include <string>
#include <vector>
#include <functional>

const unsigned int MAX = 4000000;

using namespace std;


struct vakiodata{

  int winclass_size[4];
  double exp_components[4];

  double prob;
  double kelly;
  bool unini;
  vakiodata()
  {
    unini = true;
  }
};

typedef vector<vector<vakiodata> > data_map_type;

class StateHandlerCallback;

class VakioAnalyzer {
  
 private:
 
  data_map_type data;

  int row_length;

  void produce_combinations(int, unsigned int);
  string stateToString(unsigned int state);
  
  void neighbourSet(unsigned int state, int k,
		    StateHandlerCallback&);

  void neighbourRecursion(unsigned int, 
			  unsigned int,
			  StateHandlerCallback&,
			  int, 
			  int);

  unsigned int parseState(string);
  void computeWinSetSizes();

 public:
  VakioAnalyzer(int row_length);
  int rowlength();
  void init();
  void test();
};

#include <iostream>

class StateHandlerCallback {
  
private:
  data_map_type &datamap;
  int winclass;
  vakiodata &orig;

public:
  StateHandlerCallback(data_map_type &m,
		       int w, vakiodata &o) :
    datamap(m), winclass(w), orig(o) {}

  void operator() (vakiodata &other) {
    orig.winclass_size[winclass] += 
      other.winclass_size[0];
  }

};



VakioAnalyzer::VakioAnalyzer(int row_length) {
  this->row_length = row_length;
  cout << "Created thingy of size " << row_length << endl;
}


int VakioAnalyzer::rowlength() {
  return row_length;
}



void VakioAnalyzer::produce_combinations(int pos, unsigned int state) {

  
  if (pos == rowlength()) {
  if(state%MAX>=data.size())data.resize(state%MAX+1);
  if(state/MAX>=data[state%MAX].size())data[state%MAX].resize(state/MAX+1);
    vakiodata &item = data[state%MAX][state/MAX];
    item.prob = 0;
    item.unini = false;
  }
  else {
    for (int i = 0; i < 3; ++i)
      produce_combinations(pos+1,
			   state | (i << (pos*2)));
	
  }
   
}



unsigned int set_bits(unsigned int orig,
		      unsigned int set_to,
		      unsigned int pos,
		      unsigned int width) {

  unsigned int mask = ((1 << width) - 1) << (pos*width);
  return (orig & (~mask)) | (set_to << (pos*width));

}

unsigned int get_bits(unsigned int i,
		      unsigned int pos,
		      unsigned int width) {
  
  unsigned int mask = ((1 << width) - 1) << (pos * width);
  return (i & mask) >> (pos * width);

}



void VakioAnalyzer::neighbourRecursion(unsigned int orig,
				       unsigned int neighbour,
				       StateHandlerCallback &cb,
				       int left,
				       int pos) {

  unsigned int it,it1;

 if (left > pos+1 || neighbour < orig)
   return;
      
  else if (left == 0){ if(neighbour != orig &&
      (it = neighbour%MAX) < data.size() && 
      (it1 = neighbour/MAX) < data[it].size() &&
      data[it][it1].unini==false) {
    cb(data[it][it1]);
    }
  }
  else if(pos>=0){

    // The case where it is not set to anything, just skipped
    neighbourRecursion(orig, neighbour, cb, left, pos-1);
    // The other cases
 
    for (unsigned int i = 0; i < 3; ++i) {
      if (i != get_bits(orig, pos, 2)) {
	neighbourRecursion(orig,
			   set_bits(neighbour, i, pos, 2),
			   cb,
			   left-1,
			   pos-1);
      }
    }
  }
}



void VakioAnalyzer::neighbourSet(unsigned int state, int k,
				 StateHandlerCallback &cb) {

  neighbourRecursion(state, state, cb, k, 0);

}



void VakioAnalyzer::init() {

  produce_combinations(0,0);
    
}






string VakioAnalyzer::stateToString(unsigned int state) {

  string s;

  for (int i = 0; i < rowlength(); ++i) {

    int state_item = get_bits(state, i, 2);

    if (state_item == 0)
      s = '1' + s;
    else if (state_item == 1)
      s = 'X' + s;
    else if (state_item == 2)
      s = '2' + s;
  }

  return s;

}


unsigned int VakioAnalyzer::parseState(string s) {

  unsigned int result = 0;
  int pos = 0;
  
  for (string::reverse_iterator iter = s.rbegin();
       iter != s.rend();
       ++iter) {

    switch (*iter) {

    case 'X':
      result = set_bits(result, 1, pos, 2);
      break;
      
    case '2':
      result = set_bits(result, 2, pos, 2);
      break;
    }
    
    pos++;

  }

  return result;
}



void VakioAnalyzer::computeWinSetSizes() {

  unsigned cnt=0;
  for (unsigned int j =0; 
	 j != data.size();
       ++j) 
   for(unsigned jj=0;
       jj!=data[j].size();
       ++jj) {
       if(data[j][jj].unini == true)continue;
       ++cnt;//continue;
    for (int i = 1; i < 4; i++) {
   
      StateHandlerCallback cb(data, i, data[j][jj]);

      neighbourSet(j, i, cb);
      
      /*
      cout << stateToString(iter->first) << " "
	   << i << endl;
      */
    }
  }
  cout<<"elements:"<<cnt<<'\n';

}


void VakioAnalyzer::test() {

  init();


  cout << "initing material..." << endl;
  init();
  cout << "Inited" << endl;

  cout << "Winset size computation.." << endl;

  computeWinSetSizes();

  cout << "Winset size computation done" << endl;
  
}

int main()
{
  VakioAnalyzer a(13);
  a.test();
}

```

Perhaps Ive mistaken somewhere?
Recursive search is done based on corrected java version.

edit:
with proper initialization:
```

void VakioAnalyzer::neighbourSet(unsigned int state, int k,
                                 StateHandlerCallback &cb) {

  neighbourRecursion(state, state, cb, k, rowlength()-1);
// my error was
}



```
bmaxa@maxa:~$ time ./vakio
Created thingy of size 13
initing material...
Inited
Winset size computation..
elements:1594323
Winset size computation done

real	1m41.392s
user	1m40.938s
sys	0m0.428s


Greets, Branimir.

---

### Post by CptPicard on 2009-01-29
Hmm.. you are almost certainly doing something wrong, your C++ running time seems pretty wild :) Don't have the time to investigate right now though...

---

