---
title: "Advanced programming exercise: All permutations"
date: 2011-06-20
forum: Programming Talk
---

### Post by slavik on 2011-06-20
Hot on the heels of the power set exercise (aka all combinations), comes this nonetheless interesting exercide of generating all permutations of a list.

Idea is simple: given a list of items (hardcoded, read in via stdin, whatever), generate a list of permutations of the items. Algorithms can be found on wikipedia.

For a larger challenge, think of how you could parallelize the algorithm.

---

### Post by cgroza on 2011-06-20
So basically, we need to take a list and then generate permutations from it?

---

### Post by schauerlich on 2011-06-20
```
import itertools
print list(itertools.permutations([1, 2, 3]))
```

---

### Post by cgroza on 2011-06-20
```

#!/usr/bin/env python

#permutations generator

def do_permutations(str):
    if len(str) <=1:
        yield str
    else:
        for perm in do_permutations(str[1:]):
            for i in range(len(perm)+1):
                yield perm[:i] + str[0:1] + perm[i:]



test = range(0,5)
result = []
for p in  do_permutations(test):
    result.append(p)


print result
print len(result)
                                               



```

---

### Post by slavik on 2011-06-20
> **schauerlich said:**
> ```
import itertools
print list(itertools.permutations([1, 2, 3]))
```
5 for cleverness, 2 for solution ... point is for you to write that function. :)

---

### Post by slavik on 2011-06-20
> **cgroza said:**
> So basically, we need to take a list and then generate permutations from it?
yes

---

