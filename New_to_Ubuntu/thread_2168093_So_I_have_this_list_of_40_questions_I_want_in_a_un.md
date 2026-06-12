---
title: "So I have this list of 40 questions I want in a unique order 351 times"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by bostoncab2 on 2013-08-16
So I have this list of 40 questions I want in a unique order 351 times

The list of questions is in a text file but I am willing to copy and paste them into whatever format is needed. 

I need 351 unique sets of the same questions witch each set in a different order. What can I do on ubtunu to hit my needs?

Mike

---

### Post by VMC on 2013-08-16
[I give up or don't understand the question]

---

### Post by tgalati4 on 2013-08-16
Searching the web:  [http://en.wikipedia.org/wiki/Permutations](http://en.wikipedia.org/wiki/Permutations)

You want a reduced set of permutations (40 questions taken 40 at a time, order is important AND no repetition of questions).  The following link is a calculator and list creator:  [http://www.mathsisfun.com/combinatorics/combinations-permutations-calculator.html](http://www.mathsisfun.com/combinatorics/combinations-permutations-calculator.html) with some explanation:  [http://www.mathsisfun.com/combinatorics/combinations-permutations.html](http://www.mathsisfun.com/combinatorics/combinations-permutations.html)

In linux, two commands are helpful *apropos* and *apt-cache search*:

tgalati4@Mint14-Extensa ~ $ apropos permutation
shuf (1)             - generate random permutations
tgalati4@Mint14-Extensa ~ $ apt-cache search permutation
libbtf1.1.0 - permutation to block triangular form library for sparse matrices
libsuitesparse-dbg - libraries for sparse matrices computations (debugging symbols)
libsuitesparse-dev - libraries for sparse matrices computations (development files)
libsuitesparse-metis-3.1.0 - collection of libraries for computations for sparse matrices
libsuitesparse-metis-dbg - collection of libraries for computations for sparse matrices
libsuitesparse-metis-dev - collection of libraries for computations for sparse matrices
libalgorithm-permute-perl - module to perform permutations with object oriented interface
libghc-hcard-dev - library for implementing a Deck of Cards
libghc-hcard-doc - library for implementing a Deck of Cards; documentation
libghc-hcard-prof - library for implementing a Deck of Cards; profiling libraries
libitsol-dev - ITerative SOLvers - devel
libitsol1 - ITerative SOLvers - runtime
libmath-combinatorics-perl - module for performing combinations and permutations on lists
libstring-glob-permute-perl - Expand {foo,bar,baz}[2-4] style string globs
libxml-semanticdiff-perl - Perl extension for comparing XML documents
python-pytools - big bag of things supplementing Python standard library
python3-pytools - big bag of things supplementing Python 3 standard library
r-cran-gregmisc - GNU R package with miscellaneous functions by Greg Warnes et al
r-cran-permute - R functions for generating restricted permutations of data
unsort - reorders lines in a file in semirandom ways

*apropos* will search your system for any commands that have a keyword, in this case **permutation**. *apt-cache search* will search the repositories for any packages that might perform permutations.

You can write a script to take your list of 40 lines and jumble it 351 times to create your new lists.

From *apropos*, there is a command call *shuf* (presumably from shuffle) that gets you closer:

Open a terminal:

```
man shuf
```

You can also install *unsort* and see what it offers.  

There are probably 10 ways to do this, but you want to find the most elegant way.

Create a text file with your 40 questions and start playing with it:

tgalati4@Mint14-Extensa ~ $ cat shuffle_test.txt 
This is line number 1.
This is line number 2.
This is line number 3.
This is line number 4.
This is line number 5.
This is line number 6.
This is line number 7.
This is line number 8.
This is line number 9.
This is line number 10.
tgalati4@Mint14-Extensa ~ $ shuf shuffle_test.txt
This is line number 5.
This is line number 9.
This is line number 1.
This is line number 7.
This is line number 4.
This is line number 2.
This is line number 3.
This is line number 6.
This is line number 10.
This is line number 8.

Now write a script to check for duplicates and save to unique file names.

---

### Post by GwL3eNC on 2013-08-16
Do you know something about statistic and programming?

---

### Post by bapoumba on 2013-08-16
> **VMC said:**
> Is this a class assignment?

Is it ? bostoncab2 please answer the question, thanks.

---

### Post by Crusty Old Fart on 2013-08-17
Here you go, Mike.
Run this:
```

#!/bin/bash
set -e

echo -e "\nStep 1: Get a deck of playing cards." \
  "\nStep 2: Remove the jokers and the face cards." \
  "\nStep 3: Use gedit in Ubuntu to create a text file where you manually map each of the remaining forty cards to a unique question."
for i in {4..1056..3}; do
  echo "Step $i: Manually shuffle the cards."
  echo -e "Step $(( i + 1 )): Create a new text file using gedit in which you arrange the questions according to the order of your shuffled cards" \
  "\n           and the mapping you made in Step 3."
  echo "Step $(( i + 2 )): Print the file on a piece of paper."
done
echo -e "Step 1057: Stack all your printed papers and bind the stack with a couple of rubber bands." \
  "\nStep 1058: Turn the stack in to your teacher." \
  "\nStep 1059: Don't worry about any duplicates in your stack." \
  "\n           There's hardly any chance that your teacher is going to check them.\n"

exit 0

```
Don't work too hard, Mike.

Crusty

---

### Post by evilsoup on 2013-08-17
```
for f in {1..351}; do shuf --random-source=<(echo $f) input.txt > output${f}.txt; done
```

The above assumes that you want each permutation in a different file; you will end up with 351 output files. Please note that I haven't tested this extensively.

---

### Post by Crusty Old Fart on 2013-08-17
> **evilsoup said:**
> ...The above assumes that you want each permutation in a different file; you will end up with 351 output files...
It also assumes it isn't homework, which is an assumption that is this close --><-- to impossible for me.
Perhaps I'm getting increasingly crusty with age, or I'm suffering from chronic female supervision deficiency syndrome, or both.

---

### Post by coffeecat on 2013-08-17
Since answers are still being given despite the fact that the OP has not yet answered the question as to whether or not this is homework, I've closed the thread, at least for the time being.

@bostoncab2, from the [Posting Guidelines](http://ubuntuforums.org/showthread.php?t=2158945) which form part of the forum rules:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

If this is not homework, and you need more help, click on the [img]http://ubuntuforums.org/images/ubuntu-VB4/buttons/report-40b.png[/img] button in your own post to send a request for re-opening to the staff area.

---

