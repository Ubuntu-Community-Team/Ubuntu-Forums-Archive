---
title: "double loop in vector C++"
date: 2009-02-26
forum: Programming Talk
---

### Post by diamantis13 on 2009-02-26
Hi,
I have a vector of objects and I would like to access them in pairs of i,j where i>=j. Perhaps I am only used to thinking with simple arrays, but I tried something like:
```

  int a =0;
  for (vector<int>::iterator i = v.begin();
       i != v.end(); ++i){
    a++;
    for(vector<int>::iterator j = v.at(a-1);
	j != v.end(); ++j){
      cout <<i<<' '<<j<<endl;
    }
  }

```
which doesn't seem to work. Is there a nice way of doing this?
Thank you!

---

### Post by stumbleUpon on 2009-02-26
> **diamantis13 said:**
> Hi,
I have a vector of objects and I would like to access them in pairs of i,j where i>=j. Perhaps I am only used to thinking with simple arrays, but I tried something like:
```

  int a =0;
  for (vector<int>::iterator i = v.begin();
       i != v.end(); ++i){
    a++;
    for(vector<int>::iterator j = v.at(a-1);
	j != v.end(); ++j){
      cout <<i<<' '<<j<<endl;
    }
  }

```
which doesn't seem to work. Is there a nice way of doing this?
Thank you!



How about this?

```

for(int i = 0; i < n; i++)
  for(int j = i; j < n; j++)
    cout<<i<<"  "<<j<<endl;

```

n is the maximum size.

---

### Post by Npl on 2009-02-26
If you want to use iterators, do it like this:
```

  for (vector<int>::iterator i = v.begin();
       i != v.end(); ++i){
    vector<int>::iterator j = v.begin();
    while (true) {
       cout << *i << ' ' << *j << endl;
       if( j == i)
          break;
       ++j;
    }
  }

```

---

### Post by diamantis13 on 2009-02-27
> **Npl said:**
> If you want to use iterators, do it like this:
```

  for (vector<int>::iterator i = v.begin();
       i != v.end(); ++i){
    vector<int>::iterator j = v.begin();
    while (true) {
       cout << *i << ' ' << *j << endl;
       if( j == i)
          break;
       ++j;
    }
  }

```

The code you give will print out the pairs in a different order 
if the vector is 1 2 3 4 then the output would be:
1 1
2 1
2 2
3 1
3 2
3 3
4 1
4 2
4 3
4 4
but what I am trying to create is something similar with a double loop through an array that would output:
1 1
1 2
1 3
1 4
2 2
2 3
2 4
3 3
3 4
4 4
and it seems that I cannot compare an iterator with a reverse iterator!

---

### Post by krazyd on 2009-02-27
I've got a quick test program which seems to do what you want. Have a look at the nested for loops specifically.

```
#include<iostream>
#include<vector>

using std::cout;
using std::vector;
using std::endl;
using std::cin;

int main() {
	vector<int> v;
	int input;
	
	while(cin >> input)
		v.push_back(input);
		
	for (vector<int>::iterator i = v.begin(); i != v.end(); ++i) {		
		for (vector<int>::iterator j = i; j != v.end(); ++j) {
			cout << *i << ' ' << *j << endl;
		}
	}
	
	return 0;
}
```

---

### Post by Npl on 2009-02-27
> **diamantis13 said:**
> The code you give will print out the pairs in a different order 
if the vector is 1 2 3 4 then the output would be:
1 1
2 1
2 2
3 1
3 2
3 3
4 1
4 2
4 3
4 4
but what I am trying to create is something similar with a double loop through an array that would output:
1 1
1 2
1 3
1 4
2 2
2 3
2 4
3 3
3 4
4 4
and it seems that I cannot compare an iterator with a reverse iterator!Well, you specifically asked for pairs i j, with i>=j. Im no psychic to know what you said is the opposite of what you want ;)

---

