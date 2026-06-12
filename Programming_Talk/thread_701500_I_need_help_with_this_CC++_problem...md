---
title: "I need help with this C/C++ problem.."
date: 2008-02-19
forum: Programming Talk
---

### Post by laxmanb on 2008-02-19
I need to do this problem:

>  Fibonacci's Fury

A sequence of strings is generated as follows: the first two strings are given and each successive string is made by joining together the previous two strings (in their original order). For example, if the first string is abc and the second string is cde, the third string will be abccde and the fourth will be cdeabccde. The task for this question is to determine the ith character in the sequence of strings (not the ith string). In the previous example the 2nd character is b, the 5th is d, as is the 11th. The 13th character, which happens to be the 1st character of the 4th term, is c.
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


I can't figure out how to do this!! Fibonacci numbers get so huge so fast that you run out of space very quickly, and so the string lenghts would get too big too handle. Can somebody help me to figure this thing out!

---

### Post by LaRoza on 2008-02-19
[color="red"]Acting as moderator:[/color]
Is this homework? Or something you are doing for fun?

It has all the symptoms of homework, I am closing it. PM if this is not homework.

---

### Post by LaRoza on 2008-02-19
Re-opened, because it isn't homework. 

It sure looks like it though, but it is just an exercise for practicing for an event.

---

### Post by popch on 2008-02-19
> **laxmanb said:**
> (...) Fibonacci numbers get so huge so fast that you run out of space very quickly, and so the string lenghts would get too big too handle. (...)

Actually, the problem is about 'Fibonaccy strings', not 'Fibonacci numbers'. With this kind of tasks, it pays to pick extreme nits.

And then: the string ***lengths ***do not get too big to handle. It's the strings which get too big to handle, i.e. too long. The lengths can be handled just fine.

---

### Post by CptPicard on 2008-02-19
There's a fine line between suggesting approaches to homework (which was acceptable at least when I was a student), and doing it outright.

And this doesn't seem like homework, it has no obvious pedagogical value. It would be too hard for a general programming class assignment.

EDIT: well, actually at least a simple solution is pretty trivial. You just maintain two strings that you sum up as you go as you would in iteratively computing fibonacci numbers, and as you compute the strings, you just subtract from the index the amount of characters you've already bypassed. I have a nagging feeling though that this can be done even smarter as you repeat so much structure inside the strings that end up still being pretty long...

---

### Post by laxmanb on 2008-02-19
> **popch said:**
> Actually, the problem is about 'Fibonaccy strings', not 'Fibonacci numbers'. With this kind of tasks, it pays to pick _extreme nits_.

And then: the string ***lengths ***do not get too big to handle. It's the strings which get too big to handle, i.e. too long. The lengths can be handled just fine.

exteme nits??

---

### Post by popch on 2008-02-19
> **laxmanb said:**
> exteme nits??

Sorry, thtat was not intended to be confusing. I used it conversationally for 'being ext_***r***_emely nit-picking'.

---

### Post by laxmanb on 2008-02-19
> **CptPicard said:**
> There's a fine line between suggesting approaches to homework (which was acceptable at least when I was a student), and doing it outright.

And this doesn't seem like homework, it has no obvious pedagogical value. It would be too hard for a general programming class assignment.

EDIT: well, actually at least a simple solution is pretty trivial. You just maintain two strings that you sum up as you go as you would in iteratively computing fibonacci numbers, and as you compute the strings, you just subtract from the index the amount of characters you've already bypassed. I have a nagging feeling though that this can be done even smarter as you repeat so much structure inside the strings that end up still being pretty long...

I thought it like that as well. But again the strings would get too long, too fast. The compiler we use has a limit of about 9999 as array length. Since the lenghts increase almost exponentially, I would reach that in the 20th iteration.  How will I ever get to the 1000,000th character? I guess would need to use strings to add them up, right??

---

### Post by CptPicard on 2008-02-19
> **laxmanb said:**
> How will I ever get to the 1000,000th character? I guess would need to use strings to add them up, right??

1 000 000th character is still easy, just allocate on the heap instead of the stack...

---

### Post by aks44 on 2008-02-19
Count me in... ;)