### Post by nvteighen on 2011-06-21
Gah... I suck! :(

I've been trying this on Common Lisp and I'm not sure whether it's my own incompetence (most likely) or the torrid weather there is here today. I'll try this again, but expect no success in a couple of years.

---

### Post by JupiterV2 on 2011-06-21
> **nvteighen said:**
> Gah... I suck! :(

Amen to that! I feel stupid right now. Trying to do this with concurrency in Go. I think I've almost wrapped my head around it. Just need to implement it.

---

### Post by schauerlich on 2011-06-21
Clojure:

```
(defn split
  "Equivalent to zip (inits xs) (tails xs) in haskell"
  [coll]
  (for [x (range (inc (count coll)))]
    (list (take x coll) (drop x coll))))


(defn permutations
  "Returns all permutations of the given sequence"
  [coll]
  (if (empty? coll)
    '(())
    (for [xs (permutations (next coll))
          ps (split xs)]
      (concat (first ps) (list (first coll)) (second ps)))))


```

---

### Post by NovaAesa on 2011-06-21
> **nvteighen said:**
> Gah... I suck! :(

I've been trying this on Common Lisp and I'm not sure whether it's my own incompetence (most likely) or the torrid weather there is here today. I'll try this again, but expect no success in a couple of years.
I had a similar experience yesterday, tried doing it with Scheme and after 15 minutes of not being able to work it out I asked myself "Why on earth am I doing this while I have *real* homework to do?".

---

### Post by schauerlich on 2011-06-21
> **nvteighen said:**
> Gah... I suck! :(

I've been trying this on Common Lisp and I'm not sure whether it's my own incompetence (most likely) or the torrid weather there is here today. I'll try this again, but expect no success in a couple of years.

> **NovaAesa said:**
> I had a similar experience yesterday, tried doing it with Scheme and after 15 minutes of not being able to work it out I asked myself "Why on earth am I doing this while I have *real* homework to do?".

The basic idea that helped me is: For each element of the list, create a  bunch of lists containing that element in every possible position of each permutation of the rest of the list. Then, let recursion do the rest. :)

---

### Post by slavik on 2011-06-21
> **schauerlich said:**
> The basic idea that helped me is: For each element of the list, create a  bunch of lists containing that element in every possible position of each permutation of the rest of the list. Then, let recursion do the rest. :)
that is one algorithm I did in C, but I think the lexicographic order one is faster (never tested them). of course it also depends on tail recursion optimization.

---

### Post by schauerlich on 2011-06-22
> **slavik said:**
> that is one algorithm I did in C, but I think the lexicographic order one is faster (never tested them). of course it also depends on tail recursion optimization.

I never claimed it was efficient. :)

---

### Post by ziekfiguur on 2011-06-22
I still had this lying around from a problem on project euler, before i realized itertools.permutations existed.

```
#!/usr/bin/env python

def permutations(a):
    x = len(a)
    while True:
        k = -1
        for xk in xrange(x - 1):
            if a[xk] < a[xk + 1]:
                k = xk
        if k == -1:
            return
        l = -1
        for xl in xrange(k + 1, x):
            if a[k] < a[xl]:
                l = xl
        a[k], a[l] = a[l], a[k]
        b = a[k + 1:]
        b.reverse()
        a[k + 1:] = b
        yield [i for i in a]

for x in permutations(range(4)):
    print x
```

I think it's based on an algorithm i found on wikipedia, but i'm not sure anymore.

---

### Post by krazyd on 2011-06-22
Ruby entry:

[PHP]#!/usr/bin/ruby

def permute set
    perms = []
    set.each do |s|
        perms << [s] && next if perms.empty?
        new_perms = []
        perms.each do |p|
            (p.size+1).times do |i|
                new_perms << p.dup.insert(i,s)
            end
        end
        perms = new_perms
    end
    perms
end

a = [1,2,3]
p permute a
[/PHP]

---

### Post by StephenF on 2011-06-22
Python entry (recursive generator).
```

def permutations(sequence):
    t = tuple(sequence)
    if not t:
        yield ()
        
    for i, this in enumerate(t):
        for rest in permutations(t[:i] + t[i+1:]):
            yield (this, ) + rest


for each in permutations((1, 2, 3)):
    print each

```

---

### Post by stchman on 2011-06-22
The Java world rings in.

```

public class Permutations {
    public static void main( String[] args ) {
        // get out of static main and call the permutations method
        Permutations m = new Permutations();
        
        if( args.length == 0 ) {
            System.out.println( "Please input a valid string." );
            System.exit( 0 );
        }
        else {
            m.perm( "", args[ 0 ] );
        }
    }    
    
    public void perm( String prefix, String s ) {
        if ( s.length() == 0 ) {
            System.out.println( prefix );
        }    
        else {
            for ( int i = 0; i < s.length(); i++ ) {
               perm( prefix + s.charAt( i ), s.substring( 0, i ) + s.substring( i + 1, s.length() ) );
            }
        }
    }
}

```

---

### Post by ve4cib on 2011-06-22
We had to do this in a course I took back in September.  Here are two programs I did for the first assignment (written in Java), along with their outputs.

Both programs work by calculating the successor to a given permutation.  One uses standard lexicographic order, and the other uses Trotter-Johnson order.

**Lexicographic Order**
```

public class LexicographicOrder
{
	// args:
	//	- n (int :: the length of the list)
    public static void main(String[] args)
    {
		int n = 0;
		int[] list;
		int rank=0;
		
		// parse the command-line arguments, bailing out if we see anything we don't like
		if(args.length == 0)
		{
			System.out.println("\n\nUsage:\n\t$java LexicographicOrder n\n\n(where n is the length of the list to permute)\n\n");
			return;
		}
		try
		{
			n = Integer.parseInt(args[0]);
			if(n<=0)
				throw new Exception("n must be greater than zero");
			
			list = new int[n];
		}
		catch(Exception e)
		{
			System.out.println("\n\nInvalid value for n\nFound: "+args[0]+"\nExpected: positive integer\n");
			return;
		}
        
        // fill the array with the initial ordering
        for(int i=0; i<n; i++)
			list[i] = i+1;
			
		
		System.out.println("All permutations in lexicographic order for n="+n);
		System.out.println("Rank\tOrdering");
		printPermutation(rank,list);
		
		int[] successor = getSuccessor(list);
		while(successor != null)
		{
			rank++;
			printPermutation(rank, successor);
			successor = getSuccessor(successor);
		}
    }
    
    // calculates the successor permutation to the provided list in-situ and returns it
    // successor is determined by lexicographic ordering
    // returns null if there is no successor
    //
    // see algorithm 0.1: PermLexSuccessor
    //
    // NB: array indices are 0-based, so they should all be off-by-one compared to
    // the original algorithm
    private static int[] getSuccessor(int[] list)
    {	
		// find the position of the first element from the right that is smaller than
		// its right-hand neighbour
		int i=list.length-1;
		while(i>0 && list[i] < list[i-1])
			i--;
		i--;	// necessary to avoid off-by-1 problems
		
		// there is no successor; all values are in reverse-order
		if(i<0)
			return null;
		
		// find the smallest element to the right of list[i] that is greater than list[i]
		int j=list.length-1;
		while(list[j] < list[i])
			j--;
			
		// swap items i and j
		int tmp = list[i];
		list[i] = list[j];
		list[j] = tmp;
		
		// swap the items from i+1 to the end
		int numItems = list.length - i - 1;
		for(int h=1; h<=numItems/2; h++)
		{
			tmp = list[i+h];
			list[i+h] = list[list.length-h];
			list[list.length-h] = tmp;
		}
		
		return list;
	}
    
    // prints a permutation and the rank associated with it
    private static void printPermutation(int rank, int[] list)
    {
		System.out.print(rank);
		System.out.print("\t");
		for(int i=0; i<list.length-1; i++)
			System.out.print(list[i]+",");
			
		System.out.print(list[list.length-1]);
		System.out.println();
	}
}

```

```
$ java LexicographicOrder 4
All permutations in lexicographic order for n=4
Rank	Ordering
0	1,2,3,4
1	1,2,4,3
2	1,3,2,4
3	1,3,4,2
4	1,4,2,3
5	1,4,3,2
6	2,1,3,4
7	2,1,4,3
8	2,3,1,4
9	2,3,4,1
10	2,4,1,3
11	2,4,3,1
12	3,1,2,4
13	3,1,4,2
14	3,2,1,4
15	3,2,4,1
16	3,4,1,2
17	3,4,2,1
18	4,1,2,3
19	4,1,3,2
20	4,2,1,3
21	4,2,3,1
22	4,3,1,2
23	4,3,2,1
```


**Trotter-Johnson Order**
```

public class TrotterJohnsonOrder
{
	// args:
	//	- n (int :: the length of the list)
    public static void main(String[] args)
    {
		int n = 0;
		int[] list;
		int rank=0;
		
		// parse the command-line arguments, bailing out if we see anything we don't like
		if(args.length == 0)
		{
			System.out.println("\n\nUsage:\n\t$java TrotterJohnsonOrder n\n\n(where n is the length of the list to permute)\n\n");
			return;
		}
		try
		{
			n = Integer.parseInt(args[0]);
			if(n<=0)
				throw new Exception("n must be greater than zero");
			
			list = new int[n];
		}
		catch(Exception e)
		{
			System.out.println("\n\nInvalid value for n\nFound: "+args[0]+"\nExpected: positive integer\n");
			return;
		}
        
        // fill the array with the initial ordering
        for(int i=0; i<n; i++)
			list[i] = i+1;
			
		
		System.out.println("All permutations in Trotter-Johnson order for n="+n);
		System.out.println("Rank\tOrdering");
		printPermutation(rank,list);
		
		int[] successor = getSuccessor(list);
		while(successor != null)
		{
			rank++;
			printPermutation(rank, successor);
			successor = getSuccessor(successor);
		}
    }
    
    // calculates the successor permutation to the provided list in-situ and returns it
    // successor is determined by trotter-johnson ordering
    // returns null if there is no successor
    //
    // see algorithm 0.3: PermTrotterJohnsonSuccessor
    //
    // NB: array indices are 0-based, so they should all be off-by-one compared to
    // the original algorithm
    private static int[] getSuccessor(int[] list)
    {	
		boolean done = false;
        int s = 0;
        int m = list.length;
        int tmp;
        boolean isEven;
        
        // copy the array into rho
        int[] rho = new int[list.length];
        for(int i=0; i<list.length; i++)
            rho[i] = list[i];
            
        int d;
        while (m>1 && !done)
        {
            d = 1;
            while(rho[d - 1] != m)        // offset the index by -1
                d++;

            // shift the elements in rho down by 1 position
            for(int i=d; i<=m-1; i++)
                rho[i-1] = rho[i];      // offset the index by -1
                            
            // calculate the parity of the permutation
            isEven = isEven(rho, m-1);
                            
            if(!isEven)
            {
                if(d==m)
                {
                    m--;
                }
                else
                {
                    // offset the indices by -1
                    tmp = list[s+d-1];
                    list[s+d-1] = list[s+d];
                    list[s+d] = tmp;
                    done = true;
                }
            }
            else
            {
                if(d==1)
                {
                    m--;
                    s++;
                }
                else
                {
                    // offset the indices by -1
                    tmp = list[s+d-1];
                    list[s+d-1] = list[s+d-2];
                    list[s+d-2] = tmp;
                    done = true;
                }
            }
        }
		
        if(m==1)
            return null;
        else
            return list;
	}
    
    // calculates the parity of a permutation by counting the number of pairs [i,j]
    // where list[i] > list[j] and 0 <= i < j < n
    // returns true if the permutation is even, false if it is odd
    //
    // args:
    //  list: the permutation to be examined
    //  length: the length of the current sub-permutation
    private static boolean isEven(int[] list, int length)
    {
        int i, j;
        int count = 0;
        
        for(i=0; i<length-1; i++)
        {
            for(j=i+1; j<length; j++)
            {
                if(list[i] > list[j])
                    count++;
            }
        }
        
        return count%2==0;
    }
    
    // prints a permutation and the rank associated with it
    private static void printPermutation(int rank, int[] list)
    {
		System.out.print(rank);
		System.out.print("\t");
		for(int i=0; i<list.length-1; i++)
        {
            System.out.print(list[i]+",");
        }
        
        System.out.print(list[list.length-1]);
		System.out.println();
	}
}
```

```
$ java TrotterJohnsonOrder 4
All permutations in Trotter-Johnson order for n=4
Rank	Ordering
0	1,2,3,4
1	1,2,4,3
2	1,4,2,3
3	4,1,2,3
4	4,1,3,2
5	1,4,3,2
6	1,3,4,2
7	1,3,2,4
8	3,1,2,4
9	3,1,4,2
10	3,4,1,2
11	4,3,1,2
12	4,3,2,1
13	3,4,2,1
14	3,2,4,1
15	3,2,1,4
16	2,3,1,4
17	2,3,4,1
18	2,4,3,1
19	4,2,3,1
20	4,2,1,3
21	2,4,1,3
22	2,1,4,3
23	2,1,3,4

```

---

### Post by JupiterV2 on 2011-06-22
A classic implementation in Go:
```
package main

import . "fmt"

func permute (inp []int) ([]int, bool) {
    // look for the key
    key := len(inp) - 1
    for ; key > 0; key-- {
        if inp[key-1] < inp[key] {
            break
        }
    }
    
    // if key == 0, we're done, array is in reverse order
    if key == 0 {
        return inp, false
    }
    // find value to switch with key
    key--
    next := len(inp) - 1
    for ; next > key; next-- {
        if inp[next] > inp[key] {
            break
        }
    }
    
    // swap values
    inp[next], inp[key] = inp[key], inp[next]
    
    // sort tail to be in lexical order
    y := len(inp) - 1
    for x := key+1; x <= y; x++ {
        inp[x], inp[y] = inp[y], inp[x]
        y--
    }
    
    return inp, true
}

func main() {
    array := []int{1,2,3,4}
    
    Println(array)
    for array, more := permute(array); more; {
        Println(array)
        array, more = permute(array)
    }
}
```

I gave up on the concurrent version and I don't do the language justice as I've just started learning it.

---

### Post by slavik on 2011-06-23
since you have both in java, have you ever tried to time them?

---

### Post by ve4cib on 2011-06-23
> **slavik said:**
> since you have both in java, have you ever tried to time them?

Not sure if that was directed at me or not, but some times for both algorithms I posted:

n=6
Lex: 0.050s
T-J: 0.040s

n=7
Lex: 0.110s
T-J: 0.070s

n=8
Lex: 0.580s
T-J: 0.630s

I just did one run each time, so the times fluctuate a fair bit.  Generally-speaking I think the lexicographic order was slightly faster for larger values of n, and Trotter-Johnson order was faster for smaller values.  I think.  I'd need to do a bunch of runs and average them again.  The difference between the two is pretty small at any rate.

---

### Post by cyberslayer on 2011-06-23
```

CL-USER> (defun p (l)
           (if l
               (mapcan (lambda (x)
                         (mapcar (lambda (s) (cons x s))
                                 (p (remove x l))))
                       l)
               '(nil)))
P
CL-USER> (p '(1 2 3))
((1 2 3) (1 3 2) (2 1 3) (2 3 1) (3 1 2) (3 2 1))

```

---

### Post by schauerlich on 2011-06-23
My attempt at parallelizing it - desugar the list comprehension, and replace a map with pmap. :)

