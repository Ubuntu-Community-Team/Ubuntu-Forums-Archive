---
title: "bash script - word list generator / brute force guesser"
date: 2008-01-05
forum: Programming Talk
---

### Post by musther on 2008-01-05
I'm wondering how to write a bash script to generate a brute force wordlist:

a
b
c
d
.......
aaa
aab
aac
aad

and so on.

Firstly, I know if I was serious about doing this I would not be using bash, and there are plenty of scripts and programs around that do this.  Think of this more as a bash programming exercise.

So, any ideas how I could go about doing this?

Cheers

---

### Post by Wybiral on 2008-01-05
Think about it like counting. Every time a digit reaches it's maximum, you increment the value to its left and reset it to the minimum.

---

### Post by ghostdog74 on 2008-01-06
Please read the [Bash guide.]("http://tldp.org/LDP/abs/html/"). You will come across [Chapter 3]("http://tldp.org/LDP/abs/html/special-chars.html"). Read that page and you will read about brace expansion and extended brace extension. You can try that for a start.

---

### Post by musther on 2008-01-06
Ok, I can see the usefulness of brace expansion, and I can sort of see the direction this is going, but I can't quite sort out the logical progression of it in my head.  Any further clues?  :wink:

---

### Post by ghostdog74 on 2008-01-06
its all about experimentation. Try it on the command line
```
]
# echo {a..z}
a b c d e f g h i j k l m n o p q r s t u v w x y z
# echo {a..z}{a..z}

```

---

### Post by seventhc on 2008-01-06
> **ghostdog74 said:**
> its all about experimentation. Try it on the command line
```
]
# echo {a..z}
a b c d e f g h i j k l m n o p q r s t u v w x y z
# echo {a..z}{a..z}

```
Thats cool
but it crashes if you do it to much ;)

---

### Post by musther on 2008-01-06
Ah yes, I see that.  What I was trying to work out though, was a way to construct them from a loop, so you could do something based on them.

```
while there are 'words' to generate
   generate next 'word' #if only it were this simple :)
   do something with 'word'
done

```

True, I could do something like:

```
echo {a..z}{a..z}{a..z} >> words.txt
for i in $(cat words.txt)
    do something
done
```

But that wasn't what I had in mind, I was thinking of doing it in real time, without generating a 'dictionary' first.

---

### Post by wolfbone on 2008-01-06
Nested loops? 

$ for x in {a..c}; do for y in {a..c}; do for z in {a..c}; do echo $x$y$z; done; done; done

---

### Post by musther on 2008-01-06
Ok, that's looking good, very good in fact.  Are there other ranges I can use.  I've experimented and found I can do {0..9}, but how would I do a to z AND 0 to 9.  

Finally, if I could also let it use a null character, all the options would be there, at the moment it's only doing all three, so an a b or c, and another, and another, rather than also including ab for example.

---

### Post by ghostdog74 on 2008-01-06
> **musther said:**
> but how would I do a to z AND 0 to 9.  

```

echo {a..z}{0..9}

```

---

### Post by musther on 2008-01-06
That's not it, that will give:

a to z followed by 0 to 9, rather than a to z 0 to 9 in each space.

---

### Post by wolfbone on 2008-01-06
I think ghostdog74 meant you should use that expression in what you've already got:

$ s=$(echo {a..c} {0..2}); for x in $s; do for y in $s; do for z in $s; do echo $x$y$z; done; done; done

---

### Post by musther on 2008-01-06
Oh sorry, I missed that, thanks.

---

### Post by musther on 2008-01-06
Now I'm just trying to wrap the whole thing in code to make it do one character, then two, then three etc...  ...but I'm struggling again. I think I've got the right idea, using a similar kind of nested loop, but can't get it quite right.

---

### Post by jadjay on 2008-04-30
I have the hint:
!!!! attention ce code n'est pas encore bash mais il y a l'idée générale !!!!!

Mot = ""
list = [a-z]

while length(Mot) < 10 (on peut le demander par un input)
   
    for j in list 
        
         for i in list
       
             echo mot + list[i]

         done

         mot = mot + list[j]

     done

done

Je fais le test des ce soir!!!!

---

### Post by Zugzwang on 2008-04-30
> **jadjay said:**
> I have the hint:
!!!! attention ce code n'est pas encore bash mais il y a l'idée générale !!!!!


I doubt that this will actually work (not to mention the fact that not everyone here will understand French).

To the OP's question: The most elegant solution uses recursion. Consider the following pseudo-code:

[PHP]
function printAllCombinationsRecursive(String prefix, int levelsLeft) {
  if (levelsLeft==0) 
    print prefix
  else
    for letter in [a..z] do
      printAllCombinationsRecursive(prefix+letter,levelsLeft-1)
    end for
end function
[/PHP]

...which you use in the following function...

[PHP]
function printAllCombinationsUpToLength(int levels) {
  for i=1 to levels do
    printAllCombinationsRecursive("",i)
  end for
end function
[/PHP]

...which does what you want (EDIT: ..if you adapt the letter range. ;-)) Converting this to some Bash or Python script is left as an exercise. If you replace the "print" line by what you actually want to do, you also won't run into memory problems.

---

### Post by matteoredaelli on 2009-05-04
For a powerful free and opensource wordlist generator see

 [http://code.google.com/p/ruby-words-generators/](http://code.google.com/p/ruby-words-generators/)

or wg.pl at [http://matteoredaelli.wordpress.com/downloads/](http://matteoredaelli.wordpress.com/downloads/)

---

### Post by JK3mp on 2009-05-04
I believe Perl or Python would be a better alternative for this...will avoid your *crashing* issue for sure. As far as brute force, perl is generally really stable for constant programs. But python is great and very easy as long as you don't break variables much (causing it to run slow) :D

---

### Post by stroyan on 2009-05-04
As this old posting has been resurrected, I feel compelled to answer the old original question.
Bash can generate a word list with both letter and number sequences.
Just use nesting of {a..z} and {0..9} inside of {,}.
Here is a two character word list.
```

$ for w in {{a..z},{0..9}}{{a..z},{0..9}} ;do echo $w;done

```

---

