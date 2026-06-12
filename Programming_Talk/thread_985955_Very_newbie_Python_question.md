---
title: "Very newbie Python question"
date: 2008-11-18
forum: Programming Talk
---

### Post by abraxas_swa on 2008-11-18
Hey folks, apologies for taking up your time with something I'm sure is very simple.

I am writing a simple guessing game in Python. I'm trying to extract a word at random from a text file, which the user then has to guess. To do this I'm using:

```
targets = []
f = open("targets.txt", "r")
for line in f:
	stripped = line.strip().split("\r")
	targets.append(stripped)

target = random.choice(targets)
```

The text file consists of individual words, each on a new line.

This returns single characters as list items and I'm not sure how to fix it. I've spent some time Googling but haven't found anything that works. Any help/explanation would be greatly appreciated.

---

### Post by Tony Flury on 2008-11-18
is targets a list of words, or a list of letters ?


i think the problem might be that the choice function is seeing your list of words as a squence of letters...


to be honest i would have been tempted to try this 
(code split apart for clarity

```

_len = len(targets)
_range = range(_len)
_choice = random.choice(_range)
target = targets[_choice]

or - all in one statement
target = targets[random.choice(range(len(targets)))]

```
does that work ?

---

### Post by geirha on 2008-11-18
I'd just do
```
targets= file('targets.txt').readlines()
target= random.choice(targets).strip()

```

EDIT: The only problem with your version is that you add the unnecessary .split('\r') which returns a sequence. The strip-method removes ending '\n's and '\r's.

---

### Post by ghostdog74 on 2008-11-18
> **abraxas_swa said:**
> Hey folks, apologies for taking up your time with something I'm sure is very simple.

I am writing a simple guessing game in Python. I'm trying to extract a word at random from a text file, which the user then has to guess. To do this I'm using:

```
targets = []
f = open("targets.txt", "r")
for line in f:
	stripped = line.strip().split("\r")
	targets.append(stripped)

target = random.choice(targets)
```

The text file consists of individual words, each on a new line.

This returns single characters as list items and I'm not sure how to fix it. I've spent some time Googling but haven't found anything that works. Any help/explanation would be greatly appreciated.

```

data = open("file").readlines()
data = [i.strip() for i in data ]

```

---

### Post by abraxas_swa on 2008-11-18
Thank you very much folks. Got it working now with readlines().

---

### Post by fiddler616 on 2008-11-18
(It'd be really great if you marked the thread as solved...Go to thread tools at the top and click "Mark Thread as Solved")(Thanks)

---

