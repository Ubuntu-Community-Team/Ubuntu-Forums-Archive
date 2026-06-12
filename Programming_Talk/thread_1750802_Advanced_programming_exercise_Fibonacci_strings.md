---
title: "Advanced programming exercise: Fibonacci strings"
date: 2011-05-05
forum: Programming Talk
---

### Post by slavik on 2011-05-05
Source: Below is a problem which originates from uva.onlinejudge.com (I can tell based on how the problem definition is presented). Source where I saw it will be revealed next week on Sunday. Since this is the first problem of the series, you have an extra 3 days to work on it.

Remember: The input can be coded as you feel like (you do not have to adhere to the problem guidelines). Same for the output.

Everyone knows the fibonacci sequence (1,1,2,3,5,8,13,21,34,..). Now if we overload addition to be concatenation for strings, things can get interesting.

**EDIT: to make things more interesting, you have to indicate which string (first or second) and the index in that string where the target character is**

> A sequence of strings is generated as follows: the first two strings are given and each successive string is made by joining together the previous two strings (in their original order). For example, if the first string is abc and the second string is cde, the third string will be abccde and the fourth will be cdeabccde. The task for this question is to determine the ith character in the sequence of strings (not the ith string). In the previous example the 2nd character is b, the 5th is d, as is the 11th. The 13th character, which happens to be the 1st character of the 4th term, is c.
**Input**

The first line will contain the first string, of between 1 and 10 characters, using lower case letters. The second line will contain the second string, again between 1 and 10 lower case letters. The third line will be a single integer i (1 <= i <= 2^30). Please note that there can be any number of sets of input, each consisting of the specified three lines of input.
Sample input


[FONT="Courier New"]fibonacci
revenge
1000000
[/FONT]

**Output**

Output the ith character in each input sequence, separated by lines.
Sample output


[FONT="Courier New"]e[/FONT]


---

### Post by krazyd on 2011-05-06
Interesting challenge.

I initially coded a solution which gives the string and index of the character within that string, but runs out of memory in a worst-case scenario of two single-letter words and the 2^30th character.

By throwing away the extra information, I got a version which "only" uses a peak of ~500MiB on my machine, and gives reasonable performance:
```
$ time ./fib_strings.rb fibonacci revenge 1000000

"e" found in iteration stage 24 of the sequence.

real    0m0.019s
user    0m0.000s
sys     0m0.010s
```

```
$ time ./fib_strings.rb fibonacci revenge 1073741824

"r" found in iteration stage 38 of the sequence.

real    0m1.243s
user    0m0.660s
sys     0m0.570s
```

```
$ time ./fib_strings.rb f r 1073741824

"r" found in iteration stage 42 of the sequence.

real    0m1.109s
user    0m0.580s
sys     0m0.520s
```

Note: this takes three command line inputs: word1, word2, number, and outputs to stdout. There is no multiple-inputs as in the original question.

[PHP]#!/usr/bin/ruby

class FibString

    attr_accessor :stages, :length, :num_stages

    def initialize(string0, string1)
        @stages = [string0, string1]
        @length = string0.length + string1.length
        @last_stage_index = 1
    end

    def increment
        @stages[0],@stages[1] = @stages[1],@stages[0]+@stages[1]
        @length += @stages[1].length
        @last_stage_index += 1
    end

    def get_character(index)

        case index
        when 0..(@stages[0].length-1)
            containing_stage = 0
            index_in_stage = index
            return [@stages[0][index_in_stage],containing_stage]
        when (@stages[0].length)..(@stages[0].length + @stages[1].length - 1)
            containing_stage = 1
            index_in_stage = index - @stages[0].length
        else
            until @length-1 >= index do                                                                        
                increment()                                                                                    
            end                                                                                                
            containing_stage = @last_stage_index                                                               
            index_in_stage = index - @length + @stages[1].length                                               
        end                                                                                                    
                                                                                                               
        [@stages[1][index_in_stage],containing_stage]                                                          
    end                                                                                                        