There has to be a simple solution (that does not eat all your comp's memory)...

---

### Post by Lster on 2008-02-19
This intrigues me. I'm also trying to find an elegant solution - the only one I can think of is almost identical to CptPicard's.

---

### Post by klytu on 2008-02-19
> **laxmanb said:**
> I need to do this problem:



I can't figure out how to do this!! Fibonacci numbers get so huge so fast that you run out of space very quickly, and so the string lenghts would get too big too handle. Can somebody help me to figure this thing out!

My intuition is that you can do this without too much difficulty by focusing on the ***lengths*** of the original strings.  The lengths of the generated strings would form a fibonacci sequence and the positions of the letters are shifted by amounts in a fibonacci sequence. I think this hint should help you immensely. :-) When I get home, I'm going to try it!

---

### Post by aks44 on 2008-02-19
> **klytu said:**
> My intuition is that you can do this without too much difficulty by focusing on the ***lengths*** of the original strings.  The lengths of the generated strings would form a fibonacci sequence and the positions of the letters are shifted by amounts in a fibonacci sequence. I think this hint should help you immensely. :-) When I get home, I'm going to try it!

Shhhh... you damn idea stealer... ;)

---

### Post by CptPicard on 2008-02-19
Yes, and essentially you might be able to do a kind of "mod-offset" by the length of those strings into your original strings, which, after all, are just stuck one after the other to form the result... like, if you've got "abc" and "def", then your result is composed of those arranged in some order.

Now, the &#8364;1000 question for me is whether you can discard history (the "long tail") from those two strings you would manipulate in the straightforward solution. After all, your too-big strings contain everything that went before, and you're mostly just interested in indexing something at the *end* of the latest result, if your index fits into that newest result. I do fear though that the long string does contain some essential information about the state of the computation...


```


					foo
					 ba
				      fooba
				    bafooba
			       foobabafooba
			bafoobafoobabafooba
	    foobabafoobabafoobafoobabafooba

```

This sort of demonstrates the structure we might want to get rid of... if there was a way to tell how the *head* of the sequence behaves when you've got strings of length of some fibonacci number...

EDIT: My current approach focuses on first finding the term for the series in which our index is located, and let's say this "i" is then the "n:th" character in this term... it should simplify, and you might even be able to work backwards from there in the same way...

---

### Post by laxmanb on 2008-02-19
This question ***seems*** so hard!!!!!!!!!! I still trying to solve it, all I'm getting is my IDE crashing!!

---

### Post by rye_ on 2008-02-19
I'll dedicate the next 20 mins or so having a go.

great fun

---

### Post by pmasiar on 2008-02-19
This is nice task. Solving by brute force is trivial (just get the files), to be safe for  case when it does not fit into RAM. But I have gut feeling there is smarter solution.

BTW if someone is thinking about FAQ thread with tasks to solve, this one is good candidate too.

---

### Post by rye_ on 2008-02-19
OK.

I now wish I'd joined the gnome vs kde thread.

still trying though

---

### Post by aks44 on 2008-02-19
> **CptPicard said:**
> This sort of demonstrates the structure we might want to get rid of... if there was a way to tell how the *head* of the sequence behaves when you've got strings of length of some fibonacci number...

EDIT: My current approach focuses on first finding the term for the series in which our index is located, and let's say this "i" is then the "n:th" character in this term... it should simplify, and you might even be able to work backwards from there in the same way...

I'm also trying this approach. It may help you to use single characters instead of full strings for now (dots are string #1, X's are string #2):
```
                                                                                        .
                                                                                        X
                                                                                       .X
                                                                                      X.X
                                                                                    .XX.X
                                                                                 X.X.XX.X
                                                                            .XX.XX.X.XX.X
                                                                    X.X.XX.X.XX.XX.X.XX.X
                                                       .XX.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.X
                                  X.X.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.X
.XX.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.XX.X.XX.X.XX.XX.X.XX.X
```


