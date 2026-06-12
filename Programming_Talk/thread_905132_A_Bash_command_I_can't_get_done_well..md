---
title: "A Bash command I can't get done well."
date: 2008-08-30
forum: Programming Talk
---

### Post by Mamsaac on 2008-08-30
I just need a command that does the following:

-Read a file which contains words (one per line).
-Words can be repeated over the file.
-Check how many times the words are repeated.

So... imagine this:

Michael
Kyle
Michelle
Michael
Joseph
Henry
Kyle

Since there are two pairs of repeated words (names in this case), the command should output a 2.

I've been thinking on this one, but I don't have enough experience in Bash to do it. I would really appreciate your help.

Thanks in advance.

---

### Post by jmontelius on 2008-08-30
quick trick

>grep Michale foo.txt | wc -l

ok?

---

### Post by Mamsaac on 2008-08-30
The thing is: I don't know what names are in the file. I know how that works (what you proposed), but I don't know what names will be in the file.

I forgot to say, I know the file will always have 20 names.

---

### Post by ghostdog74 on 2008-08-30
> **Mamsaac said:**
> I just need a command that does the following:

-Read a file which contains words (one per line).
-Words can be repeated over the file.
-Check how many times the words are repeated.

So... imagine this:

Michael
Kyle
Michelle
Michael
Joseph
Henry
Kyle

Since there are two pairs of repeated words (names in this case), the command should output a 2.

I've been thinking on this one, but I don't have enough experience in Bash to do it. I would really appreciate your help.

Thanks in advance.

i give you the benefit of the doubt that this is not some kind of homework
```

# grep -c "Michael" file
2
# awk '/Michael/{c++}END{print c}' file
2
# awk '{a[$0]++}END{for (i in a) print a[i],i}' file

```
see my sig to learn more about bash too.

---

### Post by MaxIBoy on 2008-08-30
It's hard to tell what you want. If you just want the number of words which are repeated, but don't care how many times they're repeated, the following script should work.


Save the following code in a file with a name ending in ".py" and tell me if it works (can't be bothered to test it myself.)

```
file = open("source.dat", 'r') #change "source.dat" to whatever the name of your file is
words = []
currentWord = file.readline()
words += [[currentWord, 1]] #In this case, "1" is the number of times that the current word 
#has appeared in the file so far. So for instance, if the word "george" appeared 3 times,
#by the time the script was finished running, the entry for "george" would look like this:
#   ["george", 3]
numberOfDuplicates = 0 #how many words have been seen more than once

while currentWord != "":
    currentWord = file.readline()
    currentWordIsDuplicate = False
    for i in words:
        if i[0] == currentWord:
            if i[1] == 1:
                numberOfDuplicates += 1
            i[1] += 1
            currentWordIsDuplicate = True
            break
    if not currentWordIsDuplicate:
        words += [[currentWord, 1]]

print numberOfDuplicates

```

Can't guarantee that this will work, but it's worth a shot.


This assumes the name of your file is "source.dat." Any filename will do, edit the first line and change the filename to what you need. Then drop the .py file in the right folder, fire up BASH, cd to the folder, and type
```
python <whatever name you gave to the script>.py
```

---

### Post by ghostdog74 on 2008-08-30
you can make use of dicts in Python
```

d={}
for line in open("file"):
    line=line.strip()
    d.setdefault(line,0)
    d[line]=d[line]+1
print d

```

---

### Post by Mamsaac on 2008-08-30
Ok, I will elaborate so you don't act in a way of distrust.

I know Python, I know PHP (going for certification), I know Java, etc etc.

I can't use but a single command only in bash... obviously needing a pipeline. The need of the command IS for college but not exactly as homework, but more for a small project... and it happens to need this to be executed as a command of terminal and not a .sh (so, no loops). The professor told me I should try doing it, kinda like a dare... So, I've been trying but, honestly, I've no experience with bash.

The idea is:

Read file -> check how many words appear more than once -> output.

All in a command that should use pipelines.

If I could use a loop or python, (or others) it would be very simple and easy, but it's not allowed ¬¬.

Hope you don't mind.

---

### Post by MaxIBoy on 2008-08-30
Oh, so Python would be cheating?

Hee hee, how about assembly?



Seriously, though, I'm having trouble understanding what you're saying. Either that or I understand you but can't believe it. Do you want us to look up to see if there is an existing command that will do the trick? Are multiple commands okay but you can only hit "enter" once? And loops aren't allowed?

Taking that dare was a pretty stupid idea, if you'll excuse my saying so. I can think of a few ways to do it in only one line, right off the top of my head, but they all involve cramming one or two entire loops into that one line, which of course won't do. 

This is a very interesting problem, now you've got me interested. I'll see what I can come up with (although BASH scripting isn't a specialty of mine.)

---

### Post by stylishpants on 2008-08-30
```

# your test data
fraser@ged:/tmp$ cat file
Michael
Kyle
Michelle
Michael
Joseph
Henry
Kyle

# print counts for each name
fraser@ged:/tmp$ sort file | uniq -c
      1 Henry
      1 Joseph
      2 Kyle
      2 Michael
      1 Michelle

# suppress the names that have a count of 1
fraser@ged:/tmp$ sort file | uniq -c | sed -n '/^ *1 /!p'
      2 Kyle
      2 Michael

# count the unique names that remain 
fraser@ged:/tmp$ sort file | uniq -c | sed -n '/^ *1 /!p' | wc -l
2



# I think that's how you arrive at the 2 in your example, is that right?

```

---

### Post by Mamsaac on 2008-08-30
Thank you so much for that command. That's what I needed... I wouldn't have been able to do that :S

Thanks for all that tried =)

G'night.

---

### Post by MaxIBoy on 2008-08-30
EDIT: On further testing, my method needs fine-tuning. I'll get back to you with a working version.



Hang on, just a damn moment, I figured out how to get it all into one line!


Start the line out with this:
```
let counter=0;
```


Then, copy and paste the following into your line, over and over again:
```
string=$(cat yourfile | line) ; if [ -z string ] ; then echo $counter ; fi ; if [ $(grep -c $string yourfile) -gt 0 ] ; then let counter=counter+1 ; fi; $(grep -v $string yourfile) > yourfile ;
```

Replace "yourfile" with the name of your file. 




Also, you might want to back up the file with all the names in it before you run this, as this command will eat through the file like a plague.





However, I figured out how to do this while only hitting enter once, and no loops, and I'm not even very good at this. I demand attribution, even if you don't wind up using my solution. ;-)

---

### Post by rangalo on 2008-08-30
Hi guys,

[EDIT:]
Sorry,  forget this post, somebody already replied 
with this solution.

I am not an expert by shouldn't following  command work ?
```

cat filename | sort | uniq -c

```

regards,
Hardik

---

### Post by ghostdog74 on 2008-08-30
> **rangalo said:**
> 
I am not an expert by shouldn't following  command work ?
```

cat filename | sort | uniq -c

```


no need for cat. most tools in *nix takes in a file as input.
```

sort file | uniq -c

```

---

### Post by stroyan on 2008-08-30
uniq -d is a better match than uniq -c.
It outputs lines that have duplicates.
Then a wc command can report the number of such lines.
```

sort file | uniq -d | wc -l

```

---