end                                                                                                            
                                                                                                               
target = ARGV[2].to_i - 1                                                                                      
sequence = FibString.new(ARGV[0], ARGV[1])                                                                     
character,stage = sequence.get_character(target)                                                               
                                                                                                               
puts                                                                                                           
puts "\"#{character}\" found in iteration stage #{stage} of the sequence."[/PHP]

---

### Post by StephenF on 2011-05-07
My 0.02 is that the words can be encoded in a single bit. 0 = first word, 1 = second, then you eventually get something like

0, 1, 01, 101, 01101, 10101101, 0110110101101, 101011010110110101101,
0110110101101101011010110110101101....

Once the sequences get unwieldy they can be taken as the root of a new sequence where 0 and 1 encode the last two items of the previous sequence. The sequence strings of 0 and 1 will turn out exactly the same as before so they can be copied rather than generated.

Metadata will need to be stored with each element in the sequence like the number of 0's and 1's up to the current element and within, so each sequence item also has a few 32 bit integers. The idea is to keep enough metadata that the character can be identified.

Treated as orders of magnitude like this the algorithm performance ought to be O(log n), be very fast, and use very little memory.

---

### Post by Arndt on 2011-05-09
With a bit of math, one can do without constructing any strings at all. What's needed are closed form expressions for the number of occurrences of the first string and the second string in string i, respectively, as well as one for the total length up to and including string i.

---

### Post by StephenF on 2011-05-09
> **Arndt said:**
> With a bit of math, one can do without constructing any strings at all. What's needed are closed form expressions for the number of occurrences of the first string and the second string in string i, respectively, as well as one for the total length up to and including string i.
I'm hoping to derive such from my code which is at an advanced stage.

---

### Post by slavik on 2011-05-09
> **Arndt said:**
> With a bit of math, one can do without constructing any strings at all. What's needed are closed form expressions for the number of occurrences of the first string and the second string in string i, respectively, as well as one for the total length up to and including string i.
you're on the right track. I did something similar. except I backtracked from the item in the list which would have the character.

---