```
(defn perms
  [coll]
  (if (empty? coll)
    '(())
    (let [x (first coll)
          xs (next coll)] 
      (apply concat
             (pmap (fn [xs-]
                    (map (fn [ps]
                           (concat (first ps)
                                   (list x)
                                   (second ps)))             
                         (split xs-)))
                  (perms xs))))))

```

---

### Post by slooksterpsv on 2011-06-23
> **cyberslayer said:**
> ```

CL-USER> (defun p (l)
           (if l
               (mapcan (lambda (x)
                         (mapcar (lambda (s) (cons x s))
                                 (p (remove x l))))
                       l)
               '(nil)))
P
CL-USER> (p '(1 2 3))
((1 2 3) (1 3 2) (2 1 3) (2 3 1) (3 1 2) (3 2 1))

```

???????????????? The others I understood, Ruby, Java, Python, Go, etc. etc. this makes no sense to me so far I figure:

define function p argument l
if l contains data
??? change in x
??? change in s ????
run function removing x in l ????

---

### Post by schauerlich on 2011-06-23
> **slooksterpsv said:**
> ???????????????? The others I understood, Ruby, Java, Python, Go, etc. etc. this makes no sense to me so far I figure:

define function p argument l
if l contains data
??? change in x
??? change in s ????
run function removing x in l ????

mapcar will take a function and a list, apply the function to each element of the list, and collect those results. mapcan will run mapcar on the list, but also concatenate the results together into a big list. So, he sticks some element x in front of every possible permutation of the rest of the list, does this for each element in the input, and concatenates the results.

---

### Post by nvteighen on 2011-06-23
> **cyberslayer said:**
> ```

CL-USER> (defun p (l)
           (if l
               (mapcan (lambda (x)
                         (mapcar (lambda (s) (cons x s))
                                 (p (remove x l))))
                       l)
               '(nil)))
P
CL-USER> (p '(1 2 3))
((1 2 3) (1 3 2) (2 1 3) (2 3 1) (3 1 2) (3 2 1))

```


And this shows how much I still have to learn.

---

