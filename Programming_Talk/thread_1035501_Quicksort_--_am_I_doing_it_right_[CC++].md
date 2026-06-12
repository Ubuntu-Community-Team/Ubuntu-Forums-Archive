---
title: "Quicksort -- am I doing it right? [C/C++]"
date: 2009-01-09
forum: Programming Talk
---

### Post by Znupi on 2009-01-09
Well, I'm studying for some exams I'll be taking this year (going to college) and it seems I missed the class when quicksort was taught. So I used the all-mighty knowledge source - Wikipedia to learn it, but I'm not very sure I've done it right. Here's my implementation:
```

#include <iostream>
#include <fstream>
using namespace std;
int v[100], n=0;

void quicksort(int start, int end) {
	if (start >= end || start < 0 || end > n) return;
	int aux, i, poz = end;
	for (i=start; i < poz; i++) {
		if (v[i] > v[poz]) {
			aux = v[i];
			v[i] = v[poz-1];
			v[poz-1] = v[poz];
			poz--;
			v[poz+1] = aux;
			i--;
		}
	}
	quicksort(start, poz-1);
	quicksort(poz, end);
}

int main() {
	ifstream f("datafiles/v3.3.txt");
	int i;
	while (!f.eof()) {
		f>>v[n++];
	}
	if (!n) {
		cout<<"No numbers?";
		return 0;
	}
	quicksort(0, n-1);
	for (i=0; i < n; i++)
		cout<<v[i]<<" ";
	return 0;
}

```
Can you tell me if it's right? Also, please excuse me using cout<< and cin>>, I know I should to use printf() and scanf() but it's just the way they taught us at school.

---

### Post by kjohansen on 2009-01-09
sorting is pretty easy to test....  try some different inputs and see if it works.

---

### Post by drubin on 2009-01-09
> **kjohansen said:**
> sorting is pretty easy to test....  try some different inputs and see if it works.

Sorting can be some of the most complex algorithms to work with. And since the quick sort is not a in order sort some sub sets of data my appear to be sorted where others wont be.

---

### Post by monkeyking on 2009-01-09
> **drubin said:**
> Sorting can be some of the most complex algorithms to work with. And since the quick sort is not a in order sort some sub sets of data my appear to be sorted where others wont be.

On each call he can check the loop variant condition.
That is,

all elements before the pivot should be smaller,
all elements after the pivot should be greater.

It should be easy to check.

---

### Post by CptPicard on 2009-01-10
Interesting way the OP is swapping values inside the loop... it seems to work, but admittedly is somewhat hard to read :)

---

### Post by Znupi on 2009-01-10
Here's a hopefully more readable version, with a few comments and this one reads directly from stdin so you can easily compile it and test it. Maybe I'll post a schematic of how it works (I'd do anything to draw schematics!):
```
#include <iostream>
using namespace std;
int v[100], n=0;

void quicksort(int start, int end) {
	if (start >= end || start < 0 || end > n) return;
	int aux, i, pivot = end; // we set the pivot at the end of the partition
	for (i=start; i < pivot; i++) {
		if (v[i] > v[pivot]) {
			// we move greater elements after the pivot, like this:
			// 1. we swap the element right before the pivot with the current element
			// 2. we move the pivot one position back
			// 3. in the now open position after the pivot, we put the greater element
			aux = v[i];
			v[i] = v[pivot-1];
			v[pivot-1] = v[pivot];
			pivot--;
			v[pivot+1] = aux;
			i--;
		}
	}
	quicksort(start, pivot-1);
	quicksort(pivot, end);
}

int main() {
	int i;
	do {
		cout<<"n: ";
		cin>>n;
	}
	while (n < 0 && n > 100);
	for (i=0; i < n; i++) {
		cout<<i<<": ";
		cin>>v[i];
	}
	quicksort(0, n-1);
	for (i=0; i < n; i++)
		cout<<v[i]<<" ";
	cout<<endl;
	return 0;
}
```

---

### Post by CptPicard on 2009-01-10
This is a pretty good example why I wouldn't want to mix teaching of algorithms and C, as I argued in another thread... the concept is much clearer in Python, and the ability to get your indexes and other variables right adds nothing to actual understanding of the core idea:

```


def qsort(li):

  if len(li) <= 1:
    return li

  pivot = li[0]
  rest = li[1:]

  smaller = [x for x in rest if x <= pivot]
  bigger = [x for x in rest if x > pivot]

  return qsort(smaller) + [pivot] + qsort(bigger)


```

---

### Post by Znupi on 2009-01-10
Indeed, higher-level programming languages offer a much wider set of tools that aid in understanding algorithms. Unfortunately, my exams will test my C/C++ knowledge.

Schematic!
[IMG]http://i498.photobucket.com/albums/rr348/Znupi2/quicksort.png[/IMG]

---