### Post by StephenF on 2011-05-09
Competition entry.
```

#! /usr/bin/python2

"""fibstring.py: A fibonnacci string character locator program."""


def fibstring(s1, s2, n):
    n -= 1  # Index from letter number.

    parts = [0, len(s1), len(s1) + len(s2)]
    
    # Make partitions upwards until n is enclosed.
    while n >= parts[2]:
        parts.append(2 * parts[2] - parts.pop(0))
        
    # Make partitions downwards taking n with it.
    while parts[0]:
        if n >= parts[1]:
            n -= parts[2] - parts[1]
        parts.insert(0, 2 * parts[1] - parts.pop())

    # Word and letter counting from zero.
    w = int(n >= parts[1])
    l = n - w * len(s1)
    
    return {"char": (s1, s2)[w][l], "word": w + 1, "letter": l + 1}


if __name__ == "__main__":
    import time
    from sys import argv, stdout
    from functools import partial
    
 
    appname = "fibstring.py"
 
    
    def unit_test(s1, s2, stages, dotrate):
        while 1:
            try:
                print "Unit test on '{0}', '{1}', {2} stages.".format(
                                                    s1, s2, stages)
                print "Ctrl+C to skip."
                print "Building strings."
                test = [s1, s2]
                for i in range(stages):
                    test.append(test[-2] + test[-1])
                test = "".join(test)
                
                print "Checking", len(test), "characters, a single '.'" \
                                    " for every", dotrate, "checked."
                for i in range(len(test)):
                    if fibstring(s1, s2, i + 1)["char"] != test[i]:
                        print "\n*Failed* on character {0}.".format(i + 1)
                        exit(5)
                    if i % dotrate == 0 and i:
                        stdout.write(".")
                        stdout.flush()

            except MemoryError:
                print "Failed with memory error - will try fewer stages."
                if test in locals():
                    del test
                stages -= 1
            except KeyboardInterrupt:
                print " Test cancelled."
                return
            else:
                break

        print "\nTest completed successfully."

    
    def benchmark(s1, s2, stop_pow, step_pow):
        print "Unchecked sweep to 2^{stop_pow} step 2^{step_pow}". \
                            format(stop_pow=stop_pow, step_pow=step_pow),
        print "using '{0}', '{1}'.".format(s1, s2)

        stop = 1 << stop_pow
        step = 1 << step_pow
        
        commenced = time.time()
        for i in range(1, stop, step):
            fibstring(s1, s2, i)
        duration = time.time() - commenced
        
        print "Tested", stop / step, "time", duration
        print "Rate", stop / (step * duration), "per second"


    def user_query(s1, s2, n):
        print "Found character '{char}' of word {word} " \
                    "letter {letter}.".format(**fibstring(s1, s2, n))


    options = { "unittests":
                    { "executor": unit_test,
                      "action":   "unit test",
                      "argtable": (("fibonacci", "revenge", 25, 10000),
                                   ("cheezburger", "lolcat", 20, 5000),
                                   ("tiny", "awholelotbigger", 20, 5000), 
                                   ("shrubbery", "ni", 20, 5000),
                                   ("f", "r", 32, 20000)) },
                "benchmarks":
                    { "executor": benchmark,
                      "action":   "benchmark",
                      "argtable": (("fibonacci", "revenge", 30, 15),
                                   ("f", "r", 30, 15),
                                   ("fibonacci", "revenge", 20, 5),
                                   ("f", "r", 20, 5),
                                   ("massive", "value", 212, 200)) }
    }

    
    def for_all(executor, action, argtable):
        for i, args in enumerate(argtable):
            print "\nRunning {action} {number}".format(action=action,
                                                        number = i + 1)
            executor(*args)


    def main():
        try:
            if len(argv) == 2:
                run = partial(for_all, **options[argv[1]])
            elif len(argv) == 4:
                args = argv[1], argv[2], int(argv[3])
                assert args[2] >= 1, "first valid index at zero."
                run = partial(user_query, *args)
            else:
                raise ValueError("wrong number of args.")
        except Exception:
            print "Usage:", appname, "str:str1 str:str2 int>0:index"
            for key in options:
                print "      ", appname, key
        else:
            run()

    main()

```

---

### Post by Leuchten on 2011-06-30
Here's my entry in Scala (way late I know).

```
import scala.collection.mutable.ArrayBuffer
import scala.util.matching.Regex

object Fibbonacho {
  
  def main(args: Array[String]) {
    def fib(n: Int, s1: String, s2: String):Char = {
      def fibLength(n: Int, buffer: ArrayBuffer[Int]):ArrayBuffer[Int] = {
        return buffer :+ (buffer(n-1) + buffer(n-2))
      }
      
      def findInSequence(size: Int, level: Int, buffer: ArrayBuffer[Int], desired: Int):Boolean = {
        if((buffer(level-2) + size) < desired) 
          return true
        else 
          return false
      }
      
      var buffer = new ArrayBuffer[Int]
      buffer += s1.length()
      buffer += s2.length()
      
      {
        var i = 2;
        var accum = buffer(0) + buffer(1);
        
        while(accum < n) {
          buffer = fibLength(i, buffer)
          i += 1
          accum += buffer(buffer.size-1)
        }
      }
      
      var size = 0
      var level = buffer.size-1
      
      println("Level: " + level)
      println(buffer.size)
      
      val mem0 = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory()
      
      println("Memory Consumed:" + mem0 + " bytes")
      
      {
        var i = 0
	    while(i < level) {
	        size += buffer(i)
	        i += 1
	    }
      }
      
      println("Accum = " + size)
      
      while(level != 0 && level != 1) {
        if(findInSequence(size, level, buffer, n)) {
          level -= 1
          size += buffer(level-1);
        }
        else 
          level -= 2;
      }
      
      val output = if(level == 0) s1 else s2
      
      println(output)
      
      return output(n-size-1);
    }
    
    var s: Array[String] = null
    val regex = """\d+""".r;
    {
      var isInt: Boolean = false;
	    while(s == null || s.size < 3 || !isInt) {
	      var ret = javax.swing.JOptionPane.showInputDialog(null,
	        "Enter the character to find and the fib 0 and 1 strings seperated by commas.");
	      if(ret == null) {
	        return
	      } else {
	        s = ret.split(",")
	        isInt = regex.pattern.matcher(s(0)).matches
	      }
	    }
    }
    
    val n = Integer.parseInt(s(0))
    
    val fin = fib(n, s(1), s(2))
    
    javax.swing.JOptionPane.showMessageDialog(null, fin)
  }

}
```