### Post by JupiterV2 on 2011-06-23
> **cyberslayer said:**
> ```

CL-USER> (defun p (l)
           (if l
               (mapcan (lambda (x)
                         (mapcar (lambda (s) (cons x s))
                                 (p (remove x l))))
                       l)
               '(nil)))
P
CL-USER> (p '(1 2 3))
((1 2 3) (1 3 2) (2 1 3) (2 3 1) (3 1 2) (3 2 1))

```

This is admittedly new for me. What language is this?

---

### Post by slavik on 2011-06-23
> **ve4cib said:**
> Not sure if that was directed at me or not, but some times for both algorithms I posted:

n=6
Lex: 0.050s
T-J: 0.040s

n=7
Lex: 0.110s
T-J: 0.070s

n=8
Lex: 0.580s
T-J: 0.630s

I just did one run each time, so the times fluctuate a fair bit.  Generally-speaking I think the lexicographic order was slightly faster for larger values of n, and Trotter-Johnson order was faster for smaller values.  I think.  I'd need to do a bunch of runs and average them again.  The difference between the two is pretty small at any rate.
then your n is not large enough :P

---

### Post by schauerlich on 2011-06-23
> **JupiterV2 said:**
> This is admittedly new for me. What language is this?

It's common lisp.

---

### Post by ve4cib on 2011-06-23
> **slavik said:**
> then your n is not large enough :P

Well, there's a limit to how much time I want to spend generating permutations.  It takes literally hours for values as small as 12-15 (depending on the speed of the computer).

For n=10, the largest I'm willing to do right now, the lexicographic order runs in 49.640s, and the Trotter-Johnson order runs in 49.140s.  Pretty insignificant difference.  They're off by a constant factor, as opposed to being O(n^2) vs O(n^3).

---

### Post by slavik on 2011-07-03
My solutions (perl and 2 versions of parallel C):

Perl:
```

#!/usr/bin/perl

#       permutations.pl
#       
#       Copyright 2011 Vyacheslav Goltser <slavikg@gmail.com>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.

use strict;
use warnings;
use diagnostics;

die "Need number > 1" unless ($ARGV[0] > 1);

my @list = (1..$ARGV[0]);
#my $count = 0;
do {
	#$count++;
#	print "[ ". join(', ', @list) ." ]\n";
	@list = next_perm(@list);
} while ($#list > 0);
#print $count ." permutations generated\n";

sub next_perm {
	my @terms = @_;

	my $n = $#terms;
	my $k = -1;
	my $l = -1;

	# find k
	for my $i (0..$#terms-1) {
		if (($i > $k) and ($terms[$i] < $terms[$i+1])) {
			$k = $i;
		}
	}

	return undef if ($k==-1);

	# find l
	for my $i (0..$#terms) {
		if (($i > $l) and ($terms[$k] < $terms[$i])) {
			$l = $i;
		}
	}
	
	# swap
	($terms[$k], $terms[$l]) = ($terms[$l], $terms[$k]);
	
	return (@terms[0..$k], reverse @terms[($k+1)..$n]);
}

```

C (message queue version):
```

/*
 *      all_perms.c
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
 */

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/msg.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <string.h>
#include <errno.h>

// number of workers to spawn
#ifndef NUM_WORKERS
#define NUM_WORKERS 4
#endif

// list size
#ifndef LIST_SIZE
#define LIST_SIZE 16
#endif

// number of lists to return at a single time
#ifndef LIST_RET
#define LIST_RET 100000
#endif

// define End Of Work and End Of Results
#define EOW 1
#define EOR 1

// work unit
typedef struct _wu {
	long mtype;
	int list[LIST_SIZE];
	int first;
	int flag;
} wu;

// result unit
typedef struct _ru {
	long mtype;
	int lists[LIST_RET][LIST_SIZE];
	int curr;
	int flag;
} ru;

// n - number of child processes to spawn
// cpid - array where to store pids of children
// only the original parent will fork until it spawns as
// many processes as asked or fork() returns -1
int sp_fork (int nc, int* cpid) {
	int iter = 0;
	int f_ret = 0;

	while(iter < nc && f_ret != -1) {
		if((f_ret = fork()) > 0) {
			cpid[iter++] = f_ret;
		}
		else if (f_ret == 0) {
			return -1;
		}
	}
	
	return iter;
}

void iterate(int* list, int first, int last, ru* res, int msg_result) {
	if (last == first) {
		int iterator;
		for (iterator = 0; iterator < LIST_SIZE; iterator++) {
			res->lists[res->curr][iterator] = list[iterator];
		}
		++res->curr;
		if (LIST_RET == res->curr) {
			msgsnd(msg_result, res, sizeof(ru), 0);
			res->curr = 0;
		}
		return;
	}

	int i, tmp;
	for(i = first; i <= last; ++i) {
		tmp = list[first];
		list[first] = list[i];
		list[i] = tmp;
		iterate(list, first+1, last, res, msg_result);
		list[i] = list[first];
		list[first] = tmp;
	}
	
	return;
}

void worker(int msg_work, int msg_result) {
	wu work;
	ru *result = (ru*)malloc(sizeof(ru));;

	fprintf(stderr, "%d - worker\n", getpid());

	result->mtype = 1;
	result->curr = 0;
	result->flag = 0;
		
	while(msgrcv(msg_work, &work, sizeof(wu), 0, 0) != -1 && work.flag != EOW){
		iterate(work.list, work.first, LIST_SIZE-1, result, msg_result);
		if (result->curr > 0 && result->curr < LIST_RET) {
			msgsnd(msg_result, result, sizeof(ru), 0);
			result->curr = 0;
		}
	}

	result->flag = EOR;
	msgsnd(msg_result, result, sizeof(ru), 0);

	return;
}

void scatter(int msg_work) {
	int iterator;
	wu work; int tmp;

	work.mtype = 1;
	work.flag = 0;
	work.first = 1;

	for(iterator = 0; iterator < LIST_SIZE; iterator++) {
		work.list[iterator] = iterator;
	}

	fprintf(stderr, "%d - scatter\n", getpid());
	//~ msgsnd(msg_work, &work, sizeof(wu), 0);
	for(iterator = 0; iterator < LIST_SIZE; ++iterator) {
		tmp = work.list[0];
		work.list[0] = work.list[iterator];
		work.list[iterator] = tmp;
		msgsnd(msg_work, &work, sizeof(wu), 0);
		work.list[iterator] = work.list[0];
		work.list[0] = tmp;
	}

	work.flag = EOW;
	for (iterator = 0; iterator < NUM_WORKERS; iterator++) {
		msgsnd(msg_work, &work, sizeof(wu), 0);
	}

	return;
}

void gather(int msg_result) {
	ru *received = (ru*)malloc(sizeof(ru));
	int done = 0;
	int counter = 0, iterator;

	fprintf(stderr, "%d - gather\n", getpid());
	msgrcv(msg_result, received, sizeof(ru), 0, 0);
	if (received->flag == EOR) done++;
	while(done < NUM_WORKERS) {
		//~ counter = 0;
		//~ while (counter < received.curr) {
			//~ for (iterator = 0; iterator < LIST_SIZE; iterator++) {
				//~ printf("%d", received.lists[counter][iterator]);
			//~ }
			//~ printf("\n");
			//~ counter++;
		//~ }
		counter+=received->curr;
		msgrcv(msg_result, received, sizeof(ru), 0, 0);
		if (received->flag == EOR) done++;
	}
	fprintf(stderr, "%d permutations\n", counter);
	fflush(NULL);
	return;
}

int main(int argc, char** argv) {
	int nc = NUM_WORKERS; int cpid[NUM_WORKERS];
	int gather_pid;

	/* create message queues */
	int msg_work = msgget(ftok(argv[0], 'w'), 0666 | IPC_CREAT | IPC_EXCL);
	int msg_result = msgget(ftok(argv[0], 'r'), 0666 | IPC_CREAT | IPC_EXCL);
	
	if(msg_work == -1) {
		perror("Could not create WORK QUEUE");
		exit(EXIT_FAILURE);
	}
	if(msg_result == -1) {
		perror("Could not create RESULT QUEUE");
		exit(EXIT_FAILURE);
	}

	fprintf(stderr, "permutating %d items with %d workers\n", LIST_SIZE, NUM_WORKERS);
	
	if(sp_fork(nc, cpid) == -1) {
		worker(msg_work, msg_result);
	}
	else {
		if((gather_pid = fork()) > 0) {
			scatter(msg_work);
			waitpid(gather_pid, NULL, 0);
			msgctl(msg_work, IPC_RMID, NULL);
			msgctl(msg_result, IPC_RMID, NULL);
		}
		else {
			gather(msg_result);
			exit(0);
		}
	}
	return 0;
}

```

