---
title: "user inputs double, program outputs int (succesfully) but what about other characters"
date: 2009-09-12
forum: Programming Talk
---

### Post by s3a on 2009-09-12
The following (java code) allows the user to input a double but it forces an output of an integer:

```
int variable = (int)kb.nextDouble();
```

That is what I want but I also want the user to be able to input letters and still be denied with a printed error message (which I've already set up as was the case before with another similar problem) but I just don't know what I have to change so that the user can input any characters (although the program will not print anything other than integers. How do I make it do what it currently does but also take in other character inputs?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by falconindy on 2009-09-12
You'll need to wrap your variable declaration inside a try/catch structure, and probably wrap that inside a while loop if you want to keep asking the user for input until they enter a proper value.

Hint: to figure out what kind of exception you need to catch, look at the output on the command line when the program crashes after you enter letters instead of numbers.

---

### Post by s3a on 2009-09-12
My class is learning while loops later (it is in a later chapter in my book). And that checking the output of the terminal tells me what I already think I know which is that the statement in the opening post needs to be modified to accept letters as well and I was hoping someone could answer that for me.

---

