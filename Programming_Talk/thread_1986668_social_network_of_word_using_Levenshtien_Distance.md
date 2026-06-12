---
title: "social network of word using Levenshtien Distance"
date: 2012-05-25
forum: Programming Talk
---

### Post by jamesbon on 2012-05-25
This is a question taken from [here]("http://www.careercup.com/question?id=13406684")

Two words are friends if they have a Levenshtein distance of 1 (For details see [http://en.wikipedia.org/wiki/Levenshtein_distance](http://en.wikipedia.org/wiki/Levenshtein_distance)). That is, you can add, remove, or substitute exactly one letter in word X to create word Y. A word’s social network consists of all of its friends, plus all of their friends, and all of their friends’ friends, and so on. Write a program to tell us how big the social network for the word 'hello' is, using this word list [https://raw.github.com/codeeval/Levenshtein-Distance-Challenge/master/input_levenshtein_distance.txt](https://raw.github.com/codeeval/Levenshtein-Distance-Challenge/master/input_levenshtein_distance.txt)
Input

Your program should accept as its first argument a path to a filename.The input file contains the word list. This list is also available at [https://raw.github.com/codeeval/Levenshtein-Distance-Challenge/master/input_levenshtein_distance.txt](https://raw.github.com/codeeval/Levenshtein-Distance-Challenge/master/input_levenshtein_distance.txt).
Output

Print out how big the social network for the word 'hello' is. e.g. The social network for the word 'abcde' is 4846.

Can any one help to come up with some logic for the same.
It is not a home work problem.

---

### Post by Barrucadu on 2012-05-25
Here is how I'd do it.

```

SocialNetworkSize (initial_word):
  Words = {}
  UncheckedWords = {initial_word}
  Count = -1

  For Word in UncheckedWords:
    UncheckedWords -= Word
    Words += Word
    Let Friends be all the friends of Word
    UncheckedWords += Friends - Words
    Count ++

  return Count

```

---