C (fifo version):
```

/*
 *      all_perms.c
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
 */

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/msg.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <string.h>
#include <errno.h>

// number of workers to spawn
#ifndef NUM_WORKERS
#define NUM_WORKERS 1
#endif

// list size
#ifndef LIST_SIZE
#define LIST_SIZE 10
#endif

// number of lists to return at a single time
#ifndef LIST_RET
#define LIST_RET 100
#endif

// define End Of Work and End Of Results
#define EOW 1
#define EOR 1

//pipes
int work_pipe[2], result_pipe[2];

// work unit
typedef struct _wu {
	long mtype;
	int list[LIST_SIZE];
	int first;
	int flag;
} wu;

// result unit
typedef struct _ru {
	long mtype;
	int lists[LIST_RET][LIST_SIZE];
	int curr;
	int flag;
} ru;

// n - number of child processes to spawn
// cpid - array where to store pids of children
// only the original parent will fork until it spawns as
// many processes as asked or fork() returns -1
int sp_fork (int nc, int* cpid) {
	int iter = 0;
	int f_ret = 0;

	while(iter < nc && f_ret != -1) {
		if((f_ret = fork()) > 0) {
			cpid[iter++] = f_ret;
		}
		else if (f_ret == 0) {
			return -1;
		}
	}
	
	return iter;
}

void iterate(int* list, int first, int last, ru* res, int result_pipe) {
	if (last == first) {
		int iterator;
		for (iterator = 0; iterator < LIST_SIZE; iterator++) {
			res->lists[res->curr][iterator] = list[iterator];
		}
		++res->curr;
			//~ for (iterator = 0; iterator < LIST_SIZE; iterator++) {
				//~ printf("%d", list[iterator]);
			//~ }
			//~ printf("\n");
		if (LIST_RET == res->curr) {
			write(result_pipe, &res, sizeof(ru));
			res->curr = 0;
		}
		return;
	}

	int i, tmp;
	for(i = first; i <= last; ++i) {
		tmp = list[first];
		list[first] = list[i];
		list[i] = tmp;
		iterate(list, first+1, last, res, result_pipe);
		list[i] = list[first];
		list[first] = tmp;
	}
	
	return;
}

void worker(int work_pipe, int result_pipe) {
	wu work;
	ru result;
	int iterator;

	fprintf(stderr, "%d - worker\n", getpid());

	result.mtype = 1;
	result.curr = 0;
	result.flag = 0;
		
	while(read(work_pipe, &work, sizeof(wu)) != EOF && work.flag != EOW){
		iterate(work.list, work.first, LIST_SIZE-1, &result, result_pipe);
		if (result.curr > 0 && result.curr < LIST_RET) {
			write(result_pipe, &result, sizeof(ru));
			result.curr = 0;
		}
		//~ for (iterator = 0; iterator < LIST_SIZE; iterator++) printf("%d ",work.list[iterator]);
		//~ printf("\n");
	}

	//~ close(result_pipe);
	result.flag = EOR;
	write(result_pipe, &result, sizeof(ru));

	return;
}

void scatter(int work_pipe) {
	int iterator;
	wu work; int tmp;

	work.mtype = 1;
	work.flag = 0;
	work.first = 1;

	for(iterator = 0; iterator < LIST_SIZE; iterator++) {
		work.list[iterator] = iterator;
	}

	fprintf(stderr, "%d - scatter\n", getpid());
	for(iterator = 0; iterator < LIST_SIZE; ++iterator) {
		tmp = work.list[0];
		work.list[0] = work.list[iterator];
		work.list[iterator] = tmp;
		write(work_pipe, &work, sizeof(wu));
		work.list[iterator] = work.list[0];
		work.list[0] = tmp;
	}

	//~ close(work_pipe);
	//~ close(result_pipe[1]);
	work.flag = EOW;
	for (iterator = 0; iterator < NUM_WORKERS; iterator++) {
		write(work_pipe, &work, sizeof(wu));
	}

	return;
}

void gather(int result_pipe) {
	ru received;
	int done = 0, iterator;
	int counter = 0;

	fprintf(stderr, "%d - gather\n", getpid());
	read(result_pipe, &received, sizeof(ru));
	if(received.flag == EOR) done++;
	while(done < NUM_WORKERS) {
		//~ counter = 0;
		//~ while (counter < received.curr) {
			//~ for (iterator = 0; iterator < LIST_SIZE; iterator++) {
				//~ printf("%d", received.lists[counter][iterator]);
			//~ }
			//~ printf("\n");
			//~ counter++;
		//~ }
		counter += received.curr;
		read(result_pipe, &received, sizeof(ru));
		if(received.flag == EOR) done++;
	}
	fprintf(stderr, "%d permutations\n", counter);
	fflush(NULL);
	return;
}

int main(int argc, char** argv) {
	int nc = NUM_WORKERS; int cpid[NUM_WORKERS];
	int gather_pid;
	
	/* create pipes */
	if(pipe(work_pipe) == -1) {
		perror("Could not create WORK PIPE");
		exit(EXIT_FAILURE);
	}
	if(pipe(result_pipe) == -1) {
		perror("Could not create RESULT PIPE");
		exit(EXIT_FAILURE);
	}

	fprintf(stderr, "permutating %d items with %d workers\n", LIST_SIZE, NUM_WORKERS);
	
	if(sp_fork(nc, cpid) == -1) {
		worker(work_pipe[0], result_pipe[1]);
	}
	else {
		if((gather_pid = fork()) > 0) {
			scatter(work_pipe[1]);
			waitpid(gather_pid, NULL, 0);
		}
		else {
			gather(result_pipe[0]);
			exit(0);
		}
	}
	return 0;
}

```

