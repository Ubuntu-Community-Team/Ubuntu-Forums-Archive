---
title: "Advanced programming exercise: Power set"
date: 2011-06-11
forum: Programming Talk
---

### Post by slavik on 2011-06-11
This particular exercise is not very complicated (should take 15min once you know the algorithm), but I feel it is nonetheless important for anyone to be able to do this.

The idea is that given a bunch of items to generate/output all combinations of the items.

The algorithm that you should eventually discover should be O(2^n).

---

### Post by NovaAesa on 2011-06-11
Do you mean O(2^n) rather than O(n^2)?

Consider a set S whose cardinality is n. Then the cardinality of P(S) is 2^n, so you would need an algorithm at least as complex as O(2^n) to produce P(S).

EDIT:
My answer in scheme:
```

(define (power-set set)
  (if (null? set) '(())
      (let ((r (power-set (cdr set))))
           (append r
                   (map (lambda (subset)
                          (cons (car set) subset))
                        r)))))

```

---

### Post by slavik on 2011-06-11
> **NovaAesa said:**
> Do you mean O(2^n) rather than O(n^2)?

Consider a set S whose cardinality is n. Then the cardinality of P(S) is 2^n, so you would need an algorithm at least as complex as O(2^n) to produce P(S).

EDIT:
My answer in scheme:
```

(define (power-set set)
  (if (null? set) '(())
      (let ((r (power-set (cdr set))))
           (append r
                   (map (lambda (subset)
                          (cons (car set) subset))
                        r)))))

```
fixed, thanks.

---

### Post by krazyd on 2011-06-11
Non-recursive, in ruby

```
#!/usr/bin/ruby

def power_set set
    p_set = []

    (0..2**set.size-1).each do |bin_size|
        subset = []
        bin_size.to_s(2).split(//).reverse.each_with_index do |b,i|
            subset << set[-i-1] if b == "1"
        end
        p_set << subset
    end

    p_set
end

a = [1,2,3,4]

p power_set a

```

---

### Post by Reiger on 2011-06-11
This is where Haskell shines:

```

{-
 - The idea is to generate a conceptually infinite list of “tails”
 - of the input list, then take as many elements from it as we know
 - that the real powerset will contain.
 -
 - Haskells lazy evaluation will then magically solve all problems.
 - The $ to avoid a few parentheses, the let... in construct allows
 - us to explicitly evaluate length x only once.
--}
powerset = (\x-> let l = length x in take (2^l) $ iterate tail x)

```

---

### Post by Thewhistlingwind on 2011-06-11
> **slavik said:**
> 
The idea is that given a bunch of items to generate/output all combinations of the items.




As a number, or actually output all of them? (The latter is more interesting.)

---

### Post by slavik on 2011-06-11
> **Thewhistlingwind said:**
> As a number, or actually output all of them? (The latter is more interesting.)
what you quoted is the answer to your question. :)

---

### Post by BkkBonanza on 2011-06-11
Are you expecting code for set of any size N, or are we able to assume some limit?
I'd like to play with enumerating sets by counting to 2^N but if more than 32 items it gets a bit messy without having BIGNUM type math handy. At least that's what I initially see here.

---

### Post by Thewhistlingwind on 2011-06-11
> **slavik said:**
> what you quoted is the answer to your question. :)

Well if it wasn't ambiguous I wouldn't be asking.

---

### Post by slavik on 2011-06-11
> **Thewhistlingwind said:**
> Well if it wasn't ambiguous I wouldn't be asking.
it does say to output every combination. :)

---

### Post by slavik on 2011-06-11
> **BkkBonanza said:**
> Are you expecting code for set of any size N, or are we able to assume some limit?
I'd like to play with enumerating sets by counting to 2^N but if more than 32 items it gets a bit messy without having BIGNUM type math handy. At least that's what I initially see here.
assume any limit you want :)

if you want to limit yourself to n^32, feel free. idea is that there is a bunch of things and you need all combinations of those items.

---

### Post by BkkBonanza on 2011-06-11
Here's my first crack with shell version of Power Set...