It seems to use 3 or so MB of ram and gets the result almost instantly.

---

### Post by Bachstelze on 2011-06-30
I can't for the life of me figure out what's wrong with this...

```
#!/usr/bin/env python3

a = "fibonacci" # 9
b = "revenge"   # 7
la = len(a)
lb = len(b)
n = 1000000

# Find which line the nth character first appears on
ls = la + lb
oldls = lb
while ls < n:
    tmp = oldls + ls
    oldls = ls
    ls = tmp

# Solve
while ls >= la + lb:
    oldoldls = ls - oldls
    if n > oldoldls:
        # Character is in second 'part'
        #print(ls, oldoldls, oldls, n, "second")
        n -= oldoldls
        ls = oldls
        oldls = oldoldls
    else:
        # Character is in first 'part'
        #print(ls, oldoldls, oldls, n, "first")
        tmp = oldls - oldoldls
        ls = oldoldls
        oldls = tmp

if ls == la:
    print(a[n-1], n, a)
else:
    print(b[n-1], n, b)


```

---

### Post by slavik on 2011-06-30
I realized that I never posted my solution:

```

/*
 *      fib_fury.c
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

//~ Fibonacci's Fury
//~ 
//~ A sequence of strings is generated as follows: the first two strings are
//~ given and each successive string is made by joining together the previous
//~ two strings (in their original order). For example, if the first string is
//~ abc and the second string is cde, the third string will be abccde and the
//~ fourth will be cdeabccde. The task for this question is to determine the
//~ ith character in the sequence of strings (not the ith string). In the
//~ previous example the 2nd character is b, the 5th is d, as is the 11th. The
//~ 13th character, which happens to be the 1st character of the 4th term, is c.
//~ Input
//~ 
//~ The first line will contain the first string, of between 1 and 10 characters,
//~ using lower case letters. The second line will contain the second string,
//~ again between 1 and 10 lower case letters. The third line will be a single
//~ integer i (1 <= i <= 2^30). Please note that there can be any number of
//~ sets of input, each consisting of the specified three lines of input.
//~ Sample input
//~ 
//~ 
//~ fibonacci
//~ revenge
//~ 1000000
//~ 
//~ 
//~ Output
//~ 
//~ Output the ith character in each input sequence, separated by lines.
//~ Sample output
//~ 
//~ e

//~ this code solves only 1 problem and then exits ... :)

#include <stdio.h>
#include <string.h>

int main(int argc, char** argv)
{
	char input[2][12]={{0}};
	int chnum;		// the place where wanted character appears in a term big enough to have it
	int term;		// counter and also the number of the term+1 where wanted character appears
	int len[50];	// the most number of terms we might ever have is 43 because of the input
					// ranges specified (I tested it), 50 is for "breathing room" :)
	int total=0;	// keep total length of all terms in sequence

	// get the input
	fgets(input[0], 12, stdin);
	fgets(input[1], 12, stdin);
	scanf("%d", &chnum);

	// remove the newlines from input
	input[0][strlen(input[0])-1] = input[1][strlen(input[1])-1] = '\0';

	// set the first 2 term lengths
	len[0] = strlen(input[0]);
	len[1] = strlen(input[1]);

	// fill in the rest of the term lengths
	for(term = 2; term < 50; term++) len[term] = len[term-1] + len[term-2];

	// find the term where our wanted character is
	for(term = 0; total < chnum; ++term) {
		total += len[term];
	}
	
	// calculate the position of the character in the term where it appears
	chnum -= total - len[term];
	
	// now we need to find the actual character ...
	// this is the holy grail of logic ;)
	// this is the part that took me some time to figure out
	while(term != 0 && term != 1) {
		if(chnum > len[term-2]) {
			chnum -= len[term-2];
			term--;
		}
		else {
			term -= 2;
		}
	}

	printf("%c %d %d\n", input[term][chnum-1], term, chnum-1);
	
	return 0;
}

```