---

### Post by Leuchten on 2011-07-08
My code in scala.

```

object Main {
  def main(arg: Array[String]) {
    val list = arg.toList
    println(permutations(list))
  }

  def permutations(list: List[String]): List[List[String]] = {
    if (list.size == 1)
      return List(list)
    else {
      val tmp = list.map((s) => permutations(list - s).map((r) => s :: r))
      val ret = tmp.foldRight(List[List[String]]()) {(x,list) => x ++ list}
      return ret
  }
}

```

---

### Post by JupiterV2 on 2011-07-10
I finally put together a concurrent version with Go. I gain almost a full second using the same algorithm with concurrency on a single x86 non-hyper threaded CPU (8 year old PC). Times are posted at the end. I'd be interested to see the difference on a multi-core or multi-CPU machine.

[EDIT] First, I should point out that my variable name choices are abysmal in the below code, and for that I apologize. I should also point out that 'go' starts a new thread and I essentially use a message queue to handle communication between threads. [/EDIT]

```
package main

import "fmt"

func permutate(i []int, out chan []int) {
	if len(i) <= 1 {
		out <- i
		out <- []int{} // flush channel
		return
	}

	n := i[0]
	in := make(chan []int)
	go permutate(i[1:], in)
	for x:= <-in; len(x) > 0; x = <-in {
		for y := 0; y < len(x)+1; y++ {
			var s []int
			if len(x) > y {
				s = append(s, x[:y]...)
			} else {
				s = append(s, x[:len(x)]...)
			}
			s = append(s, n)
			s = append(s, x[y:]...)
			out <- s
		}
	}
	i = []int{} // flush channel
	out <- i
	return
}

func main() {
	i := []int{1,2,3,4,5,6,7,8} // array to create permutation from
	ch := make(chan []int)
	go permutate(i, ch)
	for x := <-ch; len(x) > 0; x = <-ch {
		fmt.Println(x)
	}
}
```

With Concurrency:
real	0m4.968s
user	0m1.572s
sys	0m0.468s

Without Concurrency:
real	0m6.119s
user	0m1.716s
sys	0m0.144s

---

### Post by Lux Perpetua on 2011-07-15
Great idea, slavik! I like both the general concept and this particular exercise. Actually, generating permutations is one of my favorite toy problems, and consequently, I have a number of permutation programs in various languages. I'm thinking I'll just pick my favorite one and post it here (maybe later), but for now I'm happy trying to run some of the other submissions...

JupiterV2 - my results are the opposite of yours; actually, your nonconcurrent program seems to be almost twice as fast. Here's what I get, typically: ```
$ time perms > /dev/null

real    0m3.230s
user    0m2.290s
sys     0m0.683s
$ time perms-nc > /dev/null

real    0m1.873s
user    0m1.693s
sys     0m0.040s
```(nc is the nonconcurrent one. I changed the array to {1,2,3,4,5,6,7,8}.) This is on a single-core IBM laptop, about 5-6 years old. I just compiled your programs with "gccgo". 

slavik - I can run your perl program, but neither of your C programs seem to work. The first one seems to hang the first time and thereafter just aborts. The second one seems to exit normally, but the output doesn't make sense in any way that I can see; for example: ```
$ all_perms-v2
permutating 10 items with 1 workers
12064 - scatter
12066 - gather
12065 - worker
2315 permutations

```Is that 2315 supposed to mean something?

---

### Post by slavik on 2011-07-15
> **Lux Perpetua said:**
> Great idea, slavik! I like both the general concept and this particular exercise. Actually, generating permutations is one of my favorite toy problems, and consequently, I have a number of permutation programs in various languages. I'm thinking I'll just pick my favorite one and post it here (maybe later), but for now I'm happy trying to run some of the other submissions...

JupiterV2 - my results are the opposite of yours; actually, your nonconcurrent program seems to be almost twice as fast. Here's what I get, typically: ```
$ time perms > /dev/null

real    0m3.230s
user    0m2.290s
sys     0m0.683s
$ time perms-nc > /dev/null

real    0m1.873s
user    0m1.693s
sys     0m0.040s
```(nc is the nonconcurrent one. I changed the array to {1,2,3,4,5,6,7,8}.) This is on a single-core IBM laptop, about 5-6 years old. I just compiled your programs with "gccgo". 

slavik - I can run your perl program, but neither of your C programs seem to work. The first one seems to hang the first time and thereafter just aborts. The second one seems to exit normally, but the output doesn't make sense in any way that I can see; for example: ```
$ all_perms-v2
permutating 10 items with 1 workers
12064 - scatter
12066 - gather
12065 - worker
2315 permutations