```

# shell script to demo power set enumeration

echo "Enter items (separate with space or enter, end with Ctrl-D)"
items=( $( </dev/stdin ) )
echo
x=0
while [[ $x -lt 2**${#items[*]} ]]; do
  c=0
  echo -n "{"
  while [[ $c -lt ${#items[*]} ]]; do
    if [[ $(($x & 2**$c)) -ne 0 ]]; then
      echo -n "${items[$c]},"
    fi
    c=$(($c+1))
  done
  echo "}"
  x=$(($x+1))
done

```

Sample run:

$ ./ps
Enter items (separate with space or enter, end with Ctrl-D)
sally jill
sue
fran

{}
{sally,}
{jill,}
{sally,jill,}
{sue,}
{sally,sue,}
{jill,sue,}
{sally,jill,sue,}
{fran,}
{sally,fran,}
{jill,fran,}
{sally,jill,fran,}
{sue,fran,}
{sally,sue,fran,}
{jill,sue,fran,}
{sally,jill,sue,fran,}

---

### Post by slavik on 2011-06-11
judging by the quick responses, I think next exercise will go up tomorrow ...

---

### Post by worseisworser on 2011-06-11
[http://paste.lisp.org/display/36657](http://paste.lisp.org/display/36657)

..i think i had a much shorter version of that laying around somewhere, but dunno.. :)

---

### Post by slavik on 2011-06-12
My solution I wrote in 2008, was intended to be an OpenMP program, but that didn't work out for some reason.

```

/*
 *      combinations.c
 *      
 *      Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
 *      
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *      
 */

#include <stdio.h>
#include <omp.h>

#define ITEMS 26

inline unsigned long long int po2 (unsigned int p) {
	unsigned long long int ret = 1;
	while (p-- > 0) ret <<= 1;
	return ret;
}

int main(int argc, char** argv)
{
	int items[ITEMS] = {'A','B','C','D','E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};
	unsigned long long int max = po2(ITEMS) - 1;
	unsigned long long int counter = 0;
	unsigned long long int tmpcounter;
	unsigned long long int c;
	//omp_set_num_threads(4);

//#pragma omp parallel for default(none) shared(max, items) private(counter, tmpcounter, c)
	for (counter = 0; counter <= max; counter++) {
		tmpcounter = counter;
		c = 0;
		while (tmpcounter > 0) {
			if (tmpcounter & 1) {
				printf("%c,", items[c]);
			}
			tmpcounter >>= 1;
			c++;
		}
		printf("\b.\n");
	}
	return 0;
}

```

---

### Post by krazyd on 2011-06-12
> **Reiger said:**
> This is where Haskell shines:

```

{-
 - The idea is to generate a conceptually infinite list of &#8220;tails&#8221;
 - of the input list, then take as many elements from it as we know
 - that the real powerset will contain.
 -
 - Haskells lazy evaluation will then magically solve all problems.
 - The $ to avoid a few parentheses, the let... in construct allows
 - us to explicitly evaluate length x only once.
--}
powerset = (\x-> let l = length x in take (2^l) $ iterate tail x)

```

I don't know Haskell at all, but this is very impressive. Is it O(2^n)?

---

### Post by JupiterV2 on 2011-06-12
I thought I'd post my solution in C:

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

/* USER: change type to int, char, or char* */
typedef int type;

struct map {
    int key;
    type value;
};

void
power_set (type* arr, const int sz)
{
    int i;
    int x = 1;
    struct map* m = malloc (sizeof (struct map) * sz);
    
    for (i = 0; i < sz; i++)
      {
        m[i].key = x << i;
        m[i].value = arr[i];
      }
    
    printf ("{ ");
    
    for (i = 0; i < pow (2, sz); i++)
      {
        int tmp = i;
        
        printf ("{");
        
        for (x = sz - 1; x >= 0; x--)
          {
            if (tmp - m[x].key >= 0)
              {
                /* USER: change format to %d, %c, or %s based on 'type' */
                printf ("%d", (type) m[x].value);
                tmp -= m[x].key;
              }
          }
        printf ("}, ");
      }
    printf ("}\n");
}

