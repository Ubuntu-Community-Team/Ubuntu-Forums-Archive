---
title: "For loop with a list...bug?"
date: 2006-09-14
forum: Programming Talk
---

### Post by ridgerunner7 on 2006-09-14
It's possible to use a quoted elements list in a for loop.

for i in "A blah" "B blah"; do
  echo $i
done

which echo this: 
A blah
B blah

What I want to do is obtain a directory list so that I can do actions on each directory. Sounds simple but the problem is some directories contain spaces. But using the quoted elements as above it shouldn't be a problem, right?

I'm using this because 'ls -d' doesn't seem to work correctly:
ls -pAQ | grep / | sed 's/\///'

So I'm trying something like this:

for i in $( ls -pAQ | grep / | sed 's/\///'); do
  echo $i
done

which echo this:
"A
blah"
"B
blah"

OR to make it more obvious, using a variable, something like this:

DirectoryList=$( ls -pQ | grep / | sed 's/\///')
echo DirList=$DirectoryList; echo
for i in $DirectoryList; do
  echo $i
done

which echo this:
DirList="A blah" "B blah"

"A
blah"
"B
blah"

Anybody got an explanation for why these don't work like the first instance? Is it a bug or am I misunderstanding some syntax here? Does anyone have a solution or workaround?

---

### Post by LordHunter317 on 2006-09-14
You have to double quote the variable expansion to perserve braces.  So "$i" instead of $i.  Plus, using backticks like you are is dangerous.  Never use $() or `` on an unbounded expression.

---

### Post by ridgerunner7 on 2006-09-14
Thanks for the hint!! Although it was the list variable that needed double quotes to expand. So here's my correction.
```
for i in "$( ls -pAQ /home/shares/ | grep / | sed "s/\///")"; do
  echo $i
done
```
AFAIK, I wasn't using backticks, they were single quotes. Thanks for the reminder about unbound expressions! Actually this was more an exercise of my point than a working script. But point taken! While we're on this topic...how would you write it differently. First blush, I was thinking to use a specific directory but links could be a problem. I haven't given much thought yet to how to limit it. 

My task is to make this script run mundane tasks on user's shares on a server. User's sometimes change the permissions or group settings without thought to how it impacts their co-workers. This script will only (lol) be used by admins.

Any thoughts or suggestions? I suppose I could use "find" and limit the maxdepth.

---

### Post by LordHunter317 on 2006-09-15
Describing what you clearly want to do is a first start.  As a rule, if you're using ls, there's likely a problem.

---

