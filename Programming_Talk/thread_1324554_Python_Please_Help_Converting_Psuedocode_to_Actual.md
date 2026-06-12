---
title: "Python: Please Help Converting Psuedocode to Actual Program"
date: 2009-11-12
forum: Programming Talk
---

### Post by tdrusk on 2009-11-12
The Pseudocode is in the comments. Could you please tell me the mistakes I am making? I am having a hard time understanding some of the language of the pseudocode.
This code involves using Chomsky Normal Form in a and r.
I am not sure about these lines
[B]#This grammar contains the subset Rs which is the set of start symbols.

#If any of P[1,n,x] is true (x is iterated over the set s, where s are all the indices for Rs)
for n in range(len(a)):
    for x in range(len(r))
#  Then S is member of language
#  Else S is not member of language[/B]

Then again if anything else looks wrong please inform me. Thanks!

Oh and I haven't filled in a and r since they are just rules.

```

#Let the input be a string S consisting of n characters: a1 ... an.
a=[]
#Let the grammar contain r nonterminal symbols R1 ... Rr.
#This grammar contains the subset Rs which is the set of start symbols.
r=[]
#Let P[n,n,r] be an array of booleans. Initialize all elements of P to false.
makematrix = lambda n: [[[0,0,0,0,0] for a in xrange(0, n)] for b in xrange(0, n)] 
P = makematrix(len(a))
#For each i = 1 to n
for i in range(len(a)):
#    For each unit production Rj -> ai, set P[i,1,j] = true.
    for j in range(len(r)):
        P[i,0,j]
#For each i = 2 to n -- Length of span
for i in range(1,len(a),1):
#    For each j = 1 to n-i+1 -- Start of span
    for j in range(len(a)-i+1):
#        For each k = 1 to i-1 -- Partition of span
        for k in range(i-1):
#            For each production RA -> RB RC
            for x in len(r):
                if r[x]==str(a[j]+a[k]):
#                    If P[j,k,B] and P[j+k,i-k,C] then set P[j,i,A] = true
                    if P[j][k][x+1]==P[j+k][i-k][x+2]:
                        P[j,i,a]=1
#If any of P[1,n,x] is true (x is iterated over the set s, where s are all the indices for Rs)
for n in range(len(a)):
    for x in range(len(r))
#  Then S is member of language
#  Else S is not member of language

```

---