int
main (void)
{
/* USER: Uncomment one of the following sets in accordance to the 'type'
    selected */

/*    type   set0[] = {1, 2, 3};*/
    type   set1[] = {1, 2, 3, 4, 5};
/*    type  set2[] = {'A', 'B', 'C', 'D', 'E'};*/
/*    type* set3[] = {"ape", "bat", "cat", "dog", "elephant", "frog", "gnat"};*/
    
/*    power_set ((void*) set0, sizeof (set0) / sizeof (int));*/
    power_set ((void*) set1, sizeof (set1) / sizeof (int));
/*    power_set ((void*) set2, sizeof (set2) / sizeof (char));*/
/*    power_set ((void*) set3, sizeof (set3) / sizeof (char*));*/
    
    return 0;
}
```

Due to the strong typing of C, I couldn't think of a truly generic system, so this is the closest I could hack together. I provided 4 test sets to demonstrate how it works.

My result set from the second power set:
```
{ {}, {1}, {2}, {21}, {3}, {31}, {32}, {321}, {4}, {41}, {42}, {421}, {43}, {431}, {432}, {4321}, {5}, {51}, {52}, {521}, {53}, {531}, {532}, {5321}, {54}, {541}, {542}, {5421}, {543}, {5431}, {5432}, {54321}, }
```

Time:
real	0m0.002s
user	0m0.000s
sys	0m0.000s

[EDIT]It occurred to me this morning that my solution could be improved in two ways: 1) I could increase efficiency and eliminate the need for the use of a math library by doing a simple bit-shift in my 2nd for loop (for (i = 0; i < (1 << sz); i++)), and 2) I could increase the maximum length of the power set by increasing my iterators from int to long int or even long long int. I could squeeze an extra bit out by making them unsigned too. That said, I left my submission to stand as it does without modification.[/EDIT]

---

### Post by kingtaurus on 2011-06-12
Solution using templates in C++ 
(1) it relies upon the fact that elements are unique in std::set<type>

```

#include <iostream>
#include <set>

using namespace std;

typedef set<int>      int_set;
typedef set<int_set>  power_set;
typedef set<char>     char_set;
typedef set<char_set> power_char_set;

template <typename T>
set<set<T> > make_power_set(const set<T> & a_set, set<set<T> >& power_set)
{
	typedef typename set<T>::const_iterator set_citer;

	power_set.insert(a_set);//add the set;

	for(set_citer iter = a_set.begin(); iter != a_set.end(); ++iter)
	{
		set<T> copied_set(a_set);//copy the set ( subsequent operations are done on the copy)
		copied_set.erase(*iter);//erase the element in copied_set
		make_power_set(copied_set, power_set);//call make_power_set
	}
	return power_set;
}

int main(int argc, char * argv[])
{
	int numbers[] = {0, 1, 2, 3, 4};
	int_set current_set(numbers, numbers + 5);
	
	char char_array[] = {'a','b','c','d','e','f'};
	char_set my_char_set(char_array, char_array + 6);

	power_set a;
	make_power_set(current_set, a);

	power_char_set b;
	make_power_set(my_char_set, b);

	cout << "size of current_set = " << current_set.size() << endl;
	cout << "size of power_set a = " << a.size() << endl;
	cout << "size of my_char_set = " << my_char_set.size() << endl;
	cout << "size of power_set b = " << b.size() << endl;

	for(power_set::iterator iter = a.begin();
			iter != a.end();
			++iter)
	{
		cout << "{ ";
		char const* prefix = "";
		for(int_set::iterator iter2 = iter->begin();
				iter2 != iter->end();
				++iter2)
		{
			std::cout << prefix << *iter2;
			prefix = ", ";
		}
		cout << " }\n";
	}

	for(power_char_set::iterator iter = b.begin();
			iter != b.end();
			++iter)
	{
		cout << "{ ";
		char const* prefix = "";
		for(char_set::iterator iter2 = iter->begin();
				iter2 != iter->end();
				++iter2)
		{
			std::cout << prefix << *iter2;
			prefix = ", ";
		}
		cout << " }\n";
	}

	return 0;
}

