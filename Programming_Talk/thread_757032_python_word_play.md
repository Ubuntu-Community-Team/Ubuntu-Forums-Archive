---
title: "python word play"
date: 2008-04-16
forum: Programming Talk
---

### Post by bg11 on 2008-04-16
Partly due to the enthusiasm shown here for python, I decided to have a go at learning it.  I'm going through Downey's Python book from the green tea site.  But I'm stuck on an exercise involving reading in a word list, searching for pairs of words which are shifts or "rotations" of each other, e.g. melon shifted by -10 is cubed.

I've written some code, which seems to work, but it takes a very long time to finish the whole word list (see attachment, filename=brit-a-z).  I'm sure there's some reasonably simple way of optimising it.  Advice, tips, hints?

Here's the code:
```

dord = {}
def list_rotations(file):
    fin = open(file)
    nlines = 0
    for line in fin:
        word = line.strip()
        i = 0
        if len(word) < 4: ### for testing ###
            ord_list = []
            while i < len(word):
                if word[i] in dord: o = dord[word[i]]
                else:
                    o = ord(word[i])
                    ord_list.append(o)

                i += 1
            dord[word] = ord_list
        nlines += 1

    for k1 in dord:
        for k2 in dord:
            if k1 != k2 and len(k1) == len(k2):
                are_rotated(k1, k2)

def are_rotated(word1, word2):
    shift = [0]*len(word1)
    i = 0
    for o in dord[word1]:
        lord = dord[word2]
        if o == lord[i]: rotated = False
        shift[i] = o - lord[i]
        if shift[i] < 0: shift[i] += 26
        if i>0:
            if shift[i] != shift[i-1]: return False
        i += 1
    print word1, word2, shift[0]

list_rotations('brit-a-z.txt')

```

---

### Post by smartbei on 2008-04-17
Check this out:
```


ASCII_a = ord('a')

def main(filename):
	fd = open(filename, "r")
	words = []
	for line in fd.readlines():
		if line.find("'") == -1:
			words.append(line.strip())

	word_dict = {}
	for word in words:
		rot = calc_rotate(word)
		if word_dict.has_key(rot):
			word_dict[rot].append(word)
		else:
			word_dict[rot] = [word]
	
	to_rem = []
	for a,b in word_dict.iteritems():
		if len(b) == 1:
			to_rem.append(a)
	
	for a in to_rem:
		word_dict.pop(a)

	for a in word_dict:
		print word_dict[a]
	
def calc_rotate(word):
	diff = ord(word[0]) - ASCII_a
	return ''.join([chr(ASCII_a + ((ord(a) - ASCII_a - diff) % 26)) for a in list(word)])
	

if __name__ == "__main__":
	from sys import argv
	if len(argv) != 2:
		print "Usage: %s <input_filename>" % (argv[0],)
	else:
		main(argv[1])

```
For me this works in around a second or two. What I am doing is reducing every word to a simplified version of it, one that will be the same for every two words that exhibit the property that you demonstrated. For example, the word 'bcde' is reduced to 'abcd' and the word 'xyza' is reduced also to 'abcd' (you can shift from one to the other).

This I do to all the words and add it to a dictionary. Then, I filter the dictionary to remove the words that do not have shifts, and finally I print it out. Hope this helps you out.

**Why this is faster:** INSERT and REMOVE from a dictionary are (average) O(1) in time. Going through the list is O(N), and so my algorithm runs in O(N) time. Yours, on the other hand, works in O(N*N) time, because for every word it checks against all the other words.

If you need more explanation, don't hesitate to ask.

---

### Post by Wybiral on 2008-04-17
I would also add that "lord, word, and dord" might cause confusion :)

---

### Post by nanotube on 2008-04-18
> **Wybiral said:**
> I would also add that "lord, word, and dord" might cause confusion :)

hehe, amusing point, but with a good lesson behind it - it's a good idea to always aim for descriptive variable names. :)

---

### Post by ghostdog74 on 2008-04-18
its good for learning's sake, that you are trying to the "harder" way. Until you are satisfied with your accomplishment, you might want to take a look at what Python has to offer
```

import string        
FROM=string.ascii_lowercase
TO= "qrstuvwxyzabcdefghijklmnop" 
a = string.maketrans(FROM, TO)
print "melon".translate(a)

```
output:
```

# ./test.py
cubed

```

---

### Post by smartbei on 2008-04-18
Sorry - wrong thread.

---

