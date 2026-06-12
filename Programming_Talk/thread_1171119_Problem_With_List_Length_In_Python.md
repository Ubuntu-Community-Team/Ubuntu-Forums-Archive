---
title: "Problem With List Length In Python"
date: 2009-05-27
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-27
Ey guys, I am having some problems with list lengths. I am reading in a textfile one line at a time and place a "split" line in TempList. Here is the code:
```

def main(argv):
	f = open(sys.argv[1])
	G.fline = f.readlines()
	c = 0
	for l in G.fline:
		G.parsed.append(G.fline[c].split())
		TempList = G.parsed[c]
		print TempList, len(TempList) #this statement outputs the output below
#...
#I access different parts in the line of the file by accessing
#different indices of TempList:
        m = 0 #line is not a message
	p = parsePort(TempList[0]) #port number
	d = TempList[1] #date
	t = TempList[2] #time

```
And here is the output from the indicated print statement shown above:
```

['(000668)', '4/27/2009', '15:07:00', 'PM', '-', '(not', 'logged', 'in)', '(24.7.179.80)>', '220-'] 10

```

My question is why is it printing that the list has a length of 10, when it evidently has only 8 elements? This is really stumping me, any help would be greatly appreciated. Thanks!

---

### Post by StunnerAlpha on 2009-05-27
Nevermind guys... just being stupid again. Thought there was a tuple inside the list, its actually just three strings. Mod please delete.

---