Now if we could make sense of that pattern (from right to left, dots are dots, numbers are consecutive X's):
```
.
1
1.
1.1
1.2.
1.2.1.1
1.2.1.2.2.
1.2.1.2.2.1.2.1.1
1.2.1.2.2.1.2.1.2.2.1.2.2.
1.2.1.2.2.1.2.1.2.2.1.2.2.1.2.1.2.2.1.2.1.1
1.2.1.2.2.1.2.1.2.2.1.2.2.1.2.1.2.2.1.2.1.2.2.1.2.2.1.2.1.2.2.1.2.2.
```


EDIT: I know I'm basically saying the same as you did, but the "consecutive X's" approach can greatly simplify the algorithm IMHO...


Or to put it yet another way (pluses denote a trailing dot aka. string #1, numbers still denote consecutive X's (string #2) and they are separated by ONE string #1):
```
+
1
1+
11
12+
1211
12122+
121221211
1212212122122+
1212212122122121221211
1212212122122121221212212212122122+
```

---

### Post by Lster on 2008-02-19
Hmm...

---

### Post by popch on 2008-02-19
As I said in my first post, the problem appears to be about the lengths of the strings and not about the contents, except in a very local manner.

I would think along those lines: 

recursively add up the lengths of the strings you would get if you followed the procedure.
The boundary condition for the recursion is length >= asked position.
A tree structure holding all those lengths could yield the desired result.
On the other hand, backtracking over the computed lengths could provide an easier route to the desired position.
Backtracking is easily accomplished when unwinding the stacked (recursive) function invocations.

From here on, I would have to resort to some pencil and paper to envision the data structures involved. It's been a looong time since I have done anything along those lines.

---

### Post by rye_ on 2008-02-19
me too.

you'll notice;

for i >= 4

term(i) = term(i-2) + term(i-3) + term(i-2)

within the rule applying to each sub term within the above expression

---

### Post by CptPicard on 2008-02-19
Popch, you don't need explicit data structures, just a recursion. You get your tree implicitly. You first go down the construction, end when you've got your index inside one half, and then eventually you end up backing up into a situation where you've got your elementary strings, where you can pick up the character.

You were a bit quicker than I was in explaining ;) Well... let's see if I can come up with an implementation...

---

### Post by laxmanb on 2008-02-19
> **Lster said:**
> Wow, I'm also using similar notation! Haven't got anywhere, though!

EDIT: If you look down you can see "older" patterns in the colors...

I did note that! I can identify the term that contains the ith character easily enough. Now I just need to get to that character somehow.

---

### Post by popch on 2008-02-19
> **CptPicard said:**
> Popch, you don't need explicit data structures, just a recursion. You get your tree implicitly. .

That's a data structure, too, even if most of it is provided for free by the recursion mechanism and lives in the procedure stack.

And it is my working style not to proceed any further until I have a good grasp of the (implied) data structures.

---

### Post by rye_ on 2008-02-19
I struggle to see how a pattern based approach can be used if we cannot accurately predict the length of a term for the higher length terms.

binet's formula is an approximation only, and get's a bit ropey for strings 1000+

I concede defeat for the tonight

---

### Post by CptPicard on 2008-02-19
It's really not about patterns, its about going down the recursion using string lengths, finding on whether you're inside the first or the second term on current level, and then just backtracking in recursion from there... I think popch got it right, I'm trying to code it now... it's frying my brain a little though ;)

---

### Post by laxmanb on 2008-02-19
> **rye_ said:**
> I struggle to see how a pattern based approach can be used if we cannot accurately predict the length of a term for the higher length terms.

binet's formula is an approximation only, and get's a bit ropey for strings 1000+

I concede defeat for the tonight


lenght of a nth (n>3) term: fib(n-2)*strlen(a)+fib(n-1)*strlen(b)

where fib(n) = nth term in fibonacci series : ( 1,1, 2, 3, 5, 8.........)

---

### Post by hod139 on 2008-02-19
> **klytu said:**
> My intuition is that you can do this without too much difficulty by focusing on the ***lengths*** of the original strings.  The lengths of the generated strings would form a fibonacci sequence and the positions of the letters are shifted by amounts in a fibonacci sequence. I think this hint should help you immensely. :-) When I get home, I'm going to try it!

This is some good intuition.  Here is some pseudocode for my solution
Edit: <snip>
I was wrong

---

### Post by Lster on 2008-02-19
How are you all getting on. I'm having difficulties and not really making progress.

CptPicard, good luck with the implementation. :)

---

### Post by aks44 on 2008-02-19
> **Lster said:**
> How are you all getting on.

This sums up my situation:
> **CptPicard said:**
> it's frying my brain;)

---

### Post by Lster on 2008-02-19
And me. But I am a *_little_* further! ;)

---

### Post by CptPicard on 2008-02-19
I must admit that I'm having trouble with the backtracking phase... I have a feeling that I *know* what should happen but not exactly enough to actually express it in code. As popch said, we should

