---
title: "generating a wordlist and eliminating the 'wrong' words"
date: 2009-07-08
forum: Programming Talk
---

### Post by paolocrosetto on 2009-07-08
Hi all,

I am designing an economics experiment, which will have some scrabble-like features.

For the task, I need to write a program that does the following:

1. generates by brute force all possible words when given a set of letters as source, the number of letters of the words generated, and the number of allowed repetitions.

2. for each word generated, looks into a dictionary (say aspell, ispell, web-based...) and if the word does not exist, discards it; else, it writes it up into output file.

I have followed a discussion in this forum about generating wordlists (here: [http://ubuntuforums.org/archive/index.php/t-659624.html](http://ubuntuforums.org/archive/index.php/t-659624.html)), and so I have kind of solved point 1; I am in deep dark on point 2. I read aspell manual, but I am no programmer and lost my way.

If I use bash, as it was the case on the abovementioned thread, point one for three-letter words with no repetiton should look like 

```

s=$(echo {list}); for x in $s; do for y in $s; do for z in $s; do echo $x$y$z; done; done; done

```and then I should insert an appropriate command after the 'do echo...' to make the program spellcheck in aspell, and then delete.

I have tried 'aspell clean' but couldn't make it work the way I wished.

I am familiar with pascal, python, and a little bash, all as a novice.

Any help will be greatly appreciated!

---

### Post by stroyan on 2009-07-08
Since the 'wordlist' you are generating is rule based and the dictionary is more limited, I expect you would have an easier time filtering the words in the dictionary against the rules for your wordlist.  You could do that in a single pass instead of trying every possible letter combination against a dictionary search.

---

