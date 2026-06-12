---
title: "Help writing python code that deletes lines based on what they say"
date: 2009-12-27
forum: Programming Talk
---

### Post by antman8969 on 2009-12-27
Ok so i'm pretty new to python (new enough that you should treat me as tho I know nothing :() and I would greatly appreciate some input on what commands I would have to use to write a script which does the following:

I want to take a series of text lines and run a script that deletes all lines that dont start with "You", so that only the lines that DO start with "You" are left in the file, and make a new file for the output. So basically, I want to turn this:

 > 
 Ulgorn Raider inflicted 1 damage on Training Dummy. 
    Ulgorn Raider inflicted 1 damage on Training Dummy. 
    Ulgorn Raider inflicted 1 damage on Training Dummy. 
    Ulgorn Raider inflicted 1 damage on Training Dummy. 
   You have joined the Ishalgen region channel. 
   You have joined the Ishalgen trade channel. 
   You have joined the LFG Channel. 
   Ulgorn Raider inflicted 1 damage on Training Dummy. 
   Ulgorn Raider inflicted 1 damage on Training Dummy. 
You inflicted 54 damage on Training Dummy. 
   You inflicted 5 damage on Training Dummy. 
   You inflicted 79 damage on Training Dummy by using Weakening Severe Blow I. 
  
into this:


 > 
   You have joined the Ishalgen region channel. 
   You have joined the Ishalgen trade channel. 
   You have joined the LFG Channel. 
 You inflicted 54 damage on Training Dummy. 
   You inflicted 5 damage on Training Dummy. 
   You inflicted 79 damage on Training Dummy by using Weakening Severe Blow I.
any idea what commands I would have to use in the script for a start?

In this example there is only one message that is identical each time it appears, but other messages will come up regularly too that start differently so I can't just delete thoat content specifically.

---

### Post by BenAshton24 on 2009-12-28
[PHP]
#!/usr/bin/env python

#A list for the lines of text that start with "You"
f2 = []

#A "for" loop to go though each of the lines in "file.txt"
for line in open("file.txt"):

    # If the first three characters equal "You":
    if line[0:3] == "You":

        # Then append them to the list
        f2.append(line)

#open a new file for writing the changed text to
f = open("file2.txt","w")

#write the lines from the list
f.writelines(f2)

#close the file
f.close()
[/PHP]

---

### Post by ghostdog74 on 2009-12-28
```

>>> for line in open("file"):
...   for item in line.split():
...      if item == "You":
...           print line.strip()
...
You have joined the Ishalgen region channel.
You have joined the Ishalgen trade channel.
You have joined the LFG Channel.
You inflicted 54 damage on Training Dummy.
You inflicted 5 damage on Training Dummy.
You inflicted 79 damage on Training Dummy by using Weakening Severe Blow I.


```

---

### Post by DaithiF on 2009-12-28
slight variation to ghostdogs, as I think you only wanted to match 'You' appearing at the start of a line:
```
for line in open('somefile'):
  if line.startswith('You'):
    print line.strip()
```

---

### Post by antman8969 on 2009-12-28
lol thx a lot

Each code works too, I guess theres never one correct way to script something is there.
Do the shorter codes have any limitations to them? Is there any difference at all?

---

### Post by BenAshton24 on 2009-12-28
> **antman8969 said:**
> lol thx a lot

Each code works too, I guess theres never one correct way to script something is there.
Do the shorter codes have any limitations to them? Is there any difference at all?

In programming, with any language, there is rarely only one way to do things. For example, I subscript the string in my example to get the first 3 characters of each line (" **line[0:3]** ") whereas ghostdog74 splits the line and then checks to see if the first word is "You". DaithiF achieves the goal in yet another way by using the startswith() method.