1. Go down generating the sequence until you find a block in which your index is located
2. Pass this index up the chain, chopping the index down to size depending on whether it was on the left or right side of your recursion tree (whether you were in the "first" or "second" sequence member of the  "sum" string)
3. Finally at the end, out comes small number that indexes your original first+second string.

I'm too tired to continue tonight.. good luck :)

---

### Post by Lster on 2008-02-19
Ah, maybe I should sleep in a bit too. For now I continue... :)

---

### Post by aks44 on 2008-02-19
Ok, I'm off for tonight too.

Brain... not... work... :-|

---

### Post by popch on 2008-02-19
OK, my homework is done, and I can spare another quarter of an hour or so. 

```

f    fibonacci(f)
1    1
2    1
3    2
4    3
5    5
6    8
7    13
8    21
9    34
10    55
11    89
12    144
13    233
14    377
15    610
16    987
17    1'597
18    2'584
19    4'181
20    6'765
21    10'946
22    17'711
23    28'657
24    46'368
25    75'025
26    121'393
27    196'418
28    317'811
29    514'229
30    832'040
31    1'346'269

```Lets only consider string lengths. Also let us solve the problem for a subset of the domain first, namely for the case where the fibonacci series of string lengths is ascending only.

The procedure is to find first the smallest number f such that fibonacci(f) >= i, where i is the index of the letter to be returned. We therefore know that fibonacci(f-2) < fibonacci(f-1) < i <= fibonacci(f).

Hence, we can reduce the problem to finding char( i - fibonacci(f-2)), I think. I also think that it should be the same as finding char( i - fibonacci(f-1)). Can anyone prove either case?

Edit: Speaking of actual coding - I think the reduced version of the problem should be solvable while unwinding the stacked procedure calls for the recursive procedure used to find f.

---

### Post by popch on 2008-02-19
> **CptPicard said:**
> 
And this doesn't seem like homework, it has no obvious pedagogical value.

Would you care to come back to that statement? Some members here appear to have found some pedagogical value in it.

:lolflag:

---

### Post by CptPicard on 2008-02-19
> **popch said:**
> Would you care to come back to that statement? Some members here appear to have found some pedagogical value in it.


What I mean is that I wouldn't use this as an exercise illustrating some particular point I would want to communicate if I were teaching. It has no "obvious" pedagogical value as homework, although it is certainly an interesting problem!

> 
The procedure is to find first the smallest number f such that fibonacci(f) >= i, where i is the index of the letter to be returned.


Not sure if this is relevant, but do note that we're not dealing with the usual fibonacci sequence here, but something that starts from the original string lengths.

---

### Post by happysmileman on 2008-02-19
> **pmasiar said:**
> BTW if someone is thinking about FAQ thread with tasks to solve, this one is good candidate too.

FAQ thread with tasks to solve sounds good. I can never seem to find much tasks like this.

Anyone know where to find them? Preferably with easy ones as well as the harder ones, would be a good way to test your knowledge of programming concepts, especially since I can never think of anything to program, or I decide it's too hard/big and give up

---

### Post by popch on 2008-02-19
> **CptPicard said:**
> What I mean is that I wouldn't use this as an exercise illustrating some particular point I would want to communicate if I were teaching. It has no "obvious" pedagogical value as homework, although it is certainly an interesting problem!

OK. Finding the way how to solve it at all has been more prominent than writing a program. Despite the title of the thread, not much has been said about C/C++.

> **CptPicard said:**
> Not sure if this is relevant, but do note that we're not dealing with the usual fibonacci sequence here, but something that starts from the original string lengths.

It is relevant, but not much. Refer to my post which demands that the sequence be ascending (monotonously is the term I want, I believe). Otherwise, the algorithm will break when you are in the first pair of strings, i.e. at f=1 and f=2. Other than that, you are quite free to choose initial numbers, provided they are strictly positive.

The numbers I provided are quickly generated with a spreadsheet program. Therefore you can easily run a few test cases.

---

### Post by slavik on 2008-02-19
this is what I got so far ... it finds the term in which to look for the character