```

Output:
```

size of current_set = 5
size of power_set a = 32
size of my_char_set = 6
size of power_set b = 64
{  }
{ 0 }
{ 0, 1 }
{ 0, 1, 2 }
{ 0, 1, 2, 3 }
{ 0, 1, 2, 3, 4 }
{ 0, 1, 2, 4 }
{ 0, 1, 3 }
{ 0, 1, 3, 4 }
{ 0, 1, 4 }
{ 0, 2 }
{ 0, 2, 3 }
{ 0, 2, 3, 4 }
{ 0, 2, 4 }
{ 0, 3 }
{ 0, 3, 4 }
{ 0, 4 }
{ 1 }
{ 1, 2 }
{ 1, 2, 3 }
{ 1, 2, 3, 4 }
{ 1, 2, 4 }
{ 1, 3 }
{ 1, 3, 4 }
{ 1, 4 }
{ 2 }
{ 2, 3 }
{ 2, 3, 4 }
{ 2, 4 }
{ 3 }
{ 3, 4 }
{ 4 }
{  }
{ a }
{ a, b }
{ a, b, c }
{ a, b, c, d }
{ a, b, c, d, e }
{ a, b, c, d, e, f }
{ a, b, c, d, f }
{ a, b, c, e }
{ a, b, c, e, f }
{ a, b, c, f }
{ a, b, d }
{ a, b, d, e }
{ a, b, d, e, f }
{ a, b, d, f }
{ a, b, e }
{ a, b, e, f }
{ a, b, f }
{ a, c }
{ a, c, d }
{ a, c, d, e }
{ a, c, d, e, f }
{ a, c, d, f }
{ a, c, e }
{ a, c, e, f }
{ a, c, f }
{ a, d }
{ a, d, e }
{ a, d, e, f }
{ a, d, f }
{ a, e }
{ a, e, f }
{ a, f }
{ b }
{ b, c }
{ b, c, d }
{ b, c, d, e }
{ b, c, d, e, f }
{ b, c, d, f }
{ b, c, e }
{ b, c, e, f }
{ b, c, f }
{ b, d }
{ b, d, e }
{ b, d, e, f }
{ b, d, f }
{ b, e }
{ b, e, f }
{ b, f }
{ c }
{ c, d }
{ c, d, e }
{ c, d, e, f }
{ c, d, f }
{ c, e }
{ c, e, f }
{ c, f }
{ d }
{ d, e }
{ d, e, f }
{ d, f }
{ e }
{ e, f }
{ f }

```

---

### Post by Reiger on 2011-06-12
> **krazyd said:**
> I don't know Haskell at all, but this is very impressive. Is it O(2^n)?

EDIT: I was being stupid, I think part of my brain must've been switched off, because that code doesn't compute a powerset at all. Anyway this code does:
```

{-
 - Base case the empty set, returns a set consisting of a single empty set.
--}
powerset [] = [[]]
{-
 - Recursive case: 
 -  1 compute the powerset of the tail,
 -  2 concatenate it with a derivative set, 
 -  3 where each item (subset of the tail) has the original head element appended to it.
--}
powerset (x:xs)= let pset = powerset xs in pset ++ (map (x:) pset) 

```

---

### Post by slavik on 2011-06-14
basically, this is recursively generating a powerset of n-1 and appends n to it.

---

### Post by Reiger on 2011-06-14
> **slavik said:**
> basically, this is recursively generating a powerset of n-1 and appends n to it.

Almost. If you literally did what you wrote you would generate the original set. ;)

---

### Post by BkkBonanza on 2011-06-14
This reminds me of my days playing with Turbo Prolog back in the 80s. It's a distant fog now but I bet it would be very sucinct in Prolog (if I could just remember how to write that now).

I'm curious if there is a current day version of Prolog or if that has been left on the dustbin of computer history?

---

### Post by schauerlich on 2011-06-14
> **BkkBonanza said:**
> I'm curious if there is a current day version of Prolog or if that has been left on the dustbin of computer history?

Check out [swi-prolog](http://www.swi-prolog.org/). I used it last quarter for a computational linguistics course.

---

### Post by Leuchten on 2011-07-04
My entry in Scala (still crummy, but getting better)

```
object Main {
  def main(arg: Array[String]) {
    val set = arg toList
    val pset = powerSet(set)
    println(pset ::: List(List[String]()))
  }