Mine is the only one that does everything that you asked for (removing the lines that don't start with "You" and saving the remaining lines to a different file). ghostdog74's & DaithiF's code print out the lines that you want, but do not save them to a file.

Hope this helps,
Ben.

---

### Post by Can+~ on 2009-12-28
> **antman8969 said:**
> lol thx a lot

Each code works too, I guess theres never one correct way to script something is there.
Do the shorter codes have any limitations to them? Is there any difference at all?

All the answers tackle it different, though, some of them are better. For example:

**BenAshton's**
[PHP]    if line[0:3] == "You":[/PHP]

This is, assuming that the line doesn't start with a space, or any other character. It also has the problem of that, it will be difficult to update later (If you want to seek for lines that start with ASDAGAHGSDASDSD, will require re-mesuring the size of the slice).

And it loads everything to memory, which, could be expensive if the file is large (and it will probably be, because it looks like a WoW logfile).

**Ghostdog's**
[PHP]for item in line.split():[/PHP]

Split is great, but it's overkill in this scenario, it would be wiser to do:

[PHP]firstword, therest = line.split(" ", 1)[/PHP]

**DaithiF's**
I like this one, although, I'm more inclined with using the "with" statement, as it explicitly closes the file after using it.

**This is my approach:**
[PHP]
#!/usr/bin/env python

outfile = open("result.log", "w")

with open("infile.log") as infile:
	for line in infile:
		if line.startswith("You"):
			outfile.write(line)[/PHP]

OP: Btw, did you know you can filter combat log in Wow too?

---

### Post by ghostdog74 on 2009-12-28
> **DaithiF said:**
> slight variation to ghostdogs, as I think you only wanted to match 'You' appearing at the start of a line:
```
for line in open('somefile'):
  if line.startswith('You'):
    print line.strip()
```

that's a bit different. If "You" is what OP wants , it fails if there is "Your". better to do it like this
```

startswith("You ")

```

---

### Post by ghostdog74 on 2009-12-28
> 
[PHP]firstword, therest = line.split(" ", 1)[/PHP]

fails if line contains only 1 word. Regarding whether its overkill or not, depends on OP. If he is going to look for other fields in the string, split is certainly not overkill.

---

### Post by antman8969 on 2009-12-30
> **Can+~ said:**
> All the answers tackle it different, though, some of them are better. For example:

**BenAshton's**
[php]    if line[0:3] == "You":[/php]This is, assuming that the line doesn't start with a space, or any other character. It also has the problem of that, it will be difficult to update later (If you want to seek for lines that start with ASDAGAHGSDASDSD, will require re-mesuring the size of the slice).

And it loads everything to memory, which, could be expensive if the file is large (and it will probably be, because it looks like a WoW logfile).

**Ghostdog's**
[php]for item in line.split():[/php]Split is great, but it's overkill in this scenario, it would be wiser to do:

[php]firstword, therest = line.split(" ", 1)[/php]**DaithiF's**
I like this one, although, I'm more inclined with using the "with" statement, as it explicitly closes the file after using it.

**This is my approach:**
[php]
#!/usr/bin/env python

outfile = open("result.log", "w")

with open("infile.log") as infile:
    for line in infile:
        if line.startswith("You"):
            outfile.write(line)[/php]OP: Btw, did you know you can filter combat log in Wow too?

That was very helpful, thanks a lot. And it's actually from Aion lol. The game devs havnt implemented a real way of saving your combat log, so you have to change the config file to save ALL output in a text doc, including the LFG channel and npc talk and all that jazz. They also don't have tooltips, so I wanted to figure out how each rating from each stat converted to a percent, but to do that, i needed to save the combat log, and you see the problem lol.

Thanks for everyone else for the help too, I'm starting my computer science courses next semester (working with python) so i can't wait to be able to do this myself. :)

If it matters, I actually ended up using [BenAshton24]("http://ubuntuforums.org/member.php?u=608687")'s solution, just because with what I konw, it was the easiest to edit in terms of specifying where to save the output, and adding more search features.

---

### Post by The Cog on 2009-12-30
This:```
with open("infile.log") as infile:
    for line in infile:
        if line.startswith("You"):
            outfile.write(line)  
``` will also trigger on lines such as "Your zip is undone.". Maybe look for "You " instead?

Split() splits on tabs and newlines as well as spaces, which may or may not be what you want.

---

### Post by MaxIBoy on 2009-12-30
You do not need Python for this. Grep is a better tool.
```
cat name_of_file | grep "^You"
```If this is just part of a larger python program, use the os.system() function to run the above command:
```
output = os.system('cat name_of_file | grep "^You"')
``` or ```
os.system('echo "'+variable_containing_your_data+'" | grep "^You"')
```If you need this to be cross-platform, then unfortunately this won't work.

---

### Post by ghostdog74 on 2009-12-31
> **MaxIBoy said:**
> You do not need Python for this. Grep is a better tool.
```
cat name_of_file | grep "^You"
```

don't need to use cat. Its useless. just pass the file to grep

> 
If this is just part of a larger python program, use the os.system() function to run the above command:
```
output = os.system('cat name_of_file | grep "^You"')
``` or ```
os.system('echo "'+variable_containing_your_data+'" | grep "^You"')
```If you need this to be cross-platform, then unfortunately this won't work.
why suggest a solution that is worse than those already provided.?

---