```

#include <stdio.h>
#include <string.h>

int calc(char *one, char *two, int len_one, int len_two, int chnum, int seq) {
	if (chnum <= len_one) {
		return seq;
	}
	else if (chnum <= (len_one+len_two)) {
		return (seq+2);
	}

	return calc(one, two, len_two, len_one+len_two, chnum, seq+1);
}

int main(int argc, char** argv)
{
	char one[12]={0};
	char two[12]={0};
	int chnum;

	fgets(one, 11, stdin);
	fgets(two, 11, stdin);
	scanf("%d", &chnum);

	two[strlen(two)-1] = one[strlen(one)-1] = '\0';

	printf("%d\n",calc(one, two, strlen(one), strlen(two), chnum, 1));
	return 0;
}
```

EDIT: Another thing I noticed is that in the fibonacci number sequence, the nth terms gives us the number of strings (from the original two) in the nth string term ...

---

### Post by pmasiar on 2008-02-19
> **happysmileman said:**
> FAQ thread with tasks to solve sounds good. I can never seem to find much tasks like this.

Anyone know where to find them? Preferably with easy ones as well as the harder ones, would be a good way to test your knowledge of programming concepts, especially since I can never think of anything to program, or I decide it's too hard/big and give up

I collected bunch of task to solve in wiki (in my sig), so please look and pick. Seems you are math inclined, ProjectEuler might serve you well.

---

### Post by happysmileman on 2008-02-19
> **pmasiar said:**
> I collected bunch of task to solve in wiki (in my sig), so please look and pick. Seems you are math inclined, ProjectEuler might serve you well.

Looking now, and yeah I've done about 20 of the ones on ProjectEuler, the other ones I either haven't attempted yet or don't understand fully (I've still got another year and a half of secondary school to go :p)

---

### Post by slavik on 2008-02-19
I think I am onto something but dunno if my explanation is sound ...

so you find which term has more characters than the number you are looking for (in the example, term #27 has over a million characters, 26 has under),

pseudo code for my brain :)

start loop:
--if the 'number' within the term is greater than the length of term-2, that means that the character is in term-1 as the (length(term-2))th character.
--otherwise it is the nth character in term-2
end loop

repeat loop until you are looking at term #1 or term #2 ...

now the big question, anyone get it? if so, you owe me a bottle of vodka :D

EDIT: for some reason the example given does not conform to what my code returns, yet with the examples I wrote down on paper (1aa, 2b) it returns proper answers ... could the OP show us where he got this problem and please verify that the output in the example is the letter 'e' or correct as necessary :)

I think I got the problem wrong ... are we supposed to concatenate all the terms together?

---

### Post by slavik on 2008-02-19
> **slavik said:**
> I think I am onto something but dunno if my explanation is sound ...

so you find which term has more characters than the number you are looking for (in the example, term #27 has over a million characters, 26 has under),

pseudo code for my brain :)

start loop:
--if the 'number' within the term is greater than the length of term-2, that means that the character is in term-1 as the (length(term-2))th character.
--otherwise it is the nth character in term-2
end loop

repeat loop until you are looking at term #1 or term #2 ...

now the big question, anyone get it? if so, you owe me a bottle of vodka :D

EDIT: for some reason the example given does not conform to what my code returns, yet with the examples I wrote down on paper (1aa, 2b) it returns proper answers ... could the OP show us where he got this problem and please verify that the output in the example is the letter 'e' or correct as necessary :)

I think I got the problem wrong ... are we supposed to concatenate all the terms together?

Sorry for the bump, just making sure that all people who read my last reply see the new development ...

