---
title: "One-Time Pad / Vernam Cypher generator."
date: 2012-03-27
forum: Programming Talk
---

### Post by Krovas on 2012-03-27
I want to write a program to generate One-Time Pads (physically, on paper) utilizing **/dev/random**, which I don't suspect would be that challenging to an experienced programmer, but I haven't done any programming since ***Pascal 5.5***. 

I'll have to look at this as a learning excercise, picking up modern programming as I go along, but I need a little nudge at the beginning, i.e: where should I begin? What language should I use? Any advice would be appreciated. Thanks.

---

### Post by CynicRus on 2012-03-27
Write in C, &#1057;++ or Python. In python xor crypting:

```

 [FONT=monospace]#!/usr/bin/env python
# -*- coding: utf-8 -*- import random, itertools, struct
 def generate_strings(ikey, q=10):
keys = {}
for i in range(q):
#print "%d." % i,
keys[i] = ""
for j in range(len(ikey)):
#keys[i] += hex(random.randint(0, 15))[2 : ]
keys[i] += chr(random.randint(0, 255))
#print keys[i]
return keys
 def xor (s, key):
key = itertools.cycle(key)
return ».join(chr(ord(x) ^ ord(y)) for (x,y) in itertools.izip(s, key))
 def generate_keys(ikey):
keys = generate_strings(ikey)
for i in range(len(keys)):
keys[i] = xor(keys[i], ikey) + keys[i] #xor(keys[i], b) + b
return keys
 def bs2s(bs):
ss = ""
for i in bs:
s = hex(ord(i))[2 : ]
if len(s) == 1:
ss += "0"
ss += s
return ss
 def s2bs(ss):
bs = ""
for i in range(0, len(ss), 2):
bs += chr(int(ss[i : i +2], 16))
return bs
 def restore_key(key):
c = len(key) / 2
return xor(key[ : c], key[c : ])
 if __name__ == "__main__":
action = ""
print "Select action:\ng — generate keys\nc — encrypt or decrypt file\nq — quit"
while action != "q":
action = raw_input("&gt; ")
if action == "g":
ikey = raw_input("Enter initial key value: ")
keys = generate_keys(ikey)
print "Generated keys:"
for i in range(len(keys)):
print "%d. %s" % (i, bs2s(keys[i]))
elif action == "c":
f_in_name = raw_input("Enter input file name: ")
f_out_name = raw_input("Enter output file name: ")
key = raw_input("Enter key: ")
try:
key = restore_key(s2bs(key))
f = open(f_in_name, "rb")
c = xor(f.read(), key)
f.close()
f = open(f_out_name, "wb")
f.write(c)
f.close()
except:
print "Errors :-(."
elif action != "q":
print "Invalid action."
[/FONT]
 


```

---

### Post by Krovas on 2012-03-28
Whoa. Thanks.

---

### Post by Bachstelze on 2012-03-28
The problem with using random values is that not all of them will give printable characters, so you are going to have a problem when you want to write them on paper, or even just input them with a keyboard or display them on a screen.

So you will have to use something to make them usable by humans (base64 comes to mind...).

---

