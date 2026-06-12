---
title: "sorting my structs"
date: 2009-01-10
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-10
i have

[PHP]
struct Letter
{
     int code, timesFound;
     char ascii;
};
[/PHP]

what do i need for std::sort to sort this by timesFound?

---

### Post by jimi_hendrix on 2009-01-10
or any other way to sort it (i prefer not to have to hand code)

---

### Post by monkeyking on 2009-01-10
I did something like this some months ago, not beautifull, but fast coding.

put them in a priority queue.
edit:

I remember I also used an associative array
I haven't checked the code, but try some thing like

[PHP]
//key, container for your keys, the partial ordering
priority_queue<int, vector<int>, greater <int>  > Q
map<int, int>  mapping;
vector<YOURSTRUCT> IN
for(int i=0;i<NUMBEROFSTRUCTS;i++){
  Q.push(timesFoundID);
  mapping[YOURSTRUCT[i]] =  i;
}
[/PHP]

You should now pop your priority_queue and look up their value in associative array.
an ascending order would be
item.at(mapping.find(Q.pop()))

hope it makes sense, you might also need a q.top() argument

---

### Post by dwhitney67 on 2009-01-10
I assume the language in use is C++ (and not C):

Try something like:
[php]
#include <vector>
#include <algorithm>

...

bool sortLetters(const Letter& left, const Letter& right)
{
  return left.timesFound < right.timesFound;
}

int main()
{
  std::vector<Letter> letters;

  // populate vector

  // sort
  std::sort(letters.begin(), letters.end(), sortLetters);

  // ...
}
[/php]

---

### Post by jimi_hendrix on 2009-01-10
yes C++

---

### Post by jimi_hendrix on 2009-01-10
whats that last param you pass to std sort?

---

### Post by kjohansen on 2009-01-10
the last arg in std::sort is the custom comparison operator.

it is telling the sort to use the function he defined, this way you can tell it to sort by some field in the struct...  sort knows how to compare the built in types like int but needs explicit instructions to sort non built in types.

alternatively you could override the less than operator in your struct or class....


```

struct Letter
{
     int code, timesFound;
     char ascii;

     bool operator<(Letter par)
     {
        return(timesFound<par.TimesFound)
     }
};


int main(...

  std::vector<Letter> letters;

  // populate vector

  // sort
  std::sort(letters.begin(), letters.end());   //eliminate the parameter


```

---

### Post by dwhitney67 on 2009-01-10
> **kjohansen said:**
> the last arg in std::sort is the custom comparison operator.

it is telling the sort to use the function he defined, this way you can tell it to sort by some field in the struct...  sort knows how to compare the built in types like int but needs explicit instructions to sort non built in types.

alternatively you could override the less than operator in your struct or class....


```

struct Letter
{
     int code, timesFound;
     char ascii;

     bool operator<(Letter par)
     {
        return(timesFound<par.TimesFound)
     }
};


int main(...

  std::vector<Letter> letters;

  // populate vector

  // sort
  std::sort(letters.begin(), letters.end());   //eliminate the parameter


```

+1

But the operator<() method should be defined as const, and to save "energy", it's best to pass the object by reference:
```

bool operator<(const Letter& other) const
{
  ...
}

```

---