Here is the solution in C:
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

	printf("%c\n", input[term][chnum-1]);
	
	return 0;
}
```

---

### Post by laxmanb on 2008-02-19
Seems correct. Thanks!

---

### Post by Lux Perpetua on 2008-02-19
I had the same solution as slavik. The time complexity of that algorithm is O(log(k)) (where k is the character position sought), which I think is pretty hard to beat. :-)

---

### Post by Lster on 2008-02-20
I think you solution may have errors in it slavik. I may be wrong but when I compile your program and give it the input:

> a
b
14

it returns:

> a

I don't think this is right, is it?

**EDIT: I was wrong - see later posts and ignore me!** :)

---

### Post by Lster on 2008-02-20
Myself, I have managed to produce an algorithm that computes it in:

> O(n) time
O(n/(a+b)) space

where
	n is the character to be found
	a is the length of the first string
	b is the length of the second string

It was the best I could manage. I've got to test it first, but then I will post it and let you all scrutinize the code. :)

---

### Post by slavik on 2008-02-20
you have to concatenate all the string terms :)

---

### Post by Lster on 2008-02-20
Yes, I know. I still think it's wrong, though. Can you show me the concatenated string please? :)

---

### Post by Lux Perpetua on 2008-02-20
```
a, b, ab, bab, abbab, bababbab
1  2  3   5    8     13
```The fourteenth character is a.

---

### Post by Lster on 2008-02-20
It appears I have been misunderstanding the problem! Thank you!

---

### Post by aks44 on 2008-02-20
> **Lux Perpetua said:**
> ```
a, b, ab, bab, abbab, bababbab
1  2  3   5    8     13
```The fourteenth character is a.

> **Lster said:**
> It appears I have been misunderstanding the problem! Thank you!

Ahem. Same here. :oops:

---

### Post by Lster on 2008-02-20
In our defense, wording was unclear but I'm pleased to solve the other problem. And now to have a go on this one!

---

### Post by Lux Perpetua on 2008-02-20
What problem(s) did you guys end up solving? Do tell.

---

### Post by popch on 2008-02-20
> **Lster said:**
> In our defense, wording was unclear but I'm pleased to solve the other problem. And now to have a go on this one!

The wording is quite clear, once you bother looking at it. The fun part is, I also did not realize that particular specification, not even after suggesting to the OP to take excessive care in reading the specifications. Talk about preaching water and drinking wine.

It just happens that I came back to the thread in order to look at the specifications because I thought it weird that they should go to such length to set up an exercise which does not even have a unique solution.

---

### Post by aks44 on 2008-02-20
> **Lux Perpetua said:**
> What problem(s) did you guys end up solving? Do tell.

As far as I'm concerned: nth character in the first string that has enough characters.

eg:

A, B, 6

A (1 char, continue)
AB (2 chars, continue)
BAB (3 chars, continue)
ABBAB (5 chars, continue)
BABABBAB (8 chars, return 6th char in this string)


And I was wondering why, even with the brute-force approach, I didn't get the same result as the original example. ](*,)

> **popch said:**
> The wording is quite clear, once you bother looking at it.
+1, once you bother... :oops:

---

### Post by Wybiral on 2008-02-20
> **aks44 said:**
> As far as I'm concerned: nth character in the first string that has enough characters.

eg:

A, B, 6

A (1 char, continue)
AB (2 chars, continue)
BAB (3 chars, continue)
ABBAB (5 chars, continue)
BABABBAB (8 chars, return 6th char in this string)




+1, once you bother... :oops:

This was my first impression of the problem too, lol!

---

### Post by Lster on 2008-02-20
[QUOTE=Lux Perpetua]What problem(s) did you guys end up solving? Do tell.[/QUOTE]

The one aks44 posted. :)

[QUOTE=Wybiral]This was my first impression of the problem too, lol![/QUOTE]

[QUOTE=popch]The wording is quite clear, once you bother looking at it. The fun part is, I also did not realize that particular specification, not even after suggesting to the OP to take excessive care in reading the specifications. Talk about preaching water and drinking wine.[/QUOTE]

It is not clear in my opinion; precise, but not clear! ;) Also, I would love a little explanation of your solution. I semi-understand it, but it would be great if you could clarify it! :)

On a side note, we have got to bring back those good old programming challenges! I miss them...

---

### Post by Wybiral on 2008-02-20
> **Lster said:**
> On a side note, we have got to bring back those good old programming challenges! I miss them...

[Done!]("http://ubuntuforums.org/showthread.php?p=4370477")

---

### Post by Lster on 2008-02-20
Brilliant - thanks Wybiral! I will be sure to submit my solution soon! :)

---

### Post by aks44 on 2008-02-21
Since I screwed up with the original question, I decided (in jest) to work on slavik's code in order to make it run in **[SIZE="3"]O(1)[/SIZE]**.

I still have a few issues right now but I'll keep you in touch.

Bonus point for the person who figures out what I'm up to... ;)

---

### Post by Lster on 2008-02-21
That will be hard! Good luck aks44. :)

I too, am obsessed with this problem. I couldn't understand slavik's code so I decided to solve it myself. I arrived at almost identical code. Since then I have also extended it to solve either the problem I was trying to solve, or the original (depending on what is selected).

As for what you're up to, I'm guessing you'll use some weird binary operations and modulus? Do share your idea. :)

---

### Post by aks44 on 2008-02-21
> **Lster said:**
> Do share your idea. :)

Hint: I'm using hod139's (and slavik's) algorithm (not code, mind you) without any modification.

I can't say more without betraying myself. Please bear with me, I want to finish it before speaking about the implementation. :D

---

### Post by Lster on 2008-02-22
Good luck with that. :)

---

### Post by aks44 on 2008-02-22
I was wondering why I was having issues with my tests... then I found that slavik's code has a small error. The error case is when chnum <= len[0].

A quick and dirty workaround is to add this simple test to slavik's code, just after calculating len[0] and len[1]:```
        // ...
	// set the first 2 term lengths
	len[0] = strlen(input[0]);
	len[1] = strlen(input[1]);

        if (chnum <= len[0])
                return input[0][chnum - 1];

	// fill in the rest of the term lengths
        // ...
