---
title: "MD5 hashes"
date: 2011-08-27
forum: Programming Talk
---

### Post by Macrotus on 2011-08-27
Hi

I'm wondering which string forms MD5 hash with only numbers and which forms hash with only letters. 

Do you guys know?

---

### Post by NightwishFan on 2011-08-27
Is that possible? It goes through many layers of pre-processing.

---

### Post by haqking on 2011-08-27
> **Macrotus said:**
> Hi

I'm wondering which string forms MD5 hash with only numbers and which forms hash with only letters. 

Do you guys know?


Well a MD5 hash is hexadecimal in output so 0-9 a-f

you could convert it to octal or binary if you want only numbers ?

I dont get your question ?

do you mean which string will only create a hash that results in a hexidecimal output of only digits instead of alpha characters ? MD5 creates a fixed ouput of 128bits from a variable input

you can get a list of hashes here [http://md5pass.com](http://md5pass.com)

---

### Post by quids on 2011-08-27
Would be a clever trick if you did find one, but my money is on it not being possible

---

### Post by undecim on 2011-08-27
> **quids said:**
> Would be a clever trick if you did find one, but my money is on it not being possible

It's possible for one to exist... finding one however, will prove to be difficult. Seeing as an MD5 hash outputs 32 hexadecimal digits, the probability of any string resulting in a hash with only numbers is:

(5/8)^32 = 0.000029387%. Or in other words, about 1 in 3,402,824 hashes will be numeric.

for alphabetic: (3/8)^32 = 0.0000000000023388%, or about 1 in 42,756,232,765,800 hashes will be alphabetic.

---

### Post by Thewhistlingwind on 2011-08-27
> **undecim said:**
> It's possible for one to exist... finding one however, will prove to be difficult. Seeing as an MD5 hash outputs 32 hexadecimal digits, the probability of any string resulting in a hash with only numbers is:

(5/8)^32 = 0.000029387%. Or in other words, about 1 in 3,402,824 hashes will be numeric.

for alphabetic: (3/8)^32 = 0.0000000000023388%, or about 1 in 42,756,232,765,800 hashes will be alphabetic.

How much computing power does it take to go through 3 million guesses? (Don't even bother with the alphabet only, lol.)

Lets say the language is; C.

---

### Post by undecim on 2011-08-28
> **Thewhistlingwind said:**
> How much computing power does it take to go through 3 million guesses? (Don't even bother with the alphabet only, lol.)

Lets say the language is; C.

I just wrote a python script for it:

```
#!/usr/bin/python2.7
import hashlib
def nextText(t):
	if t == "":
		return "a"
	if t[-1] == 'z':
		return t[0:-1] + "A"
	if t[-1] == 'Z':
		return t[0:-1] + "0"
	if t[-1] == '9':
		return nextText(t[0:-1]) + "a"
	return t[0:-1] + chr(ord(t[-1])+1)

t = ""

def isNumeric(t):
	for n in t:
		if ord(n) < 48 or ord(n) > 57:
			return False
	return True

while True:
	if isNumeric(hashlib.md5(t).hexdigest()):
		print(t)
	t = nextText(t)

```

I got these outputs in about 60 seconds:
```
jctJ
wzx2
y5PA
2PP7

```

EDIT: Of Interest, the first number whose string results in a a numeric md5 is: 1518375, outputting 93240121540327474319550261818423. Found using:

```
#!/usr/bin/python2.7
import hashlib

def isNumeric(t):
        for n in t:
                if ord(n) < 48 or ord(n) > 57:
                        return False
        return True

i = 0

while True:
        if isNumeric(hashlib.md5(str(i)).hexdigest()):
                print(i)
        i+=1
```

---

### Post by Thewhistlingwind on 2011-08-28
> **undecim said:**
> 
     [undecim geeking out]  

This is win.


I was too lazy to write that script myself.

---

### Post by Macrotus on 2011-09-02
Wow, thanks undecim. That's what I was looking for. How should I change the script to find a hash with only letters a-f? Once I was quite good in Python, not any more...

Btw, how could I generate a hash, that has as much as possible numbers from pi? It's 32 fist numbers are 31415926535897932384626433832795. I'd like to know which string gives me a MD5-hash, which 12 first symbols are 314159265358. So all hashes which begins with 314159265358 are ok.

---

### Post by s.fox on 2011-09-02
Thread moved to [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

