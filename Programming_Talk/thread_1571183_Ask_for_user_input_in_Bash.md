---
title: "Ask for user input in Bash?"
date: 2010-09-09
forum: Programming Talk
---

### Post by Kdar on 2010-09-09
How can I ask for user input in Bash?

I have movie collection, with each movie having it's own directory. And I wanted to add '(YEAR)' in the end of each directory, but since all those movies are different, I want to ask user for input.

I know how to rename bunch of files and add same ending:
```
for file in * ; do mv $file $file.bak; done

```

But what can I use to ask for input?

---

### Post by ghostdog74 on 2010-09-09
```
read -p "What's the input? " input
```

---

### Post by phrostbyte on 2010-09-10
I'd also add the input is stored in a variable called $input in the last case.

---