```

Now my O(1) code is ready, I still have to check it with / port it to g++ though (I'm at work now, and it works with MSVC).
Expect to see some code in 6-7 hours from now when I come back home. :p

---

### Post by Lster on 2008-02-22
I'm waiting in anticipation and a little disbelief. :D

---

### Post by aks44 on 2008-02-22
> **Lster said:**
> I'm waiting in anticipation and a little disbelief. :D

Don't expect too much, it's a shameless cheat (now that it's done I can be honest :p).

---

### Post by Lster on 2008-02-22
Using some kind of precomputed table? I was wondering about this myself. I'll see anyway! :)

---

### Post by aks44 on 2008-02-22
> **Lster said:**
> Using some kind of precomputed table?

To be honest, I thought about a rainbow table too. But even if we found patterns in the results, the whole rainbow table would probably be too large to fit in memory. Using a database would alleviate that restriction though.


But my approach is more straightforward. No need to comment about how it doesn't meet all requirements of the OP, I'm perfectly aware of it. As I said earlier, I made it in jest, just because I could.

The fact is, once it is compiled the program actually runs in O(1).

Well, it was fun to write, and a good refresher for my memory (I don't actually write such insane code usually ;)).

All I hope is that you people will have a good laugh when you see the code... :D


EDIT: a little fix in the code (to avoid a runtime calculation).

EDIT: hmm I forgot (just in case) ... compile and run with
```
$ g++ -o fibofury fibofury.cpp && ./fibofury
```

---

### Post by Lster on 2008-02-22
LOL! Making G++ do the work!

Am I correct? I don't know C++ very well! That is a neat idea, though!

Now my question is: at what complexity does G++ evaluate that?

---

### Post by aks44 on 2008-02-22
> **Lster said:**
> LOL! Making G++ do the work!

Am I correct?
You're perfectly correct. ;)

> **Lster said:**
> Now my question is: at what complexity does G++ evaluate that?

I "ported" slavik's algorithm, so it is the same complexity. Some constants may be greater (I didn't care to factorize) but the whole O(x) is the same: O(log(nthChar)).

You can hardly distinguish compilation time from "normal" algorithm's compilation time (it's just fast enough for us mere humans).

:D


EDIT: as I said, it's a shameless cheat... but quite funny to write ;)

---

### Post by Lster on 2008-02-22
Which makes me wonder... Could the compiler be made to evaluate (at compile time) the solution if you had used the brute-force algorithm? I'm guessing it would try loop unrolling or something and then if it got to the answer, it would simplify it all to just printing that!

---

### Post by aks44 on 2008-02-22
> **Lster said:**
> Which makes me wonder... Could the compiler be made to evaluate (at compile time) the solution if you had used the brute-force algorithm?

Look carefully at the comments in my code... The only "runtime" part that I wrote is actually choosing between string0 and string1, because the compiler can't handle string literals statically.

So the answer is... no ;)

---

### Post by slavik on 2008-02-22
btw, my code can be optimized a bit better ... ie: stop filling in length once you find the term that makes the termcat big enough ...

but my question still remains, anyone understand the last while loop that I do? (it is the main piece of code that solves the problem).

---

### Post by Lster on 2008-02-22
Darn! My plans foiled. Now I'll never take over the world. Except if I go and play Enemy Territory Quake Wars some more! Muahahah! :)

---

### Post by Lster on 2008-02-22
[QUOTE=slavik]but my question still remains, anyone understand the last while loop that I do? (it is the main piece of code that solves the problem).[/QUOTE]

Yes! As I said earlier, I actually came to the same conclusion (and almost the same code!).

...See slavik's post...

---

### Post by slavik on 2008-02-22
> **Lster said:**
> Yes! As I said earlier, I actually came to the same conclusion (and almost the same code!).

But, after you have found the term that the value is in (I call this the line). You find the offset that the character is within that. Then you simply map it to an earlier term and offset, until you arrive on the first or second line.
good, me breaking my brain for 4 hours to get to that point was worth the effort :P

---

### Post by Lster on 2008-02-22
[QUOTE=slavik]good, me breaking my brain for 4 hours to get to that point was worth the effort :P[/QUOTE]

And the brilliant bit is that it is very easy to extend. I've made it solve both problems (the original and the one aks44 and I attempted).

---

### Post by aks44 on 2008-02-22
> **slavik said:**
> my question still remains, anyone understand the last while loop that I do? (it is the main piece of code that solves the problem).

As far as I'm concerned, I had hard time to understand it. TBH I'm not even sure I fully grasp it now.
But I totally suck at maths, so my opinion doesn't really matter. :p

---

### Post by Lux Perpetua on 2008-02-23
I had a feeling it would involve templates. :-)

Here's a further challenge: solve the original problem in **O(1) space**. In other words, you cannot store the lengths in an array. The necessary modification to slavik's code is nontrivial but straightforward. (My C++ solution is 38 lines, including blank lines and no comments.)

[color=red]Edit:[/color] It should still run in **O(log(k))** time, where k is the index of the sought character.

---

### Post by Lster on 2008-02-23
Will do... :)

---

### Post by Lster on 2008-02-23
I simply changed the length array to instead call a function that computes the same thing. Does anyone have a better solution?

---

### Post by aks44 on 2008-02-23
> **Lster said:**
> I simply changed the length array to instead call a function that computes the same thing.

I would do the same.
Or, cheating again, I'll just keep my templates. :p

---

### Post by Lux Perpetua on 2008-02-23
Careful, though, that could increase the time complexity if you do it naively. I should have said that it should still run in **O(log(k))** time (where k is the index of the character sought). If you use slavik's algorithm but replace the length array by a function that takes about log(n) steps to compute the length of string n of the sequence, then during the course of the procedure, you will need to compute 

length(0), length(1), ..., length(approximately log(k)),

so your running time goes up to

log(1) + log(2) + ... + log(log(k)). 

Even without making a very precise estimate of that, that clearly grows faster than log(k) (because you have log(k) terms in the sum). In other words, yes, there is a better solution.

Edit: actually, if you code your length function the most obvious way, it will take about n steps, not log(n) steps, to compute the length of term n of the sequence, so then the running time goes up to 1 + 2 + ... + log(k), which is on the order of log(k)^2.

---

### Post by Lster on 2008-02-23
Do you use something similar to Binet's formula? Is there a way to calculate it in O(1)?

[http://en.wikipedia.org/wiki/Fibonacci_number#Relation_to_the_golden_ratio](http://en.wikipedia.org/wiki/Fibonacci_number#Relation_to_the_golden_ratio)

---

### Post by Lux Perpetua on 2008-02-23
I thought of that. To compute that in O(1), I think you would have to resort to floating-point computation and rounding to integers, but I'm pretty sure that will lead to a solution. There is a Binet-like formula for the length function; if you can follow the proof on the Wikipedia page, I think you can work it out. My solution doesn't use this, but that doesn't invalidate your idea.

---

### Post by Lster on 2008-02-23
Oh I think I have an idea! I will try it tomorrow!

---

### Post by Lster on 2008-02-24
Nah. I can easily find the term (or line) that the result is in, very quickly; I can't see how the last loop would be reduced.

I give up. How did you do it? :)

---

### Post by Lux Perpetua on 2008-02-24
I don't want to give away the full solution. However, I'll say that if you know how to find length[n+2] given length[n] and length[n+1], then it should be no harder to find length[n] given length[n+1] and length[n+2]. So going backward in the sequence of lengths is no harder than going forward provided that you know two consecutive terms.

---

### Post by Lster on 2008-02-24
I've actually just solved using double precision approximation. You are right about that!

---

### Post by Lster on 2008-02-24
Done it... :) O(log(k)) (did you say?) time complexity and O(1) space complexity.

Thanks for the extra challenge and help. :) I think I've refreshed Fibonacci sequences very well now - when I started this challenge, I had to look on Wikipedia to see what the Fibonacci sequence was.

---

