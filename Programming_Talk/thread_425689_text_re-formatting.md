---
title: "text re-formatting"
date: 2007-04-27
forum: Programming Talk
---

### Post by allyourzigg on 2007-04-27
Hello, I would like to take a text file look for the occurence of a word and then insert dashes 2 lines above that word to seperate a file into logical sections is this possible to do in bash alone, or do I have to use another language?

---

### Post by pmasiar on 2007-04-27
I would go with Python, something simple like:

```

matchwords = ["a", "b", "c"]
for line in open("path/to/file.txt"):
    for word in line.split(" "):
        if word in matchwords:
            # print whatever you want

```

---

### Post by allyourzigg on 2007-04-27
python sounds good, but what you said doesn't seem to do what I wan't it to, plus if this is possible in bash it would be even better

---

### Post by pmasiar on 2007-04-27
It is not obvious to me what "insert 2 dashes" means - but you have the line and the word, do whatever you feel. 

I use Python for mostly everything. It is one language to learn to do it all :-)

---

### Post by allyourzigg on 2007-04-27
I meant like this but I cannot figure out how to make it place the dashed line there
-----

http://

---

### Post by ghostdog74 on 2007-04-28
an awk script
```

awk ' /searchstring/ { print previous2"\n--\n"   }
{
   previous2=previous1
   previous1 = $0
   
}
{print } ' "file"

```

---

### Post by allyourzigg on 2007-04-28
ghostdog that is SO close to what I want ! I knew you could do this in the shell. One problem though, the output from that looks like this:
```

   MIT Dean Resigns After Claims About Resume Surface

--

   http://www.foxnews.com/story/0,2933,268946,00.html

   Marilee Jones falsely bolstered her credentials to get a job with MIT, and
   over the course of her career claimed to have earned degrees from three
   schools.

```

when what I need is something like this
```

   -----------------------------
   MIT Dean Resigns After Claims About Resume Surface
   http://www.foxnews.com/story/0,2933,268946,00.html

   Marilee Jones falsely bolstered her credentials to get a job with MIT, and
   over the course of her career claimed to have earned degrees from three
   schools.

```
that way the news items are seperate and no one gets their eyes burnt out trying to find them. thanks for the help so far

---

### Post by ghostdog74 on 2007-04-28
hmm..you could modify the search string? mayb you want to show the actual input file?

---

### Post by allyourzigg on 2007-04-28
I can't think of a different search string because the only thing that remains constant is the http in front of the links, ( news titles change and so do their summaries ) here is a sample of the updated news feed after the html has been striped out by links -dump. This is technically ready for printing but I think you'll agree when I say it's difficult to tell where an article summary ends and the next begins.
```
 Feds: Tour Buses Used to Traffic Drugs Across United States
   http://www.foxnews.com/story/0,2933,269052,00.html

   Three men face federal charges in connection with a drug ring that used
   tour buses to move millions of dollars and marijuana between Detroit and
   Tucson, Ariz.

   Iditarod Organizers Hear Testimony of Alleged Dog Abuse
   http://www.foxnews.com/story/0,2933,269044,00.html

   Iditarod dog race organizers heard testimony from mushers and others on
   Friday as they determined the punishment for a musher disqualified for
   allegedly abusing his dogs during the race.

   NYPD Arrests Suspect in Mugging of 101-Year-Old Woman
   http://www.foxnews.com/story/0,2933,269042,00.html

   New York City police say they have arrested a man on Friday in the mugging
   last month of a 101-year-old woman. 
```

that is the raw feed after html is striped, I would like to make it look like the below sample after being processed by something , lets say awk scince it's the closest I've gotten so far.

```
	-----------------------------------------
   Feds: Tour Buses Used to Traffic Drugs Across United States
   http://www.foxnews.com/story/0,2933,269052,00.html

   Three men face federal charges in connection with a drug ring that used
   tour buses to move millions of dollars and marijuana between Detroit and
   Tucson, Ariz.
	-----------------------------------------
   Iditarod Organizers Hear Testimony of Alleged Dog Abuse
   http://www.foxnews.com/story/0,2933,269044,00.html

   Iditarod dog race organizers heard testimony from mushers and others on
   Friday as they determined the punishment for a musher disqualified for
   allegedly abusing his dogs during the race.
	-----------------------------------------
   NYPD Arrests Suspect in Mugging of 101-Year-Old Woman
   http://www.foxnews.com/story/0,2933,269042,00.html

   New York City police say they have arrested a man on Friday in the mugging
   last month of a 101-year-old woman.
```
I hope this is possible

---

### Post by ghostdog74 on 2007-04-28
that's quite difficult if you don't know your search string. the only thing i see from your sample output is for every second blank line you inserted dashes
```

awk ' /^$/ { c++ }
c%2==0 {
 for (i=0;i<60;i++) dash= dash"-"  
 sub(/^$/,dash,$0)   
}
{print ;dash=""}
' "file"

```
output:
```

./test.sh
 Feds: Tour Buses Used to Traffic Drugs Across United States
   http://www.foxnews.com/story/0,2933,269052,00.html

   Three men face federal charges in connection with a drug ring that used
   tour buses to move millions of dollars and marijuana between Detroit and
   Tucson, Ariz.
------------------------------------------------------------
   Iditarod Organizers Hear Testimony of Alleged Dog Abuse
   http://www.foxnews.com/story/0,2933,269044,00.html

   Iditarod dog race organizers heard testimony from mushers and others on
   Friday as they determined the punishment for a musher disqualified for
   allegedly abusing his dogs during the race.
------------------------------------------------------------
   NYPD Arrests Suspect in Mugging of 101-Year-Old Woman
   http://www.foxnews.com/story/0,2933,269042,00.html

   New York City police say they have arrested a man on Friday in the mugging
   last month of a 101-year-old woman.


```
this is the closest i can give you.

---

### Post by allyourzigg on 2007-04-28
thats absolutly perfect!!
Thank you so much for your time and effort, I really need to learn how to use awk and sed but the man pages are so confusing, thanks again!

---