```Is that 2315 supposed to mean something?
interesting, the C code is old ... very old. will have to take a look.

as for non-concurrent code being faster, that is obvious in your case, since you have a single cpu. in your case, it's the context switching that kills it.

---

### Post by JupiterV2 on 2011-07-15
> **Lux Perpetua said:**
> Great idea, slavik! I like both the general concept and this particular exercise. Actually, generating permutations is one of my favorite toy problems, and consequently, I have a number of permutation programs in various languages. I'm thinking I'll just pick my favorite one and post it here (maybe later), but for now I'm happy trying to run some of the other submissions...

JupiterV2 - my results are the opposite of yours; actually, your nonconcurrent program seems to be almost twice as fast. Here's what I get, typically: ```
$ time perms > /dev/null

real    0m3.230s
user    0m2.290s
sys     0m0.683s
$ time perms-nc > /dev/null

real    0m1.873s
user    0m1.693s
sys     0m0.040s
```(nc is the nonconcurrent one. I changed the array to {1,2,3,4,5,6,7,8}.) This is on a single-core IBM laptop, about 5-6 years old. I just compiled your programs with "gccgo".

If by my non-concurrent version you mean the one posted earlier, then yes, you are exactly correct. That algorithm is much faster than the one I used in my concurrent example. What I meant was, using the same algorithm I used for my concurrent version with, and without, concurrency. I can post that version for you if you like. 

As for the times, my Linux box is an old computer, 8-9 years old. Runs amazingly well for its age though! Matter of fact, it boots Ubuntu 10.10 to desktop (by that I mean, fully booted, no longer reading from the HDD while bringing up additional background apps) faster than our 1 year old PC running Windows 7! Compiled with Google's x86 32bit compiler/linker.

---

### Post by Lux Perpetua on 2011-07-16
> **JupiterV2 said:**
> If by my non-concurrent version you mean the one posted earlier, then yes, you are exactly correct. That algorithm is much faster than the one I used in my concurrent example. What I meant was, using the same algorithm I used for my concurrent version with, and without, concurrency. I can post that version for you if you like. 

As for the times, my Linux box is an old computer, 8-9 years old. Runs amazingly well for its age though! Matter of fact, it boots Ubuntu 10.10 to desktop (by that I mean, fully booted, no longer reading from the HDD while bringing up additional background apps) faster than our 1 year old PC running Windows 7! Compiled with Google's x86 32bit compiler/linker.
Ah, okay. Yes, I was confused: I thought you were comparing the two programs you posted. No pressure re. the other program; post it if you feel like it.

---

### Post by Lux Perpetua on 2011-07-30
All right, as I said, I'm posting my favorite of my permutation programs. This one requires some explanation. My idea was to use separate assembly code - which would be generated dynamically - to permute each different string, since knowing the length of the string in advance can potentially lead to more efficient code (which it did in this case). The question was: how do I generate the code? The perfect solution would probably be to use something like a dynamic x86 assembler, allowing the main program simply to add code to itself which it could then run. However, I wasn't able to find one, and I had no desire to muck around with x86 opcodes, so I resorted to generating GNU assembler source code and piping it through GCC. That still left the question of how to generate the source code. Maybe surprisingly, the easiest way I could think of was to make a template that would be preprocessed by PHP! (Recently, I tried to redo it using only assembler macros, but I failed utterly. m4 is another option, but the only savings I see there are in portability.)

**README**:```
0.  Prerequisites:

    - php
    - make
    - gcc
    - x86-compatible processor

1.  Installation: none really; just save everything in a
    convenient directory, hereafter called ${source_dir}.

2.  Usage: 

    (a) To print the permutations of "abcd" (say), cd to the
        source directory and run `make' as

            $ make p=abcd

    (b) This will create an executable named `permute{abcd}.out'
        as a side-effect. These can all be removed using 

            $ make clean

        Alternatively, running
            
            $ make p=abcd clean-one
        
        will only remove the one file `permute{abcd}.out'.

    (c) This can all be done from outside the source directory
        using (say)

            $ make -s -C ${source_dir} p=abcd

    (d) "permute" can be given explicitly as a `make' target if
        necessary (being implied by default), e. g., to show
        some permutations and clean up afterward:

            $ make p=abcd permute clean

    (e) Setting the make variable "s" to anything but the
        empty string or "print" will do all the computations but
        generate no output. Example:

            $ make p=abcd s=x permute clean

        This is useful if you want to time the computation without
        the I/O (which would otherwise dominate the running time).
```
**Makefile**: ```
.PHONY: permute bin clean clean-one

bin=permute{$(p)}$(s).out

permute: $(bin)
	@$<

bin: $(bin)

$(bin): permute-gen.php
	@php -d display_errors=stderr -f $< "$(p)" $(s) \
	    | gcc -x assembler - -o $@

clean:
	@rm -f permute{*}*.out

clean-one:
	@rm -f $(bin)
