---
title: "Adding words at the beginning of each line in a text file"
date: 2011-02-01
forum: Programming Talk
---

### Post by Datweakfreak on 2011-02-01
I wasn't sure how to phrase the title, but I guess I came close to what I wanted to ask.

I have a text file, say, **foo.txt**, whose contents are the following lines:

```
1234
5678
9876
5432
1098
```I want to add words at the beginning of each line, so that it looks like, say, this:
```

abcd - 1234
ghij - 5678
klmn - 9876
opqr - 5432
stuv - 1098
```I could, of course, manually edit the file, but I'd like to know about a command that will do this for me, as I'm going to be doing a tad more complex variant of this in a bash script.

Help appreciated, much :)

---

### Post by kurum! on 2011-02-01
```

$ ruby -ne 'BEGIN{f=open("file1")};print "#{$_.chomp} - #{f.gets}";END{f.close} ' file2


```

---

### Post by Arndt on 2011-02-01
> **Datweakfreak said:**
> I wasn't sure how to phrase the title, but I guess I came close to what I wanted to ask.

I have a text file, say, **foo.txt**, whose contents are the following lines:

```
1234
5678
9876
5432
1098
```I want to add words at the beginning of each line, so that it looks like, say, this:
```

abcd - 1234
ghij - 5678
klmn - 9876
opqr - 5432
stuv - 1098
```I could, of course, manually edit the file, but I'd like to know about a command that will do this for me, as I'm going to be doing a tad more complex variant of this in a bash script.

Help appreciated, much :)

```
paste file1 file2 | sed 's/\t/ - /'
```

---

### Post by kurum! on 2011-02-01
> **Arndt said:**
> ```
paste file1 file2 | sed 's/\t/ - /'
```
```

paste -d - file1 file2

```

---

### Post by Arndt on 2011-02-01
> **kurum! said:**
> ```

paste -d - file1 file2

```

Yes, but it looked like the OP wanted spaces around the hyphens.

---

### Post by Datweakfreak on 2011-02-01
Thanks a load, guys! That helped! :p

Um, if I'm not being a pain in the ***, I'd like to ask one more thing. How do I format it, like this:

```
abcd - 
1234
ghij - 5678
klmn - 9876
opqr - 
5432
stuv - 1098
```

I want new lines to be inserted after **abcd **and** opqr**.

---

