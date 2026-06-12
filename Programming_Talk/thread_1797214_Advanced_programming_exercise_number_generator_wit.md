---
title: "Advanced programming exercise: number generator with rules"
date: 2011-07-04
forum: Programming Talk
---

### Post by slavik on 2011-07-04
[SIZE="3"]**Revised (better) wording:**[/SIZE]
> Your task, should you choose to accept it, is to write a function/program/class/module/package/whatever to take a list of n items and generate permutations of the list according to a set of m rules. The rules dictate which items from the list are allowed (or not allowed) to be in what position in the generated permutation. The rules are left as an exercise to the reader. To make things interesting, go for at least n = 4.

[SIZE="3"]**Original (horrible) wording:**[/SIZE]
> Following on the last two exercises, this exercise consists of generating a number sequence with added rules. You are to generate a number sequence from 1 to n (you pick n, of course) where no number repeats and there are extra rules rules of what numbers can be in some places and what number cannot be in some places. That is, you can restrict the first place by having a rule that disallows certain numbers from appearing there, thus cutting down on the number of sequences you generate. (which will be less than n! due to these, the more rules, the less sequences). You may also restrict some places to specific numbers.

The next exercise will be a follow up to this one. :)

---

### Post by krazyd on 2011-07-05
I don't understand the problem description :-(

Could you please elaborate?

---

### Post by slavik on 2011-07-05
You need to generate a number sequence of numbers from 1 to n, but you also have rules that say that some numbers must be in certain spots and other numbers may not be in some spots.

The rules are yours to decide.

---

### Post by Simian Man on 2011-07-05
This is a weird exercise, but why not.  I generate the sequence in order except that the odds come first and then the evens.  This is in F#:
```

let gen_seq n =
  List.sortBy (fun x -> (x % 2 * -n) + x) [1 .. n]

printf "%A\n" (gen_seq 10)

```

---

### Post by zobayer1 on 2011-07-05
What do you mean actually?

1. A sequence of numbers using all the numbers from 1 to n?

2. Any combination / permutation of all the n numbers that follow the rules?

3. One such combination or all of them?

4. Should we take each number? or we can left some out?

Please clarify..

---

### Post by JupiterV2 on 2011-07-05
Confusing as it may seem, I think this is part of the exercise. IMO, they're purposefully ambiguous to allow for many different interpretations/implementations. My mind is boggled with possibilities for creative solutions!

---

### Post by slavik on 2011-07-05
yes, it is supposed to be ambiguous. the next exercise will tie into this one.

and all permutations of numbers from 1 to n that fit the all the rules.

---

### Post by zobayer1 on 2011-07-05
> **slavik said:**
> yes, it is supposed to be ambiguous. the next exercise will tie into this one.

and all permutations of numbers from 1 to n that fit the all the rules.
Library functions not allowed, am I right?

---

### Post by holiday on 2011-07-05
So a rule could be that the value at slot i+1 must be a multiple or factor of the value at slot i. This must be considered if i+2 is occupied by a random slotting of a previously generated value.

Is there an algorithm that fills all the slots without any discards? 

If the first value up is a 2 and the next is a 4, you're done.

But if the next is a 3 you can't put it by the 2. If you put it one slot away then you will never form a contiguous sequence. 

Legal numbers are integers 2 to 9.

You have to write two versions and the second version must better your first's average time over 100 runs.

---

### Post by lisati on 2011-07-05
My $0.02 on ambiguity: A degree of ambiguity is something we might have to face in "real world" programming tasks set by other people, e.g. the boss. How we handle the ambiguity can make the difference between an OK program, and one which is really brilliant.

---

### Post by holiday on 2011-07-05
Thinking more about this, I see many problems. 

You can generate the shortest sequence by randomly positioning (discarding) all values that are not multiples or factors of the first. Presto, the shortest possible sequence.

So we have to limit the number of slots and increase the requirement for 'sequence'. Say 5. 

The more I think about this, the less I like it. 


> **holiday said:**
> So a rule could be that the value at slot i+1 must be a multiple or factor of the value at slot i. This must be considered if i+2 is occupied by a random slotting of a previously generated value.

Is there an algorithm that fills all the slots without any discards? 

If the first value up is a 2 and the next is a 4, you're done.

But if the next is a 3 you can't put it by the 2. If you put it one slot away then you will never form a contiguous sequence. 

Legal numbers are integers 2 to 9.

You have to write two versions and the second version must better your first's average time over 100 runs.

---

### Post by slavik on 2011-07-05
library functions are fine
the rules are what digits can and cannot go in which slots (or don't care)
rules do not involve algebra between terms (ie: i+1 term must be i term  times two or something)

EDIT: as far as ambiguity, there must be some, since if I make it specific, I am giving away the next exercise.

---

### Post by ceclauson on 2011-07-05
My solution: n=1, so the trivial sequence, "1".  Simple to generate in any language.

---

### Post by sisco311 on 2011-07-05
> **slavik said:**
> Following on the last two exercises, this exercise consists of generating a number sequence with added rules. You are to generate a number sequence from 1 to n (you pick n, of course) where no number repeats and there are extra rules rules of what numbers can be in some places and what number cannot be in some places. That is, you can restrict the first place by having a rule that disallows certain numbers from appearing there, thus cutting down on the number of sequences you generate. (which will be less than n! due to these, the more rules, the less sequences). You may also restrict some places to specific numbers.


<insert a bijective function here> 

I think, the most trivial one is something like this (in pseudocode):
```

for i in 0..n-1
do
  a[i]=i
done

```

The rule is obvious. The nth number must be n.

> **slavik said:**
> 
The next exercise will be a follow up to this one. :)

What's the trick? :)

---

### Post by slavik on 2011-07-05
the trick is to be able to adjust the rule

---

### Post by jmartrican on 2011-07-05
My version in Java.

two classes:  NumberGenerator, RuleFactory
one interface:  Rule

... the implementation below is for NumberGenerator, which uses Rule and RuleFactory.

```

package generator;

import java.util.ArrayList;
import java.util.Iterator;

/**
 *
 * @author Jose
 */
public class NumberGenerator {

    private ArrayList<Integer> generatedNumbers = new ArrayList<Integer>();
    private ArrayList<Integer> numbersSetAside = new ArrayList<Integer>();
    private RuleFactory rulesFactory = new RuleFactory();
    private ArrayList<Rule> rules = new ArrayList<Rule>();
    private final Integer n = 999999;

    public static void main(String[] arg) {
        NumberGenerator numberGenerator = new NumberGenerator();
        numberGenerator.populateRules();
        numberGenerator.generate();
    }

    public void populateRules() {
        rules.clear();
        Rule rule = rulesFactory.getNextRule();
        while (rule != null) {
            rules.add(rule);
            rule = rulesFactory.getNextRule();
        }
    }//end of:  public void populateRules()

    public void generate() {
        generatedNumbers.clear();
        numbersSetAside.clear();
        for (int i = 1; i <= n; i++) {
            boolean numberIsAcceptable = false;
            Iterator<Rule> itRules = rules.iterator();
            while (itRules.hasNext()) {
                if (itRules.next().isNumberAcceptable(generatedNumbers, i) == true) {
                    generatedNumbers.add(i);
                    numberIsAcceptable = true;
                    break;
                }
            }
            if (numberIsAcceptable == false) {
                numbersSetAside.add(i);
            }
        }//for (int i = 1; i <= n; i++)

        //make an attempt to include numbersSetAside
        Iterator<Integer> itAside = numbersSetAside.iterator();
        while (itAside.hasNext()) {
            Integer i = itAside.next();
            Iterator<Rule> itRules = rules.iterator();
            while (itRules.hasNext()) {
                if (itRules.next().isNumberAcceptable(generatedNumbers, i) == true) {
                    generatedNumbers.add(i);
                    break;
                }
            }
        }

    }//end of:  public void generate()
}//end of:  public class NumberGenerator

```

....the implementation below is for the Rule interface
```

package generator;

import java.util.ArrayList;

/**
 *
 * @author Jose
 */
public interface Rule {
        public boolean isNumberAcceptable(ArrayList<Integer> previousNumbers, Integer newNumber);
}

```

---

### Post by schauerlich on 2011-07-06
```
(ns adv.ex.four
  (:use (clojure.contrib combinatorics)))

(defn follows-rules [rules sequence]
  (reduce #(and %1 %2)
          (map #(% sequence) rules)))

(defn number-generator [rules n]
  (filter #(follows-rules rules %)
          (lex-permutations (range 1 (inc n)))))

```

```

adv.ex.four> (def rules [#(=    (nth % 1) 1)                                                                            
                         #(not= (nth % 2) 2)])
#'adv.ex.four/rules                                                                                                     
adv.ex.four> (number-generator rules 4)
([2 1 3 4] [2 1 4 3] [3 1 4 2] [4 1 3 2])

```

---

### Post by krazyd on 2011-07-06
[PHP]#!/usr/bin/ruby

def generator(n, rules)
    a = *(1..n); d = []
    rules.each {|rule| a.each {|m| d << m if rule.call(m)}}
    a - d.uniq!
end

rules = [                                   # disallow if:
    -> i {i > 10 && i.odd?},                # odd and greater than 10
    -> i {(i%3).zero?},                     # multiple of 3
    -> i {i < 5 && ((Math.sqrt i)%1).zero?} # square smaller than 5
]

p generator(20, rules)
[/PHP]

```
$ ./rules.rb
[2, 5, 7, 8, 10, 14, 16, 20]
```

If anyone does this exercise in C I'd be pretty impressed :-D

---

### Post by JupiterV2 on 2011-07-06
So here is a very simple interpretation of the rules. New rule(s) can be added easily or could be chained together. The code will infinitely generate numbers until the nth number in the sequence is found.

```
package main

import "fmt"

func every_third(in, out chan int) {
	for {
		n := <-in
		if n%3 == 0 {
			out <- n
			break
		}
	}
}

func generate(ch chan int) {
	for i := 1; ; i++ {
		ch <- i
	}
}

func main() {
	in := make(chan int)
	go generate(in)            // start a new thread which generates numbers
	for i := 1; i <= 10; i++ { // find the next 10 numbers in the sequence
		out := make(chan int)
		go every_third(in, out) // replace with whatever you want
		res := <-out
		fmt.Print(i, ": ", res, "\n")
	}
}

```

---

### Post by schauerlich on 2011-07-07
It seems a lot of people are generating [1, 2, ..., n] and then applying the rules to that one sequence. However, slavik said [here](http://ubuntuforums.org/showpost.php?p=11016150&postcount=7) that you should keep *all permutations* of the sequence [1, 2, ..., n] that fit the rules.

---

### Post by slavik on 2011-07-07
think all permutations with a filter ;) filters talk about spots in sequence, not relationships between numbers.

---

### Post by ve4cib on 2011-07-07
I suppose a trivial solution would be something like this:

```

Permutation p = [1,2,3,...,n];

while(p != null)
{
    if (checkRules(p))
        output p;
    p = p.getSuccessor();
}


function checkRules(Permutation p)
{
    ...
    // return TRUE if the rules are satisfied, otherwise
    // return FALSE
}

```

One could expand this to allow checkRules to be a function pointer/lambda function that is passed as a parameter.  That would make this solution (arguably) the most general-purpose.

The down-side is obviously the run-time.  It's O(n! * n), since we're checking each permutation if it breaks the rules (O(n)), and doing that to all n! permutations.

A much more elegant solution would be to modify the permutation's successor function to take the rules into account.  That makes the solution less broad, but more efficient.

---

### Post by slavik on 2011-07-07
> **ve4cib said:**
> ...
A much more elegant solution would be to modify the permutation's successor function to take the rules into account.  That makes the solution less broad, but more efficient.

we have a winnar!!!
your prize is a handful of interwebs.

---

### Post by jmartrican on 2011-07-07
I know its cool to write short code that can wow your friends.  While mine was not the shortest it allowed for the easy integration of new rules via the RuleFactory.   A Rules interface was created that allowed for anyone to create new rules based on that interface.  The Rule interface member function took in a list of the previous numbers generated so that the rule can take into account all the previous generated numbers when deciding on the current one.  Everything was properly encapsulated to allow changes to one part of the code without affecting another.

I just do not see how the proclaimed winner's quick script could be the winner.  His function only take in the current number, and not the previous numbers.  No factory for retrieving a set of rules and ordering them.  No interface to define how a rule is used.

just sayin..... :)

thanks
jose

---

### Post by slavik on 2011-07-07
> **jmartrican said:**
> I know its cool to write short code that can wow your friends.  While mine was not the shortest it allowed for the easy integration of new rules via the RuleFactory.   A Rules interface was created that allowed for anyone to create new rules based on that interface.  The Rule interface member function took in a list of the previous numbers generated so that the rule can take into account all the previous generated numbers when deciding on the current one.  Everything was properly encapsulated to allow changes to one part of the code without affecting another.

I just do not see how the proclaimed winner's quick script could be the winner.  His function only take in the current number, and not the previous numbers.  No factory for retrieving a set of rules and ordering them.  No interface to define how a rule is used.

just sayin..... :)

thanks
jose
there is no winner ... this isn't a contest. the point I was trying to convey was that ve4clb understood what the point of the exercise is.

---

### Post by JupiterV2 on 2011-07-07
So I want to make sure I understand: The test here isn't to apply rules against numbers 1 through n but create a number generated which produces a sequence based on (a) rule(s)? Using C-ish psuedocode:

```
typedef int (*Rule)(int)

int rule(int prev) {
  // algorithm to generate next number based on previous in sequence
  return next_number;
}

void generator(Rule *r) {
  int n = 1;

  for(int i = 0; i < max_sequence_len; i++)
    print n;
    n = r(n);
  }
}

int main() {
  generate(rule);
  done;
}
```

---

### Post by Simian Man on 2011-07-07
> **slavik said:**
> there is no winner ... this isn't a contest. the point I was trying to convey was that ve4clb understood what the point of the exercise is.

If it takes 22 posts for somebody to even understand the exercise, maybe you should just explain things better :).

---

### Post by slavik on 2011-07-07
I realized that after the first post. Haven't had a chance to reword it. Maybe sometime today.

---

### Post by schauerlich on 2011-07-07
> **JupiterV2 said:**
> So I want to make sure I understand: The test here isn't to apply rules against numbers 1 through n but create a number generated which produces a sequence based on (a) rule(s)? Using C-ish psuedocode:

The idea is to find EVERY PERMUTATION of the sequence 1..n for which the rules hold.

```
adv.ex.four> (lex-permutations [1 2 3]) ; all permutations of [1 2 3]
([1 2 3] [1 3 2] [2 1 3] [2 3 1] [3 1 2] [3 2 1])                                                                       
adv.ex.four> (def rules [(fn [seq] (not= (first seq) 1))]) ; make a rule: the first number != 1
#'adv.ex.four/rules                                                                                                     
adv.ex.four> (number-generator rules 3) ; all permutations such that the first number != 1
([2 1 3] [2 3 1] [3 1 2] [3 2 1]) 
```

---

### Post by JupiterV2 on 2011-07-07
> **schauerlich said:**
> The idea is to find EVERY PERMUTATION of the sequence 1..n for which the rules hold.[/code]

"I see!" says the blind man...! I was NOT getting the **every permutation** part...with any luck I'll get something working when I get home from work.

---

### Post by Leuchten on 2011-07-08
Scala code. Dunno if this is fair or not.

```

val list = List(1,2,3,4,5)

println((list.permutations.toList).dropWhile((l) => l(0) == 1))

```

removes all permutations that start with 1.

---

### Post by slavik on 2011-07-08
Updated the wording, please let me know if it makes sense. Reproduced below:

> Your task, should you choose to accept it, is to write a function/program/class/module/package/whatever to take a list of n items and generate permutations of the list according to a set of m rules. The rules dictate which items from the list are allowed (or not allowed) to be in what position in the generated permutation. The rules are left as an exercise to the reader. To make things interesting, go for at least n = 4.

---

### Post by StephenF on 2011-07-09
> **Simian Man said:**
> If it takes 22 posts for somebody to even understand the exercise, maybe you should just explain things better :).
He's keeping the bigger picture under wraps. Next up, a sudoku solver perhaps? :-\"

---

### Post by Simian Man on 2011-07-09
Now that I understand the rules, here is my version in F#.  I have since learned that F# has a builtin permute function, but I already wrote this one, so I'm going to use it :).

```

(* insert value into each position of list and return them all *)
let rec insert value list =
  match list with
    [] -> [[value]]
    | head::tail -> (value::list) :: (List.map (fun x -> head::x) (insert value tail))

(* return all permutations of a list *)
let rec permutations = function
  head::tail -> List.concat (List.map (insert head) (permutations tail))
  | x -> [x]

(* return all permutations of a list that match every rule *)
let valid_permutations list rules =
  let rec is_valid rules list =
    List.fold (fun accum rule -> accum && (rule list)) true rules
  List.filter (is_valid rules) (permutations list)


(* and now for some examples *)


(* all *)
printf "%A\n\n" (valid_permutations [1 .. 3] [])

(* ones with one in the first element *)
let one_first = fun l -> (List.nth l 0) = 1
printf "%A\n\n" (valid_permutations [1 ..4] [one_first])

(* ones where the last element is even *)
let even_last = fun l -> (List.nth l (List.length l - 1)) % 2 = 0
printf "%A\n\n" (valid_permutations [1 ..4] [even_last])

(* ones where the first element is one AND the last element is even *)
printf "%A\n\n" (valid_permutations [1 ..5] [one_first; even_last])

```

Output:
```

[[1; 2; 3]; [2; 1; 3]; [2; 3; 1]; [1; 3; 2]; [3; 1; 2]; [3; 2; 1]]

[[1; 2; 3; 4]; [1; 3; 2; 4]; [1; 3; 4; 2]; [1; 2; 4; 3]; [1; 4; 2; 3];
 [1; 4; 3; 2]]

[[1; 2; 3; 4]; [2; 1; 3; 4]; [2; 3; 1; 4]; [1; 3; 2; 4]; [3; 1; 2; 4];
 [3; 2; 1; 4]; [1; 3; 4; 2]; [3; 1; 4; 2]; [3; 4; 1; 2]; [1; 4; 3; 2];
 [4; 1; 3; 2]; [4; 3; 1; 2]]

[[1; 3; 4; 5; 2]; [1; 4; 3; 5; 2]; [1; 4; 5; 3; 2]; [1; 2; 3; 5; 4];
 [1; 3; 2; 5; 4]; [1; 3; 5; 2; 4]; [1; 3; 5; 4; 2]; [1; 2; 5; 3; 4];
 [1; 5; 2; 3; 4]; [1; 5; 3; 2; 4]; [1; 5; 3; 4; 2]; [1; 5; 4; 3; 2]]

```

---

### Post by JupiterV2 on 2011-07-10
My first attempt at a concurrent permutation generator with filters in Go. This could be a lot nicer/cleaner I think but it gets the job done. An unlimited number of filters can be added to the call to the 'filter' function/thread. I realize I used terrible variable names in some spots but I just wanted to quickly hack it together. I might come up with better names later.

```
package main

import "fmt"

type Filter func(arr []int) bool // filter definition

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

func filter(in, out chan []int, filters ...Filter) {
	for arr := <-in; len(arr) > 0; arr = <-in {
		ok := true
		for i := range filters {
			if !filters[i](arr) {
				ok = false
				break
			}
		}
		if ok {
			out <- arr
		}
	}
	out <- []int{}
	return
}

// filter 1
func f1(arr []int) bool {
	if arr[3] != 1 {
		return true
	}
	return false
}

// filter 2
func f2(arr []int) bool {
	if arr[1] != 3 {
		return true
	}
	return false
}

func main() {
	i := []int{1,2,3,4} // array to create permutation from
	permChan := make(chan []int)
	go permutate(i, permChan)
	filChan := make(chan []int)
	go filter(permChan, filChan, f1, f2) // any number of filters
	for x := <-filChan; len(x) > 0; x = <-filChan {
		fmt.Println(x)
	}
}
```

Results:
```
[1 2 3 4]
[2 1 3 4]
[3 1 2 4]
[3 2 1 4]
[3 1 4 2]
[3 4 1 2]
[1 2 4 3]
[2 1 4 3]
[2 4 1 3]
[1 4 2 3]
[4 1 2 3]
[4 2 1 3]
[1 4 3 2]
[4 1 3 2]
```

Look ma! No 3's in column 2 and no 1's in column 4!

---

### Post by ve4cib on 2011-07-11
A very quick effort in Python.  I'm using the standard recursive algorithm for generating permutations in lexicographic order, with the checkRules function being called to prune any invalid branches.  I think I spent more time inserting comments than I did writing it.

The arbitrary rules I've chosen are:
1- the first digit must be odd
2- all even-numbered indices must contain sequential digits

```
#!/usr/bin/python
"""
Generate all permutations that satisfy the following rules:
    - the first number is odd
    - every even-numbered index (0, 2, 4, ...) contains a sequential digit
    
    e.g. [1, 2, 3, 4, 5, 6] is invalid (breaks rule 2)
    e.g. [2, 1, 3, 6, 4, 5] is invalid (breaks rule 2)
    e.g. [3, 1, 4, 2, 5, 6] is valid
"""
N = 12
X = range(N)

def genPermutation(perm, available, allPerms):
    """
    Recursively generates permutations, pruning by applying
    the checkRules function to avoid going down invalid
    branches
    """

    if len(available) == 0:
        # generated a valid permutation
        x = []
        for i in perm:
            x.insert(len(x), i)
    
        allPerms.insert(len(allPerms), x)

    else:
        # go through each available digit and add it to the list
        # if adding that digit does not invalidate the permutation
        # then recursively construct the rest of the permutation
        count = len(available)  # cannot just use len(available) in the loop since we're pusing & popping
        for i in range(count):
            x = available[i]
        
            # insert x into the permutation
            perm.insert(len(perm), x)
            available.remove(x)
           
            # check if we've violated any rules
            if checkRules(perm):
                genPermutation(perm, available, allPerms)
                
            # pop x off the permutation since we're done with it
            available.insert(i,x)
            perm.pop(len(perm)-1)
        
        
def checkRules(p):
    """
    Verfiy that our arbitrary rules are satisfied by the permutation p
    note: p may not be a complete permutation
    """

    # check that the first value is odd
    if p[0] % 2 == 0:
        return False
        
    # check that every even-numbered index contains
    # a sequential digit
    if len(p) >= 3:
        last = p[0]
        for i in range(2, len(p), 2):
            if p[i] != last+1:
                return False
            last = p[i]
     
    # if we ever reach this point the p is valid       
    return True
        
if __name__=='__main__':
    
    allPerms = []        
    genPermutation([],X, allPerms)
    
    for i in range(len(allPerms)):
        print i, allPerms[i]
```

And the output looks something like this:

```

0 [1, 0, 2, 7, 3, 8, 4, 9, 5, 10, 6, 11]
1 [1, 0, 2, 7, 3, 8, 4, 9, 5, 11, 6, 10]
2 [1, 0, 2, 7, 3, 8, 4, 10, 5, 9, 6, 11]
3 [1, 0, 2, 7, 3, 8, 4, 10, 5, 11, 6, 9]
4 [1, 0, 2, 7, 3, 8, 4, 11, 5, 9, 6, 10]
5 [1, 0, 2, 7, 3, 8, 4, 11, 5, 10, 6, 9]
6 [1, 0, 2, 7, 3, 9, 4, 8, 5, 10, 6, 11]
7 [1, 0, 2, 7, 3, 9, 4, 8, 5, 11, 6, 10]
8 [1, 0, 2, 7, 3, 9, 4, 10, 5, 8, 6, 11]
9 [1, 0, 2, 7, 3, 9, 4, 10, 5, 11, 6, 8]
10 [1, 0, 2, 7, 3, 9, 4, 11, 5, 8, 6, 10]
11 [1, 0, 2, 7, 3, 9, 4, 11, 5, 10, 6, 8]
12 [1, 0, 2, 7, 3, 10, 4, 8, 5, 9, 6, 11]
13 [1, 0, 2, 7, 3, 10, 4, 8, 5, 11, 6, 9]
14 [1, 0, 2, 7, 3, 10, 4, 9, 5, 8, 6, 11]
15 [1, 0, 2, 7, 3, 10, 4, 9, 5, 11, 6, 8]
16 [1, 0, 2, 7, 3, 10, 4, 11, 5, 8, 6, 9]
17 [1, 0, 2, 7, 3, 10, 4, 11, 5, 9, 6, 8]
18 [1, 0, 2, 7, 3, 11, 4, 8, 5, 9, 6, 10]
19 [1, 0, 2, 7, 3, 11, 4, 8, 5, 10, 6, 9]
20 [1, 0, 2, 7, 3, 11, 4, 9, 5, 8, 6, 10]
21 [1, 0, 2, 7, 3, 11, 4, 9, 5, 10, 6, 8]
22 [1, 0, 2, 7, 3, 11, 4, 10, 5, 8, 6, 9]
23 [1, 0, 2, 7, 3, 11, 4, 10, 5, 9, 6, 8]
24 [1, 0, 2, 8, 3, 7, 4, 9, 5, 10, 6, 11]
25 [1, 0, 2, 8, 3, 7, 4, 9, 5, 11, 6, 10]
26 [1, 0, 2, 8, 3, 7, 4, 10, 5, 9, 6, 11]
27 [1, 0, 2, 8, 3, 7, 4, 10, 5, 11, 6, 9]
28 [1, 0, 2, 8, 3, 7, 4, 11, 5, 9, 6, 10]
29 [1, 0, 2, 8, 3, 7, 4, 11, 5, 10, 6, 9]
30 [1, 0, 2, 8, 3, 9, 4, 7, 5, 10, 6, 11]
31 [1, 0, 2, 8, 3, 9, 4, 7, 5, 11, 6, 10]
32 [1, 0, 2, 8, 3, 9, 4, 10, 5, 7, 6, 11]
33 [1, 0, 2, 8, 3, 9, 4, 10, 5, 11, 6, 7]
34 [1, 0, 2, 8, 3, 9, 4, 11, 5, 7, 6, 10]
35 [1, 0, 2, 8, 3, 9, 4, 11, 5, 10, 6, 7]
36 [1, 0, 2, 8, 3, 10, 4, 7, 5, 9, 6, 11]
37 [1, 0, 2, 8, 3, 10, 4, 7, 5, 11, 6, 9]
38 [1, 0, 2, 8, 3, 10, 4, 9, 5, 7, 6, 11]
39 [1, 0, 2, 8, 3, 10, 4, 9, 5, 11, 6, 7]
40 [1, 0, 2, 8, 3, 10, 4, 11, 5, 7, 6, 9]
41 [1, 0, 2, 8, 3, 10, 4, 11, 5, 9, 6, 7]
42 [1, 0, 2, 8, 3, 11, 4, 7, 5, 9, 6, 10]
43 [1, 0, 2, 8, 3, 11, 4, 7, 5, 10, 6, 9]
44 [1, 0, 2, 8, 3, 11, 4, 9, 5, 7, 6, 10]
45 [1, 0, 2, 8, 3, 11, 4, 9, 5, 10, 6, 7]
46 [1, 0, 2, 8, 3, 11, 4, 10, 5, 7, 6, 9]
47 [1, 0, 2, 8, 3, 11, 4, 10, 5, 9, 6, 7]
48 [1, 0, 2, 9, 3, 7, 4, 8, 5, 10, 6, 11]
49 [1, 0, 2, 9, 3, 7, 4, 8, 5, 11, 6, 10]
50 [1, 0, 2, 9, 3, 7, 4, 10, 5, 8, 6, 11]
51 [1, 0, 2, 9, 3, 7, 4, 10, 5, 11, 6, 8]
52 [1, 0, 2, 9, 3, 7, 4, 11, 5, 8, 6, 10]
53 [1, 0, 2, 9, 3, 7, 4, 11, 5, 10, 6, 8]
54 [1, 0, 2, 9, 3, 8, 4, 7, 5, 10, 6, 11]
55 [1, 0, 2, 9, 3, 8, 4, 7, 5, 11, 6, 10]
56 [1, 0, 2, 9, 3, 8, 4, 10, 5, 7, 6, 11]
57 [1, 0, 2, 9, 3, 8, 4, 10, 5, 11, 6, 7]
58 [1, 0, 2, 9, 3, 8, 4, 11, 5, 7, 6, 10]
59 [1, 0, 2, 9, 3, 8, 4, 11, 5, 10, 6, 7]
60 [1, 0, 2, 9, 3, 10, 4, 7, 5, 8, 6, 11]
61 [1, 0, 2, 9, 3, 10, 4, 7, 5, 11, 6, 8]
62 [1, 0, 2, 9, 3, 10, 4, 8, 5, 7, 6, 11]
63 [1, 0, 2, 9, 3, 10, 4, 8, 5, 11, 6, 7]
64 [1, 0, 2, 9, 3, 10, 4, 11, 5, 7, 6, 8]
65 [1, 0, 2, 9, 3, 10, 4, 11, 5, 8, 6, 7]
66 [1, 0, 2, 9, 3, 11, 4, 7, 5, 8, 6, 10]
67 [1, 0, 2, 9, 3, 11, 4, 7, 5, 10, 6, 8]
68 [1, 0, 2, 9, 3, 11, 4, 8, 5, 7, 6, 10]
69 [1, 0, 2, 9, 3, 11, 4, 8, 5, 10, 6, 7]
70 [1, 0, 2, 9, 3, 11, 4, 10, 5, 7, 6, 8]
71 [1, 0, 2, 9, 3, 11, 4, 10, 5, 8, 6, 7]
72 [1, 0, 2, 10, 3, 7, 4, 8, 5, 9, 6, 11]
73 [1, 0, 2, 10, 3, 7, 4, 8, 5, 11, 6, 9]
74 [1, 0, 2, 10, 3, 7, 4, 9, 5, 8, 6, 11]
75 [1, 0, 2, 10, 3, 7, 4, 9, 5, 11, 6, 8]
76 [1, 0, 2, 10, 3, 7, 4, 11, 5, 8, 6, 9]
77 [1, 0, 2, 10, 3, 7, 4, 11, 5, 9, 6, 8]
78 [1, 0, 2, 10, 3, 8, 4, 7, 5, 9, 6, 11]
79 [1, 0, 2, 10, 3, 8, 4, 7, 5, 11, 6, 9]
80 [1, 0, 2, 10, 3, 8, 4, 9, 5, 7, 6, 11]
81 [1, 0, 2, 10, 3, 8, 4, 9, 5, 11, 6, 7]
82 [1, 0, 2, 10, 3, 8, 4, 11, 5, 7, 6, 9]
83 [1, 0, 2, 10, 3, 8, 4, 11, 5, 9, 6, 7]
84 [1, 0, 2, 10, 3, 9, 4, 7, 5, 8, 6, 11]
85 [1, 0, 2, 10, 3, 9, 4, 7, 5, 11, 6, 8]
86 [1, 0, 2, 10, 3, 9, 4, 8, 5, 7, 6, 11]
87 [1, 0, 2, 10, 3, 9, 4, 8, 5, 11, 6, 7]
88 [1, 0, 2, 10, 3, 9, 4, 11, 5, 7, 6, 8]
89 [1, 0, 2, 10, 3, 9, 4, 11, 5, 8, 6, 7]
90 [1, 0, 2, 10, 3, 11, 4, 7, 5, 8, 6, 9]
91 [1, 0, 2, 10, 3, 11, 4, 7, 5, 9, 6, 8]
92 [1, 0, 2, 10, 3, 11, 4, 8, 5, 7, 6, 9]
93 [1, 0, 2, 10, 3, 11, 4, 8, 5, 9, 6, 7]
94 [1, 0, 2, 10, 3, 11, 4, 9, 5, 7, 6, 8]
95 [1, 0, 2, 10, 3, 11, 4, 9, 5, 8, 6, 7]
96 [1, 0, 2, 11, 3, 7, 4, 8, 5, 9, 6, 10]
97 [1, 0, 2, 11, 3, 7, 4, 8, 5, 10, 6, 9]
98 [1, 0, 2, 11, 3, 7, 4, 9, 5, 8, 6, 10]
99 [1, 0, 2, 11, 3, 7, 4, 9, 5, 10, 6, 8]
100 [1, 0, 2, 11, 3, 7, 4, 10, 5, 8, 6, 9]
101 [1, 0, 2, 11, 3, 7, 4, 10, 5, 9, 6, 8]
102 [1, 0, 2, 11, 3, 8, 4, 7, 5, 9, 6, 10]
103 [1, 0, 2, 11, 3, 8, 4, 7, 5, 10, 6, 9]
104 [1, 0, 2, 11, 3, 8, 4, 9, 5, 7, 6, 10]
105 [1, 0, 2, 11, 3, 8, 4, 9, 5, 10, 6, 7]
106 [1, 0, 2, 11, 3, 8, 4, 10, 5, 7, 6, 9]
107 [1, 0, 2, 11, 3, 8, 4, 10, 5, 9, 6, 7]
108 [1, 0, 2, 11, 3, 9, 4, 7, 5, 8, 6, 10]
109 [1, 0, 2, 11, 3, 9, 4, 7, 5, 10, 6, 8]
110 [1, 0, 2, 11, 3, 9, 4, 8, 5, 7, 6, 10]
111 [1, 0, 2, 11, 3, 9, 4, 8, 5, 10, 6, 7]
112 [1, 0, 2, 11, 3, 9, 4, 10, 5, 7, 6, 8]
113 [1, 0, 2, 11, 3, 9, 4, 10, 5, 8, 6, 7]
114 [1, 0, 2, 11, 3, 10, 4, 7, 5, 8, 6, 9]
115 [1, 0, 2, 11, 3, 10, 4, 7, 5, 9, 6, 8]
116 [1, 0, 2, 11, 3, 10, 4, 8, 5, 7, 6, 9]
117 [1, 0, 2, 11, 3, 10, 4, 8, 5, 9, 6, 7]
118 [1, 0, 2, 11, 3, 10, 4, 9, 5, 7, 6, 8]
119 [1, 0, 2, 11, 3, 10, 4, 9, 5, 8, 6, 7]
120 [1, 7, 2, 0, 3, 8, 4, 9, 5, 10, 6, 11]
121 [1, 7, 2, 0, 3, 8, 4, 9, 5, 11, 6, 10]
122 [1, 7, 2, 0, 3, 8, 4, 10, 5, 9, 6, 11]
123 [1, 7, 2, 0, 3, 8, 4, 10, 5, 11, 6, 9]
124 [1, 7, 2, 0, 3, 8, 4, 11, 5, 9, 6, 10]
125 [1, 7, 2, 0, 3, 8, 4, 11, 5, 10, 6, 9]
126 [1, 7, 2, 0, 3, 9, 4, 8, 5, 10, 6, 11]
127 [1, 7, 2, 0, 3, 9, 4, 8, 5, 11, 6, 10]
128 [1, 7, 2, 0, 3, 9, 4, 10, 5, 8, 6, 11]
129 [1, 7, 2, 0, 3, 9, 4, 10, 5, 11, 6, 8]
130 [1, 7, 2, 0, 3, 9, 4, 11, 5, 8, 6, 10]
131 [1, 7, 2, 0, 3, 9, 4, 11, 5, 10, 6, 8]
132 [1, 7, 2, 0, 3, 10, 4, 8, 5, 9, 6, 11]
133 [1, 7, 2, 0, 3, 10, 4, 8, 5, 11, 6, 9]
134 [1, 7, 2, 0, 3, 10, 4, 9, 5, 8, 6, 11]
135 [1, 7, 2, 0, 3, 10, 4, 9, 5, 11, 6, 8]
136 [1, 7, 2, 0, 3, 10, 4, 11, 5, 8, 6, 9]
137 [1, 7, 2, 0, 3, 10, 4, 11, 5, 9, 6, 8]
138 [1, 7, 2, 0, 3, 11, 4, 8, 5, 9, 6, 10]
139 [1, 7, 2, 0, 3, 11, 4, 8, 5, 10, 6, 9]
140 [1, 7, 2, 0, 3, 11, 4, 9, 5, 8, 6, 10]
141 [1, 7, 2, 0, 3, 11, 4, 9, 5, 10, 6, 8]
142 [1, 7, 2, 0, 3, 11, 4, 10, 5, 8, 6, 9]
143 [1, 7, 2, 0, 3, 11, 4, 10, 5, 9, 6, 8]
144 [1, 7, 2, 8, 3, 0, 4, 9, 5, 10, 6, 11]
145 [1, 7, 2, 8, 3, 0, 4, 9, 5, 11, 6, 10]
146 [1, 7, 2, 8, 3, 0, 4, 10, 5, 9, 6, 11]
147 [1, 7, 2, 8, 3, 0, 4, 10, 5, 11, 6, 9]
148 [1, 7, 2, 8, 3, 0, 4, 11, 5, 9, 6, 10]
149 [1, 7, 2, 8, 3, 0, 4, 11, 5, 10, 6, 9]
150 [1, 7, 2, 8, 3, 9, 4, 0, 5, 10, 6, 11]
151 [1, 7, 2, 8, 3, 9, 4, 0, 5, 11, 6, 10]
152 [1, 7, 2, 8, 3, 9, 4, 10, 5, 0, 6, 11]
153 [1, 7, 2, 8, 3, 9, 4, 10, 5, 11, 6, 0]
154 [1, 7, 2, 8, 3, 9, 4, 11, 5, 0, 6, 10]
155 [1, 7, 2, 8, 3, 9, 4, 11, 5, 10, 6, 0]
156 [1, 7, 2, 8, 3, 10, 4, 0, 5, 9, 6, 11]
157 [1, 7, 2, 8, 3, 10, 4, 0, 5, 11, 6, 9]
158 [1, 7, 2, 8, 3, 10, 4, 9, 5, 0, 6, 11]
159 [1, 7, 2, 8, 3, 10, 4, 9, 5, 11, 6, 0]
160 [1, 7, 2, 8, 3, 10, 4, 11, 5, 0, 6, 9]
161 [1, 7, 2, 8, 3, 10, 4, 11, 5, 9, 6, 0]
162 [1, 7, 2, 8, 3, 11, 4, 0, 5, 9, 6, 10]
163 [1, 7, 2, 8, 3, 11, 4, 0, 5, 10, 6, 9]
164 [1, 7, 2, 8, 3, 11, 4, 9, 5, 0, 6, 10]
165 [1, 7, 2, 8, 3, 11, 4, 9, 5, 10, 6, 0]
166 [1, 7, 2, 8, 3, 11, 4, 10, 5, 0, 6, 9]
167 [1, 7, 2, 8, 3, 11, 4, 10, 5, 9, 6, 0]
168 [1, 7, 2, 9, 3, 0, 4, 8, 5, 10, 6, 11]
169 [1, 7, 2, 9, 3, 0, 4, 8, 5, 11, 6, 10]
170 [1, 7, 2, 9, 3, 0, 4, 10, 5, 8, 6, 11]
171 [1, 7, 2, 9, 3, 0, 4, 10, 5, 11, 6, 8]
172 [1, 7, 2, 9, 3, 0, 4, 11, 5, 8, 6, 10]
173 [1, 7, 2, 9, 3, 0, 4, 11, 5, 10, 6, 8]
174 [1, 7, 2, 9, 3, 8, 4, 0, 5, 10, 6, 11]
175 [1, 7, 2, 9, 3, 8, 4, 0, 5, 11, 6, 10]
176 [1, 7, 2, 9, 3, 8, 4, 10, 5, 0, 6, 11]
177 [1, 7, 2, 9, 3, 8, 4, 10, 5, 11, 6, 0]
178 [1, 7, 2, 9, 3, 8, 4, 11, 5, 0, 6, 10]
179 [1, 7, 2, 9, 3, 8, 4, 11, 5, 10, 6, 0]
180 [1, 7, 2, 9, 3, 10, 4, 0, 5, 8, 6, 11]
181 [1, 7, 2, 9, 3, 10, 4, 0, 5, 11, 6, 8]
182 [1, 7, 2, 9, 3, 10, 4, 8, 5, 0, 6, 11]
183 [1, 7, 2, 9, 3, 10, 4, 8, 5, 11, 6, 0]
184 [1, 7, 2, 9, 3, 10, 4, 11, 5, 0, 6, 8]
185 [1, 7, 2, 9, 3, 10, 4, 11, 5, 8, 6, 0]
186 [1, 7, 2, 9, 3, 11, 4, 0, 5, 8, 6, 10]
187 [1, 7, 2, 9, 3, 11, 4, 0, 5, 10, 6, 8]
188 [1, 7, 2, 9, 3, 11, 4, 8, 5, 0, 6, 10]
189 [1, 7, 2, 9, 3, 11, 4, 8, 5, 10, 6, 0]
190 [1, 7, 2, 9, 3, 11, 4, 10, 5, 0, 6, 8]
191 [1, 7, 2, 9, 3, 11, 4, 10, 5, 8, 6, 0]
192 [1, 7, 2, 10, 3, 0, 4, 8, 5, 9, 6, 11]
193 [1, 7, 2, 10, 3, 0, 4, 8, 5, 11, 6, 9]
194 [1, 7, 2, 10, 3, 0, 4, 9, 5, 8, 6, 11]
195 [1, 7, 2, 10, 3, 0, 4, 9, 5, 11, 6, 8]
196 [1, 7, 2, 10, 3, 0, 4, 11, 5, 8, 6, 9]
197 [1, 7, 2, 10, 3, 0, 4, 11, 5, 9, 6, 8]
198 [1, 7, 2, 10, 3, 8, 4, 0, 5, 9, 6, 11]
199 [1, 7, 2, 10, 3, 8, 4, 0, 5, 11, 6, 9]
200 [1, 7, 2, 10, 3, 8, 4, 9, 5, 0, 6, 11]
201 [1, 7, 2, 10, 3, 8, 4, 9, 5, 11, 6, 0]
202 [1, 7, 2, 10, 3, 8, 4, 11, 5, 0, 6, 9]
203 [1, 7, 2, 10, 3, 8, 4, 11, 5, 9, 6, 0]
204 [1, 7, 2, 10, 3, 9, 4, 0, 5, 8, 6, 11]
205 [1, 7, 2, 10, 3, 9, 4, 0, 5, 11, 6, 8]
206 [1, 7, 2, 10, 3, 9, 4, 8, 5, 0, 6, 11]
207 [1, 7, 2, 10, 3, 9, 4, 8, 5, 11, 6, 0]
208 [1, 7, 2, 10, 3, 9, 4, 11, 5, 0, 6, 8]
209 [1, 7, 2, 10, 3, 9, 4, 11, 5, 8, 6, 0]
210 [1, 7, 2, 10, 3, 11, 4, 0, 5, 8, 6, 9]
211 [1, 7, 2, 10, 3, 11, 4, 0, 5, 9, 6, 8]
212 [1, 7, 2, 10, 3, 11, 4, 8, 5, 0, 6, 9]
213 [1, 7, 2, 10, 3, 11, 4, 8, 5, 9, 6, 0]
214 [1, 7, 2, 10, 3, 11, 4, 9, 5, 0, 6, 8]
215 [1, 7, 2, 10, 3, 11, 4, 9, 5, 8, 6, 0]
216 [1, 7, 2, 11, 3, 0, 4, 8, 5, 9, 6, 10]
217 [1, 7, 2, 11, 3, 0, 4, 8, 5, 10, 6, 9]
218 [1, 7, 2, 11, 3, 0, 4, 9, 5, 8, 6, 10]
219 [1, 7, 2, 11, 3, 0, 4, 9, 5, 10, 6, 8]
220 [1, 7, 2, 11, 3, 0, 4, 10, 5, 8, 6, 9]
221 [1, 7, 2, 11, 3, 0, 4, 10, 5, 9, 6, 8]
222 [1, 7, 2, 11, 3, 8, 4, 0, 5, 9, 6, 10]
223 [1, 7, 2, 11, 3, 8, 4, 0, 5, 10, 6, 9]
224 [1, 7, 2, 11, 3, 8, 4, 9, 5, 0, 6, 10]
225 [1, 7, 2, 11, 3, 8, 4, 9, 5, 10, 6, 0]
226 [1, 7, 2, 11, 3, 8, 4, 10, 5, 0, 6, 9]
227 [1, 7, 2, 11, 3, 8, 4, 10, 5, 9, 6, 0]
228 [1, 7, 2, 11, 3, 9, 4, 0, 5, 8, 6, 10]
229 [1, 7, 2, 11, 3, 9, 4, 0, 5, 10, 6, 8]
230 [1, 7, 2, 11, 3, 9, 4, 8, 5, 0, 6, 10]
231 [1, 7, 2, 11, 3, 9, 4, 8, 5, 10, 6, 0]
232 [1, 7, 2, 11, 3, 9, 4, 10, 5, 0, 6, 8]
233 [1, 7, 2, 11, 3, 9, 4, 10, 5, 8, 6, 0]
234 [1, 7, 2, 11, 3, 10, 4, 0, 5, 8, 6, 9]
235 [1, 7, 2, 11, 3, 10, 4, 0, 5, 9, 6, 8]
236 [1, 7, 2, 11, 3, 10, 4, 8, 5, 0, 6, 9]
237 [1, 7, 2, 11, 3, 10, 4, 8, 5, 9, 6, 0]
238 [1, 7, 2, 11, 3, 10, 4, 9, 5, 0, 6, 8]
239 [1, 7, 2, 11, 3, 10, 4, 9, 5, 8, 6, 0]
240 [1, 8, 2, 0, 3, 7, 4, 9, 5, 10, 6, 11]
241 [1, 8, 2, 0, 3, 7, 4, 9, 5, 11, 6, 10]
242 [1, 8, 2, 0, 3, 7, 4, 10, 5, 9, 6, 11]
243 [1, 8, 2, 0, 3, 7, 4, 10, 5, 11, 6, 9]
244 [1, 8, 2, 0, 3, 7, 4, 11, 5, 9, 6, 10]
245 [1, 8, 2, 0, 3, 7, 4, 11, 5, 10, 6, 9]
246 [1, 8, 2, 0, 3, 9, 4, 7, 5, 10, 6, 11]
247 [1, 8, 2, 0, 3, 9, 4, 7, 5, 11, 6, 10]
248 [1, 8, 2, 0, 3, 9, 4, 10, 5, 7, 6, 11]
249 [1, 8, 2, 0, 3, 9, 4, 10, 5, 11, 6, 7]
250 [1, 8, 2, 0, 3, 9, 4, 11, 5, 7, 6, 10]
251 [1, 8, 2, 0, 3, 9, 4, 11, 5, 10, 6, 7]
252 [1, 8, 2, 0, 3, 10, 4, 7, 5, 9, 6, 11]
253 [1, 8, 2, 0, 3, 10, 4, 7, 5, 11, 6, 9]
254 [1, 8, 2, 0, 3, 10, 4, 9, 5, 7, 6, 11]
255 [1, 8, 2, 0, 3, 10, 4, 9, 5, 11, 6, 7]
256 [1, 8, 2, 0, 3, 10, 4, 11, 5, 7, 6, 9]
257 [1, 8, 2, 0, 3, 10, 4, 11, 5, 9, 6, 7]
258 [1, 8, 2, 0, 3, 11, 4, 7, 5, 9, 6, 10]
259 [1, 8, 2, 0, 3, 11, 4, 7, 5, 10, 6, 9]
260 [1, 8, 2, 0, 3, 11, 4, 9, 5, 7, 6, 10]
261 [1, 8, 2, 0, 3, 11, 4, 9, 5, 10, 6, 7]
262 [1, 8, 2, 0, 3, 11, 4, 10, 5, 7, 6, 9]
263 [1, 8, 2, 0, 3, 11, 4, 10, 5, 9, 6, 7]
264 [1, 8, 2, 7, 3, 0, 4, 9, 5, 10, 6, 11]
265 [1, 8, 2, 7, 3, 0, 4, 9, 5, 11, 6, 10]
266 [1, 8, 2, 7, 3, 0, 4, 10, 5, 9, 6, 11]
267 [1, 8, 2, 7, 3, 0, 4, 10, 5, 11, 6, 9]
268 [1, 8, 2, 7, 3, 0, 4, 11, 5, 9, 6, 10]
269 [1, 8, 2, 7, 3, 0, 4, 11, 5, 10, 6, 9]
270 [1, 8, 2, 7, 3, 9, 4, 0, 5, 10, 6, 11]
271 [1, 8, 2, 7, 3, 9, 4, 0, 5, 11, 6, 10]
272 [1, 8, 2, 7, 3, 9, 4, 10, 5, 0, 6, 11]
273 [1, 8, 2, 7, 3, 9, 4, 10, 5, 11, 6, 0]
274 [1, 8, 2, 7, 3, 9, 4, 11, 5, 0, 6, 10]
275 [1, 8, 2, 7, 3, 9, 4, 11, 5, 10, 6, 0]
276 [1, 8, 2, 7, 3, 10, 4, 0, 5, 9, 6, 11]
277 [1, 8, 2, 7, 3, 10, 4, 0, 5, 11, 6, 9]
278 [1, 8, 2, 7, 3, 10, 4, 9, 5, 0, 6, 11]
279 [1, 8, 2, 7, 3, 10, 4, 9, 5, 11, 6, 0]
280 [1, 8, 2, 7, 3, 10, 4, 11, 5, 0, 6, 9]
281 [1, 8, 2, 7, 3, 10, 4, 11, 5, 9, 6, 0]
282 [1, 8, 2, 7, 3, 11, 4, 0, 5, 9, 6, 10]
283 [1, 8, 2, 7, 3, 11, 4, 0, 5, 10, 6, 9]
284 [1, 8, 2, 7, 3, 11, 4, 9, 5, 0, 6, 10]
285 [1, 8, 2, 7, 3, 11, 4, 9, 5, 10, 6, 0]
286 [1, 8, 2, 7, 3, 11, 4, 10, 5, 0, 6, 9]
287 [1, 8, 2, 7, 3, 11, 4, 10, 5, 9, 6, 0]
288 [1, 8, 2, 9, 3, 0, 4, 7, 5, 10, 6, 11]
289 [1, 8, 2, 9, 3, 0, 4, 7, 5, 11, 6, 10]
290 [1, 8, 2, 9, 3, 0, 4, 10, 5, 7, 6, 11]
291 [1, 8, 2, 9, 3, 0, 4, 10, 5, 11, 6, 7]
292 [1, 8, 2, 9, 3, 0, 4, 11, 5, 7, 6, 10]
293 [1, 8, 2, 9, 3, 0, 4, 11, 5, 10, 6, 7]
294 [1, 8, 2, 9, 3, 7, 4, 0, 5, 10, 6, 11]
295 [1, 8, 2, 9, 3, 7, 4, 0, 5, 11, 6, 10]
296 [1, 8, 2, 9, 3, 7, 4, 10, 5, 0, 6, 11]
297 [1, 8, 2, 9, 3, 7, 4, 10, 5, 11, 6, 0]
298 [1, 8, 2, 9, 3, 7, 4, 11, 5, 0, 6, 10]
299 [1, 8, 2, 9, 3, 7, 4, 11, 5, 10, 6, 0]
300 [1, 8, 2, 9, 3, 10, 4, 0, 5, 7, 6, 11]
301 [1, 8, 2, 9, 3, 10, 4, 0, 5, 11, 6, 7]
302 [1, 8, 2, 9, 3, 10, 4, 7, 5, 0, 6, 11]
303 [1, 8, 2, 9, 3, 10, 4, 7, 5, 11, 6, 0]
304 [1, 8, 2, 9, 3, 10, 4, 11, 5, 0, 6, 7]
305 [1, 8, 2, 9, 3, 10, 4, 11, 5, 7, 6, 0]
306 [1, 8, 2, 9, 3, 11, 4, 0, 5, 7, 6, 10]
307 [1, 8, 2, 9, 3, 11, 4, 0, 5, 10, 6, 7]
308 [1, 8, 2, 9, 3, 11, 4, 7, 5, 0, 6, 10]
309 [1, 8, 2, 9, 3, 11, 4, 7, 5, 10, 6, 0]
310 [1, 8, 2, 9, 3, 11, 4, 10, 5, 0, 6, 7]
311 [1, 8, 2, 9, 3, 11, 4, 10, 5, 7, 6, 0]
312 [1, 8, 2, 10, 3, 0, 4, 7, 5, 9, 6, 11]
313 [1, 8, 2, 10, 3, 0, 4, 7, 5, 11, 6, 9]
314 [1, 8, 2, 10, 3, 0, 4, 9, 5, 7, 6, 11]
315 [1, 8, 2, 10, 3, 0, 4, 9, 5, 11, 6, 7]
316 [1, 8, 2, 10, 3, 0, 4, 11, 5, 7, 6, 9]
317 [1, 8, 2, 10, 3, 0, 4, 11, 5, 9, 6, 7]
318 [1, 8, 2, 10, 3, 7, 4, 0, 5, 9, 6, 11]
319 [1, 8, 2, 10, 3, 7, 4, 0, 5, 11, 6, 9]
320 [1, 8, 2, 10, 3, 7, 4, 9, 5, 0, 6, 11]
321 [1, 8, 2, 10, 3, 7, 4, 9, 5, 11, 6, 0]
322 [1, 8, 2, 10, 3, 7, 4, 11, 5, 0, 6, 9]
323 [1, 8, 2, 10, 3, 7, 4, 11, 5, 9, 6, 0]
324 [1, 8, 2, 10, 3, 9, 4, 0, 5, 7, 6, 11]
325 [1, 8, 2, 10, 3, 9, 4, 0, 5, 11, 6, 7]
326 [1, 8, 2, 10, 3, 9, 4, 7, 5, 0, 6, 11]
327 [1, 8, 2, 10, 3, 9, 4, 7, 5, 11, 6, 0]
328 [1, 8, 2, 10, 3, 9, 4, 11, 5, 0, 6, 7]
329 [1, 8, 2, 10, 3, 9, 4, 11, 5, 7, 6, 0]
330 [1, 8, 2, 10, 3, 11, 4, 0, 5, 7, 6, 9]
331 [1, 8, 2, 10, 3, 11, 4, 0, 5, 9, 6, 7]
332 [1, 8, 2, 10, 3, 11, 4, 7, 5, 0, 6, 9]
333 [1, 8, 2, 10, 3, 11, 4, 7, 5, 9, 6, 0]
334 [1, 8, 2, 10, 3, 11, 4, 9, 5, 0, 6, 7]
335 [1, 8, 2, 10, 3, 11, 4, 9, 5, 7, 6, 0]
336 [1, 8, 2, 11, 3, 0, 4, 7, 5, 9, 6, 10]
337 [1, 8, 2, 11, 3, 0, 4, 7, 5, 10, 6, 9]
338 [1, 8, 2, 11, 3, 0, 4, 9, 5, 7, 6, 10]
339 [1, 8, 2, 11, 3, 0, 4, 9, 5, 10, 6, 7]
340 [1, 8, 2, 11, 3, 0, 4, 10, 5, 7, 6, 9]
341 [1, 8, 2, 11, 3, 0, 4, 10, 5, 9, 6, 7]
342 [1, 8, 2, 11, 3, 7, 4, 0, 5, 9, 6, 10]
343 [1, 8, 2, 11, 3, 7, 4, 0, 5, 10, 6, 9]
344 [1, 8, 2, 11, 3, 7, 4, 9, 5, 0, 6, 10]
345 [1, 8, 2, 11, 3, 7, 4, 9, 5, 10, 6, 0]
346 [1, 8, 2, 11, 3, 7, 4, 10, 5, 0, 6, 9]
347 [1, 8, 2, 11, 3, 7, 4, 10, 5, 9, 6, 0]
348 [1, 8, 2, 11, 3, 9, 4, 0, 5, 7, 6, 10]
349 [1, 8, 2, 11, 3, 9, 4, 0, 5, 10, 6, 7]
350 [1, 8, 2, 11, 3, 9, 4, 7, 5, 0, 6, 10]
351 [1, 8, 2, 11, 3, 9, 4, 7, 5, 10, 6, 0]
352 [1, 8, 2, 11, 3, 9, 4, 10, 5, 0, 6, 7]
353 [1, 8, 2, 11, 3, 9, 4, 10, 5, 7, 6, 0]
354 [1, 8, 2, 11, 3, 10, 4, 0, 5, 7, 6, 9]
355 [1, 8, 2, 11, 3, 10, 4, 0, 5, 9, 6, 7]
356 [1, 8, 2, 11, 3, 10, 4, 7, 5, 0, 6, 9]
357 [1, 8, 2, 11, 3, 10, 4, 7, 5, 9, 6, 0]
358 [1, 8, 2, 11, 3, 10, 4, 9, 5, 0, 6, 7]
359 [1, 8, 2, 11, 3, 10, 4, 9, 5, 7, 6, 0]
360 [1, 9, 2, 0, 3, 7, 4, 8, 5, 10, 6, 11]
361 [1, 9, 2, 0, 3, 7, 4, 8, 5, 11, 6, 10]
362 [1, 9, 2, 0, 3, 7, 4, 10, 5, 8, 6, 11]
363 [1, 9, 2, 0, 3, 7, 4, 10, 5, 11, 6, 8]
364 [1, 9, 2, 0, 3, 7, 4, 11, 5, 8, 6, 10]
365 [1, 9, 2, 0, 3, 7, 4, 11, 5, 10, 6, 8]
366 [1, 9, 2, 0, 3, 8, 4, 7, 5, 10, 6, 11]
367 [1, 9, 2, 0, 3, 8, 4, 7, 5, 11, 6, 10]
368 [1, 9, 2, 0, 3, 8, 4, 10, 5, 7, 6, 11]
369 [1, 9, 2, 0, 3, 8, 4, 10, 5, 11, 6, 7]
370 [1, 9, 2, 0, 3, 8, 4, 11, 5, 7, 6, 10]
371 [1, 9, 2, 0, 3, 8, 4, 11, 5, 10, 6, 7]
372 [1, 9, 2, 0, 3, 10, 4, 7, 5, 8, 6, 11]
373 [1, 9, 2, 0, 3, 10, 4, 7, 5, 11, 6, 8]
374 [1, 9, 2, 0, 3, 10, 4, 8, 5, 7, 6, 11]
375 [1, 9, 2, 0, 3, 10, 4, 8, 5, 11, 6, 7]
376 [1, 9, 2, 0, 3, 10, 4, 11, 5, 7, 6, 8]
377 [1, 9, 2, 0, 3, 10, 4, 11, 5, 8, 6, 7]
378 [1, 9, 2, 0, 3, 11, 4, 7, 5, 8, 6, 10]
379 [1, 9, 2, 0, 3, 11, 4, 7, 5, 10, 6, 8]
380 [1, 9, 2, 0, 3, 11, 4, 8, 5, 7, 6, 10]
381 [1, 9, 2, 0, 3, 11, 4, 8, 5, 10, 6, 7]
382 [1, 9, 2, 0, 3, 11, 4, 10, 5, 7, 6, 8]
383 [1, 9, 2, 0, 3, 11, 4, 10, 5, 8, 6, 7]
384 [1, 9, 2, 7, 3, 0, 4, 8, 5, 10, 6, 11]
385 [1, 9, 2, 7, 3, 0, 4, 8, 5, 11, 6, 10]
386 [1, 9, 2, 7, 3, 0, 4, 10, 5, 8, 6, 11]
387 [1, 9, 2, 7, 3, 0, 4, 10, 5, 11, 6, 8]
388 [1, 9, 2, 7, 3, 0, 4, 11, 5, 8, 6, 10]
389 [1, 9, 2, 7, 3, 0, 4, 11, 5, 10, 6, 8]
390 [1, 9, 2, 7, 3, 8, 4, 0, 5, 10, 6, 11]
391 [1, 9, 2, 7, 3, 8, 4, 0, 5, 11, 6, 10]
392 [1, 9, 2, 7, 3, 8, 4, 10, 5, 0, 6, 11]
393 [1, 9, 2, 7, 3, 8, 4, 10, 5, 11, 6, 0]
394 [1, 9, 2, 7, 3, 8, 4, 11, 5, 0, 6, 10]
395 [1, 9, 2, 7, 3, 8, 4, 11, 5, 10, 6, 0]
396 [1, 9, 2, 7, 3, 10, 4, 0, 5, 8, 6, 11]
397 [1, 9, 2, 7, 3, 10, 4, 0, 5, 11, 6, 8]
398 [1, 9, 2, 7, 3, 10, 4, 8, 5, 0, 6, 11]
399 [1, 9, 2, 7, 3, 10, 4, 8, 5, 11, 6, 0]
400 [1, 9, 2, 7, 3, 10, 4, 11, 5, 0, 6, 8]
401 [1, 9, 2, 7, 3, 10, 4, 11, 5, 8, 6, 0]
402 [1, 9, 2, 7, 3, 11, 4, 0, 5, 8, 6, 10]
403 [1, 9, 2, 7, 3, 11, 4, 0, 5, 10, 6, 8]
404 [1, 9, 2, 7, 3, 11, 4, 8, 5, 0, 6, 10]
405 [1, 9, 2, 7, 3, 11, 4, 8, 5, 10, 6, 0]
406 [1, 9, 2, 7, 3, 11, 4, 10, 5, 0, 6, 8]
407 [1, 9, 2, 7, 3, 11, 4, 10, 5, 8, 6, 0]
408 [1, 9, 2, 8, 3, 0, 4, 7, 5, 10, 6, 11]
409 [1, 9, 2, 8, 3, 0, 4, 7, 5, 11, 6, 10]
410 [1, 9, 2, 8, 3, 0, 4, 10, 5, 7, 6, 11]
411 [1, 9, 2, 8, 3, 0, 4, 10, 5, 11, 6, 7]
412 [1, 9, 2, 8, 3, 0, 4, 11, 5, 7, 6, 10]
413 [1, 9, 2, 8, 3, 0, 4, 11, 5, 10, 6, 7]
414 [1, 9, 2, 8, 3, 7, 4, 0, 5, 10, 6, 11]
415 [1, 9, 2, 8, 3, 7, 4, 0, 5, 11, 6, 10]
416 [1, 9, 2, 8, 3, 7, 4, 10, 5, 0, 6, 11]
417 [1, 9, 2, 8, 3, 7, 4, 10, 5, 11, 6, 0]
418 [1, 9, 2, 8, 3, 7, 4, 11, 5, 0, 6, 10]
419 [1, 9, 2, 8, 3, 7, 4, 11, 5, 10, 6, 0]
420 [1, 9, 2, 8, 3, 10, 4, 0, 5, 7, 6, 11]
421 [1, 9, 2, 8, 3, 10, 4, 0, 5, 11, 6, 7]
422 [1, 9, 2, 8, 3, 10, 4, 7, 5, 0, 6, 11]
423 [1, 9, 2, 8, 3, 10, 4, 7, 5, 11, 6, 0]
424 [1, 9, 2, 8, 3, 10, 4, 11, 5, 0, 6, 7]
425 [1, 9, 2, 8, 3, 10, 4, 11, 5, 7, 6, 0]
426 [1, 9, 2, 8, 3, 11, 4, 0, 5, 7, 6, 10]
427 [1, 9, 2, 8, 3, 11, 4, 0, 5, 10, 6, 7]
428 [1, 9, 2, 8, 3, 11, 4, 7, 5, 0, 6, 10]
429 [1, 9, 2, 8, 3, 11, 4, 7, 5, 10, 6, 0]
430 [1, 9, 2, 8, 3, 11, 4, 10, 5, 0, 6, 7]
431 [1, 9, 2, 8, 3, 11, 4, 10, 5, 7, 6, 0]
432 [1, 9, 2, 10, 3, 0, 4, 7, 5, 8, 6, 11]
433 [1, 9, 2, 10, 3, 0, 4, 7, 5, 11, 6, 8]
434 [1, 9, 2, 10, 3, 0, 4, 8, 5, 7, 6, 11]
435 [1, 9, 2, 10, 3, 0, 4, 8, 5, 11, 6, 7]
436 [1, 9, 2, 10, 3, 0, 4, 11, 5, 7, 6, 8]
437 [1, 9, 2, 10, 3, 0, 4, 11, 5, 8, 6, 7]
438 [1, 9, 2, 10, 3, 7, 4, 0, 5, 8, 6, 11]
439 [1, 9, 2, 10, 3, 7, 4, 0, 5, 11, 6, 8]
440 [1, 9, 2, 10, 3, 7, 4, 8, 5, 0, 6, 11]
441 [1, 9, 2, 10, 3, 7, 4, 8, 5, 11, 6, 0]
442 [1, 9, 2, 10, 3, 7, 4, 11, 5, 0, 6, 8]
443 [1, 9, 2, 10, 3, 7, 4, 11, 5, 8, 6, 0]
444 [1, 9, 2, 10, 3, 8, 4, 0, 5, 7, 6, 11]
445 [1, 9, 2, 10, 3, 8, 4, 0, 5, 11, 6, 7]
446 [1, 9, 2, 10, 3, 8, 4, 7, 5, 0, 6, 11]
447 [1, 9, 2, 10, 3, 8, 4, 7, 5, 11, 6, 0]
448 [1, 9, 2, 10, 3, 8, 4, 11, 5, 0, 6, 7]
449 [1, 9, 2, 10, 3, 8, 4, 11, 5, 7, 6, 0]
450 [1, 9, 2, 10, 3, 11, 4, 0, 5, 7, 6, 8]
451 [1, 9, 2, 10, 3, 11, 4, 0, 5, 8, 6, 7]
452 [1, 9, 2, 10, 3, 11, 4, 7, 5, 0, 6, 8]
453 [1, 9, 2, 10, 3, 11, 4, 7, 5, 8, 6, 0]
454 [1, 9, 2, 10, 3, 11, 4, 8, 5, 0, 6, 7]
455 [1, 9, 2, 10, 3, 11, 4, 8, 5, 7, 6, 0]
456 [1, 9, 2, 11, 3, 0, 4, 7, 5, 8, 6, 10]
457 [1, 9, 2, 11, 3, 0, 4, 7, 5, 10, 6, 8]
458 [1, 9, 2, 11, 3, 0, 4, 8, 5, 7, 6, 10]
459 [1, 9, 2, 11, 3, 0, 4, 8, 5, 10, 6, 7]
460 [1, 9, 2, 11, 3, 0, 4, 10, 5, 7, 6, 8]
461 [1, 9, 2, 11, 3, 0, 4, 10, 5, 8, 6, 7]
462 [1, 9, 2, 11, 3, 7, 4, 0, 5, 8, 6, 10]
463 [1, 9, 2, 11, 3, 7, 4, 0, 5, 10, 6, 8]
464 [1, 9, 2, 11, 3, 7, 4, 8, 5, 0, 6, 10]
465 [1, 9, 2, 11, 3, 7, 4, 8, 5, 10, 6, 0]
466 [1, 9, 2, 11, 3, 7, 4, 10, 5, 0, 6, 8]
467 [1, 9, 2, 11, 3, 7, 4, 10, 5, 8, 6, 0]
468 [1, 9, 2, 11, 3, 8, 4, 0, 5, 7, 6, 10]
469 [1, 9, 2, 11, 3, 8, 4, 0, 5, 10, 6, 7]
470 [1, 9, 2, 11, 3, 8, 4, 7, 5, 0, 6, 10]
471 [1, 9, 2, 11, 3, 8, 4, 7, 5, 10, 6, 0]
472 [1, 9, 2, 11, 3, 8, 4, 10, 5, 0, 6, 7]
473 [1, 9, 2, 11, 3, 8, 4, 10, 5, 7, 6, 0]
474 [1, 9, 2, 11, 3, 10, 4, 0, 5, 7, 6, 8]
475 [1, 9, 2, 11, 3, 10, 4, 0, 5, 8, 6, 7]
476 [1, 9, 2, 11, 3, 10, 4, 7, 5, 0, 6, 8]
477 [1, 9, 2, 11, 3, 10, 4, 7, 5, 8, 6, 0]
478 [1, 9, 2, 11, 3, 10, 4, 8, 5, 0, 6, 7]
479 [1, 9, 2, 11, 3, 10, 4, 8, 5, 7, 6, 0]
480 [1, 10, 2, 0, 3, 7, 4, 8, 5, 9, 6, 11]
481 [1, 10, 2, 0, 3, 7, 4, 8, 5, 11, 6, 9]
482 [1, 10, 2, 0, 3, 7, 4, 9, 5, 8, 6, 11]
483 [1, 10, 2, 0, 3, 7, 4, 9, 5, 11, 6, 8]
484 [1, 10, 2, 0, 3, 7, 4, 11, 5, 8, 6, 9]
485 [1, 10, 2, 0, 3, 7, 4, 11, 5, 9, 6, 8]
486 [1, 10, 2, 0, 3, 8, 4, 7, 5, 9, 6, 11]
487 [1, 10, 2, 0, 3, 8, 4, 7, 5, 11, 6, 9]
488 [1, 10, 2, 0, 3, 8, 4, 9, 5, 7, 6, 11]
489 [1, 10, 2, 0, 3, 8, 4, 9, 5, 11, 6, 7]
490 [1, 10, 2, 0, 3, 8, 4, 11, 5, 7, 6, 9]
491 [1, 10, 2, 0, 3, 8, 4, 11, 5, 9, 6, 7]
492 [1, 10, 2, 0, 3, 9, 4, 7, 5, 8, 6, 11]
493 [1, 10, 2, 0, 3, 9, 4, 7, 5, 11, 6, 8]
494 [1, 10, 2, 0, 3, 9, 4, 8, 5, 7, 6, 11]
495 [1, 10, 2, 0, 3, 9, 4, 8, 5, 11, 6, 7]
496 [1, 10, 2, 0, 3, 9, 4, 11, 5, 7, 6, 8]
497 [1, 10, 2, 0, 3, 9, 4, 11, 5, 8, 6, 7]
498 [1, 10, 2, 0, 3, 11, 4, 7, 5, 8, 6, 9]
499 [1, 10, 2, 0, 3, 11, 4, 7, 5, 9, 6, 8]
500 [1, 10, 2, 0, 3, 11, 4, 8, 5, 7, 6, 9]
501 [1, 10, 2, 0, 3, 11, 4, 8, 5, 9, 6, 7]
502 [1, 10, 2, 0, 3, 11, 4, 9, 5, 7, 6, 8]
503 [1, 10, 2, 0, 3, 11, 4, 9, 5, 8, 6, 7]
504 [1, 10, 2, 7, 3, 0, 4, 8, 5, 9, 6, 11]
505 [1, 10, 2, 7, 3, 0, 4, 8, 5, 11, 6, 9]
506 [1, 10, 2, 7, 3, 0, 4, 9, 5, 8, 6, 11]
507 [1, 10, 2, 7, 3, 0, 4, 9, 5, 11, 6, 8]
508 [1, 10, 2, 7, 3, 0, 4, 11, 5, 8, 6, 9]
509 [1, 10, 2, 7, 3, 0, 4, 11, 5, 9, 6, 8]
510 [1, 10, 2, 7, 3, 8, 4, 0, 5, 9, 6, 11]
511 [1, 10, 2, 7, 3, 8, 4, 0, 5, 11, 6, 9]
512 [1, 10, 2, 7, 3, 8, 4, 9, 5, 0, 6, 11]
513 [1, 10, 2, 7, 3, 8, 4, 9, 5, 11, 6, 0]
514 [1, 10, 2, 7, 3, 8, 4, 11, 5, 0, 6, 9]
515 [1, 10, 2, 7, 3, 8, 4, 11, 5, 9, 6, 0]
516 [1, 10, 2, 7, 3, 9, 4, 0, 5, 8, 6, 11]
517 [1, 10, 2, 7, 3, 9, 4, 0, 5, 11, 6, 8]
518 [1, 10, 2, 7, 3, 9, 4, 8, 5, 0, 6, 11]
519 [1, 10, 2, 7, 3, 9, 4, 8, 5, 11, 6, 0]
520 [1, 10, 2, 7, 3, 9, 4, 11, 5, 0, 6, 8]
521 [1, 10, 2, 7, 3, 9, 4, 11, 5, 8, 6, 0]
522 [1, 10, 2, 7, 3, 11, 4, 0, 5, 8, 6, 9]
523 [1, 10, 2, 7, 3, 11, 4, 0, 5, 9, 6, 8]
524 [1, 10, 2, 7, 3, 11, 4, 8, 5, 0, 6, 9]
525 [1, 10, 2, 7, 3, 11, 4, 8, 5, 9, 6, 0]
526 [1, 10, 2, 7, 3, 11, 4, 9, 5, 0, 6, 8]
527 [1, 10, 2, 7, 3, 11, 4, 9, 5, 8, 6, 0]
528 [1, 10, 2, 8, 3, 0, 4, 7, 5, 9, 6, 11]
529 [1, 10, 2, 8, 3, 0, 4, 7, 5, 11, 6, 9]
530 [1, 10, 2, 8, 3, 0, 4, 9, 5, 7, 6, 11]
531 [1, 10, 2, 8, 3, 0, 4, 9, 5, 11, 6, 7]
532 [1, 10, 2, 8, 3, 0, 4, 11, 5, 7, 6, 9]
533 [1, 10, 2, 8, 3, 0, 4, 11, 5, 9, 6, 7]
534 [1, 10, 2, 8, 3, 7, 4, 0, 5, 9, 6, 11]
535 [1, 10, 2, 8, 3, 7, 4, 0, 5, 11, 6, 9]
536 [1, 10, 2, 8, 3, 7, 4, 9, 5, 0, 6, 11]
537 [1, 10, 2, 8, 3, 7, 4, 9, 5, 11, 6, 0]
538 [1, 10, 2, 8, 3, 7, 4, 11, 5, 0, 6, 9]
539 [1, 10, 2, 8, 3, 7, 4, 11, 5, 9, 6, 0]
540 [1, 10, 2, 8, 3, 9, 4, 0, 5, 7, 6, 11]
541 [1, 10, 2, 8, 3, 9, 4, 0, 5, 11, 6, 7]
542 [1, 10, 2, 8, 3, 9, 4, 7, 5, 0, 6, 11]
543 [1, 10, 2, 8, 3, 9, 4, 7, 5, 11, 6, 0]
544 [1, 10, 2, 8, 3, 9, 4, 11, 5, 0, 6, 7]
545 [1, 10, 2, 8, 3, 9, 4, 11, 5, 7, 6, 0]
546 [1, 10, 2, 8, 3, 11, 4, 0, 5, 7, 6, 9]
547 [1, 10, 2, 8, 3, 11, 4, 0, 5, 9, 6, 7]
548 [1, 10, 2, 8, 3, 11, 4, 7, 5, 0, 6, 9]
549 [1, 10, 2, 8, 3, 11, 4, 7, 5, 9, 6, 0]
550 [1, 10, 2, 8, 3, 11, 4, 9, 5, 0, 6, 7]
551 [1, 10, 2, 8, 3, 11, 4, 9, 5, 7, 6, 0]
552 [1, 10, 2, 9, 3, 0, 4, 7, 5, 8, 6, 11]
553 [1, 10, 2, 9, 3, 0, 4, 7, 5, 11, 6, 8]
554 [1, 10, 2, 9, 3, 0, 4, 8, 5, 7, 6, 11]
555 [1, 10, 2, 9, 3, 0, 4, 8, 5, 11, 6, 7]
556 [1, 10, 2, 9, 3, 0, 4, 11, 5, 7, 6, 8]
557 [1, 10, 2, 9, 3, 0, 4, 11, 5, 8, 6, 7]
558 [1, 10, 2, 9, 3, 7, 4, 0, 5, 8, 6, 11]
559 [1, 10, 2, 9, 3, 7, 4, 0, 5, 11, 6, 8]
560 [1, 10, 2, 9, 3, 7, 4, 8, 5, 0, 6, 11]
561 [1, 10, 2, 9, 3, 7, 4, 8, 5, 11, 6, 0]
562 [1, 10, 2, 9, 3, 7, 4, 11, 5, 0, 6, 8]
563 [1, 10, 2, 9, 3, 7, 4, 11, 5, 8, 6, 0]
564 [1, 10, 2, 9, 3, 8, 4, 0, 5, 7, 6, 11]
565 [1, 10, 2, 9, 3, 8, 4, 0, 5, 11, 6, 7]
566 [1, 10, 2, 9, 3, 8, 4, 7, 5, 0, 6, 11]
567 [1, 10, 2, 9, 3, 8, 4, 7, 5, 11, 6, 0]
568 [1, 10, 2, 9, 3, 8, 4, 11, 5, 0, 6, 7]
569 [1, 10, 2, 9, 3, 8, 4, 11, 5, 7, 6, 0]
570 [1, 10, 2, 9, 3, 11, 4, 0, 5, 7, 6, 8]
571 [1, 10, 2, 9, 3, 11, 4, 0, 5, 8, 6, 7]
572 [1, 10, 2, 9, 3, 11, 4, 7, 5, 0, 6, 8]
573 [1, 10, 2, 9, 3, 11, 4, 7, 5, 8, 6, 0]
574 [1, 10, 2, 9, 3, 11, 4, 8, 5, 0, 6, 7]
575 [1, 10, 2, 9, 3, 11, 4, 8, 5, 7, 6, 0]
576 [1, 10, 2, 11, 3, 0, 4, 7, 5, 8, 6, 9]
577 [1, 10, 2, 11, 3, 0, 4, 7, 5, 9, 6, 8]
578 [1, 10, 2, 11, 3, 0, 4, 8, 5, 7, 6, 9]
579 [1, 10, 2, 11, 3, 0, 4, 8, 5, 9, 6, 7]
580 [1, 10, 2, 11, 3, 0, 4, 9, 5, 7, 6, 8]
581 [1, 10, 2, 11, 3, 0, 4, 9, 5, 8, 6, 7]
582 [1, 10, 2, 11, 3, 7, 4, 0, 5, 8, 6, 9]
583 [1, 10, 2, 11, 3, 7, 4, 0, 5, 9, 6, 8]
584 [1, 10, 2, 11, 3, 7, 4, 8, 5, 0, 6, 9]
585 [1, 10, 2, 11, 3, 7, 4, 8, 5, 9, 6, 0]
586 [1, 10, 2, 11, 3, 7, 4, 9, 5, 0, 6, 8]
587 [1, 10, 2, 11, 3, 7, 4, 9, 5, 8, 6, 0]
588 [1, 10, 2, 11, 3, 8, 4, 0, 5, 7, 6, 9]
589 [1, 10, 2, 11, 3, 8, 4, 0, 5, 9, 6, 7]
590 [1, 10, 2, 11, 3, 8, 4, 7, 5, 0, 6, 9]
591 [1, 10, 2, 11, 3, 8, 4, 7, 5, 9, 6, 0]
592 [1, 10, 2, 11, 3, 8, 4, 9, 5, 0, 6, 7]
593 [1, 10, 2, 11, 3, 8, 4, 9, 5, 7, 6, 0]
594 [1, 10, 2, 11, 3, 9, 4, 0, 5, 7, 6, 8]
595 [1, 10, 2, 11, 3, 9, 4, 0, 5, 8, 6, 7]
596 [1, 10, 2, 11, 3, 9, 4, 7, 5, 0, 6, 8]
597 [1, 10, 2, 11, 3, 9, 4, 7, 5, 8, 6, 0]
598 [1, 10, 2, 11, 3, 9, 4, 8, 5, 0, 6, 7]
599 [1, 10, 2, 11, 3, 9, 4, 8, 5, 7, 6, 0]
600 [1, 11, 2, 0, 3, 7, 4, 8, 5, 9, 6, 10]
601 [1, 11, 2, 0, 3, 7, 4, 8, 5, 10, 6, 9]
602 [1, 11, 2, 0, 3, 7, 4, 9, 5, 8, 6, 10]
603 [1, 11, 2, 0, 3, 7, 4, 9, 5, 10, 6, 8]
604 [1, 11, 2, 0, 3, 7, 4, 10, 5, 8, 6, 9]
605 [1, 11, 2, 0, 3, 7, 4, 10, 5, 9, 6, 8]
606 [1, 11, 2, 0, 3, 8, 4, 7, 5, 9, 6, 10]
607 [1, 11, 2, 0, 3, 8, 4, 7, 5, 10, 6, 9]
608 [1, 11, 2, 0, 3, 8, 4, 9, 5, 7, 6, 10]
609 [1, 11, 2, 0, 3, 8, 4, 9, 5, 10, 6, 7]
610 [1, 11, 2, 0, 3, 8, 4, 10, 5, 7, 6, 9]
611 [1, 11, 2, 0, 3, 8, 4, 10, 5, 9, 6, 7]
612 [1, 11, 2, 0, 3, 9, 4, 7, 5, 8, 6, 10]
613 [1, 11, 2, 0, 3, 9, 4, 7, 5, 10, 6, 8]
614 [1, 11, 2, 0, 3, 9, 4, 8, 5, 7, 6, 10]
615 [1, 11, 2, 0, 3, 9, 4, 8, 5, 10, 6, 7]
616 [1, 11, 2, 0, 3, 9, 4, 10, 5, 7, 6, 8]
617 [1, 11, 2, 0, 3, 9, 4, 10, 5, 8, 6, 7]
618 [1, 11, 2, 0, 3, 10, 4, 7, 5, 8, 6, 9]
619 [1, 11, 2, 0, 3, 10, 4, 7, 5, 9, 6, 8]
620 [1, 11, 2, 0, 3, 10, 4, 8, 5, 7, 6, 9]
621 [1, 11, 2, 0, 3, 10, 4, 8, 5, 9, 6, 7]
622 [1, 11, 2, 0, 3, 10, 4, 9, 5, 7, 6, 8]
623 [1, 11, 2, 0, 3, 10, 4, 9, 5, 8, 6, 7]
624 [1, 11, 2, 7, 3, 0, 4, 8, 5, 9, 6, 10]
625 [1, 11, 2, 7, 3, 0, 4, 8, 5, 10, 6, 9]
626 [1, 11, 2, 7, 3, 0, 4, 9, 5, 8, 6, 10]
627 [1, 11, 2, 7, 3, 0, 4, 9, 5, 10, 6, 8]
628 [1, 11, 2, 7, 3, 0, 4, 10, 5, 8, 6, 9]
629 [1, 11, 2, 7, 3, 0, 4, 10, 5, 9, 6, 8]
630 [1, 11, 2, 7, 3, 8, 4, 0, 5, 9, 6, 10]
631 [1, 11, 2, 7, 3, 8, 4, 0, 5, 10, 6, 9]
632 [1, 11, 2, 7, 3, 8, 4, 9, 5, 0, 6, 10]
633 [1, 11, 2, 7, 3, 8, 4, 9, 5, 10, 6, 0]
634 [1, 11, 2, 7, 3, 8, 4, 10, 5, 0, 6, 9]
635 [1, 11, 2, 7, 3, 8, 4, 10, 5, 9, 6, 0]
636 [1, 11, 2, 7, 3, 9, 4, 0, 5, 8, 6, 10]
637 [1, 11, 2, 7, 3, 9, 4, 0, 5, 10, 6, 8]
638 [1, 11, 2, 7, 3, 9, 4, 8, 5, 0, 6, 10]
639 [1, 11, 2, 7, 3, 9, 4, 8, 5, 10, 6, 0]
640 [1, 11, 2, 7, 3, 9, 4, 10, 5, 0, 6, 8]
641 [1, 11, 2, 7, 3, 9, 4, 10, 5, 8, 6, 0]
642 [1, 11, 2, 7, 3, 10, 4, 0, 5, 8, 6, 9]
643 [1, 11, 2, 7, 3, 10, 4, 0, 5, 9, 6, 8]
644 [1, 11, 2, 7, 3, 10, 4, 8, 5, 0, 6, 9]
645 [1, 11, 2, 7, 3, 10, 4, 8, 5, 9, 6, 0]
646 [1, 11, 2, 7, 3, 10, 4, 9, 5, 0, 6, 8]
647 [1, 11, 2, 7, 3, 10, 4, 9, 5, 8, 6, 0]
648 [1, 11, 2, 8, 3, 0, 4, 7, 5, 9, 6, 10]
649 [1, 11, 2, 8, 3, 0, 4, 7, 5, 10, 6, 9]
650 [1, 11, 2, 8, 3, 0, 4, 9, 5, 7, 6, 10]
651 [1, 11, 2, 8, 3, 0, 4, 9, 5, 10, 6, 7]
652 [1, 11, 2, 8, 3, 0, 4, 10, 5, 7, 6, 9]
653 [1, 11, 2, 8, 3, 0, 4, 10, 5, 9, 6, 7]
654 [1, 11, 2, 8, 3, 7, 4, 0, 5, 9, 6, 10]
655 [1, 11, 2, 8, 3, 7, 4, 0, 5, 10, 6, 9]
656 [1, 11, 2, 8, 3, 7, 4, 9, 5, 0, 6, 10]
657 [1, 11, 2, 8, 3, 7, 4, 9, 5, 10, 6, 0]
658 [1, 11, 2, 8, 3, 7, 4, 10, 5, 0, 6, 9]
659 [1, 11, 2, 8, 3, 7, 4, 10, 5, 9, 6, 0]
660 [1, 11, 2, 8, 3, 9, 4, 0, 5, 7, 6, 10]
661 [1, 11, 2, 8, 3, 9, 4, 0, 5, 10, 6, 7]
662 [1, 11, 2, 8, 3, 9, 4, 7, 5, 0, 6, 10]
663 [1, 11, 2, 8, 3, 9, 4, 7, 5, 10, 6, 0]
664 [1, 11, 2, 8, 3, 9, 4, 10, 5, 0, 6, 7]
665 [1, 11, 2, 8, 3, 9, 4, 10, 5, 7, 6, 0]
666 [1, 11, 2, 8, 3, 10, 4, 0, 5, 7, 6, 9]
667 [1, 11, 2, 8, 3, 10, 4, 0, 5, 9, 6, 7]
668 [1, 11, 2, 8, 3, 10, 4, 7, 5, 0, 6, 9]
669 [1, 11, 2, 8, 3, 10, 4, 7, 5, 9, 6, 0]
670 [1, 11, 2, 8, 3, 10, 4, 9, 5, 0, 6, 7]
671 [1, 11, 2, 8, 3, 10, 4, 9, 5, 7, 6, 0]
672 [1, 11, 2, 9, 3, 0, 4, 7, 5, 8, 6, 10]
673 [1, 11, 2, 9, 3, 0, 4, 7, 5, 10, 6, 8]
674 [1, 11, 2, 9, 3, 0, 4, 8, 5, 7, 6, 10]
675 [1, 11, 2, 9, 3, 0, 4, 8, 5, 10, 6, 7]
676 [1, 11, 2, 9, 3, 0, 4, 10, 5, 7, 6, 8]
677 [1, 11, 2, 9, 3, 0, 4, 10, 5, 8, 6, 7]
678 [1, 11, 2, 9, 3, 7, 4, 0, 5, 8, 6, 10]
679 [1, 11, 2, 9, 3, 7, 4, 0, 5, 10, 6, 8]
680 [1, 11, 2, 9, 3, 7, 4, 8, 5, 0, 6, 10]
681 [1, 11, 2, 9, 3, 7, 4, 8, 5, 10, 6, 0]
682 [1, 11, 2, 9, 3, 7, 4, 10, 5, 0, 6, 8]
683 [1, 11, 2, 9, 3, 7, 4, 10, 5, 8, 6, 0]
684 [1, 11, 2, 9, 3, 8, 4, 0, 5, 7, 6, 10]
685 [1, 11, 2, 9, 3, 8, 4, 0, 5, 10, 6, 7]
686 [1, 11, 2, 9, 3, 8, 4, 7, 5, 0, 6, 10]
687 [1, 11, 2, 9, 3, 8, 4, 7, 5, 10, 6, 0]
688 [1, 11, 2, 9, 3, 8, 4, 10, 5, 0, 6, 7]
689 [1, 11, 2, 9, 3, 8, 4, 10, 5, 7, 6, 0]
690 [1, 11, 2, 9, 3, 10, 4, 0, 5, 7, 6, 8]
691 [1, 11, 2, 9, 3, 10, 4, 0, 5, 8, 6, 7]
692 [1, 11, 2, 9, 3, 10, 4, 7, 5, 0, 6, 8]
693 [1, 11, 2, 9, 3, 10, 4, 7, 5, 8, 6, 0]
694 [1, 11, 2, 9, 3, 10, 4, 8, 5, 0, 6, 7]
695 [1, 11, 2, 9, 3, 10, 4, 8, 5, 7, 6, 0]
696 [1, 11, 2, 10, 3, 0, 4, 7, 5, 8, 6, 9]
697 [1, 11, 2, 10, 3, 0, 4, 7, 5, 9, 6, 8]
698 [1, 11, 2, 10, 3, 0, 4, 8, 5, 7, 6, 9]
699 [1, 11, 2, 10, 3, 0, 4, 8, 5, 9, 6, 7]
700 [1, 11, 2, 10, 3, 0, 4, 9, 5, 7, 6, 8]
701 [1, 11, 2, 10, 3, 0, 4, 9, 5, 8, 6, 7]
702 [1, 11, 2, 10, 3, 7, 4, 0, 5, 8, 6, 9]
703 [1, 11, 2, 10, 3, 7, 4, 0, 5, 9, 6, 8]
704 [1, 11, 2, 10, 3, 7, 4, 8, 5, 0, 6, 9]
705 [1, 11, 2, 10, 3, 7, 4, 8, 5, 9, 6, 0]
706 [1, 11, 2, 10, 3, 7, 4, 9, 5, 0, 6, 8]
707 [1, 11, 2, 10, 3, 7, 4, 9, 5, 8, 6, 0]
708 [1, 11, 2, 10, 3, 8, 4, 0, 5, 7, 6, 9]
709 [1, 11, 2, 10, 3, 8, 4, 0, 5, 9, 6, 7]
710 [1, 11, 2, 10, 3, 8, 4, 7, 5, 0, 6, 9]
711 [1, 11, 2, 10, 3, 8, 4, 7, 5, 9, 6, 0]
712 [1, 11, 2, 10, 3, 8, 4, 9, 5, 0, 6, 7]
713 [1, 11, 2, 10, 3, 8, 4, 9, 5, 7, 6, 0]
714 [1, 11, 2, 10, 3, 9, 4, 0, 5, 7, 6, 8]
715 [1, 11, 2, 10, 3, 9, 4, 0, 5, 8, 6, 7]
716 [1, 11, 2, 10, 3, 9, 4, 7, 5, 0, 6, 8]
717 [1, 11, 2, 10, 3, 9, 4, 7, 5, 8, 6, 0]
718 [1, 11, 2, 10, 3, 9, 4, 8, 5, 0, 6, 7]
719 [1, 11, 2, 10, 3, 9, 4, 8, 5, 7, 6, 0]
720 [3, 0, 4, 1, 5, 2, 6, 9, 7, 10, 8, 11]
721 [3, 0, 4, 1, 5, 2, 6, 9, 7, 11, 8, 10]
722 [3, 0, 4, 1, 5, 2, 6, 10, 7, 9, 8, 11]
723 [3, 0, 4, 1, 5, 2, 6, 10, 7, 11, 8, 9]
724 [3, 0, 4, 1, 5, 2, 6, 11, 7, 9, 8, 10]
725 [3, 0, 4, 1, 5, 2, 6, 11, 7, 10, 8, 9]
726 [3, 0, 4, 1, 5, 9, 6, 2, 7, 10, 8, 11]
727 [3, 0, 4, 1, 5, 9, 6, 2, 7, 11, 8, 10]
728 [3, 0, 4, 1, 5, 9, 6, 10, 7, 2, 8, 11]
729 [3, 0, 4, 1, 5, 9, 6, 10, 7, 11, 8, 2]
730 [3, 0, 4, 1, 5, 9, 6, 11, 7, 2, 8, 10]
731 [3, 0, 4, 1, 5, 9, 6, 11, 7, 10, 8, 2]
732 [3, 0, 4, 1, 5, 10, 6, 2, 7, 9, 8, 11]
733 [3, 0, 4, 1, 5, 10, 6, 2, 7, 11, 8, 9]
734 [3, 0, 4, 1, 5, 10, 6, 9, 7, 2, 8, 11]
735 [3, 0, 4, 1, 5, 10, 6, 9, 7, 11, 8, 2]
736 [3, 0, 4, 1, 5, 10, 6, 11, 7, 2, 8, 9]
737 [3, 0, 4, 1, 5, 10, 6, 11, 7, 9, 8, 2]
738 [3, 0, 4, 1, 5, 11, 6, 2, 7, 9, 8, 10]
739 [3, 0, 4, 1, 5, 11, 6, 2, 7, 10, 8, 9]
740 [3, 0, 4, 1, 5, 11, 6, 9, 7, 2, 8, 10]
741 [3, 0, 4, 1, 5, 11, 6, 9, 7, 10, 8, 2]
742 [3, 0, 4, 1, 5, 11, 6, 10, 7, 2, 8, 9]
743 [3, 0, 4, 1, 5, 11, 6, 10, 7, 9, 8, 2]
744 [3, 0, 4, 2, 5, 1, 6, 9, 7, 10, 8, 11]
745 [3, 0, 4, 2, 5, 1, 6, 9, 7, 11, 8, 10]
746 [3, 0, 4, 2, 5, 1, 6, 10, 7, 9, 8, 11]
747 [3, 0, 4, 2, 5, 1, 6, 10, 7, 11, 8, 9]
748 [3, 0, 4, 2, 5, 1, 6, 11, 7, 9, 8, 10]
749 [3, 0, 4, 2, 5, 1, 6, 11, 7, 10, 8, 9]
750 [3, 0, 4, 2, 5, 9, 6, 1, 7, 10, 8, 11]
751 [3, 0, 4, 2, 5, 9, 6, 1, 7, 11, 8, 10]
752 [3, 0, 4, 2, 5, 9, 6, 10, 7, 1, 8, 11]
753 [3, 0, 4, 2, 5, 9, 6, 10, 7, 11, 8, 1]
754 [3, 0, 4, 2, 5, 9, 6, 11, 7, 1, 8, 10]
755 [3, 0, 4, 2, 5, 9, 6, 11, 7, 10, 8, 1]
756 [3, 0, 4, 2, 5, 10, 6, 1, 7, 9, 8, 11]
757 [3, 0, 4, 2, 5, 10, 6, 1, 7, 11, 8, 9]
758 [3, 0, 4, 2, 5, 10, 6, 9, 7, 1, 8, 11]
759 [3, 0, 4, 2, 5, 10, 6, 9, 7, 11, 8, 1]
760 [3, 0, 4, 2, 5, 10, 6, 11, 7, 1, 8, 9]
761 [3, 0, 4, 2, 5, 10, 6, 11, 7, 9, 8, 1]
762 [3, 0, 4, 2, 5, 11, 6, 1, 7, 9, 8, 10]
763 [3, 0, 4, 2, 5, 11, 6, 1, 7, 10, 8, 9]
764 [3, 0, 4, 2, 5, 11, 6, 9, 7, 1, 8, 10]
765 [3, 0, 4, 2, 5, 11, 6, 9, 7, 10, 8, 1]
766 [3, 0, 4, 2, 5, 11, 6, 10, 7, 1, 8, 9]
767 [3, 0, 4, 2, 5, 11, 6, 10, 7, 9, 8, 1]
768 [3, 0, 4, 9, 5, 1, 6, 2, 7, 10, 8, 11]
769 [3, 0, 4, 9, 5, 1, 6, 2, 7, 11, 8, 10]
770 [3, 0, 4, 9, 5, 1, 6, 10, 7, 2, 8, 11]
771 [3, 0, 4, 9, 5, 1, 6, 10, 7, 11, 8, 2]
772 [3, 0, 4, 9, 5, 1, 6, 11, 7, 2, 8, 10]
773 [3, 0, 4, 9, 5, 1, 6, 11, 7, 10, 8, 2]
774 [3, 0, 4, 9, 5, 2, 6, 1, 7, 10, 8, 11]
775 [3, 0, 4, 9, 5, 2, 6, 1, 7, 11, 8, 10]
776 [3, 0, 4, 9, 5, 2, 6, 10, 7, 1, 8, 11]
777 [3, 0, 4, 9, 5, 2, 6, 10, 7, 11, 8, 1]
778 [3, 0, 4, 9, 5, 2, 6, 11, 7, 1, 8, 10]
779 [3, 0, 4, 9, 5, 2, 6, 11, 7, 10, 8, 1]
780 [3, 0, 4, 9, 5, 10, 6, 1, 7, 2, 8, 11]
781 [3, 0, 4, 9, 5, 10, 6, 1, 7, 11, 8, 2]
782 [3, 0, 4, 9, 5, 10, 6, 2, 7, 1, 8, 11]
783 [3, 0, 4, 9, 5, 10, 6, 2, 7, 11, 8, 1]
784 [3, 0, 4, 9, 5, 10, 6, 11, 7, 1, 8, 2]
785 [3, 0, 4, 9, 5, 10, 6, 11, 7, 2, 8, 1]
786 [3, 0, 4, 9, 5, 11, 6, 1, 7, 2, 8, 10]
787 [3, 0, 4, 9, 5, 11, 6, 1, 7, 10, 8, 2]
788 [3, 0, 4, 9, 5, 11, 6, 2, 7, 1, 8, 10]
789 [3, 0, 4, 9, 5, 11, 6, 2, 7, 10, 8, 1]
790 [3, 0, 4, 9, 5, 11, 6, 10, 7, 1, 8, 2]
791 [3, 0, 4, 9, 5, 11, 6, 10, 7, 2, 8, 1]
792 [3, 0, 4, 10, 5, 1, 6, 2, 7, 9, 8, 11]
793 [3, 0, 4, 10, 5, 1, 6, 2, 7, 11, 8, 9]
794 [3, 0, 4, 10, 5, 1, 6, 9, 7, 2, 8, 11]
795 [3, 0, 4, 10, 5, 1, 6, 9, 7, 11, 8, 2]
796 [3, 0, 4, 10, 5, 1, 6, 11, 7, 2, 8, 9]
797 [3, 0, 4, 10, 5, 1, 6, 11, 7, 9, 8, 2]
798 [3, 0, 4, 10, 5, 2, 6, 1, 7, 9, 8, 11]
799 [3, 0, 4, 10, 5, 2, 6, 1, 7, 11, 8, 9]
800 [3, 0, 4, 10, 5, 2, 6, 9, 7, 1, 8, 11]
801 [3, 0, 4, 10, 5, 2, 6, 9, 7, 11, 8, 1]
802 [3, 0, 4, 10, 5, 2, 6, 11, 7, 1, 8, 9]
803 [3, 0, 4, 10, 5, 2, 6, 11, 7, 9, 8, 1]
804 [3, 0, 4, 10, 5, 9, 6, 1, 7, 2, 8, 11]
805 [3, 0, 4, 10, 5, 9, 6, 1, 7, 11, 8, 2]
806 [3, 0, 4, 10, 5, 9, 6, 2, 7, 1, 8, 11]
807 [3, 0, 4, 10, 5, 9, 6, 2, 7, 11, 8, 1]
808 [3, 0, 4, 10, 5, 9, 6, 11, 7, 1, 8, 2]
809 [3, 0, 4, 10, 5, 9, 6, 11, 7, 2, 8, 1]
810 [3, 0, 4, 10, 5, 11, 6, 1, 7, 2, 8, 9]
811 [3, 0, 4, 10, 5, 11, 6, 1, 7, 9, 8, 2]
812 [3, 0, 4, 10, 5, 11, 6, 2, 7, 1, 8, 9]
813 [3, 0, 4, 10, 5, 11, 6, 2, 7, 9, 8, 1]
814 [3, 0, 4, 10, 5, 11, 6, 9, 7, 1, 8, 2]
815 [3, 0, 4, 10, 5, 11, 6, 9, 7, 2, 8, 1]
816 [3, 0, 4, 11, 5, 1, 6, 2, 7, 9, 8, 10]
817 [3, 0, 4, 11, 5, 1, 6, 2, 7, 10, 8, 9]
818 [3, 0, 4, 11, 5, 1, 6, 9, 7, 2, 8, 10]
819 [3, 0, 4, 11, 5, 1, 6, 9, 7, 10, 8, 2]
820 [3, 0, 4, 11, 5, 1, 6, 10, 7, 2, 8, 9]
821 [3, 0, 4, 11, 5, 1, 6, 10, 7, 9, 8, 2]
822 [3, 0, 4, 11, 5, 2, 6, 1, 7, 9, 8, 10]
823 [3, 0, 4, 11, 5, 2, 6, 1, 7, 10, 8, 9]
824 [3, 0, 4, 11, 5, 2, 6, 9, 7, 1, 8, 10]
825 [3, 0, 4, 11, 5, 2, 6, 9, 7, 10, 8, 1]
826 [3, 0, 4, 11, 5, 2, 6, 10, 7, 1, 8, 9]
827 [3, 0, 4, 11, 5, 2, 6, 10, 7, 9, 8, 1]
828 [3, 0, 4, 11, 5, 9, 6, 1, 7, 2, 8, 10]
829 [3, 0, 4, 11, 5, 9, 6, 1, 7, 10, 8, 2]
830 [3, 0, 4, 11, 5, 9, 6, 2, 7, 1, 8, 10]
831 [3, 0, 4, 11, 5, 9, 6, 2, 7, 10, 8, 1]
832 [3, 0, 4, 11, 5, 9, 6, 10, 7, 1, 8, 2]
833 [3, 0, 4, 11, 5, 9, 6, 10, 7, 2, 8, 1]
834 [3, 0, 4, 11, 5, 10, 6, 1, 7, 2, 8, 9]
835 [3, 0, 4, 11, 5, 10, 6, 1, 7, 9, 8, 2]
836 [3, 0, 4, 11, 5, 10, 6, 2, 7, 1, 8, 9]
837 [3, 0, 4, 11, 5, 10, 6, 2, 7, 9, 8, 1]
838 [3, 0, 4, 11, 5, 10, 6, 9, 7, 1, 8, 2]
839 [3, 0, 4, 11, 5, 10, 6, 9, 7, 2, 8, 1]
840 [3, 1, 4, 0, 5, 2, 6, 9, 7, 10, 8, 11]
841 [3, 1, 4, 0, 5, 2, 6, 9, 7, 11, 8, 10]
842 [3, 1, 4, 0, 5, 2, 6, 10, 7, 9, 8, 11]
843 [3, 1, 4, 0, 5, 2, 6, 10, 7, 11, 8, 9]
844 [3, 1, 4, 0, 5, 2, 6, 11, 7, 9, 8, 10]
845 [3, 1, 4, 0, 5, 2, 6, 11, 7, 10, 8, 9]
846 [3, 1, 4, 0, 5, 9, 6, 2, 7, 10, 8, 11]
847 [3, 1, 4, 0, 5, 9, 6, 2, 7, 11, 8, 10]
848 [3, 1, 4, 0, 5, 9, 6, 10, 7, 2, 8, 11]
849 [3, 1, 4, 0, 5, 9, 6, 10, 7, 11, 8, 2]
850 [3, 1, 4, 0, 5, 9, 6, 11, 7, 2, 8, 10]
851 [3, 1, 4, 0, 5, 9, 6, 11, 7, 10, 8, 2]
852 [3, 1, 4, 0, 5, 10, 6, 2, 7, 9, 8, 11]
853 [3, 1, 4, 0, 5, 10, 6, 2, 7, 11, 8, 9]
854 [3, 1, 4, 0, 5, 10, 6, 9, 7, 2, 8, 11]
855 [3, 1, 4, 0, 5, 10, 6, 9, 7, 11, 8, 2]
856 [3, 1, 4, 0, 5, 10, 6, 11, 7, 2, 8, 9]
857 [3, 1, 4, 0, 5, 10, 6, 11, 7, 9, 8, 2]
858 [3, 1, 4, 0, 5, 11, 6, 2, 7, 9, 8, 10]
859 [3, 1, 4, 0, 5, 11, 6, 2, 7, 10, 8, 9]
860 [3, 1, 4, 0, 5, 11, 6, 9, 7, 2, 8, 10]
861 [3, 1, 4, 0, 5, 11, 6, 9, 7, 10, 8, 2]
862 [3, 1, 4, 0, 5, 11, 6, 10, 7, 2, 8, 9]
863 [3, 1, 4, 0, 5, 11, 6, 10, 7, 9, 8, 2]
864 [3, 1, 4, 2, 5, 0, 6, 9, 7, 10, 8, 11]
865 [3, 1, 4, 2, 5, 0, 6, 9, 7, 11, 8, 10]
866 [3, 1, 4, 2, 5, 0, 6, 10, 7, 9, 8, 11]
867 [3, 1, 4, 2, 5, 0, 6, 10, 7, 11, 8, 9]
868 [3, 1, 4, 2, 5, 0, 6, 11, 7, 9, 8, 10]
869 [3, 1, 4, 2, 5, 0, 6, 11, 7, 10, 8, 9]
870 [3, 1, 4, 2, 5, 9, 6, 0, 7, 10, 8, 11]
871 [3, 1, 4, 2, 5, 9, 6, 0, 7, 11, 8, 10]
872 [3, 1, 4, 2, 5, 9, 6, 10, 7, 0, 8, 11]
873 [3, 1, 4, 2, 5, 9, 6, 10, 7, 11, 8, 0]
874 [3, 1, 4, 2, 5, 9, 6, 11, 7, 0, 8, 10]
875 [3, 1, 4, 2, 5, 9, 6, 11, 7, 10, 8, 0]
876 [3, 1, 4, 2, 5, 10, 6, 0, 7, 9, 8, 11]
877 [3, 1, 4, 2, 5, 10, 6, 0, 7, 11, 8, 9]
878 [3, 1, 4, 2, 5, 10, 6, 9, 7, 0, 8, 11]
879 [3, 1, 4, 2, 5, 10, 6, 9, 7, 11, 8, 0]
880 [3, 1, 4, 2, 5, 10, 6, 11, 7, 0, 8, 9]
881 [3, 1, 4, 2, 5, 10, 6, 11, 7, 9, 8, 0]
882 [3, 1, 4, 2, 5, 11, 6, 0, 7, 9, 8, 10]
883 [3, 1, 4, 2, 5, 11, 6, 0, 7, 10, 8, 9]
884 [3, 1, 4, 2, 5, 11, 6, 9, 7, 0, 8, 10]
885 [3, 1, 4, 2, 5, 11, 6, 9, 7, 10, 8, 0]
886 [3, 1, 4, 2, 5, 11, 6, 10, 7, 0, 8, 9]
887 [3, 1, 4, 2, 5, 11, 6, 10, 7, 9, 8, 0]
888 [3, 1, 4, 9, 5, 0, 6, 2, 7, 10, 8, 11]
889 [3, 1, 4, 9, 5, 0, 6, 2, 7, 11, 8, 10]
890 [3, 1, 4, 9, 5, 0, 6, 10, 7, 2, 8, 11]
891 [3, 1, 4, 9, 5, 0, 6, 10, 7, 11, 8, 2]
892 [3, 1, 4, 9, 5, 0, 6, 11, 7, 2, 8, 10]
893 [3, 1, 4, 9, 5, 0, 6, 11, 7, 10, 8, 2]
894 [3, 1, 4, 9, 5, 2, 6, 0, 7, 10, 8, 11]
895 [3, 1, 4, 9, 5, 2, 6, 0, 7, 11, 8, 10]
896 [3, 1, 4, 9, 5, 2, 6, 10, 7, 0, 8, 11]
897 [3, 1, 4, 9, 5, 2, 6, 10, 7, 11, 8, 0]
898 [3, 1, 4, 9, 5, 2, 6, 11, 7, 0, 8, 10]
899 [3, 1, 4, 9, 5, 2, 6, 11, 7, 10, 8, 0]
900 [3, 1, 4, 9, 5, 10, 6, 0, 7, 2, 8, 11]
901 [3, 1, 4, 9, 5, 10, 6, 0, 7, 11, 8, 2]
902 [3, 1, 4, 9, 5, 10, 6, 2, 7, 0, 8, 11]
903 [3, 1, 4, 9, 5, 10, 6, 2, 7, 11, 8, 0]
904 [3, 1, 4, 9, 5, 10, 6, 11, 7, 0, 8, 2]
905 [3, 1, 4, 9, 5, 10, 6, 11, 7, 2, 8, 0]
906 [3, 1, 4, 9, 5, 11, 6, 0, 7, 2, 8, 10]
907 [3, 1, 4, 9, 5, 11, 6, 0, 7, 10, 8, 2]
908 [3, 1, 4, 9, 5, 11, 6, 2, 7, 0, 8, 10]
909 [3, 1, 4, 9, 5, 11, 6, 2, 7, 10, 8, 0]
910 [3, 1, 4, 9, 5, 11, 6, 10, 7, 0, 8, 2]
911 [3, 1, 4, 9, 5, 11, 6, 10, 7, 2, 8, 0]
912 [3, 1, 4, 10, 5, 0, 6, 2, 7, 9, 8, 11]
913 [3, 1, 4, 10, 5, 0, 6, 2, 7, 11, 8, 9]
914 [3, 1, 4, 10, 5, 0, 6, 9, 7, 2, 8, 11]
915 [3, 1, 4, 10, 5, 0, 6, 9, 7, 11, 8, 2]
916 [3, 1, 4, 10, 5, 0, 6, 11, 7, 2, 8, 9]
917 [3, 1, 4, 10, 5, 0, 6, 11, 7, 9, 8, 2]
918 [3, 1, 4, 10, 5, 2, 6, 0, 7, 9, 8, 11]
919 [3, 1, 4, 10, 5, 2, 6, 0, 7, 11, 8, 9]
920 [3, 1, 4, 10, 5, 2, 6, 9, 7, 0, 8, 11]
921 [3, 1, 4, 10, 5, 2, 6, 9, 7, 11, 8, 0]
922 [3, 1, 4, 10, 5, 2, 6, 11, 7, 0, 8, 9]
923 [3, 1, 4, 10, 5, 2, 6, 11, 7, 9, 8, 0]
924 [3, 1, 4, 10, 5, 9, 6, 0, 7, 2, 8, 11]
925 [3, 1, 4, 10, 5, 9, 6, 0, 7, 11, 8, 2]
926 [3, 1, 4, 10, 5, 9, 6, 2, 7, 0, 8, 11]
927 [3, 1, 4, 10, 5, 9, 6, 2, 7, 11, 8, 0]
928 [3, 1, 4, 10, 5, 9, 6, 11, 7, 0, 8, 2]
929 [3, 1, 4, 10, 5, 9, 6, 11, 7, 2, 8, 0]
930 [3, 1, 4, 10, 5, 11, 6, 0, 7, 2, 8, 9]
931 [3, 1, 4, 10, 5, 11, 6, 0, 7, 9, 8, 2]
932 [3, 1, 4, 10, 5, 11, 6, 2, 7, 0, 8, 9]
933 [3, 1, 4, 10, 5, 11, 6, 2, 7, 9, 8, 0]
934 [3, 1, 4, 10, 5, 11, 6, 9, 7, 0, 8, 2]
935 [3, 1, 4, 10, 5, 11, 6, 9, 7, 2, 8, 0]
936 [3, 1, 4, 11, 5, 0, 6, 2, 7, 9, 8, 10]
937 [3, 1, 4, 11, 5, 0, 6, 2, 7, 10, 8, 9]
938 [3, 1, 4, 11, 5, 0, 6, 9, 7, 2, 8, 10]
939 [3, 1, 4, 11, 5, 0, 6, 9, 7, 10, 8, 2]
940 [3, 1, 4, 11, 5, 0, 6, 10, 7, 2, 8, 9]
941 [3, 1, 4, 11, 5, 0, 6, 10, 7, 9, 8, 2]
942 [3, 1, 4, 11, 5, 2, 6, 0, 7, 9, 8, 10]
943 [3, 1, 4, 11, 5, 2, 6, 0, 7, 10, 8, 9]
944 [3, 1, 4, 11, 5, 2, 6, 9, 7, 0, 8, 10]
945 [3, 1, 4, 11, 5, 2, 6, 9, 7, 10, 8, 0]
946 [3, 1, 4, 11, 5, 2, 6, 10, 7, 0, 8, 9]
947 [3, 1, 4, 11, 5, 2, 6, 10, 7, 9, 8, 0]
948 [3, 1, 4, 11, 5, 9, 6, 0, 7, 2, 8, 10]
949 [3, 1, 4, 11, 5, 9, 6, 0, 7, 10, 8, 2]
950 [3, 1, 4, 11, 5, 9, 6, 2, 7, 0, 8, 10]
951 [3, 1, 4, 11, 5, 9, 6, 2, 7, 10, 8, 0]
952 [3, 1, 4, 11, 5, 9, 6, 10, 7, 0, 8, 2]
953 [3, 1, 4, 11, 5, 9, 6, 10, 7, 2, 8, 0]
954 [3, 1, 4, 11, 5, 10, 6, 0, 7, 2, 8, 9]
955 [3, 1, 4, 11, 5, 10, 6, 0, 7, 9, 8, 2]
956 [3, 1, 4, 11, 5, 10, 6, 2, 7, 0, 8, 9]
957 [3, 1, 4, 11, 5, 10, 6, 2, 7, 9, 8, 0]
958 [3, 1, 4, 11, 5, 10, 6, 9, 7, 0, 8, 2]
959 [3, 1, 4, 11, 5, 10, 6, 9, 7, 2, 8, 0]
960 [3, 2, 4, 0, 5, 1, 6, 9, 7, 10, 8, 11]
961 [3, 2, 4, 0, 5, 1, 6, 9, 7, 11, 8, 10]
962 [3, 2, 4, 0, 5, 1, 6, 10, 7, 9, 8, 11]
963 [3, 2, 4, 0, 5, 1, 6, 10, 7, 11, 8, 9]
964 [3, 2, 4, 0, 5, 1, 6, 11, 7, 9, 8, 10]
965 [3, 2, 4, 0, 5, 1, 6, 11, 7, 10, 8, 9]
966 [3, 2, 4, 0, 5, 9, 6, 1, 7, 10, 8, 11]
967 [3, 2, 4, 0, 5, 9, 6, 1, 7, 11, 8, 10]
968 [3, 2, 4, 0, 5, 9, 6, 10, 7, 1, 8, 11]
969 [3, 2, 4, 0, 5, 9, 6, 10, 7, 11, 8, 1]
970 [3, 2, 4, 0, 5, 9, 6, 11, 7, 1, 8, 10]
971 [3, 2, 4, 0, 5, 9, 6, 11, 7, 10, 8, 1]
972 [3, 2, 4, 0, 5, 10, 6, 1, 7, 9, 8, 11]
973 [3, 2, 4, 0, 5, 10, 6, 1, 7, 11, 8, 9]
974 [3, 2, 4, 0, 5, 10, 6, 9, 7, 1, 8, 11]
975 [3, 2, 4, 0, 5, 10, 6, 9, 7, 11, 8, 1]
976 [3, 2, 4, 0, 5, 10, 6, 11, 7, 1, 8, 9]
977 [3, 2, 4, 0, 5, 10, 6, 11, 7, 9, 8, 1]
978 [3, 2, 4, 0, 5, 11, 6, 1, 7, 9, 8, 10]
979 [3, 2, 4, 0, 5, 11, 6, 1, 7, 10, 8, 9]
980 [3, 2, 4, 0, 5, 11, 6, 9, 7, 1, 8, 10]
981 [3, 2, 4, 0, 5, 11, 6, 9, 7, 10, 8, 1]
982 [3, 2, 4, 0, 5, 11, 6, 10, 7, 1, 8, 9]
983 [3, 2, 4, 0, 5, 11, 6, 10, 7, 9, 8, 1]
984 [3, 2, 4, 1, 5, 0, 6, 9, 7, 10, 8, 11]
985 [3, 2, 4, 1, 5, 0, 6, 9, 7, 11, 8, 10]
986 [3, 2, 4, 1, 5, 0, 6, 10, 7, 9, 8, 11]
987 [3, 2, 4, 1, 5, 0, 6, 10, 7, 11, 8, 9]
988 [3, 2, 4, 1, 5, 0, 6, 11, 7, 9, 8, 10]
989 [3, 2, 4, 1, 5, 0, 6, 11, 7, 10, 8, 9]
990 [3, 2, 4, 1, 5, 9, 6, 0, 7, 10, 8, 11]
991 [3, 2, 4, 1, 5, 9, 6, 0, 7, 11, 8, 10]
992 [3, 2, 4, 1, 5, 9, 6, 10, 7, 0, 8, 11]
993 [3, 2, 4, 1, 5, 9, 6, 10, 7, 11, 8, 0]
994 [3, 2, 4, 1, 5, 9, 6, 11, 7, 0, 8, 10]
995 [3, 2, 4, 1, 5, 9, 6, 11, 7, 10, 8, 0]
996 [3, 2, 4, 1, 5, 10, 6, 0, 7, 9, 8, 11]
997 [3, 2, 4, 1, 5, 10, 6, 0, 7, 11, 8, 9]
998 [3, 2, 4, 1, 5, 10, 6, 9, 7, 0, 8, 11]
999 [3, 2, 4, 1, 5, 10, 6, 9, 7, 11, 8, 0]
1000 [3, 2, 4, 1, 5, 10, 6, 11, 7, 0, 8, 9]
1001 [3, 2, 4, 1, 5, 10, 6, 11, 7, 9, 8, 0]
1002 [3, 2, 4, 1, 5, 11, 6, 0, 7, 9, 8, 10]
1003 [3, 2, 4, 1, 5, 11, 6, 0, 7, 10, 8, 9]
1004 [3, 2, 4, 1, 5, 11, 6, 9, 7, 0, 8, 10]
1005 [3, 2, 4, 1, 5, 11, 6, 9, 7, 10, 8, 0]
1006 [3, 2, 4, 1, 5, 11, 6, 10, 7, 0, 8, 9]
1007 [3, 2, 4, 1, 5, 11, 6, 10, 7, 9, 8, 0]
1008 [3, 2, 4, 9, 5, 0, 6, 1, 7, 10, 8, 11]
1009 [3, 2, 4, 9, 5, 0, 6, 1, 7, 11, 8, 10]
1010 [3, 2, 4, 9, 5, 0, 6, 10, 7, 1, 8, 11]
1011 [3, 2, 4, 9, 5, 0, 6, 10, 7, 11, 8, 1]
1012 [3, 2, 4, 9, 5, 0, 6, 11, 7, 1, 8, 10]
1013 [3, 2, 4, 9, 5, 0, 6, 11, 7, 10, 8, 1]
1014 [3, 2, 4, 9, 5, 1, 6, 0, 7, 10, 8, 11]
1015 [3, 2, 4, 9, 5, 1, 6, 0, 7, 11, 8, 10]
1016 [3, 2, 4, 9, 5, 1, 6, 10, 7, 0, 8, 11]
1017 [3, 2, 4, 9, 5, 1, 6, 10, 7, 11, 8, 0]
1018 [3, 2, 4, 9, 5, 1, 6, 11, 7, 0, 8, 10]
1019 [3, 2, 4, 9, 5, 1, 6, 11, 7, 10, 8, 0]
1020 [3, 2, 4, 9, 5, 10, 6, 0, 7, 1, 8, 11]
1021 [3, 2, 4, 9, 5, 10, 6, 0, 7, 11, 8, 1]
1022 [3, 2, 4, 9, 5, 10, 6, 1, 7, 0, 8, 11]
1023 [3, 2, 4, 9, 5, 10, 6, 1, 7, 11, 8, 0]
1024 [3, 2, 4, 9, 5, 10, 6, 11, 7, 0, 8, 1]
1025 [3, 2, 4, 9, 5, 10, 6, 11, 7, 1, 8, 0]
1026 [3, 2, 4, 9, 5, 11, 6, 0, 7, 1, 8, 10]
1027 [3, 2, 4, 9, 5, 11, 6, 0, 7, 10, 8, 1]
1028 [3, 2, 4, 9, 5, 11, 6, 1, 7, 0, 8, 10]
1029 [3, 2, 4, 9, 5, 11, 6, 1, 7, 10, 8, 0]
1030 [3, 2, 4, 9, 5, 11, 6, 10, 7, 0, 8, 1]
1031 [3, 2, 4, 9, 5, 11, 6, 10, 7, 1, 8, 0]
1032 [3, 2, 4, 10, 5, 0, 6, 1, 7, 9, 8, 11]
1033 [3, 2, 4, 10, 5, 0, 6, 1, 7, 11, 8, 9]
1034 [3, 2, 4, 10, 5, 0, 6, 9, 7, 1, 8, 11]
1035 [3, 2, 4, 10, 5, 0, 6, 9, 7, 11, 8, 1]
1036 [3, 2, 4, 10, 5, 0, 6, 11, 7, 1, 8, 9]
1037 [3, 2, 4, 10, 5, 0, 6, 11, 7, 9, 8, 1]
1038 [3, 2, 4, 10, 5, 1, 6, 0, 7, 9, 8, 11]
1039 [3, 2, 4, 10, 5, 1, 6, 0, 7, 11, 8, 9]
1040 [3, 2, 4, 10, 5, 1, 6, 9, 7, 0, 8, 11]
1041 [3, 2, 4, 10, 5, 1, 6, 9, 7, 11, 8, 0]
1042 [3, 2, 4, 10, 5, 1, 6, 11, 7, 0, 8, 9]
1043 [3, 2, 4, 10, 5, 1, 6, 11, 7, 9, 8, 0]
1044 [3, 2, 4, 10, 5, 9, 6, 0, 7, 1, 8, 11]
1045 [3, 2, 4, 10, 5, 9, 6, 0, 7, 11, 8, 1]
1046 [3, 2, 4, 10, 5, 9, 6, 1, 7, 0, 8, 11]
1047 [3, 2, 4, 10, 5, 9, 6, 1, 7, 11, 8, 0]
1048 [3, 2, 4, 10, 5, 9, 6, 11, 7, 0, 8, 1]
1049 [3, 2, 4, 10, 5, 9, 6, 11, 7, 1, 8, 0]
1050 [3, 2, 4, 10, 5, 11, 6, 0, 7, 1, 8, 9]
1051 [3, 2, 4, 10, 5, 11, 6, 0, 7, 9, 8, 1]
1052 [3, 2, 4, 10, 5, 11, 6, 1, 7, 0, 8, 9]
1053 [3, 2, 4, 10, 5, 11, 6, 1, 7, 9, 8, 0]
1054 [3, 2, 4, 10, 5, 11, 6, 9, 7, 0, 8, 1]
1055 [3, 2, 4, 10, 5, 11, 6, 9, 7, 1, 8, 0]
1056 [3, 2, 4, 11, 5, 0, 6, 1, 7, 9, 8, 10]
1057 [3, 2, 4, 11, 5, 0, 6, 1, 7, 10, 8, 9]
1058 [3, 2, 4, 11, 5, 0, 6, 9, 7, 1, 8, 10]
1059 [3, 2, 4, 11, 5, 0, 6, 9, 7, 10, 8, 1]
1060 [3, 2, 4, 11, 5, 0, 6, 10, 7, 1, 8, 9]
1061 [3, 2, 4, 11, 5, 0, 6, 10, 7, 9, 8, 1]
1062 [3, 2, 4, 11, 5, 1, 6, 0, 7, 9, 8, 10]
1063 [3, 2, 4, 11, 5, 1, 6, 0, 7, 10, 8, 9]
1064 [3, 2, 4, 11, 5, 1, 6, 9, 7, 0, 8, 10]
1065 [3, 2, 4, 11, 5, 1, 6, 9, 7, 10, 8, 0]
1066 [3, 2, 4, 11, 5, 1, 6, 10, 7, 0, 8, 9]
1067 [3, 2, 4, 11, 5, 1, 6, 10, 7, 9, 8, 0]
1068 [3, 2, 4, 11, 5, 9, 6, 0, 7, 1, 8, 10]
1069 [3, 2, 4, 11, 5, 9, 6, 0, 7, 10, 8, 1]
1070 [3, 2, 4, 11, 5, 9, 6, 1, 7, 0, 8, 10]
1071 [3, 2, 4, 11, 5, 9, 6, 1, 7, 10, 8, 0]
1072 [3, 2, 4, 11, 5, 9, 6, 10, 7, 0, 8, 1]
1073 [3, 2, 4, 11, 5, 9, 6, 10, 7, 1, 8, 0]
1074 [3, 2, 4, 11, 5, 10, 6, 0, 7, 1, 8, 9]
1075 [3, 2, 4, 11, 5, 10, 6, 0, 7, 9, 8, 1]
1076 [3, 2, 4, 11, 5, 10, 6, 1, 7, 0, 8, 9]
1077 [3, 2, 4, 11, 5, 10, 6, 1, 7, 9, 8, 0]
1078 [3, 2, 4, 11, 5, 10, 6, 9, 7, 0, 8, 1]
1079 [3, 2, 4, 11, 5, 10, 6, 9, 7, 1, 8, 0]
1080 [3, 9, 4, 0, 5, 1, 6, 2, 7, 10, 8, 11]
1081 [3, 9, 4, 0, 5, 1, 6, 2, 7, 11, 8, 10]
1082 [3, 9, 4, 0, 5, 1, 6, 10, 7, 2, 8, 11]
1083 [3, 9, 4, 0, 5, 1, 6, 10, 7, 11, 8, 2]
1084 [3, 9, 4, 0, 5, 1, 6, 11, 7, 2, 8, 10]
1085 [3, 9, 4, 0, 5, 1, 6, 11, 7, 10, 8, 2]
1086 [3, 9, 4, 0, 5, 2, 6, 1, 7, 10, 8, 11]
1087 [3, 9, 4, 0, 5, 2, 6, 1, 7, 11, 8, 10]
1088 [3, 9, 4, 0, 5, 2, 6, 10, 7, 1, 8, 11]
1089 [3, 9, 4, 0, 5, 2, 6, 10, 7, 11, 8, 1]
1090 [3, 9, 4, 0, 5, 2, 6, 11, 7, 1, 8, 10]
1091 [3, 9, 4, 0, 5, 2, 6, 11, 7, 10, 8, 1]
1092 [3, 9, 4, 0, 5, 10, 6, 1, 7, 2, 8, 11]
1093 [3, 9, 4, 0, 5, 10, 6, 1, 7, 11, 8, 2]
1094 [3, 9, 4, 0, 5, 10, 6, 2, 7, 1, 8, 11]
1095 [3, 9, 4, 0, 5, 10, 6, 2, 7, 11, 8, 1]
1096 [3, 9, 4, 0, 5, 10, 6, 11, 7, 1, 8, 2]
1097 [3, 9, 4, 0, 5, 10, 6, 11, 7, 2, 8, 1]
1098 [3, 9, 4, 0, 5, 11, 6, 1, 7, 2, 8, 10]
1099 [3, 9, 4, 0, 5, 11, 6, 1, 7, 10, 8, 2]
1100 [3, 9, 4, 0, 5, 11, 6, 2, 7, 1, 8, 10]
1101 [3, 9, 4, 0, 5, 11, 6, 2, 7, 10, 8, 1]
1102 [3, 9, 4, 0, 5, 11, 6, 10, 7, 1, 8, 2]
1103 [3, 9, 4, 0, 5, 11, 6, 10, 7, 2, 8, 1]
1104 [3, 9, 4, 1, 5, 0, 6, 2, 7, 10, 8, 11]
1105 [3, 9, 4, 1, 5, 0, 6, 2, 7, 11, 8, 10]
1106 [3, 9, 4, 1, 5, 0, 6, 10, 7, 2, 8, 11]
1107 [3, 9, 4, 1, 5, 0, 6, 10, 7, 11, 8, 2]
1108 [3, 9, 4, 1, 5, 0, 6, 11, 7, 2, 8, 10]
1109 [3, 9, 4, 1, 5, 0, 6, 11, 7, 10, 8, 2]
1110 [3, 9, 4, 1, 5, 2, 6, 0, 7, 10, 8, 11]
1111 [3, 9, 4, 1, 5, 2, 6, 0, 7, 11, 8, 10]
1112 [3, 9, 4, 1, 5, 2, 6, 10, 7, 0, 8, 11]
1113 [3, 9, 4, 1, 5, 2, 6, 10, 7, 11, 8, 0]
1114 [3, 9, 4, 1, 5, 2, 6, 11, 7, 0, 8, 10]
1115 [3, 9, 4, 1, 5, 2, 6, 11, 7, 10, 8, 0]
1116 [3, 9, 4, 1, 5, 10, 6, 0, 7, 2, 8, 11]
1117 [3, 9, 4, 1, 5, 10, 6, 0, 7, 11, 8, 2]
1118 [3, 9, 4, 1, 5, 10, 6, 2, 7, 0, 8, 11]
1119 [3, 9, 4, 1, 5, 10, 6, 2, 7, 11, 8, 0]
1120 [3, 9, 4, 1, 5, 10, 6, 11, 7, 0, 8, 2]
1121 [3, 9, 4, 1, 5, 10, 6, 11, 7, 2, 8, 0]
1122 [3, 9, 4, 1, 5, 11, 6, 0, 7, 2, 8, 10]
1123 [3, 9, 4, 1, 5, 11, 6, 0, 7, 10, 8, 2]
1124 [3, 9, 4, 1, 5, 11, 6, 2, 7, 0, 8, 10]
1125 [3, 9, 4, 1, 5, 11, 6, 2, 7, 10, 8, 0]
1126 [3, 9, 4, 1, 5, 11, 6, 10, 7, 0, 8, 2]
1127 [3, 9, 4, 1, 5, 11, 6, 10, 7, 2, 8, 0]
1128 [3, 9, 4, 2, 5, 0, 6, 1, 7, 10, 8, 11]
1129 [3, 9, 4, 2, 5, 0, 6, 1, 7, 11, 8, 10]
1130 [3, 9, 4, 2, 5, 0, 6, 10, 7, 1, 8, 11]
1131 [3, 9, 4, 2, 5, 0, 6, 10, 7, 11, 8, 1]
1132 [3, 9, 4, 2, 5, 0, 6, 11, 7, 1, 8, 10]
1133 [3, 9, 4, 2, 5, 0, 6, 11, 7, 10, 8, 1]
1134 [3, 9, 4, 2, 5, 1, 6, 0, 7, 10, 8, 11]
1135 [3, 9, 4, 2, 5, 1, 6, 0, 7, 11, 8, 10]
1136 [3, 9, 4, 2, 5, 1, 6, 10, 7, 0, 8, 11]
1137 [3, 9, 4, 2, 5, 1, 6, 10, 7, 11, 8, 0]
1138 [3, 9, 4, 2, 5, 1, 6, 11, 7, 0, 8, 10]
1139 [3, 9, 4, 2, 5, 1, 6, 11, 7, 10, 8, 0]
1140 [3, 9, 4, 2, 5, 10, 6, 0, 7, 1, 8, 11]
1141 [3, 9, 4, 2, 5, 10, 6, 0, 7, 11, 8, 1]
1142 [3, 9, 4, 2, 5, 10, 6, 1, 7, 0, 8, 11]
1143 [3, 9, 4, 2, 5, 10, 6, 1, 7, 11, 8, 0]
1144 [3, 9, 4, 2, 5, 10, 6, 11, 7, 0, 8, 1]
1145 [3, 9, 4, 2, 5, 10, 6, 11, 7, 1, 8, 0]
1146 [3, 9, 4, 2, 5, 11, 6, 0, 7, 1, 8, 10]
1147 [3, 9, 4, 2, 5, 11, 6, 0, 7, 10, 8, 1]
1148 [3, 9, 4, 2, 5, 11, 6, 1, 7, 0, 8, 10]
1149 [3, 9, 4, 2, 5, 11, 6, 1, 7, 10, 8, 0]
1150 [3, 9, 4, 2, 5, 11, 6, 10, 7, 0, 8, 1]
1151 [3, 9, 4, 2, 5, 11, 6, 10, 7, 1, 8, 0]
1152 [3, 9, 4, 10, 5, 0, 6, 1, 7, 2, 8, 11]
1153 [3, 9, 4, 10, 5, 0, 6, 1, 7, 11, 8, 2]
1154 [3, 9, 4, 10, 5, 0, 6, 2, 7, 1, 8, 11]
1155 [3, 9, 4, 10, 5, 0, 6, 2, 7, 11, 8, 1]
1156 [3, 9, 4, 10, 5, 0, 6, 11, 7, 1, 8, 2]
1157 [3, 9, 4, 10, 5, 0, 6, 11, 7, 2, 8, 1]
1158 [3, 9, 4, 10, 5, 1, 6, 0, 7, 2, 8, 11]
1159 [3, 9, 4, 10, 5, 1, 6, 0, 7, 11, 8, 2]
1160 [3, 9, 4, 10, 5, 1, 6, 2, 7, 0, 8, 11]
1161 [3, 9, 4, 10, 5, 1, 6, 2, 7, 11, 8, 0]
1162 [3, 9, 4, 10, 5, 1, 6, 11, 7, 0, 8, 2]
1163 [3, 9, 4, 10, 5, 1, 6, 11, 7, 2, 8, 0]
1164 [3, 9, 4, 10, 5, 2, 6, 0, 7, 1, 8, 11]
1165 [3, 9, 4, 10, 5, 2, 6, 0, 7, 11, 8, 1]
1166 [3, 9, 4, 10, 5, 2, 6, 1, 7, 0, 8, 11]
1167 [3, 9, 4, 10, 5, 2, 6, 1, 7, 11, 8, 0]
1168 [3, 9, 4, 10, 5, 2, 6, 11, 7, 0, 8, 1]
1169 [3, 9, 4, 10, 5, 2, 6, 11, 7, 1, 8, 0]
1170 [3, 9, 4, 10, 5, 11, 6, 0, 7, 1, 8, 2]
1171 [3, 9, 4, 10, 5, 11, 6, 0, 7, 2, 8, 1]
1172 [3, 9, 4, 10, 5, 11, 6, 1, 7, 0, 8, 2]
1173 [3, 9, 4, 10, 5, 11, 6, 1, 7, 2, 8, 0]
1174 [3, 9, 4, 10, 5, 11, 6, 2, 7, 0, 8, 1]
1175 [3, 9, 4, 10, 5, 11, 6, 2, 7, 1, 8, 0]
1176 [3, 9, 4, 11, 5, 0, 6, 1, 7, 2, 8, 10]
1177 [3, 9, 4, 11, 5, 0, 6, 1, 7, 10, 8, 2]
1178 [3, 9, 4, 11, 5, 0, 6, 2, 7, 1, 8, 10]
1179 [3, 9, 4, 11, 5, 0, 6, 2, 7, 10, 8, 1]
1180 [3, 9, 4, 11, 5, 0, 6, 10, 7, 1, 8, 2]
1181 [3, 9, 4, 11, 5, 0, 6, 10, 7, 2, 8, 1]
1182 [3, 9, 4, 11, 5, 1, 6, 0, 7, 2, 8, 10]
1183 [3, 9, 4, 11, 5, 1, 6, 0, 7, 10, 8, 2]
1184 [3, 9, 4, 11, 5, 1, 6, 2, 7, 0, 8, 10]
1185 [3, 9, 4, 11, 5, 1, 6, 2, 7, 10, 8, 0]
1186 [3, 9, 4, 11, 5, 1, 6, 10, 7, 0, 8, 2]
1187 [3, 9, 4, 11, 5, 1, 6, 10, 7, 2, 8, 0]
1188 [3, 9, 4, 11, 5, 2, 6, 0, 7, 1, 8, 10]
1189 [3, 9, 4, 11, 5, 2, 6, 0, 7, 10, 8, 1]
1190 [3, 9, 4, 11, 5, 2, 6, 1, 7, 0, 8, 10]
1191 [3, 9, 4, 11, 5, 2, 6, 1, 7, 10, 8, 0]
1192 [3, 9, 4, 11, 5, 2, 6, 10, 7, 0, 8, 1]
1193 [3, 9, 4, 11, 5, 2, 6, 10, 7, 1, 8, 0]
1194 [3, 9, 4, 11, 5, 10, 6, 0, 7, 1, 8, 2]
1195 [3, 9, 4, 11, 5, 10, 6, 0, 7, 2, 8, 1]
1196 [3, 9, 4, 11, 5, 10, 6, 1, 7, 0, 8, 2]
1197 [3, 9, 4, 11, 5, 10, 6, 1, 7, 2, 8, 0]
1198 [3, 9, 4, 11, 5, 10, 6, 2, 7, 0, 8, 1]
1199 [3, 9, 4, 11, 5, 10, 6, 2, 7, 1, 8, 0]
1200 [3, 10, 4, 0, 5, 1, 6, 2, 7, 9, 8, 11]
1201 [3, 10, 4, 0, 5, 1, 6, 2, 7, 11, 8, 9]
1202 [3, 10, 4, 0, 5, 1, 6, 9, 7, 2, 8, 11]
1203 [3, 10, 4, 0, 5, 1, 6, 9, 7, 11, 8, 2]
1204 [3, 10, 4, 0, 5, 1, 6, 11, 7, 2, 8, 9]
1205 [3, 10, 4, 0, 5, 1, 6, 11, 7, 9, 8, 2]
1206 [3, 10, 4, 0, 5, 2, 6, 1, 7, 9, 8, 11]
1207 [3, 10, 4, 0, 5, 2, 6, 1, 7, 11, 8, 9]
1208 [3, 10, 4, 0, 5, 2, 6, 9, 7, 1, 8, 11]
1209 [3, 10, 4, 0, 5, 2, 6, 9, 7, 11, 8, 1]
1210 [3, 10, 4, 0, 5, 2, 6, 11, 7, 1, 8, 9]
1211 [3, 10, 4, 0, 5, 2, 6, 11, 7, 9, 8, 1]
1212 [3, 10, 4, 0, 5, 9, 6, 1, 7, 2, 8, 11]
1213 [3, 10, 4, 0, 5, 9, 6, 1, 7, 11, 8, 2]
1214 [3, 10, 4, 0, 5, 9, 6, 2, 7, 1, 8, 11]
1215 [3, 10, 4, 0, 5, 9, 6, 2, 7, 11, 8, 1]
1216 [3, 10, 4, 0, 5, 9, 6, 11, 7, 1, 8, 2]
1217 [3, 10, 4, 0, 5, 9, 6, 11, 7, 2, 8, 1]
1218 [3, 10, 4, 0, 5, 11, 6, 1, 7, 2, 8, 9]
1219 [3, 10, 4, 0, 5, 11, 6, 1, 7, 9, 8, 2]
1220 [3, 10, 4, 0, 5, 11, 6, 2, 7, 1, 8, 9]
1221 [3, 10, 4, 0, 5, 11, 6, 2, 7, 9, 8, 1]
1222 [3, 10, 4, 0, 5, 11, 6, 9, 7, 1, 8, 2]
1223 [3, 10, 4, 0, 5, 11, 6, 9, 7, 2, 8, 1]
1224 [3, 10, 4, 1, 5, 0, 6, 2, 7, 9, 8, 11]
1225 [3, 10, 4, 1, 5, 0, 6, 2, 7, 11, 8, 9]
1226 [3, 10, 4, 1, 5, 0, 6, 9, 7, 2, 8, 11]
1227 [3, 10, 4, 1, 5, 0, 6, 9, 7, 11, 8, 2]
1228 [3, 10, 4, 1, 5, 0, 6, 11, 7, 2, 8, 9]
1229 [3, 10, 4, 1, 5, 0, 6, 11, 7, 9, 8, 2]
1230 [3, 10, 4, 1, 5, 2, 6, 0, 7, 9, 8, 11]
1231 [3, 10, 4, 1, 5, 2, 6, 0, 7, 11, 8, 9]
1232 [3, 10, 4, 1, 5, 2, 6, 9, 7, 0, 8, 11]
1233 [3, 10, 4, 1, 5, 2, 6, 9, 7, 11, 8, 0]
1234 [3, 10, 4, 1, 5, 2, 6, 11, 7, 0, 8, 9]
1235 [3, 10, 4, 1, 5, 2, 6, 11, 7, 9, 8, 0]
1236 [3, 10, 4, 1, 5, 9, 6, 0, 7, 2, 8, 11]
1237 [3, 10, 4, 1, 5, 9, 6, 0, 7, 11, 8, 2]
1238 [3, 10, 4, 1, 5, 9, 6, 2, 7, 0, 8, 11]
1239 [3, 10, 4, 1, 5, 9, 6, 2, 7, 11, 8, 0]
1240 [3, 10, 4, 1, 5, 9, 6, 11, 7, 0, 8, 2]
1241 [3, 10, 4, 1, 5, 9, 6, 11, 7, 2, 8, 0]
1242 [3, 10, 4, 1, 5, 11, 6, 0, 7, 2, 8, 9]
1243 [3, 10, 4, 1, 5, 11, 6, 0, 7, 9, 8, 2]
1244 [3, 10, 4, 1, 5, 11, 6, 2, 7, 0, 8, 9]
1245 [3, 10, 4, 1, 5, 11, 6, 2, 7, 9, 8, 0]
1246 [3, 10, 4, 1, 5, 11, 6, 9, 7, 0, 8, 2]
1247 [3, 10, 4, 1, 5, 11, 6, 9, 7, 2, 8, 0]
1248 [3, 10, 4, 2, 5, 0, 6, 1, 7, 9, 8, 11]
1249 [3, 10, 4, 2, 5, 0, 6, 1, 7, 11, 8, 9]
1250 [3, 10, 4, 2, 5, 0, 6, 9, 7, 1, 8, 11]
1251 [3, 10, 4, 2, 5, 0, 6, 9, 7, 11, 8, 1]
1252 [3, 10, 4, 2, 5, 0, 6, 11, 7, 1, 8, 9]
1253 [3, 10, 4, 2, 5, 0, 6, 11, 7, 9, 8, 1]
1254 [3, 10, 4, 2, 5, 1, 6, 0, 7, 9, 8, 11]
1255 [3, 10, 4, 2, 5, 1, 6, 0, 7, 11, 8, 9]
1256 [3, 10, 4, 2, 5, 1, 6, 9, 7, 0, 8, 11]
1257 [3, 10, 4, 2, 5, 1, 6, 9, 7, 11, 8, 0]
1258 [3, 10, 4, 2, 5, 1, 6, 11, 7, 0, 8, 9]
1259 [3, 10, 4, 2, 5, 1, 6, 11, 7, 9, 8, 0]
1260 [3, 10, 4, 2, 5, 9, 6, 0, 7, 1, 8, 11]
1261 [3, 10, 4, 2, 5, 9, 6, 0, 7, 11, 8, 1]
1262 [3, 10, 4, 2, 5, 9, 6, 1, 7, 0, 8, 11]
1263 [3, 10, 4, 2, 5, 9, 6, 1, 7, 11, 8, 0]
1264 [3, 10, 4, 2, 5, 9, 6, 11, 7, 0, 8, 1]
1265 [3, 10, 4, 2, 5, 9, 6, 11, 7, 1, 8, 0]
1266 [3, 10, 4, 2, 5, 11, 6, 0, 7, 1, 8, 9]
1267 [3, 10, 4, 2, 5, 11, 6, 0, 7, 9, 8, 1]
1268 [3, 10, 4, 2, 5, 11, 6, 1, 7, 0, 8, 9]
1269 [3, 10, 4, 2, 5, 11, 6, 1, 7, 9, 8, 0]
1270 [3, 10, 4, 2, 5, 11, 6, 9, 7, 0, 8, 1]
1271 [3, 10, 4, 2, 5, 11, 6, 9, 7, 1, 8, 0]
1272 [3, 10, 4, 9, 5, 0, 6, 1, 7, 2, 8, 11]
1273 [3, 10, 4, 9, 5, 0, 6, 1, 7, 11, 8, 2]
1274 [3, 10, 4, 9, 5, 0, 6, 2, 7, 1, 8, 11]
1275 [3, 10, 4, 9, 5, 0, 6, 2, 7, 11, 8, 1]
1276 [3, 10, 4, 9, 5, 0, 6, 11, 7, 1, 8, 2]
1277 [3, 10, 4, 9, 5, 0, 6, 11, 7, 2, 8, 1]
1278 [3, 10, 4, 9, 5, 1, 6, 0, 7, 2, 8, 11]
1279 [3, 10, 4, 9, 5, 1, 6, 0, 7, 11, 8, 2]
1280 [3, 10, 4, 9, 5, 1, 6, 2, 7, 0, 8, 11]
1281 [3, 10, 4, 9, 5, 1, 6, 2, 7, 11, 8, 0]
1282 [3, 10, 4, 9, 5, 1, 6, 11, 7, 0, 8, 2]
1283 [3, 10, 4, 9, 5, 1, 6, 11, 7, 2, 8, 0]
1284 [3, 10, 4, 9, 5, 2, 6, 0, 7, 1, 8, 11]
1285 [3, 10, 4, 9, 5, 2, 6, 0, 7, 11, 8, 1]
1286 [3, 10, 4, 9, 5, 2, 6, 1, 7, 0, 8, 11]
1287 [3, 10, 4, 9, 5, 2, 6, 1, 7, 11, 8, 0]
1288 [3, 10, 4, 9, 5, 2, 6, 11, 7, 0, 8, 1]
1289 [3, 10, 4, 9, 5, 2, 6, 11, 7, 1, 8, 0]
1290 [3, 10, 4, 9, 5, 11, 6, 0, 7, 1, 8, 2]
1291 [3, 10, 4, 9, 5, 11, 6, 0, 7, 2, 8, 1]
1292 [3, 10, 4, 9, 5, 11, 6, 1, 7, 0, 8, 2]
1293 [3, 10, 4, 9, 5, 11, 6, 1, 7, 2, 8, 0]
1294 [3, 10, 4, 9, 5, 11, 6, 2, 7, 0, 8, 1]
1295 [3, 10, 4, 9, 5, 11, 6, 2, 7, 1, 8, 0]
1296 [3, 10, 4, 11, 5, 0, 6, 1, 7, 2, 8, 9]
1297 [3, 10, 4, 11, 5, 0, 6, 1, 7, 9, 8, 2]
1298 [3, 10, 4, 11, 5, 0, 6, 2, 7, 1, 8, 9]
1299 [3, 10, 4, 11, 5, 0, 6, 2, 7, 9, 8, 1]
1300 [3, 10, 4, 11, 5, 0, 6, 9, 7, 1, 8, 2]
1301 [3, 10, 4, 11, 5, 0, 6, 9, 7, 2, 8, 1]
1302 [3, 10, 4, 11, 5, 1, 6, 0, 7, 2, 8, 9]
1303 [3, 10, 4, 11, 5, 1, 6, 0, 7, 9, 8, 2]
1304 [3, 10, 4, 11, 5, 1, 6, 2, 7, 0, 8, 9]
1305 [3, 10, 4, 11, 5, 1, 6, 2, 7, 9, 8, 0]
1306 [3, 10, 4, 11, 5, 1, 6, 9, 7, 0, 8, 2]
1307 [3, 10, 4, 11, 5, 1, 6, 9, 7, 2, 8, 0]
1308 [3, 10, 4, 11, 5, 2, 6, 0, 7, 1, 8, 9]
1309 [3, 10, 4, 11, 5, 2, 6, 0, 7, 9, 8, 1]
1310 [3, 10, 4, 11, 5, 2, 6, 1, 7, 0, 8, 9]
1311 [3, 10, 4, 11, 5, 2, 6, 1, 7, 9, 8, 0]
1312 [3, 10, 4, 11, 5, 2, 6, 9, 7, 0, 8, 1]
1313 [3, 10, 4, 11, 5, 2, 6, 9, 7, 1, 8, 0]
1314 [3, 10, 4, 11, 5, 9, 6, 0, 7, 1, 8, 2]
1315 [3, 10, 4, 11, 5, 9, 6, 0, 7, 2, 8, 1]
1316 [3, 10, 4, 11, 5, 9, 6, 1, 7, 0, 8, 2]
1317 [3, 10, 4, 11, 5, 9, 6, 1, 7, 2, 8, 0]
1318 [3, 10, 4, 11, 5, 9, 6, 2, 7, 0, 8, 1]
1319 [3, 10, 4, 11, 5, 9, 6, 2, 7, 1, 8, 0]
1320 [3, 11, 4, 0, 5, 1, 6, 2, 7, 9, 8, 10]
1321 [3, 11, 4, 0, 5, 1, 6, 2, 7, 10, 8, 9]
1322 [3, 11, 4, 0, 5, 1, 6, 9, 7, 2, 8, 10]
1323 [3, 11, 4, 0, 5, 1, 6, 9, 7, 10, 8, 2]
1324 [3, 11, 4, 0, 5, 1, 6, 10, 7, 2, 8, 9]
1325 [3, 11, 4, 0, 5, 1, 6, 10, 7, 9, 8, 2]
1326 [3, 11, 4, 0, 5, 2, 6, 1, 7, 9, 8, 10]
1327 [3, 11, 4, 0, 5, 2, 6, 1, 7, 10, 8, 9]
1328 [3, 11, 4, 0, 5, 2, 6, 9, 7, 1, 8, 10]
1329 [3, 11, 4, 0, 5, 2, 6, 9, 7, 10, 8, 1]
1330 [3, 11, 4, 0, 5, 2, 6, 10, 7, 1, 8, 9]
1331 [3, 11, 4, 0, 5, 2, 6, 10, 7, 9, 8, 1]
1332 [3, 11, 4, 0, 5, 9, 6, 1, 7, 2, 8, 10]
1333 [3, 11, 4, 0, 5, 9, 6, 1, 7, 10, 8, 2]
1334 [3, 11, 4, 0, 5, 9, 6, 2, 7, 1, 8, 10]
1335 [3, 11, 4, 0, 5, 9, 6, 2, 7, 10, 8, 1]
1336 [3, 11, 4, 0, 5, 9, 6, 10, 7, 1, 8, 2]
1337 [3, 11, 4, 0, 5, 9, 6, 10, 7, 2, 8, 1]
1338 [3, 11, 4, 0, 5, 10, 6, 1, 7, 2, 8, 9]
1339 [3, 11, 4, 0, 5, 10, 6, 1, 7, 9, 8, 2]
1340 [3, 11, 4, 0, 5, 10, 6, 2, 7, 1, 8, 9]
1341 [3, 11, 4, 0, 5, 10, 6, 2, 7, 9, 8, 1]
1342 [3, 11, 4, 0, 5, 10, 6, 9, 7, 1, 8, 2]
1343 [3, 11, 4, 0, 5, 10, 6, 9, 7, 2, 8, 1]
1344 [3, 11, 4, 1, 5, 0, 6, 2, 7, 9, 8, 10]
1345 [3, 11, 4, 1, 5, 0, 6, 2, 7, 10, 8, 9]
1346 [3, 11, 4, 1, 5, 0, 6, 9, 7, 2, 8, 10]
1347 [3, 11, 4, 1, 5, 0, 6, 9, 7, 10, 8, 2]
1348 [3, 11, 4, 1, 5, 0, 6, 10, 7, 2, 8, 9]
1349 [3, 11, 4, 1, 5, 0, 6, 10, 7, 9, 8, 2]
1350 [3, 11, 4, 1, 5, 2, 6, 0, 7, 9, 8, 10]
1351 [3, 11, 4, 1, 5, 2, 6, 0, 7, 10, 8, 9]
1352 [3, 11, 4, 1, 5, 2, 6, 9, 7, 0, 8, 10]
1353 [3, 11, 4, 1, 5, 2, 6, 9, 7, 10, 8, 0]
1354 [3, 11, 4, 1, 5, 2, 6, 10, 7, 0, 8, 9]
1355 [3, 11, 4, 1, 5, 2, 6, 10, 7, 9, 8, 0]
1356 [3, 11, 4, 1, 5, 9, 6, 0, 7, 2, 8, 10]
1357 [3, 11, 4, 1, 5, 9, 6, 0, 7, 10, 8, 2]
1358 [3, 11, 4, 1, 5, 9, 6, 2, 7, 0, 8, 10]
1359 [3, 11, 4, 1, 5, 9, 6, 2, 7, 10, 8, 0]
1360 [3, 11, 4, 1, 5, 9, 6, 10, 7, 0, 8, 2]
1361 [3, 11, 4, 1, 5, 9, 6, 10, 7, 2, 8, 0]
1362 [3, 11, 4, 1, 5, 10, 6, 0, 7, 2, 8, 9]
1363 [3, 11, 4, 1, 5, 10, 6, 0, 7, 9, 8, 2]
1364 [3, 11, 4, 1, 5, 10, 6, 2, 7, 0, 8, 9]
1365 [3, 11, 4, 1, 5, 10, 6, 2, 7, 9, 8, 0]
1366 [3, 11, 4, 1, 5, 10, 6, 9, 7, 0, 8, 2]
1367 [3, 11, 4, 1, 5, 10, 6, 9, 7, 2, 8, 0]
1368 [3, 11, 4, 2, 5, 0, 6, 1, 7, 9, 8, 10]
1369 [3, 11, 4, 2, 5, 0, 6, 1, 7, 10, 8, 9]
1370 [3, 11, 4, 2, 5, 0, 6, 9, 7, 1, 8, 10]
1371 [3, 11, 4, 2, 5, 0, 6, 9, 7, 10, 8, 1]
1372 [3, 11, 4, 2, 5, 0, 6, 10, 7, 1, 8, 9]
1373 [3, 11, 4, 2, 5, 0, 6, 10, 7, 9, 8, 1]
1374 [3, 11, 4, 2, 5, 1, 6, 0, 7, 9, 8, 10]
1375 [3, 11, 4, 2, 5, 1, 6, 0, 7, 10, 8, 9]
1376 [3, 11, 4, 2, 5, 1, 6, 9, 7, 0, 8, 10]
1377 [3, 11, 4, 2, 5, 1, 6, 9, 7, 10, 8, 0]
1378 [3, 11, 4, 2, 5, 1, 6, 10, 7, 0, 8, 9]
1379 [3, 11, 4, 2, 5, 1, 6, 10, 7, 9, 8, 0]
1380 [3, 11, 4, 2, 5, 9, 6, 0, 7, 1, 8, 10]
1381 [3, 11, 4, 2, 5, 9, 6, 0, 7, 10, 8, 1]
1382 [3, 11, 4, 2, 5, 9, 6, 1, 7, 0, 8, 10]
1383 [3, 11, 4, 2, 5, 9, 6, 1, 7, 10, 8, 0]
1384 [3, 11, 4, 2, 5, 9, 6, 10, 7, 0, 8, 1]
1385 [3, 11, 4, 2, 5, 9, 6, 10, 7, 1, 8, 0]
1386 [3, 11, 4, 2, 5, 10, 6, 0, 7, 1, 8, 9]
1387 [3, 11, 4, 2, 5, 10, 6, 0, 7, 9, 8, 1]
1388 [3, 11, 4, 2, 5, 10, 6, 1, 7, 0, 8, 9]
1389 [3, 11, 4, 2, 5, 10, 6, 1, 7, 9, 8, 0]
1390 [3, 11, 4, 2, 5, 10, 6, 9, 7, 0, 8, 1]
1391 [3, 11, 4, 2, 5, 10, 6, 9, 7, 1, 8, 0]
1392 [3, 11, 4, 9, 5, 0, 6, 1, 7, 2, 8, 10]
1393 [3, 11, 4, 9, 5, 0, 6, 1, 7, 10, 8, 2]
1394 [3, 11, 4, 9, 5, 0, 6, 2, 7, 1, 8, 10]
1395 [3, 11, 4, 9, 5, 0, 6, 2, 7, 10, 8, 1]
1396 [3, 11, 4, 9, 5, 0, 6, 10, 7, 1, 8, 2]
1397 [3, 11, 4, 9, 5, 0, 6, 10, 7, 2, 8, 1]
1398 [3, 11, 4, 9, 5, 1, 6, 0, 7, 2, 8, 10]
1399 [3, 11, 4, 9, 5, 1, 6, 0, 7, 10, 8, 2]
1400 [3, 11, 4, 9, 5, 1, 6, 2, 7, 0, 8, 10]
1401 [3, 11, 4, 9, 5, 1, 6, 2, 7, 10, 8, 0]
1402 [3, 11, 4, 9, 5, 1, 6, 10, 7, 0, 8, 2]
1403 [3, 11, 4, 9, 5, 1, 6, 10, 7, 2, 8, 0]
1404 [3, 11, 4, 9, 5, 2, 6, 0, 7, 1, 8, 10]
1405 [3, 11, 4, 9, 5, 2, 6, 0, 7, 10, 8, 1]
1406 [3, 11, 4, 9, 5, 2, 6, 1, 7, 0, 8, 10]
1407 [3, 11, 4, 9, 5, 2, 6, 1, 7, 10, 8, 0]
1408 [3, 11, 4, 9, 5, 2, 6, 10, 7, 0, 8, 1]
1409 [3, 11, 4, 9, 5, 2, 6, 10, 7, 1, 8, 0]
1410 [3, 11, 4, 9, 5, 10, 6, 0, 7, 1, 8, 2]
1411 [3, 11, 4, 9, 5, 10, 6, 0, 7, 2, 8, 1]
1412 [3, 11, 4, 9, 5, 10, 6, 1, 7, 0, 8, 2]
1413 [3, 11, 4, 9, 5, 10, 6, 1, 7, 2, 8, 0]
1414 [3, 11, 4, 9, 5, 10, 6, 2, 7, 0, 8, 1]
1415 [3, 11, 4, 9, 5, 10, 6, 2, 7, 1, 8, 0]
1416 [3, 11, 4, 10, 5, 0, 6, 1, 7, 2, 8, 9]
1417 [3, 11, 4, 10, 5, 0, 6, 1, 7, 9, 8, 2]
1418 [3, 11, 4, 10, 5, 0, 6, 2, 7, 1, 8, 9]
1419 [3, 11, 4, 10, 5, 0, 6, 2, 7, 9, 8, 1]
1420 [3, 11, 4, 10, 5, 0, 6, 9, 7, 1, 8, 2]
1421 [3, 11, 4, 10, 5, 0, 6, 9, 7, 2, 8, 1]
1422 [3, 11, 4, 10, 5, 1, 6, 0, 7, 2, 8, 9]
1423 [3, 11, 4, 10, 5, 1, 6, 0, 7, 9, 8, 2]
1424 [3, 11, 4, 10, 5, 1, 6, 2, 7, 0, 8, 9]
1425 [3, 11, 4, 10, 5, 1, 6, 2, 7, 9, 8, 0]
1426 [3, 11, 4, 10, 5, 1, 6, 9, 7, 0, 8, 2]
1427 [3, 11, 4, 10, 5, 1, 6, 9, 7, 2, 8, 0]
1428 [3, 11, 4, 10, 5, 2, 6, 0, 7, 1, 8, 9]
1429 [3, 11, 4, 10, 5, 2, 6, 0, 7, 9, 8, 1]
1430 [3, 11, 4, 10, 5, 2, 6, 1, 7, 0, 8, 9]
1431 [3, 11, 4, 10, 5, 2, 6, 1, 7, 9, 8, 0]
1432 [3, 11, 4, 10, 5, 2, 6, 9, 7, 0, 8, 1]
1433 [3, 11, 4, 10, 5, 2, 6, 9, 7, 1, 8, 0]
1434 [3, 11, 4, 10, 5, 9, 6, 0, 7, 1, 8, 2]
1435 [3, 11, 4, 10, 5, 9, 6, 0, 7, 2, 8, 1]
1436 [3, 11, 4, 10, 5, 9, 6, 1, 7, 0, 8, 2]
1437 [3, 11, 4, 10, 5, 9, 6, 1, 7, 2, 8, 0]
1438 [3, 11, 4, 10, 5, 9, 6, 2, 7, 0, 8, 1]
1439 [3, 11, 4, 10, 5, 9, 6, 2, 7, 1, 8, 0]
1440 [5, 0, 6, 1, 7, 2, 8, 3, 9, 4, 10, 11]
1441 [5, 0, 6, 1, 7, 2, 8, 3, 9, 11, 10, 4]
1442 [5, 0, 6, 1, 7, 2, 8, 4, 9, 3, 10, 11]
1443 [5, 0, 6, 1, 7, 2, 8, 4, 9, 11, 10, 3]
1444 [5, 0, 6, 1, 7, 2, 8, 11, 9, 3, 10, 4]
1445 [5, 0, 6, 1, 7, 2, 8, 11, 9, 4, 10, 3]
1446 [5, 0, 6, 1, 7, 3, 8, 2, 9, 4, 10, 11]
1447 [5, 0, 6, 1, 7, 3, 8, 2, 9, 11, 10, 4]
1448 [5, 0, 6, 1, 7, 3, 8, 4, 9, 2, 10, 11]
1449 [5, 0, 6, 1, 7, 3, 8, 4, 9, 11, 10, 2]
1450 [5, 0, 6, 1, 7, 3, 8, 11, 9, 2, 10, 4]
1451 [5, 0, 6, 1, 7, 3, 8, 11, 9, 4, 10, 2]
1452 [5, 0, 6, 1, 7, 4, 8, 2, 9, 3, 10, 11]
1453 [5, 0, 6, 1, 7, 4, 8, 2, 9, 11, 10, 3]
1454 [5, 0, 6, 1, 7, 4, 8, 3, 9, 2, 10, 11]
1455 [5, 0, 6, 1, 7, 4, 8, 3, 9, 11, 10, 2]
1456 [5, 0, 6, 1, 7, 4, 8, 11, 9, 2, 10, 3]
1457 [5, 0, 6, 1, 7, 4, 8, 11, 9, 3, 10, 2]
1458 [5, 0, 6, 1, 7, 11, 8, 2, 9, 3, 10, 4]
1459 [5, 0, 6, 1, 7, 11, 8, 2, 9, 4, 10, 3]
1460 [5, 0, 6, 1, 7, 11, 8, 3, 9, 2, 10, 4]
1461 [5, 0, 6, 1, 7, 11, 8, 3, 9, 4, 10, 2]
1462 [5, 0, 6, 1, 7, 11, 8, 4, 9, 2, 10, 3]
1463 [5, 0, 6, 1, 7, 11, 8, 4, 9, 3, 10, 2]
1464 [5, 0, 6, 2, 7, 1, 8, 3, 9, 4, 10, 11]
1465 [5, 0, 6, 2, 7, 1, 8, 3, 9, 11, 10, 4]
1466 [5, 0, 6, 2, 7, 1, 8, 4, 9, 3, 10, 11]
1467 [5, 0, 6, 2, 7, 1, 8, 4, 9, 11, 10, 3]
1468 [5, 0, 6, 2, 7, 1, 8, 11, 9, 3, 10, 4]
1469 [5, 0, 6, 2, 7, 1, 8, 11, 9, 4, 10, 3]
1470 [5, 0, 6, 2, 7, 3, 8, 1, 9, 4, 10, 11]
1471 [5, 0, 6, 2, 7, 3, 8, 1, 9, 11, 10, 4]
1472 [5, 0, 6, 2, 7, 3, 8, 4, 9, 1, 10, 11]
1473 [5, 0, 6, 2, 7, 3, 8, 4, 9, 11, 10, 1]
1474 [5, 0, 6, 2, 7, 3, 8, 11, 9, 1, 10, 4]
1475 [5, 0, 6, 2, 7, 3, 8, 11, 9, 4, 10, 1]
1476 [5, 0, 6, 2, 7, 4, 8, 1, 9, 3, 10, 11]
1477 [5, 0, 6, 2, 7, 4, 8, 1, 9, 11, 10, 3]
1478 [5, 0, 6, 2, 7, 4, 8, 3, 9, 1, 10, 11]
1479 [5, 0, 6, 2, 7, 4, 8, 3, 9, 11, 10, 1]
1480 [5, 0, 6, 2, 7, 4, 8, 11, 9, 1, 10, 3]
1481 [5, 0, 6, 2, 7, 4, 8, 11, 9, 3, 10, 1]
1482 [5, 0, 6, 2, 7, 11, 8, 1, 9, 3, 10, 4]
1483 [5, 0, 6, 2, 7, 11, 8, 1, 9, 4, 10, 3]
1484 [5, 0, 6, 2, 7, 11, 8, 3, 9, 1, 10, 4]
1485 [5, 0, 6, 2, 7, 11, 8, 3, 9, 4, 10, 1]
1486 [5, 0, 6, 2, 7, 11, 8, 4, 9, 1, 10, 3]
1487 [5, 0, 6, 2, 7, 11, 8, 4, 9, 3, 10, 1]
1488 [5, 0, 6, 3, 7, 1, 8, 2, 9, 4, 10, 11]
1489 [5, 0, 6, 3, 7, 1, 8, 2, 9, 11, 10, 4]
1490 [5, 0, 6, 3, 7, 1, 8, 4, 9, 2, 10, 11]
1491 [5, 0, 6, 3, 7, 1, 8, 4, 9, 11, 10, 2]
1492 [5, 0, 6, 3, 7, 1, 8, 11, 9, 2, 10, 4]
1493 [5, 0, 6, 3, 7, 1, 8, 11, 9, 4, 10, 2]
1494 [5, 0, 6, 3, 7, 2, 8, 1, 9, 4, 10, 11]
1495 [5, 0, 6, 3, 7, 2, 8, 1, 9, 11, 10, 4]
1496 [5, 0, 6, 3, 7, 2, 8, 4, 9, 1, 10, 11]
1497 [5, 0, 6, 3, 7, 2, 8, 4, 9, 11, 10, 1]
1498 [5, 0, 6, 3, 7, 2, 8, 11, 9, 1, 10, 4]
1499 [5, 0, 6, 3, 7, 2, 8, 11, 9, 4, 10, 1]
1500 [5, 0, 6, 3, 7, 4, 8, 1, 9, 2, 10, 11]
1501 [5, 0, 6, 3, 7, 4, 8, 1, 9, 11, 10, 2]
1502 [5, 0, 6, 3, 7, 4, 8, 2, 9, 1, 10, 11]
1503 [5, 0, 6, 3, 7, 4, 8, 2, 9, 11, 10, 1]
1504 [5, 0, 6, 3, 7, 4, 8, 11, 9, 1, 10, 2]
1505 [5, 0, 6, 3, 7, 4, 8, 11, 9, 2, 10, 1]
1506 [5, 0, 6, 3, 7, 11, 8, 1, 9, 2, 10, 4]
1507 [5, 0, 6, 3, 7, 11, 8, 1, 9, 4, 10, 2]
1508 [5, 0, 6, 3, 7, 11, 8, 2, 9, 1, 10, 4]
1509 [5, 0, 6, 3, 7, 11, 8, 2, 9, 4, 10, 1]
1510 [5, 0, 6, 3, 7, 11, 8, 4, 9, 1, 10, 2]
1511 [5, 0, 6, 3, 7, 11, 8, 4, 9, 2, 10, 1]
1512 [5, 0, 6, 4, 7, 1, 8, 2, 9, 3, 10, 11]
1513 [5, 0, 6, 4, 7, 1, 8, 2, 9, 11, 10, 3]
1514 [5, 0, 6, 4, 7, 1, 8, 3, 9, 2, 10, 11]
1515 [5, 0, 6, 4, 7, 1, 8, 3, 9, 11, 10, 2]
1516 [5, 0, 6, 4, 7, 1, 8, 11, 9, 2, 10, 3]
1517 [5, 0, 6, 4, 7, 1, 8, 11, 9, 3, 10, 2]
1518 [5, 0, 6, 4, 7, 2, 8, 1, 9, 3, 10, 11]
1519 [5, 0, 6, 4, 7, 2, 8, 1, 9, 11, 10, 3]
1520 [5, 0, 6, 4, 7, 2, 8, 3, 9, 1, 10, 11]
1521 [5, 0, 6, 4, 7, 2, 8, 3, 9, 11, 10, 1]
1522 [5, 0, 6, 4, 7, 2, 8, 11, 9, 1, 10, 3]
1523 [5, 0, 6, 4, 7, 2, 8, 11, 9, 3, 10, 1]
1524 [5, 0, 6, 4, 7, 3, 8, 1, 9, 2, 10, 11]
1525 [5, 0, 6, 4, 7, 3, 8, 1, 9, 11, 10, 2]
1526 [5, 0, 6, 4, 7, 3, 8, 2, 9, 1, 10, 11]
1527 [5, 0, 6, 4, 7, 3, 8, 2, 9, 11, 10, 1]
1528 [5, 0, 6, 4, 7, 3, 8, 11, 9, 1, 10, 2]
1529 [5, 0, 6, 4, 7, 3, 8, 11, 9, 2, 10, 1]
1530 [5, 0, 6, 4, 7, 11, 8, 1, 9, 2, 10, 3]
1531 [5, 0, 6, 4, 7, 11, 8, 1, 9, 3, 10, 2]
1532 [5, 0, 6, 4, 7, 11, 8, 2, 9, 1, 10, 3]
1533 [5, 0, 6, 4, 7, 11, 8, 2, 9, 3, 10, 1]
1534 [5, 0, 6, 4, 7, 11, 8, 3, 9, 1, 10, 2]
1535 [5, 0, 6, 4, 7, 11, 8, 3, 9, 2, 10, 1]
1536 [5, 0, 6, 11, 7, 1, 8, 2, 9, 3, 10, 4]
1537 [5, 0, 6, 11, 7, 1, 8, 2, 9, 4, 10, 3]
1538 [5, 0, 6, 11, 7, 1, 8, 3, 9, 2, 10, 4]
1539 [5, 0, 6, 11, 7, 1, 8, 3, 9, 4, 10, 2]
1540 [5, 0, 6, 11, 7, 1, 8, 4, 9, 2, 10, 3]
1541 [5, 0, 6, 11, 7, 1, 8, 4, 9, 3, 10, 2]
1542 [5, 0, 6, 11, 7, 2, 8, 1, 9, 3, 10, 4]
1543 [5, 0, 6, 11, 7, 2, 8, 1, 9, 4, 10, 3]
1544 [5, 0, 6, 11, 7, 2, 8, 3, 9, 1, 10, 4]
1545 [5, 0, 6, 11, 7, 2, 8, 3, 9, 4, 10, 1]
1546 [5, 0, 6, 11, 7, 2, 8, 4, 9, 1, 10, 3]
1547 [5, 0, 6, 11, 7, 2, 8, 4, 9, 3, 10, 1]
1548 [5, 0, 6, 11, 7, 3, 8, 1, 9, 2, 10, 4]
1549 [5, 0, 6, 11, 7, 3, 8, 1, 9, 4, 10, 2]
1550 [5, 0, 6, 11, 7, 3, 8, 2, 9, 1, 10, 4]
1551 [5, 0, 6, 11, 7, 3, 8, 2, 9, 4, 10, 1]
1552 [5, 0, 6, 11, 7, 3, 8, 4, 9, 1, 10, 2]
1553 [5, 0, 6, 11, 7, 3, 8, 4, 9, 2, 10, 1]
1554 [5, 0, 6, 11, 7, 4, 8, 1, 9, 2, 10, 3]
1555 [5, 0, 6, 11, 7, 4, 8, 1, 9, 3, 10, 2]
1556 [5, 0, 6, 11, 7, 4, 8, 2, 9, 1, 10, 3]
1557 [5, 0, 6, 11, 7, 4, 8, 2, 9, 3, 10, 1]
1558 [5, 0, 6, 11, 7, 4, 8, 3, 9, 1, 10, 2]
1559 [5, 0, 6, 11, 7, 4, 8, 3, 9, 2, 10, 1]
1560 [5, 1, 6, 0, 7, 2, 8, 3, 9, 4, 10, 11]
1561 [5, 1, 6, 0, 7, 2, 8, 3, 9, 11, 10, 4]
1562 [5, 1, 6, 0, 7, 2, 8, 4, 9, 3, 10, 11]
1563 [5, 1, 6, 0, 7, 2, 8, 4, 9, 11, 10, 3]
1564 [5, 1, 6, 0, 7, 2, 8, 11, 9, 3, 10, 4]
1565 [5, 1, 6, 0, 7, 2, 8, 11, 9, 4, 10, 3]
1566 [5, 1, 6, 0, 7, 3, 8, 2, 9, 4, 10, 11]
1567 [5, 1, 6, 0, 7, 3, 8, 2, 9, 11, 10, 4]
1568 [5, 1, 6, 0, 7, 3, 8, 4, 9, 2, 10, 11]
1569 [5, 1, 6, 0, 7, 3, 8, 4, 9, 11, 10, 2]
1570 [5, 1, 6, 0, 7, 3, 8, 11, 9, 2, 10, 4]
1571 [5, 1, 6, 0, 7, 3, 8, 11, 9, 4, 10, 2]
1572 [5, 1, 6, 0, 7, 4, 8, 2, 9, 3, 10, 11]
1573 [5, 1, 6, 0, 7, 4, 8, 2, 9, 11, 10, 3]
1574 [5, 1, 6, 0, 7, 4, 8, 3, 9, 2, 10, 11]
1575 [5, 1, 6, 0, 7, 4, 8, 3, 9, 11, 10, 2]
1576 [5, 1, 6, 0, 7, 4, 8, 11, 9, 2, 10, 3]
1577 [5, 1, 6, 0, 7, 4, 8, 11, 9, 3, 10, 2]
1578 [5, 1, 6, 0, 7, 11, 8, 2, 9, 3, 10, 4]
1579 [5, 1, 6, 0, 7, 11, 8, 2, 9, 4, 10, 3]
1580 [5, 1, 6, 0, 7, 11, 8, 3, 9, 2, 10, 4]
1581 [5, 1, 6, 0, 7, 11, 8, 3, 9, 4, 10, 2]
1582 [5, 1, 6, 0, 7, 11, 8, 4, 9, 2, 10, 3]
1583 [5, 1, 6, 0, 7, 11, 8, 4, 9, 3, 10, 2]
1584 [5, 1, 6, 2, 7, 0, 8, 3, 9, 4, 10, 11]
1585 [5, 1, 6, 2, 7, 0, 8, 3, 9, 11, 10, 4]
1586 [5, 1, 6, 2, 7, 0, 8, 4, 9, 3, 10, 11]
1587 [5, 1, 6, 2, 7, 0, 8, 4, 9, 11, 10, 3]
1588 [5, 1, 6, 2, 7, 0, 8, 11, 9, 3, 10, 4]
1589 [5, 1, 6, 2, 7, 0, 8, 11, 9, 4, 10, 3]
1590 [5, 1, 6, 2, 7, 3, 8, 0, 9, 4, 10, 11]
1591 [5, 1, 6, 2, 7, 3, 8, 0, 9, 11, 10, 4]
1592 [5, 1, 6, 2, 7, 3, 8, 4, 9, 0, 10, 11]
1593 [5, 1, 6, 2, 7, 3, 8, 4, 9, 11, 10, 0]
1594 [5, 1, 6, 2, 7, 3, 8, 11, 9, 0, 10, 4]
1595 [5, 1, 6, 2, 7, 3, 8, 11, 9, 4, 10, 0]
1596 [5, 1, 6, 2, 7, 4, 8, 0, 9, 3, 10, 11]
1597 [5, 1, 6, 2, 7, 4, 8, 0, 9, 11, 10, 3]
1598 [5, 1, 6, 2, 7, 4, 8, 3, 9, 0, 10, 11]
1599 [5, 1, 6, 2, 7, 4, 8, 3, 9, 11, 10, 0]
1600 [5, 1, 6, 2, 7, 4, 8, 11, 9, 0, 10, 3]
1601 [5, 1, 6, 2, 7, 4, 8, 11, 9, 3, 10, 0]
1602 [5, 1, 6, 2, 7, 11, 8, 0, 9, 3, 10, 4]
1603 [5, 1, 6, 2, 7, 11, 8, 0, 9, 4, 10, 3]
1604 [5, 1, 6, 2, 7, 11, 8, 3, 9, 0, 10, 4]
1605 [5, 1, 6, 2, 7, 11, 8, 3, 9, 4, 10, 0]
1606 [5, 1, 6, 2, 7, 11, 8, 4, 9, 0, 10, 3]
1607 [5, 1, 6, 2, 7, 11, 8, 4, 9, 3, 10, 0]
1608 [5, 1, 6, 3, 7, 0, 8, 2, 9, 4, 10, 11]
1609 [5, 1, 6, 3, 7, 0, 8, 2, 9, 11, 10, 4]
1610 [5, 1, 6, 3, 7, 0, 8, 4, 9, 2, 10, 11]
1611 [5, 1, 6, 3, 7, 0, 8, 4, 9, 11, 10, 2]
1612 [5, 1, 6, 3, 7, 0, 8, 11, 9, 2, 10, 4]
1613 [5, 1, 6, 3, 7, 0, 8, 11, 9, 4, 10, 2]
1614 [5, 1, 6, 3, 7, 2, 8, 0, 9, 4, 10, 11]
1615 [5, 1, 6, 3, 7, 2, 8, 0, 9, 11, 10, 4]
1616 [5, 1, 6, 3, 7, 2, 8, 4, 9, 0, 10, 11]
1617 [5, 1, 6, 3, 7, 2, 8, 4, 9, 11, 10, 0]
1618 [5, 1, 6, 3, 7, 2, 8, 11, 9, 0, 10, 4]
1619 [5, 1, 6, 3, 7, 2, 8, 11, 9, 4, 10, 0]
1620 [5, 1, 6, 3, 7, 4, 8, 0, 9, 2, 10, 11]
1621 [5, 1, 6, 3, 7, 4, 8, 0, 9, 11, 10, 2]
1622 [5, 1, 6, 3, 7, 4, 8, 2, 9, 0, 10, 11]
1623 [5, 1, 6, 3, 7, 4, 8, 2, 9, 11, 10, 0]
1624 [5, 1, 6, 3, 7, 4, 8, 11, 9, 0, 10, 2]
1625 [5, 1, 6, 3, 7, 4, 8, 11, 9, 2, 10, 0]
1626 [5, 1, 6, 3, 7, 11, 8, 0, 9, 2, 10, 4]
1627 [5, 1, 6, 3, 7, 11, 8, 0, 9, 4, 10, 2]
1628 [5, 1, 6, 3, 7, 11, 8, 2, 9, 0, 10, 4]
1629 [5, 1, 6, 3, 7, 11, 8, 2, 9, 4, 10, 0]
1630 [5, 1, 6, 3, 7, 11, 8, 4, 9, 0, 10, 2]
1631 [5, 1, 6, 3, 7, 11, 8, 4, 9, 2, 10, 0]
1632 [5, 1, 6, 4, 7, 0, 8, 2, 9, 3, 10, 11]
1633 [5, 1, 6, 4, 7, 0, 8, 2, 9, 11, 10, 3]
1634 [5, 1, 6, 4, 7, 0, 8, 3, 9, 2, 10, 11]
1635 [5, 1, 6, 4, 7, 0, 8, 3, 9, 11, 10, 2]
1636 [5, 1, 6, 4, 7, 0, 8, 11, 9, 2, 10, 3]
1637 [5, 1, 6, 4, 7, 0, 8, 11, 9, 3, 10, 2]
1638 [5, 1, 6, 4, 7, 2, 8, 0, 9, 3, 10, 11]
1639 [5, 1, 6, 4, 7, 2, 8, 0, 9, 11, 10, 3]
1640 [5, 1, 6, 4, 7, 2, 8, 3, 9, 0, 10, 11]
1641 [5, 1, 6, 4, 7, 2, 8, 3, 9, 11, 10, 0]
1642 [5, 1, 6, 4, 7, 2, 8, 11, 9, 0, 10, 3]
1643 [5, 1, 6, 4, 7, 2, 8, 11, 9, 3, 10, 0]
1644 [5, 1, 6, 4, 7, 3, 8, 0, 9, 2, 10, 11]
1645 [5, 1, 6, 4, 7, 3, 8, 0, 9, 11, 10, 2]
1646 [5, 1, 6, 4, 7, 3, 8, 2, 9, 0, 10, 11]
1647 [5, 1, 6, 4, 7, 3, 8, 2, 9, 11, 10, 0]
1648 [5, 1, 6, 4, 7, 3, 8, 11, 9, 0, 10, 2]
1649 [5, 1, 6, 4, 7, 3, 8, 11, 9, 2, 10, 0]
1650 [5, 1, 6, 4, 7, 11, 8, 0, 9, 2, 10, 3]
1651 [5, 1, 6, 4, 7, 11, 8, 0, 9, 3, 10, 2]
1652 [5, 1, 6, 4, 7, 11, 8, 2, 9, 0, 10, 3]
1653 [5, 1, 6, 4, 7, 11, 8, 2, 9, 3, 10, 0]
1654 [5, 1, 6, 4, 7, 11, 8, 3, 9, 0, 10, 2]
1655 [5, 1, 6, 4, 7, 11, 8, 3, 9, 2, 10, 0]
1656 [5, 1, 6, 11, 7, 0, 8, 2, 9, 3, 10, 4]
1657 [5, 1, 6, 11, 7, 0, 8, 2, 9, 4, 10, 3]
1658 [5, 1, 6, 11, 7, 0, 8, 3, 9, 2, 10, 4]
1659 [5, 1, 6, 11, 7, 0, 8, 3, 9, 4, 10, 2]
1660 [5, 1, 6, 11, 7, 0, 8, 4, 9, 2, 10, 3]
1661 [5, 1, 6, 11, 7, 0, 8, 4, 9, 3, 10, 2]
1662 [5, 1, 6, 11, 7, 2, 8, 0, 9, 3, 10, 4]
1663 [5, 1, 6, 11, 7, 2, 8, 0, 9, 4, 10, 3]
1664 [5, 1, 6, 11, 7, 2, 8, 3, 9, 0, 10, 4]
1665 [5, 1, 6, 11, 7, 2, 8, 3, 9, 4, 10, 0]
1666 [5, 1, 6, 11, 7, 2, 8, 4, 9, 0, 10, 3]
1667 [5, 1, 6, 11, 7, 2, 8, 4, 9, 3, 10, 0]
1668 [5, 1, 6, 11, 7, 3, 8, 0, 9, 2, 10, 4]
1669 [5, 1, 6, 11, 7, 3, 8, 0, 9, 4, 10, 2]
1670 [5, 1, 6, 11, 7, 3, 8, 2, 9, 0, 10, 4]
1671 [5, 1, 6, 11, 7, 3, 8, 2, 9, 4, 10, 0]
1672 [5, 1, 6, 11, 7, 3, 8, 4, 9, 0, 10, 2]
1673 [5, 1, 6, 11, 7, 3, 8, 4, 9, 2, 10, 0]
1674 [5, 1, 6, 11, 7, 4, 8, 0, 9, 2, 10, 3]
1675 [5, 1, 6, 11, 7, 4, 8, 0, 9, 3, 10, 2]
1676 [5, 1, 6, 11, 7, 4, 8, 2, 9, 0, 10, 3]
1677 [5, 1, 6, 11, 7, 4, 8, 2, 9, 3, 10, 0]
1678 [5, 1, 6, 11, 7, 4, 8, 3, 9, 0, 10, 2]
1679 [5, 1, 6, 11, 7, 4, 8, 3, 9, 2, 10, 0]
1680 [5, 2, 6, 0, 7, 1, 8, 3, 9, 4, 10, 11]
1681 [5, 2, 6, 0, 7, 1, 8, 3, 9, 11, 10, 4]
1682 [5, 2, 6, 0, 7, 1, 8, 4, 9, 3, 10, 11]
1683 [5, 2, 6, 0, 7, 1, 8, 4, 9, 11, 10, 3]
1684 [5, 2, 6, 0, 7, 1, 8, 11, 9, 3, 10, 4]
1685 [5, 2, 6, 0, 7, 1, 8, 11, 9, 4, 10, 3]
1686 [5, 2, 6, 0, 7, 3, 8, 1, 9, 4, 10, 11]
1687 [5, 2, 6, 0, 7, 3, 8, 1, 9, 11, 10, 4]
1688 [5, 2, 6, 0, 7, 3, 8, 4, 9, 1, 10, 11]
1689 [5, 2, 6, 0, 7, 3, 8, 4, 9, 11, 10, 1]
1690 [5, 2, 6, 0, 7, 3, 8, 11, 9, 1, 10, 4]
1691 [5, 2, 6, 0, 7, 3, 8, 11, 9, 4, 10, 1]
1692 [5, 2, 6, 0, 7, 4, 8, 1, 9, 3, 10, 11]
1693 [5, 2, 6, 0, 7, 4, 8, 1, 9, 11, 10, 3]
1694 [5, 2, 6, 0, 7, 4, 8, 3, 9, 1, 10, 11]
1695 [5, 2, 6, 0, 7, 4, 8, 3, 9, 11, 10, 1]
1696 [5, 2, 6, 0, 7, 4, 8, 11, 9, 1, 10, 3]
1697 [5, 2, 6, 0, 7, 4, 8, 11, 9, 3, 10, 1]
1698 [5, 2, 6, 0, 7, 11, 8, 1, 9, 3, 10, 4]
1699 [5, 2, 6, 0, 7, 11, 8, 1, 9, 4, 10, 3]
1700 [5, 2, 6, 0, 7, 11, 8, 3, 9, 1, 10, 4]
1701 [5, 2, 6, 0, 7, 11, 8, 3, 9, 4, 10, 1]
1702 [5, 2, 6, 0, 7, 11, 8, 4, 9, 1, 10, 3]
1703 [5, 2, 6, 0, 7, 11, 8, 4, 9, 3, 10, 1]
1704 [5, 2, 6, 1, 7, 0, 8, 3, 9, 4, 10, 11]
1705 [5, 2, 6, 1, 7, 0, 8, 3, 9, 11, 10, 4]
1706 [5, 2, 6, 1, 7, 0, 8, 4, 9, 3, 10, 11]
1707 [5, 2, 6, 1, 7, 0, 8, 4, 9, 11, 10, 3]
1708 [5, 2, 6, 1, 7, 0, 8, 11, 9, 3, 10, 4]
1709 [5, 2, 6, 1, 7, 0, 8, 11, 9, 4, 10, 3]
1710 [5, 2, 6, 1, 7, 3, 8, 0, 9, 4, 10, 11]
1711 [5, 2, 6, 1, 7, 3, 8, 0, 9, 11, 10, 4]
1712 [5, 2, 6, 1, 7, 3, 8, 4, 9, 0, 10, 11]
1713 [5, 2, 6, 1, 7, 3, 8, 4, 9, 11, 10, 0]
1714 [5, 2, 6, 1, 7, 3, 8, 11, 9, 0, 10, 4]
1715 [5, 2, 6, 1, 7, 3, 8, 11, 9, 4, 10, 0]
1716 [5, 2, 6, 1, 7, 4, 8, 0, 9, 3, 10, 11]
1717 [5, 2, 6, 1, 7, 4, 8, 0, 9, 11, 10, 3]
1718 [5, 2, 6, 1, 7, 4, 8, 3, 9, 0, 10, 11]
1719 [5, 2, 6, 1, 7, 4, 8, 3, 9, 11, 10, 0]
1720 [5, 2, 6, 1, 7, 4, 8, 11, 9, 0, 10, 3]
1721 [5, 2, 6, 1, 7, 4, 8, 11, 9, 3, 10, 0]
1722 [5, 2, 6, 1, 7, 11, 8, 0, 9, 3, 10, 4]
1723 [5, 2, 6, 1, 7, 11, 8, 0, 9, 4, 10, 3]
1724 [5, 2, 6, 1, 7, 11, 8, 3, 9, 0, 10, 4]
1725 [5, 2, 6, 1, 7, 11, 8, 3, 9, 4, 10, 0]
1726 [5, 2, 6, 1, 7, 11, 8, 4, 9, 0, 10, 3]
1727 [5, 2, 6, 1, 7, 11, 8, 4, 9, 3, 10, 0]
1728 [5, 2, 6, 3, 7, 0, 8, 1, 9, 4, 10, 11]
1729 [5, 2, 6, 3, 7, 0, 8, 1, 9, 11, 10, 4]
1730 [5, 2, 6, 3, 7, 0, 8, 4, 9, 1, 10, 11]
1731 [5, 2, 6, 3, 7, 0, 8, 4, 9, 11, 10, 1]
1732 [5, 2, 6, 3, 7, 0, 8, 11, 9, 1, 10, 4]
1733 [5, 2, 6, 3, 7, 0, 8, 11, 9, 4, 10, 1]
1734 [5, 2, 6, 3, 7, 1, 8, 0, 9, 4, 10, 11]
1735 [5, 2, 6, 3, 7, 1, 8, 0, 9, 11, 10, 4]
1736 [5, 2, 6, 3, 7, 1, 8, 4, 9, 0, 10, 11]
1737 [5, 2, 6, 3, 7, 1, 8, 4, 9, 11, 10, 0]
1738 [5, 2, 6, 3, 7, 1, 8, 11, 9, 0, 10, 4]
1739 [5, 2, 6, 3, 7, 1, 8, 11, 9, 4, 10, 0]
1740 [5, 2, 6, 3, 7, 4, 8, 0, 9, 1, 10, 11]
1741 [5, 2, 6, 3, 7, 4, 8, 0, 9, 11, 10, 1]
1742 [5, 2, 6, 3, 7, 4, 8, 1, 9, 0, 10, 11]
1743 [5, 2, 6, 3, 7, 4, 8, 1, 9, 11, 10, 0]
1744 [5, 2, 6, 3, 7, 4, 8, 11, 9, 0, 10, 1]
1745 [5, 2, 6, 3, 7, 4, 8, 11, 9, 1, 10, 0]
1746 [5, 2, 6, 3, 7, 11, 8, 0, 9, 1, 10, 4]
1747 [5, 2, 6, 3, 7, 11, 8, 0, 9, 4, 10, 1]
1748 [5, 2, 6, 3, 7, 11, 8, 1, 9, 0, 10, 4]
1749 [5, 2, 6, 3, 7, 11, 8, 1, 9, 4, 10, 0]
1750 [5, 2, 6, 3, 7, 11, 8, 4, 9, 0, 10, 1]
1751 [5, 2, 6, 3, 7, 11, 8, 4, 9, 1, 10, 0]
1752 [5, 2, 6, 4, 7, 0, 8, 1, 9, 3, 10, 11]
1753 [5, 2, 6, 4, 7, 0, 8, 1, 9, 11, 10, 3]
1754 [5, 2, 6, 4, 7, 0, 8, 3, 9, 1, 10, 11]
1755 [5, 2, 6, 4, 7, 0, 8, 3, 9, 11, 10, 1]
1756 [5, 2, 6, 4, 7, 0, 8, 11, 9, 1, 10, 3]
1757 [5, 2, 6, 4, 7, 0, 8, 11, 9, 3, 10, 1]
1758 [5, 2, 6, 4, 7, 1, 8, 0, 9, 3, 10, 11]
1759 [5, 2, 6, 4, 7, 1, 8, 0, 9, 11, 10, 3]
1760 [5, 2, 6, 4, 7, 1, 8, 3, 9, 0, 10, 11]
1761 [5, 2, 6, 4, 7, 1, 8, 3, 9, 11, 10, 0]
1762 [5, 2, 6, 4, 7, 1, 8, 11, 9, 0, 10, 3]
1763 [5, 2, 6, 4, 7, 1, 8, 11, 9, 3, 10, 0]
1764 [5, 2, 6, 4, 7, 3, 8, 0, 9, 1, 10, 11]
1765 [5, 2, 6, 4, 7, 3, 8, 0, 9, 11, 10, 1]
1766 [5, 2, 6, 4, 7, 3, 8, 1, 9, 0, 10, 11]
1767 [5, 2, 6, 4, 7, 3, 8, 1, 9, 11, 10, 0]
1768 [5, 2, 6, 4, 7, 3, 8, 11, 9, 0, 10, 1]
1769 [5, 2, 6, 4, 7, 3, 8, 11, 9, 1, 10, 0]
1770 [5, 2, 6, 4, 7, 11, 8, 0, 9, 1, 10, 3]
1771 [5, 2, 6, 4, 7, 11, 8, 0, 9, 3, 10, 1]
1772 [5, 2, 6, 4, 7, 11, 8, 1, 9, 0, 10, 3]
1773 [5, 2, 6, 4, 7, 11, 8, 1, 9, 3, 10, 0]
1774 [5, 2, 6, 4, 7, 11, 8, 3, 9, 0, 10, 1]
1775 [5, 2, 6, 4, 7, 11, 8, 3, 9, 1, 10, 0]
1776 [5, 2, 6, 11, 7, 0, 8, 1, 9, 3, 10, 4]
1777 [5, 2, 6, 11, 7, 0, 8, 1, 9, 4, 10, 3]
1778 [5, 2, 6, 11, 7, 0, 8, 3, 9, 1, 10, 4]
1779 [5, 2, 6, 11, 7, 0, 8, 3, 9, 4, 10, 1]
1780 [5, 2, 6, 11, 7, 0, 8, 4, 9, 1, 10, 3]
1781 [5, 2, 6, 11, 7, 0, 8, 4, 9, 3, 10, 1]
1782 [5, 2, 6, 11, 7, 1, 8, 0, 9, 3, 10, 4]
1783 [5, 2, 6, 11, 7, 1, 8, 0, 9, 4, 10, 3]
1784 [5, 2, 6, 11, 7, 1, 8, 3, 9, 0, 10, 4]
1785 [5, 2, 6, 11, 7, 1, 8, 3, 9, 4, 10, 0]
1786 [5, 2, 6, 11, 7, 1, 8, 4, 9, 0, 10, 3]
1787 [5, 2, 6, 11, 7, 1, 8, 4, 9, 3, 10, 0]
1788 [5, 2, 6, 11, 7, 3, 8, 0, 9, 1, 10, 4]
1789 [5, 2, 6, 11, 7, 3, 8, 0, 9, 4, 10, 1]
1790 [5, 2, 6, 11, 7, 3, 8, 1, 9, 0, 10, 4]
1791 [5, 2, 6, 11, 7, 3, 8, 1, 9, 4, 10, 0]
1792 [5, 2, 6, 11, 7, 3, 8, 4, 9, 0, 10, 1]
1793 [5, 2, 6, 11, 7, 3, 8, 4, 9, 1, 10, 0]
1794 [5, 2, 6, 11, 7, 4, 8, 0, 9, 1, 10, 3]
1795 [5, 2, 6, 11, 7, 4, 8, 0, 9, 3, 10, 1]
1796 [5, 2, 6, 11, 7, 4, 8, 1, 9, 0, 10, 3]
1797 [5, 2, 6, 11, 7, 4, 8, 1, 9, 3, 10, 0]
1798 [5, 2, 6, 11, 7, 4, 8, 3, 9, 0, 10, 1]
1799 [5, 2, 6, 11, 7, 4, 8, 3, 9, 1, 10, 0]
1800 [5, 3, 6, 0, 7, 1, 8, 2, 9, 4, 10, 11]
1801 [5, 3, 6, 0, 7, 1, 8, 2, 9, 11, 10, 4]
1802 [5, 3, 6, 0, 7, 1, 8, 4, 9, 2, 10, 11]
1803 [5, 3, 6, 0, 7, 1, 8, 4, 9, 11, 10, 2]
1804 [5, 3, 6, 0, 7, 1, 8, 11, 9, 2, 10, 4]
1805 [5, 3, 6, 0, 7, 1, 8, 11, 9, 4, 10, 2]
1806 [5, 3, 6, 0, 7, 2, 8, 1, 9, 4, 10, 11]
1807 [5, 3, 6, 0, 7, 2, 8, 1, 9, 11, 10, 4]
1808 [5, 3, 6, 0, 7, 2, 8, 4, 9, 1, 10, 11]
1809 [5, 3, 6, 0, 7, 2, 8, 4, 9, 11, 10, 1]
1810 [5, 3, 6, 0, 7, 2, 8, 11, 9, 1, 10, 4]
1811 [5, 3, 6, 0, 7, 2, 8, 11, 9, 4, 10, 1]
1812 [5, 3, 6, 0, 7, 4, 8, 1, 9, 2, 10, 11]
1813 [5, 3, 6, 0, 7, 4, 8, 1, 9, 11, 10, 2]
1814 [5, 3, 6, 0, 7, 4, 8, 2, 9, 1, 10, 11]
1815 [5, 3, 6, 0, 7, 4, 8, 2, 9, 11, 10, 1]
1816 [5, 3, 6, 0, 7, 4, 8, 11, 9, 1, 10, 2]
1817 [5, 3, 6, 0, 7, 4, 8, 11, 9, 2, 10, 1]
1818 [5, 3, 6, 0, 7, 11, 8, 1, 9, 2, 10, 4]
1819 [5, 3, 6, 0, 7, 11, 8, 1, 9, 4, 10, 2]
1820 [5, 3, 6, 0, 7, 11, 8, 2, 9, 1, 10, 4]
1821 [5, 3, 6, 0, 7, 11, 8, 2, 9, 4, 10, 1]
1822 [5, 3, 6, 0, 7, 11, 8, 4, 9, 1, 10, 2]
1823 [5, 3, 6, 0, 7, 11, 8, 4, 9, 2, 10, 1]
1824 [5, 3, 6, 1, 7, 0, 8, 2, 9, 4, 10, 11]
1825 [5, 3, 6, 1, 7, 0, 8, 2, 9, 11, 10, 4]
1826 [5, 3, 6, 1, 7, 0, 8, 4, 9, 2, 10, 11]
1827 [5, 3, 6, 1, 7, 0, 8, 4, 9, 11, 10, 2]
1828 [5, 3, 6, 1, 7, 0, 8, 11, 9, 2, 10, 4]
1829 [5, 3, 6, 1, 7, 0, 8, 11, 9, 4, 10, 2]
1830 [5, 3, 6, 1, 7, 2, 8, 0, 9, 4, 10, 11]
1831 [5, 3, 6, 1, 7, 2, 8, 0, 9, 11, 10, 4]
1832 [5, 3, 6, 1, 7, 2, 8, 4, 9, 0, 10, 11]
1833 [5, 3, 6, 1, 7, 2, 8, 4, 9, 11, 10, 0]
1834 [5, 3, 6, 1, 7, 2, 8, 11, 9, 0, 10, 4]
1835 [5, 3, 6, 1, 7, 2, 8, 11, 9, 4, 10, 0]
1836 [5, 3, 6, 1, 7, 4, 8, 0, 9, 2, 10, 11]
1837 [5, 3, 6, 1, 7, 4, 8, 0, 9, 11, 10, 2]
1838 [5, 3, 6, 1, 7, 4, 8, 2, 9, 0, 10, 11]
1839 [5, 3, 6, 1, 7, 4, 8, 2, 9, 11, 10, 0]
1840 [5, 3, 6, 1, 7, 4, 8, 11, 9, 0, 10, 2]
1841 [5, 3, 6, 1, 7, 4, 8, 11, 9, 2, 10, 0]
1842 [5, 3, 6, 1, 7, 11, 8, 0, 9, 2, 10, 4]
1843 [5, 3, 6, 1, 7, 11, 8, 0, 9, 4, 10, 2]
1844 [5, 3, 6, 1, 7, 11, 8, 2, 9, 0, 10, 4]
1845 [5, 3, 6, 1, 7, 11, 8, 2, 9, 4, 10, 0]
1846 [5, 3, 6, 1, 7, 11, 8, 4, 9, 0, 10, 2]
1847 [5, 3, 6, 1, 7, 11, 8, 4, 9, 2, 10, 0]
1848 [5, 3, 6, 2, 7, 0, 8, 1, 9, 4, 10, 11]
1849 [5, 3, 6, 2, 7, 0, 8, 1, 9, 11, 10, 4]
1850 [5, 3, 6, 2, 7, 0, 8, 4, 9, 1, 10, 11]
1851 [5, 3, 6, 2, 7, 0, 8, 4, 9, 11, 10, 1]
1852 [5, 3, 6, 2, 7, 0, 8, 11, 9, 1, 10, 4]
1853 [5, 3, 6, 2, 7, 0, 8, 11, 9, 4, 10, 1]
1854 [5, 3, 6, 2, 7, 1, 8, 0, 9, 4, 10, 11]
1855 [5, 3, 6, 2, 7, 1, 8, 0, 9, 11, 10, 4]
1856 [5, 3, 6, 2, 7, 1, 8, 4, 9, 0, 10, 11]
1857 [5, 3, 6, 2, 7, 1, 8, 4, 9, 11, 10, 0]
1858 [5, 3, 6, 2, 7, 1, 8, 11, 9, 0, 10, 4]
1859 [5, 3, 6, 2, 7, 1, 8, 11, 9, 4, 10, 0]
1860 [5, 3, 6, 2, 7, 4, 8, 0, 9, 1, 10, 11]
1861 [5, 3, 6, 2, 7, 4, 8, 0, 9, 11, 10, 1]
1862 [5, 3, 6, 2, 7, 4, 8, 1, 9, 0, 10, 11]
1863 [5, 3, 6, 2, 7, 4, 8, 1, 9, 11, 10, 0]
1864 [5, 3, 6, 2, 7, 4, 8, 11, 9, 0, 10, 1]
1865 [5, 3, 6, 2, 7, 4, 8, 11, 9, 1, 10, 0]
1866 [5, 3, 6, 2, 7, 11, 8, 0, 9, 1, 10, 4]
1867 [5, 3, 6, 2, 7, 11, 8, 0, 9, 4, 10, 1]
1868 [5, 3, 6, 2, 7, 11, 8, 1, 9, 0, 10, 4]
1869 [5, 3, 6, 2, 7, 11, 8, 1, 9, 4, 10, 0]
1870 [5, 3, 6, 2, 7, 11, 8, 4, 9, 0, 10, 1]
1871 [5, 3, 6, 2, 7, 11, 8, 4, 9, 1, 10, 0]
1872 [5, 3, 6, 4, 7, 0, 8, 1, 9, 2, 10, 11]
1873 [5, 3, 6, 4, 7, 0, 8, 1, 9, 11, 10, 2]
1874 [5, 3, 6, 4, 7, 0, 8, 2, 9, 1, 10, 11]
1875 [5, 3, 6, 4, 7, 0, 8, 2, 9, 11, 10, 1]
1876 [5, 3, 6, 4, 7, 0, 8, 11, 9, 1, 10, 2]
1877 [5, 3, 6, 4, 7, 0, 8, 11, 9, 2, 10, 1]
1878 [5, 3, 6, 4, 7, 1, 8, 0, 9, 2, 10, 11]
1879 [5, 3, 6, 4, 7, 1, 8, 0, 9, 11, 10, 2]
1880 [5, 3, 6, 4, 7, 1, 8, 2, 9, 0, 10, 11]
1881 [5, 3, 6, 4, 7, 1, 8, 2, 9, 11, 10, 0]
1882 [5, 3, 6, 4, 7, 1, 8, 11, 9, 0, 10, 2]
1883 [5, 3, 6, 4, 7, 1, 8, 11, 9, 2, 10, 0]
1884 [5, 3, 6, 4, 7, 2, 8, 0, 9, 1, 10, 11]
1885 [5, 3, 6, 4, 7, 2, 8, 0, 9, 11, 10, 1]
1886 [5, 3, 6, 4, 7, 2, 8, 1, 9, 0, 10, 11]
1887 [5, 3, 6, 4, 7, 2, 8, 1, 9, 11, 10, 0]
1888 [5, 3, 6, 4, 7, 2, 8, 11, 9, 0, 10, 1]
1889 [5, 3, 6, 4, 7, 2, 8, 11, 9, 1, 10, 0]
1890 [5, 3, 6, 4, 7, 11, 8, 0, 9, 1, 10, 2]
1891 [5, 3, 6, 4, 7, 11, 8, 0, 9, 2, 10, 1]
1892 [5, 3, 6, 4, 7, 11, 8, 1, 9, 0, 10, 2]
1893 [5, 3, 6, 4, 7, 11, 8, 1, 9, 2, 10, 0]
1894 [5, 3, 6, 4, 7, 11, 8, 2, 9, 0, 10, 1]
1895 [5, 3, 6, 4, 7, 11, 8, 2, 9, 1, 10, 0]
1896 [5, 3, 6, 11, 7, 0, 8, 1, 9, 2, 10, 4]
1897 [5, 3, 6, 11, 7, 0, 8, 1, 9, 4, 10, 2]
1898 [5, 3, 6, 11, 7, 0, 8, 2, 9, 1, 10, 4]
1899 [5, 3, 6, 11, 7, 0, 8, 2, 9, 4, 10, 1]
1900 [5, 3, 6, 11, 7, 0, 8, 4, 9, 1, 10, 2]
1901 [5, 3, 6, 11, 7, 0, 8, 4, 9, 2, 10, 1]
1902 [5, 3, 6, 11, 7, 1, 8, 0, 9, 2, 10, 4]
1903 [5, 3, 6, 11, 7, 1, 8, 0, 9, 4, 10, 2]
1904 [5, 3, 6, 11, 7, 1, 8, 2, 9, 0, 10, 4]
1905 [5, 3, 6, 11, 7, 1, 8, 2, 9, 4, 10, 0]
1906 [5, 3, 6, 11, 7, 1, 8, 4, 9, 0, 10, 2]
1907 [5, 3, 6, 11, 7, 1, 8, 4, 9, 2, 10, 0]
1908 [5, 3, 6, 11, 7, 2, 8, 0, 9, 1, 10, 4]
1909 [5, 3, 6, 11, 7, 2, 8, 0, 9, 4, 10, 1]
1910 [5, 3, 6, 11, 7, 2, 8, 1, 9, 0, 10, 4]
1911 [5, 3, 6, 11, 7, 2, 8, 1, 9, 4, 10, 0]
1912 [5, 3, 6, 11, 7, 2, 8, 4, 9, 0, 10, 1]
1913 [5, 3, 6, 11, 7, 2, 8, 4, 9, 1, 10, 0]
1914 [5, 3, 6, 11, 7, 4, 8, 0, 9, 1, 10, 2]
1915 [5, 3, 6, 11, 7, 4, 8, 0, 9, 2, 10, 1]
1916 [5, 3, 6, 11, 7, 4, 8, 1, 9, 0, 10, 2]
1917 [5, 3, 6, 11, 7, 4, 8, 1, 9, 2, 10, 0]
1918 [5, 3, 6, 11, 7, 4, 8, 2, 9, 0, 10, 1]
1919 [5, 3, 6, 11, 7, 4, 8, 2, 9, 1, 10, 0]
1920 [5, 4, 6, 0, 7, 1, 8, 2, 9, 3, 10, 11]
1921 [5, 4, 6, 0, 7, 1, 8, 2, 9, 11, 10, 3]
1922 [5, 4, 6, 0, 7, 1, 8, 3, 9, 2, 10, 11]
1923 [5, 4, 6, 0, 7, 1, 8, 3, 9, 11, 10, 2]
1924 [5, 4, 6, 0, 7, 1, 8, 11, 9, 2, 10, 3]
1925 [5, 4, 6, 0, 7, 1, 8, 11, 9, 3, 10, 2]
1926 [5, 4, 6, 0, 7, 2, 8, 1, 9, 3, 10, 11]
1927 [5, 4, 6, 0, 7, 2, 8, 1, 9, 11, 10, 3]
1928 [5, 4, 6, 0, 7, 2, 8, 3, 9, 1, 10, 11]
1929 [5, 4, 6, 0, 7, 2, 8, 3, 9, 11, 10, 1]
1930 [5, 4, 6, 0, 7, 2, 8, 11, 9, 1, 10, 3]
1931 [5, 4, 6, 0, 7, 2, 8, 11, 9, 3, 10, 1]
1932 [5, 4, 6, 0, 7, 3, 8, 1, 9, 2, 10, 11]
1933 [5, 4, 6, 0, 7, 3, 8, 1, 9, 11, 10, 2]
1934 [5, 4, 6, 0, 7, 3, 8, 2, 9, 1, 10, 11]
1935 [5, 4, 6, 0, 7, 3, 8, 2, 9, 11, 10, 1]
1936 [5, 4, 6, 0, 7, 3, 8, 11, 9, 1, 10, 2]
1937 [5, 4, 6, 0, 7, 3, 8, 11, 9, 2, 10, 1]
1938 [5, 4, 6, 0, 7, 11, 8, 1, 9, 2, 10, 3]
1939 [5, 4, 6, 0, 7, 11, 8, 1, 9, 3, 10, 2]
1940 [5, 4, 6, 0, 7, 11, 8, 2, 9, 1, 10, 3]
1941 [5, 4, 6, 0, 7, 11, 8, 2, 9, 3, 10, 1]
1942 [5, 4, 6, 0, 7, 11, 8, 3, 9, 1, 10, 2]
1943 [5, 4, 6, 0, 7, 11, 8, 3, 9, 2, 10, 1]
1944 [5, 4, 6, 1, 7, 0, 8, 2, 9, 3, 10, 11]
1945 [5, 4, 6, 1, 7, 0, 8, 2, 9, 11, 10, 3]
1946 [5, 4, 6, 1, 7, 0, 8, 3, 9, 2, 10, 11]
1947 [5, 4, 6, 1, 7, 0, 8, 3, 9, 11, 10, 2]
1948 [5, 4, 6, 1, 7, 0, 8, 11, 9, 2, 10, 3]
1949 [5, 4, 6, 1, 7, 0, 8, 11, 9, 3, 10, 2]
1950 [5, 4, 6, 1, 7, 2, 8, 0, 9, 3, 10, 11]
1951 [5, 4, 6, 1, 7, 2, 8, 0, 9, 11, 10, 3]
1952 [5, 4, 6, 1, 7, 2, 8, 3, 9, 0, 10, 11]
1953 [5, 4, 6, 1, 7, 2, 8, 3, 9, 11, 10, 0]
1954 [5, 4, 6, 1, 7, 2, 8, 11, 9, 0, 10, 3]
1955 [5, 4, 6, 1, 7, 2, 8, 11, 9, 3, 10, 0]
1956 [5, 4, 6, 1, 7, 3, 8, 0, 9, 2, 10, 11]
1957 [5, 4, 6, 1, 7, 3, 8, 0, 9, 11, 10, 2]
1958 [5, 4, 6, 1, 7, 3, 8, 2, 9, 0, 10, 11]
1959 [5, 4, 6, 1, 7, 3, 8, 2, 9, 11, 10, 0]
1960 [5, 4, 6, 1, 7, 3, 8, 11, 9, 0, 10, 2]
1961 [5, 4, 6, 1, 7, 3, 8, 11, 9, 2, 10, 0]
1962 [5, 4, 6, 1, 7, 11, 8, 0, 9, 2, 10, 3]
1963 [5, 4, 6, 1, 7, 11, 8, 0, 9, 3, 10, 2]
1964 [5, 4, 6, 1, 7, 11, 8, 2, 9, 0, 10, 3]
1965 [5, 4, 6, 1, 7, 11, 8, 2, 9, 3, 10, 0]
1966 [5, 4, 6, 1, 7, 11, 8, 3, 9, 0, 10, 2]
1967 [5, 4, 6, 1, 7, 11, 8, 3, 9, 2, 10, 0]
1968 [5, 4, 6, 2, 7, 0, 8, 1, 9, 3, 10, 11]
1969 [5, 4, 6, 2, 7, 0, 8, 1, 9, 11, 10, 3]
1970 [5, 4, 6, 2, 7, 0, 8, 3, 9, 1, 10, 11]
1971 [5, 4, 6, 2, 7, 0, 8, 3, 9, 11, 10, 1]
1972 [5, 4, 6, 2, 7, 0, 8, 11, 9, 1, 10, 3]
1973 [5, 4, 6, 2, 7, 0, 8, 11, 9, 3, 10, 1]
1974 [5, 4, 6, 2, 7, 1, 8, 0, 9, 3, 10, 11]
1975 [5, 4, 6, 2, 7, 1, 8, 0, 9, 11, 10, 3]
1976 [5, 4, 6, 2, 7, 1, 8, 3, 9, 0, 10, 11]
1977 [5, 4, 6, 2, 7, 1, 8, 3, 9, 11, 10, 0]
1978 [5, 4, 6, 2, 7, 1, 8, 11, 9, 0, 10, 3]
1979 [5, 4, 6, 2, 7, 1, 8, 11, 9, 3, 10, 0]
1980 [5, 4, 6, 2, 7, 3, 8, 0, 9, 1, 10, 11]
1981 [5, 4, 6, 2, 7, 3, 8, 0, 9, 11, 10, 1]
1982 [5, 4, 6, 2, 7, 3, 8, 1, 9, 0, 10, 11]
1983 [5, 4, 6, 2, 7, 3, 8, 1, 9, 11, 10, 0]
1984 [5, 4, 6, 2, 7, 3, 8, 11, 9, 0, 10, 1]
1985 [5, 4, 6, 2, 7, 3, 8, 11, 9, 1, 10, 0]
1986 [5, 4, 6, 2, 7, 11, 8, 0, 9, 1, 10, 3]
1987 [5, 4, 6, 2, 7, 11, 8, 0, 9, 3, 10, 1]
1988 [5, 4, 6, 2, 7, 11, 8, 1, 9, 0, 10, 3]
1989 [5, 4, 6, 2, 7, 11, 8, 1, 9, 3, 10, 0]
1990 [5, 4, 6, 2, 7, 11, 8, 3, 9, 0, 10, 1]
1991 [5, 4, 6, 2, 7, 11, 8, 3, 9, 1, 10, 0]
1992 [5, 4, 6, 3, 7, 0, 8, 1, 9, 2, 10, 11]
1993 [5, 4, 6, 3, 7, 0, 8, 1, 9, 11, 10, 2]
1994 [5, 4, 6, 3, 7, 0, 8, 2, 9, 1, 10, 11]
1995 [5, 4, 6, 3, 7, 0, 8, 2, 9, 11, 10, 1]
1996 [5, 4, 6, 3, 7, 0, 8, 11, 9, 1, 10, 2]
1997 [5, 4, 6, 3, 7, 0, 8, 11, 9, 2, 10, 1]
1998 [5, 4, 6, 3, 7, 1, 8, 0, 9, 2, 10, 11]
1999 [5, 4, 6, 3, 7, 1, 8, 0, 9, 11, 10, 2]
2000 [5, 4, 6, 3, 7, 1, 8, 2, 9, 0, 10, 11]
2001 [5, 4, 6, 3, 7, 1, 8, 2, 9, 11, 10, 0]
2002 [5, 4, 6, 3, 7, 1, 8, 11, 9, 0, 10, 2]
2003 [5, 4, 6, 3, 7, 1, 8, 11, 9, 2, 10, 0]
2004 [5, 4, 6, 3, 7, 2, 8, 0, 9, 1, 10, 11]
2005 [5, 4, 6, 3, 7, 2, 8, 0, 9, 11, 10, 1]
2006 [5, 4, 6, 3, 7, 2, 8, 1, 9, 0, 10, 11]
2007 [5, 4, 6, 3, 7, 2, 8, 1, 9, 11, 10, 0]
2008 [5, 4, 6, 3, 7, 2, 8, 11, 9, 0, 10, 1]
2009 [5, 4, 6, 3, 7, 2, 8, 11, 9, 1, 10, 0]
2010 [5, 4, 6, 3, 7, 11, 8, 0, 9, 1, 10, 2]
2011 [5, 4, 6, 3, 7, 11, 8, 0, 9, 2, 10, 1]
2012 [5, 4, 6, 3, 7, 11, 8, 1, 9, 0, 10, 2]
2013 [5, 4, 6, 3, 7, 11, 8, 1, 9, 2, 10, 0]
2014 [5, 4, 6, 3, 7, 11, 8, 2, 9, 0, 10, 1]
2015 [5, 4, 6, 3, 7, 11, 8, 2, 9, 1, 10, 0]
2016 [5, 4, 6, 11, 7, 0, 8, 1, 9, 2, 10, 3]
2017 [5, 4, 6, 11, 7, 0, 8, 1, 9, 3, 10, 2]
2018 [5, 4, 6, 11, 7, 0, 8, 2, 9, 1, 10, 3]
2019 [5, 4, 6, 11, 7, 0, 8, 2, 9, 3, 10, 1]
2020 [5, 4, 6, 11, 7, 0, 8, 3, 9, 1, 10, 2]
2021 [5, 4, 6, 11, 7, 0, 8, 3, 9, 2, 10, 1]
2022 [5, 4, 6, 11, 7, 1, 8, 0, 9, 2, 10, 3]
2023 [5, 4, 6, 11, 7, 1, 8, 0, 9, 3, 10, 2]
2024 [5, 4, 6, 11, 7, 1, 8, 2, 9, 0, 10, 3]
2025 [5, 4, 6, 11, 7, 1, 8, 2, 9, 3, 10, 0]
2026 [5, 4, 6, 11, 7, 1, 8, 3, 9, 0, 10, 2]
2027 [5, 4, 6, 11, 7, 1, 8, 3, 9, 2, 10, 0]
2028 [5, 4, 6, 11, 7, 2, 8, 0, 9, 1, 10, 3]
2029 [5, 4, 6, 11, 7, 2, 8, 0, 9, 3, 10, 1]
2030 [5, 4, 6, 11, 7, 2, 8, 1, 9, 0, 10, 3]
2031 [5, 4, 6, 11, 7, 2, 8, 1, 9, 3, 10, 0]
2032 [5, 4, 6, 11, 7, 2, 8, 3, 9, 0, 10, 1]
2033 [5, 4, 6, 11, 7, 2, 8, 3, 9, 1, 10, 0]
2034 [5, 4, 6, 11, 7, 3, 8, 0, 9, 1, 10, 2]
2035 [5, 4, 6, 11, 7, 3, 8, 0, 9, 2, 10, 1]
2036 [5, 4, 6, 11, 7, 3, 8, 1, 9, 0, 10, 2]
2037 [5, 4, 6, 11, 7, 3, 8, 1, 9, 2, 10, 0]
2038 [5, 4, 6, 11, 7, 3, 8, 2, 9, 0, 10, 1]
2039 [5, 4, 6, 11, 7, 3, 8, 2, 9, 1, 10, 0]
2040 [5, 11, 6, 0, 7, 1, 8, 2, 9, 3, 10, 4]
2041 [5, 11, 6, 0, 7, 1, 8, 2, 9, 4, 10, 3]
2042 [5, 11, 6, 0, 7, 1, 8, 3, 9, 2, 10, 4]
2043 [5, 11, 6, 0, 7, 1, 8, 3, 9, 4, 10, 2]
2044 [5, 11, 6, 0, 7, 1, 8, 4, 9, 2, 10, 3]
2045 [5, 11, 6, 0, 7, 1, 8, 4, 9, 3, 10, 2]
2046 [5, 11, 6, 0, 7, 2, 8, 1, 9, 3, 10, 4]
2047 [5, 11, 6, 0, 7, 2, 8, 1, 9, 4, 10, 3]
2048 [5, 11, 6, 0, 7, 2, 8, 3, 9, 1, 10, 4]
2049 [5, 11, 6, 0, 7, 2, 8, 3, 9, 4, 10, 1]
2050 [5, 11, 6, 0, 7, 2, 8, 4, 9, 1, 10, 3]
2051 [5, 11, 6, 0, 7, 2, 8, 4, 9, 3, 10, 1]
2052 [5, 11, 6, 0, 7, 3, 8, 1, 9, 2, 10, 4]
2053 [5, 11, 6, 0, 7, 3, 8, 1, 9, 4, 10, 2]
2054 [5, 11, 6, 0, 7, 3, 8, 2, 9, 1, 10, 4]
2055 [5, 11, 6, 0, 7, 3, 8, 2, 9, 4, 10, 1]
2056 [5, 11, 6, 0, 7, 3, 8, 4, 9, 1, 10, 2]
2057 [5, 11, 6, 0, 7, 3, 8, 4, 9, 2, 10, 1]
2058 [5, 11, 6, 0, 7, 4, 8, 1, 9, 2, 10, 3]
2059 [5, 11, 6, 0, 7, 4, 8, 1, 9, 3, 10, 2]
2060 [5, 11, 6, 0, 7, 4, 8, 2, 9, 1, 10, 3]
2061 [5, 11, 6, 0, 7, 4, 8, 2, 9, 3, 10, 1]
2062 [5, 11, 6, 0, 7, 4, 8, 3, 9, 1, 10, 2]
2063 [5, 11, 6, 0, 7, 4, 8, 3, 9, 2, 10, 1]
2064 [5, 11, 6, 1, 7, 0, 8, 2, 9, 3, 10, 4]
2065 [5, 11, 6, 1, 7, 0, 8, 2, 9, 4, 10, 3]
2066 [5, 11, 6, 1, 7, 0, 8, 3, 9, 2, 10, 4]
2067 [5, 11, 6, 1, 7, 0, 8, 3, 9, 4, 10, 2]
2068 [5, 11, 6, 1, 7, 0, 8, 4, 9, 2, 10, 3]
2069 [5, 11, 6, 1, 7, 0, 8, 4, 9, 3, 10, 2]
2070 [5, 11, 6, 1, 7, 2, 8, 0, 9, 3, 10, 4]
2071 [5, 11, 6, 1, 7, 2, 8, 0, 9, 4, 10, 3]
2072 [5, 11, 6, 1, 7, 2, 8, 3, 9, 0, 10, 4]
2073 [5, 11, 6, 1, 7, 2, 8, 3, 9, 4, 10, 0]
2074 [5, 11, 6, 1, 7, 2, 8, 4, 9, 0, 10, 3]
2075 [5, 11, 6, 1, 7, 2, 8, 4, 9, 3, 10, 0]
2076 [5, 11, 6, 1, 7, 3, 8, 0, 9, 2, 10, 4]
2077 [5, 11, 6, 1, 7, 3, 8, 0, 9, 4, 10, 2]
2078 [5, 11, 6, 1, 7, 3, 8, 2, 9, 0, 10, 4]
2079 [5, 11, 6, 1, 7, 3, 8, 2, 9, 4, 10, 0]
2080 [5, 11, 6, 1, 7, 3, 8, 4, 9, 0, 10, 2]
2081 [5, 11, 6, 1, 7, 3, 8, 4, 9, 2, 10, 0]
2082 [5, 11, 6, 1, 7, 4, 8, 0, 9, 2, 10, 3]
2083 [5, 11, 6, 1, 7, 4, 8, 0, 9, 3, 10, 2]
2084 [5, 11, 6, 1, 7, 4, 8, 2, 9, 0, 10, 3]
2085 [5, 11, 6, 1, 7, 4, 8, 2, 9, 3, 10, 0]
2086 [5, 11, 6, 1, 7, 4, 8, 3, 9, 0, 10, 2]
2087 [5, 11, 6, 1, 7, 4, 8, 3, 9, 2, 10, 0]
2088 [5, 11, 6, 2, 7, 0, 8, 1, 9, 3, 10, 4]
2089 [5, 11, 6, 2, 7, 0, 8, 1, 9, 4, 10, 3]
2090 [5, 11, 6, 2, 7, 0, 8, 3, 9, 1, 10, 4]
2091 [5, 11, 6, 2, 7, 0, 8, 3, 9, 4, 10, 1]
2092 [5, 11, 6, 2, 7, 0, 8, 4, 9, 1, 10, 3]
2093 [5, 11, 6, 2, 7, 0, 8, 4, 9, 3, 10, 1]
2094 [5, 11, 6, 2, 7, 1, 8, 0, 9, 3, 10, 4]
2095 [5, 11, 6, 2, 7, 1, 8, 0, 9, 4, 10, 3]
2096 [5, 11, 6, 2, 7, 1, 8, 3, 9, 0, 10, 4]
2097 [5, 11, 6, 2, 7, 1, 8, 3, 9, 4, 10, 0]
2098 [5, 11, 6, 2, 7, 1, 8, 4, 9, 0, 10, 3]
2099 [5, 11, 6, 2, 7, 1, 8, 4, 9, 3, 10, 0]
2100 [5, 11, 6, 2, 7, 3, 8, 0, 9, 1, 10, 4]
2101 [5, 11, 6, 2, 7, 3, 8, 0, 9, 4, 10, 1]
2102 [5, 11, 6, 2, 7, 3, 8, 1, 9, 0, 10, 4]
2103 [5, 11, 6, 2, 7, 3, 8, 1, 9, 4, 10, 0]
2104 [5, 11, 6, 2, 7, 3, 8, 4, 9, 0, 10, 1]
2105 [5, 11, 6, 2, 7, 3, 8, 4, 9, 1, 10, 0]
2106 [5, 11, 6, 2, 7, 4, 8, 0, 9, 1, 10, 3]
2107 [5, 11, 6, 2, 7, 4, 8, 0, 9, 3, 10, 1]
2108 [5, 11, 6, 2, 7, 4, 8, 1, 9, 0, 10, 3]
2109 [5, 11, 6, 2, 7, 4, 8, 1, 9, 3, 10, 0]
2110 [5, 11, 6, 2, 7, 4, 8, 3, 9, 0, 10, 1]
2111 [5, 11, 6, 2, 7, 4, 8, 3, 9, 1, 10, 0]
2112 [5, 11, 6, 3, 7, 0, 8, 1, 9, 2, 10, 4]
2113 [5, 11, 6, 3, 7, 0, 8, 1, 9, 4, 10, 2]
2114 [5, 11, 6, 3, 7, 0, 8, 2, 9, 1, 10, 4]
2115 [5, 11, 6, 3, 7, 0, 8, 2, 9, 4, 10, 1]
2116 [5, 11, 6, 3, 7, 0, 8, 4, 9, 1, 10, 2]
2117 [5, 11, 6, 3, 7, 0, 8, 4, 9, 2, 10, 1]
2118 [5, 11, 6, 3, 7, 1, 8, 0, 9, 2, 10, 4]
2119 [5, 11, 6, 3, 7, 1, 8, 0, 9, 4, 10, 2]
2120 [5, 11, 6, 3, 7, 1, 8, 2, 9, 0, 10, 4]
2121 [5, 11, 6, 3, 7, 1, 8, 2, 9, 4, 10, 0]
2122 [5, 11, 6, 3, 7, 1, 8, 4, 9, 0, 10, 2]
2123 [5, 11, 6, 3, 7, 1, 8, 4, 9, 2, 10, 0]
2124 [5, 11, 6, 3, 7, 2, 8, 0, 9, 1, 10, 4]
2125 [5, 11, 6, 3, 7, 2, 8, 0, 9, 4, 10, 1]
2126 [5, 11, 6, 3, 7, 2, 8, 1, 9, 0, 10, 4]
2127 [5, 11, 6, 3, 7, 2, 8, 1, 9, 4, 10, 0]
2128 [5, 11, 6, 3, 7, 2, 8, 4, 9, 0, 10, 1]
2129 [5, 11, 6, 3, 7, 2, 8, 4, 9, 1, 10, 0]
2130 [5, 11, 6, 3, 7, 4, 8, 0, 9, 1, 10, 2]
2131 [5, 11, 6, 3, 7, 4, 8, 0, 9, 2, 10, 1]
2132 [5, 11, 6, 3, 7, 4, 8, 1, 9, 0, 10, 2]
2133 [5, 11, 6, 3, 7, 4, 8, 1, 9, 2, 10, 0]
2134 [5, 11, 6, 3, 7, 4, 8, 2, 9, 0, 10, 1]
2135 [5, 11, 6, 3, 7, 4, 8, 2, 9, 1, 10, 0]
2136 [5, 11, 6, 4, 7, 0, 8, 1, 9, 2, 10, 3]
2137 [5, 11, 6, 4, 7, 0, 8, 1, 9, 3, 10, 2]
2138 [5, 11, 6, 4, 7, 0, 8, 2, 9, 1, 10, 3]
2139 [5, 11, 6, 4, 7, 0, 8, 2, 9, 3, 10, 1]
2140 [5, 11, 6, 4, 7, 0, 8, 3, 9, 1, 10, 2]
2141 [5, 11, 6, 4, 7, 0, 8, 3, 9, 2, 10, 1]
2142 [5, 11, 6, 4, 7, 1, 8, 0, 9, 2, 10, 3]
2143 [5, 11, 6, 4, 7, 1, 8, 0, 9, 3, 10, 2]
2144 [5, 11, 6, 4, 7, 1, 8, 2, 9, 0, 10, 3]
2145 [5, 11, 6, 4, 7, 1, 8, 2, 9, 3, 10, 0]
2146 [5, 11, 6, 4, 7, 1, 8, 3, 9, 0, 10, 2]
2147 [5, 11, 6, 4, 7, 1, 8, 3, 9, 2, 10, 0]
2148 [5, 11, 6, 4, 7, 2, 8, 0, 9, 1, 10, 3]
2149 [5, 11, 6, 4, 7, 2, 8, 0, 9, 3, 10, 1]
2150 [5, 11, 6, 4, 7, 2, 8, 1, 9, 0, 10, 3]
2151 [5, 11, 6, 4, 7, 2, 8, 1, 9, 3, 10, 0]
2152 [5, 11, 6, 4, 7, 2, 8, 3, 9, 0, 10, 1]
2153 [5, 11, 6, 4, 7, 2, 8, 3, 9, 1, 10, 0]
2154 [5, 11, 6, 4, 7, 3, 8, 0, 9, 1, 10, 2]
2155 [5, 11, 6, 4, 7, 3, 8, 0, 9, 2, 10, 1]
2156 [5, 11, 6, 4, 7, 3, 8, 1, 9, 0, 10, 2]
2157 [5, 11, 6, 4, 7, 3, 8, 1, 9, 2, 10, 0]
2158 [5, 11, 6, 4, 7, 3, 8, 2, 9, 0, 10, 1]
2159 [5, 11, 6, 4, 7, 3, 8, 2, 9, 1, 10, 0]

```

Note that there are 2160 permutations that satisfy these rules, instead of the 12! total permutations we'd generate without rules.  Running time with n=12 is under 1 second.


Obviously the big drawback here is that I have zero way of dynamically changing the rules, nor have I defined mechanism that would allow one to define rules in an external file.

Issue #1 could be trivially resolved by simply passing the checkRules function as a parameter to genPermutation.  That way you'd use the same algorithm to generate permutations with different rules by simply passing in a different parameter.

Issue #2 is tricker, and I'm far too tired to create a parser that would allow the user to create a set of m rules.  Just write your own rule-checking function that checks for whatever rules you happen to think are important, and pass that function in as a parameter (after the fix for issue #1 is implemented).

---