  def powerSet(set: List[String]): List[List[String]] = {
    val part:String = if(set.size > 0) set(0) else null

    if(part == null)
      return List[List[String]]()
    else {
      val temp = powerSet(set - part)
      val plus = addEach(part,temp)
      return temp ::: plus
    }
  }

  def addEach(part: String, set: List[List[String]]): List[List[String]] = {
    if(set.size < 1)
      return List(List(part))
    else
      return List((set(0) :+ part).toList) ::: addEach(part, set-set(0))
  }
}
```

---

### Post by zobayer1 on 2011-07-04
I think this one is simpler:
C++
```

void gen(int n, int *a, vector<int> *V) {
    for(int i = 0; i < (1<<n); i++) {
        V[i].clear();
        for(int j = 0; j < n; j++) {
            if(i & (1<<j)) {
                V[i].push_back(a[j]);
            }
        }
    }
}

```Here, n is number of items in array a[], V is a vector array, which will contain the sets.

---

### Post by zobayer1 on 2011-07-04
Here is my complete implementation:
```

#include <vector>
#include <cstdio>
using namespace std;

const int MAX = 10;

void gen(int n, int *a, vector<int> *V) {
    int i, j;
    for(i = 0; i < (1<<n); i++) {
        V[i].clear();
        for(j = 0; j < n; j++) if(i & (1<<j)) V[i].push_back(a[j]);
    }
}

int main() {
    int i, j, n, a[MAX];
    vector< int > V[1<<MAX];
    while(scanf("%d", &n)==1) {
        for(i = 0; i < n; i++) scanf("%d", a + i);
        gen(n, a, V);
        for(i = 0; i < (1<<n); i++) {
            printf("Set %d:", i);
            if(V[i].empty()) printf(" empty");
            else for(j = 0; j < V[i].size(); j++) printf(" %d", V[i][j]);
            printf("\n");
        }
    }
    return 0;
}
```

---

### Post by Leuchten on 2011-07-04
> **Reiger said:**
> EDIT: I was being stupid, I think part of my brain must've been switched off, because that code doesn't compute a powerset at all. Anyway this code does:
```

{-
 - Base case the empty set, returns a set consisting of a single empty set.
--}
powerset [] = [[]]
{-
 - Recursive case: 
 -  1 compute the powerset of the tail,
 -  2 concatenate it with a derivative set, 
 -  3 where each item (subset of the tail) has the original head element appended to it.
--}
powerset (x:xs)= let pset = powerset xs in pset ++ (map (x:) pset) 

```

After reviewing this code some more and learning more about the functional paradigm, I have shrunk my submission.

```
object Main {
  def main(arg: Array[String]) {
    val set = arg toList
    val pset = powerSet(set)
    println(pset)
  }

  def powerSet(set: List[String]): List[List[String]] = {
    if(set.size < 1)
      return List(set)

    val pset = () => powerSet(set - set(0))
    return pset() ++ pset().map((l: List[String]) => set(0) :: l)
  }
}
```

---

### Post by fiddler616 on 2012-04-26
SML.

In retrospect, this is basically the same thing as the Haskell version.

```

fun powerset [] = [[]]
  | powerset (x::xs) = 
    let
	val pset = powerset(xs)
    in
	pset@(map (fn y => x::y) pset)
    end;

```

---

### Post by LemursDontExist on 2012-04-27
Since no one ever posted a Python version, and the elegant Haskell one-liner was already taken...

```
def powerset(l):
    if len(l) == 0:
        return [[]]
    else:
        x = l.pop()
        pset = powerset(l)
        return pset + [[x] + m for m in pset]
```

---

