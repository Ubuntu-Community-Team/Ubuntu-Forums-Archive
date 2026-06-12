---
title: "Generating permutations with constraints"
date: 2011-02-10
forum: Programming Talk
---

### Post by nipunreddevil on 2011-02-10
Given two sets of strings
set a="b8","b7",,,,...."b1"
set b="c2","c1","c0"

I wish to list out all the permutations of the form

b8c2 b7c2 b6c1 b5c1 b5c0 b5c0 b1c0 b1c0

of length 8 each wherein 
the ordering is maintained like non increasing indices from set a and also from set b.
A more formal defintion of the requirement would be to generate 8 tuple permutations of the form

bindex1cindex1  bindex2cindex2..............bindexcindex8

where index1>=index2>=index3>=...index8 for both b and c

What would be the suggested algorithm

---

### Post by nipunreddevil on 2011-02-15
Any suggestions?

---

### Post by Zugzwang on 2011-02-15
What you want to do can be done quite well recursively. Write a function of the form (pseudo-code):

```

enumerateCombinations(fixedSoFar : array of pairs, min_further_index_b : int, min_further_index_c : int)

```

that loops over the possible next values for b and c, pushes these to a copy of fixedSoFar, and continues recursively on these new values. Once "fixedSoFar" has reached length 8, you return.

---