```
**permute-gen.php**: [php]<?php 

/* Command-line arguments: $word [$something]
 * - $word is the word to permute
 * - if $something is anything other than "print",
 *   then the compiled code will go through the
 *   permutations without printing anything out.
 *   ("print" is the default if the argument is
 *   omitted.) 
 */ 

if (!isset($argv[1])):
    $argv[1] = "";
endif;

$word = $argv[1];
$n = strlen($word);

if (!isset($argv[2])):
    $argv[2] = "print";
endif;

/* For convenience, the printing is all done through
 * this function 
 */
function process($arg) {
    switch($arg):
    case "print":
?>
        call    fwrite
<?php
        break;
    default:
    endswitch;
}

function swap($r1, $r2) { ?>
        movb    <?php echo $r1; ?>, %dl
        movb    <?php echo $r2; ?>, %dh
        movb    %dl,    <?php echo $r2; ?> 
        movb    %dh,    <?php echo $r1; ?> 
<?php
}
?>
        .data
word:
        .asciz "<?php echo addslashes($word); ?>\n"
        
        .text

        .global main
main:
<?php 
/* Special case for strings of one or zero
 * characters
 */ 
if ($n <= 1): 
?>
        pushl   stdout
        pushl   $<?php echo $n+1; ?> 
        pushl   $1
        pushl   $word

<?php   process($argv[2]); ?>

        addl    $16,    %esp
        xorl    %eax,   %eax
        ret
<?php
else:
?>
        pushl   %ebp
        movl    %esp,   %ebp

        subl    $12,     %esp
        
        movl    %ebx,   -4(%ebp)
        movl    %edi,   -8(%ebp)
        movl    %esi,   -12(%ebp)

<?php   /* Initialize the counter */ ?>
        movl    $<?php echo $n-1; ?>,     %ecx

        jmp     loop_end
init_loop:
        pushl   $0
loop_end:
        loop    init_loop

<?php   /* Set up the call to fwrite (once and for all,
         * since we don't call any other functions)
         */ ?>
        pushl   stdout
        pushl   $<?php echo $n+1; ?> 
        pushl   $1
        pushl   $word

<?php   /* The proper algorithm follows */ ?>

        xorl    %esi,   %esi
        jmp     iterate

swap:
<?php   /* The classic method to take the absolute
         * value of EAX in three instructions
         */ ?>
        cltd
        xorl    %edx,   %eax
        subl    %edx,   %eax

        addl    %ebx,   %eax

<?php   swap("-1(%eax)", "(%eax)"); ?>

iterate:
<?php   process($argv[2]); ?>

        movl    (%esp), %ebx
        testl   %esi,   %esi
        jnz     backward

<?php   
    /* The unrolled inner loop (2 versions, for
     * swapping forward or backward)
     */ 
    for ($k = 0; $k <= $n-2; ++$k): 
        swap("$k(%ebx)", ($k+1)."(%ebx)");
        process($argv[2]);
    endfor; 
?>
        jmp     counter_update

backward:
<?php   
    for ($k = $n-2; $k >= 0; --$k): 
        swap("$k(%ebx)", ($k+1)."(%ebx)");
        process($argv[2]); 
    endfor; 
?>
        incl    %ebx
<?php   /* As we can see, the big counter-update loop is 
         * also simplified to a nested sequence of loops
         */ ?>
counter_update:
        xorl    $1,     %esi
<?php   
    for ($k = $n-2; $k >= 2; --$k): 
?>
        movl    <?php echo ($k+3)*4; ?>(%esp), %eax
        incl    %eax
        jz      inc_<?php echo $k; ?> 
        cmpl    $<?php echo $k+1; ?>,    %eax
        jz      carry_<?php echo $k; ?>

        movl    %eax,    <?php echo ($k+3)*4; ?>(%esp)
        jmp     swap

inc_<?php echo $k; ?>:
        incl    %ebx
carry_<?php echo $k; ?>:
        negl    %eax
        movl    %eax,    <?php echo ($k+3)*4; ?>(%esp)
<?php   
    endfor; 

    if ($n > 2): 
        /* 2-character strings are a special case here */
?>
        movl    16(%esp), %eax
        incl    %eax
        cmpl    $2,    %eax
        jz      final

        movl    %eax,   16(%esp)
        jmp     swap
<?php   
    endif;
?>

final:
<?php   /* This returns the string to its original state.
         * (Not strictly necessary, but it's an interesting
         * feature of this particular permutation sequence
         * that the last permutation is one swap away from
         * the first one.)
         */ ?>
        movl    (%esp), %ebx
        
<?php   swap(($n-2)."(%ebx)", ($n-1)."(%ebx)"); ?>
        
        movl    -12(%ebp), %esi
        movl    -8(%ebp), %edi
        movl    -4(%ebp), %ebx

        movl    %ebp,   %esp
        popl    %ebp

        xorl    %eax,   %eax
        ret
<?php 
endif; 
?>[/php]Concerning efficiency: for small strings, the running time is dominated by assembly & linking (with make & php also having a small contribution), which makes it not competitive with other optimized code. However, for anything with about 11 characters or more, this beats all of my other programs.

---

### Post by mo.reina on 2012-08-09
Super late to the party but...

Common Lisp:
```
(defun list-switch (a b lst)
  "Switch elements at position a & b with each other"
  (let ((newlst (copy-list lst)))
    (psetf (nth a newlst) (nth b newlst)
           (nth b newlst) (nth a newlst))
    newlst))

(defun permute (lst)
  ;; reduces the results from start-algo function
  (let ((final nil))
    (mapcar (lambda (x)
              (if (= (length x) (length lst))
                  (push x final)))
            (start-algo lst))
    final))

(defun start-algo (lst)  
  (let ((container nil))
    (push (list (car lst) (cadr lst)) container)
    (push (list-switch 0 1 (car container)) container)
    (setf lst (cddr lst))
    (dotimes (n (length lst))
      (mapcar (lambda (x)
                (setf x (push (car lst) x))
                (push x container)
                (dotimes (i (1- (length x)))
                  (push (list-switch i (1+ i) (car container)) container)))
              container)
      (setf lst (cdr lst)))
    container))
```

Results:
```
CL-USER> (permute '(1 2 3 4))

((4 1 2 3) (1 4 2 3) (1 2 4 3) (1 2 3 4) (4 1 3 2) (1 4 3 2) (1 3 4 2)
 (1 3 2 4) (4 3 1 2) (3 4 1 2) (3 1 4 2) (3 1 2 4) (4 2 1 3) (2 4 1 3)
 (2 1 4 3) (2 1 3 4) (4 2 3 1) (2 4 3 1) (2 3 4 1) (2 3 1 4) (4 3 2 1)
 (3 4 2 1) (3 2 4 1) (3 2 1 4))
```

---

### Post by Brandonlayton on 2012-11-06
Python attempt:
```
def permutations(_list):
    if(type(_list)!=list): return None;
    if(len(_list)<=1): return _list;
    perms = []
    for la in _list:
        for lb in _list:
            p = [la,lb]
            if(perms.count(p)<=0 and la != lb):
                perms.append(p)
    return perms
```
In Interpreter:
```
permutations([1,2,3,4])
[[1, 2],
 [1, 3],
 [1, 4],
 [2, 1],
 [2, 3],
 [2, 4],
 [3, 1],
 [3, 2],
 [3, 4],
 [4, 1],
 [4, 2],
 [4, 3]]
```

This seems way to simple to be correct though haha.

---

### Post by schauerlich on 2012-11-08
> **Brandonlayton said:**
> Python attempt:
```
def permutations(_list):
    if(type(_list)!=list): return None;
    if(len(_list)<=1): return _list;
    perms = []
    for la in _list:
        for lb in _list:
            p = [la,lb]
            if(perms.count(p)<=0 and la != lb):
                perms.append(p)
    return perms
```
In Interpreter:
```
permutations([1,2,3,4])
[[1, 2],
 [1, 3],
 [1, 4],
 [2, 1],
 [2, 3],
 [2, 4],
 [3, 1],
 [3, 2],
 [3, 4],
 [4, 1],
 [4, 2],
 [4, 3]]
```

This seems way to simple to be correct though haha.

That isn't generating all permutations of the list, but the Cartesian product of the list on itself except for pairs (x, y) where x == y.

---

