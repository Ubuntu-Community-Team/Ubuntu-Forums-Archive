---
title: "Extracting data from text file to input to another text file"
date: 2012-03-25
forum: Programming Talk
---

### Post by xalx on 2012-03-25
So what I have is a text file of attributes and a text file log which has these attributes and an action along side it

e.g. 10-19-attribute1: details of action 11-06-attribute2: details of action 10-19-attribute1: details of action

The list goes on for a while. So what I'm trying to do is extract each line pertaining to each attribute.

In Ubuntuu I've done grep "10-19-attribute1" /path/to/source > attribute1.txt

This works fine. But what I'd like to do is use the text file of attributes to (there are a lot) so I don't have to do this for each one individually.  Is this possible?

I made a text file with the command grep "attributeX" /path/ > attributeX.txt for all the greps I need to perform.  I thought I would be able to copy and paste this into a shell at first but it seems to skip a lot of the commands or doesn't run them properly missing some text in the lines.
I then tried to see if I could cat the text file with grep commands to pass onto grep thinking it would pick it up that way but that just didn't work.

Could anyone lend any insight on how I could achieve my goal?  I'm pretty new to Ubuntu and shell scripting.

---

### Post by r-senior on 2012-03-25
If I understand correctly, this should do it (depends on whether those number prefixes matter):

```
for attribute in $(cat attributes.txt); do grep "$attribute" log.txt > "$attribute.txt"; done
```

That assumes attributes.txt has one entry per line.

---

### Post by xalx on 2012-03-25
Thanks for the quick reply!

So I'm nearly there.  The **for** loop seems to be able to read each attribute correctly as it creates a individual text file for each attribute.  But every text file is empty.

Considering that each attribute listed in attributes.txt is in the format of *11-06-attribute2:* for my **do grep** do I need to put *"$attribute:"*?

---

### Post by r-senior on 2012-03-25
The colon shouldn't matter, grep should find the value as a substring. Whatever name the files come out as (minus the .txt suffix) is what it's searching for. What happens if you grep manually for one of those strings?

Here's my test, something must be different that I've not understood:

```
$ cat attributes.txt 
10-19-attribute1
$ cat log.txt 
10-19-attribute1: details of action 
11-06-attribute2: details of action 
10-19-attribute1: details of action
$ for attribute in $(cat attributes.txt); do grep "$attribute" log.txt > "$attribute.txt"; done
$ cat 10-19-attribute1.txt 
10-19-attribute1: details of action 
10-19-attribute1: details of action

```

---

### Post by xalx on 2012-03-25
I fed in an attribute manually to grep and it created the text file with the details I was after.  Just not sure why it isn't doing it for all of them.

---

### Post by SeijiSensei on 2012-03-25
You're not encasing $attribute in single quotes, are you?  That treats the string as a literal, rather than replacing it with the contents of $attribute.

---

### Post by xalx on 2012-03-25
> **SeijiSensei said:**
> You're not encasing $attribute in single quotes, are you?  That treats the string as a literal, rather than replacing it with the contents of $attribute.

Nope, definitely using double quotes around $attribute

---

### Post by xalx on 2012-03-25
> **r-senior said:**
> The colon shouldn't matter, grep should find the value as a substring. Whatever name the files come out as (minus the .txt suffix) is what it's searching for. What happens if you grep manually for one of those strings?

Here's my test, something must be different that I've not understood:

```
$ cat attributes.txt 
10-19-attribute1
$ cat log.txt 
10-19-attribute1: details of action 
11-06-attribute2: details of action 
10-19-attribute1: details of action
$ for attribute in $(cat attributes.txt); do grep "$attribute" log.txt > "$attribute.txt"; done
$ cat 10-19-attribute1.txt 
10-19-attribute1: details of action 
10-19-attribute1: details of action

```

I did as you did in your code, and even made a copy of my attributes.txt to just one attribute to see if it was a problem with too many.  Still output a blank file though, but with the correct attribute.txt name.

But entering a value manually it found and created the file fine.

---

### Post by SeijiSensei on 2012-03-25
How about modifying the script to report each attribute so you can check what's happening:

```

for ...
do
    echo "Attribute: $attribute"
    grep ...

done

```

---

### Post by r-senior on 2012-03-25
I'm wondering if it's trailing spaces in the attributes file ... so 

```
echo "Attribute: ($attribute)"
``` would be good.

---

### Post by xalx on 2012-03-25
Performing an echo without the () echo's fine and lists the attribute names but still creates blank files.

Thanks for your help so far with this guys

---

### Post by xalx on 2012-03-25
Ok well I somehow managed to fix it.

I copied the contents of my text files into a new file and all of a sudden it's working? Not too sure why but I can't complain either.  Maybe I had some formatting issues with one of the files.

Either way, thank you both for your help on this.  You have been a big help

---

### Post by xalx on 2012-03-25
Actually it's partially working.

So it's created the files with content now which is fine.

But after looking at some of the files it is picking up some of the wrong data.

Example would be:

10-19-attribute1.txt will contain information from 10-19-attribute19, 10-19-attribute11, 10-19-attribute12 

etc

Is there anyway to filter this so it only displays for the attribute I'm looking for in each file?

---

### Post by r-senior on 2012-03-25
You know what I said earlier about not needing a colon ... ;)

```
for attribute in $(cat attributes.txt); do grep "$attribute:" log.txt > "$attribute.txt"; done
```

---

### Post by xalx on 2012-03-25
Haha, yep thanks! I managed to work that part out just by playing around.

Ok so one last question on this and I'm done!

So I have all my files now that I need.  But I want to remove everything before the first white space in each line.

So this

10-19-attribute1: details of action 

Becomes this

details of action

I've used this sed command,

sed 's/[^ ]* //' 10-19-attribute1.txt

But it only outputs to the screen. I want it to directly write to the file but for every single one of the text files I have.  I figure using
sed 's/[^ ]* //' *.txt 
would do it but it still just writes to the screen.

---

### Post by xalx on 2012-03-25
Figured it out

sed -i 's/[^ ]* //' *.txt 

I needed -i to work on the input file.

Thanks for the help guys.  This thread has now been solved!

---