---

### Post by zobayer1 on 2011-07-01
Can you give the problem number? I was a regular solver there 2 years ago...

---

### Post by zobayer1 on 2011-07-01
You can also try this one, I solved it during the last contest, pretty easy though.
[http://uva.onlinejudge.org/external/120/12041.html](http://uva.onlinejudge.org/external/120/12041.html)

And for uva problems, it is pointless to write solutions using languages other than C/C++/Java/Pascal cause you can never test whether they are correct or not. Trust me, solutions have many bugs even though they look or sound ok :)

---

### Post by slavik on 2011-07-01
The problem with UVA and the ACM is that you are limited to C/C++/Java/Ada for solutions, this makes simple string manipulation problems tedious to solve.

---

### Post by slavik on 2011-07-01
> **Bachstelze said:**
> I can't for the life of me figure out what's wrong with this...

```
#!/usr/bin/env python3

a = "fibonacci" # 9
b = "revenge"   # 7
la = len(a)
lb = len(b)
n = 1000000

# Find which line the nth character first appears on
ls = la + lb
oldls = lb
while ls < n:
    tmp = oldls + ls
    oldls = ls
    ls = tmp

# Solve
while ls >= la + lb:
    oldoldls = ls - oldls
    if n > oldoldls:
        # Character is in second 'part'
        #print(ls, oldoldls, oldls, n, "second")
        n -= oldoldls
        ls = oldls
        oldls = oldoldls
    else:
        # Character is in first 'part'
        #print(ls, oldoldls, oldls, n, "first")
        tmp = oldls - oldoldls
        ls = oldoldls
        oldls = tmp

if ls == la:
    print(a[n-1], n, a)
else:
    print(b[n-1], n, b)


```
try printing everything out and use a smaller test case, it appears that you are using a similar approach to mine.

---

### Post by zobayer1 on 2011-07-01
> **slavik said:**
> The problem with UVA and the ACM is that you are limited to C/C++/Java/Ada for solutions, this makes simple string manipulation problems tedious to solve.

Haha, if you have a whole library to do string manipulation, then what's the point of solving that one either?

Well, you may like this one, probably you have already met with it, my most favorite one...
[https://www.spoj.pl/](https://www.spoj.pl/)

There are lots of problems and they support lots of languages. However, one still need to be quick and clever enough to complete a task, for example, python would do a math with 1000 digits, but doing so in a naive fashion will surely lead to a "Time Limit Exceed" verdict. The point is, they focus on algorithms, in a language independent way.

---

### Post by slavik on 2011-07-01
> **zobayer1 said:**
> Haha, if you have a whole library to do string manipulation, then what's the point of solving that one either?

Well, you may like this one, probably you have already met with it, my most favorite one...
[https://www.spoj.pl/](https://www.spoj.pl/)

There are lots of problems and they support lots of languages. However, one still need to be quick and clever enough to complete a task, for example, python would do a math with 1000 digits, but doing so in a naive fashion will surely lead to a "Time Limit Exceed" verdict. The point is, they focus on algorithms, in a language independent way.
exactly. :)

look at my solution, no string manipulation. I just figure out which term has the letter we need, then backtrack to the initial string.

---

