---
title: "How to manipulate content of text file into separate strings?"
date: 2007-10-17
forum: Programming Talk
---

### Post by nightfrost on 2007-10-17
Hi all!

I'm playing around with bash a little (I'm no programmer, but one day soon I will dive into python, I'm thinking) and need some help when it comes to reading a text file and manipulating the string. More specifically, I want to read the file ~/.smb/fusesmb.cache, which might for example hold:

/WORKGROUP/COMPUTER/Samba Share

And then, I want to add each string between the slashes in different variables so that I have.

$WORKGROUP="WORKGROUP"
$SERVER="COMPUTER"
$SHARE="Samba Share"

The question is, how do I manipulate the text file into separate strings?

Thanks a lot!

---

### Post by jfinkels on 2007-10-17
> **nightfrost said:**
> 
The question is, how do I manipulate the text file into separate strings?


The answer is, "Use python!":```

>>> st = '/WORKGROUP/COMPUTER/Samba Share'
>>> l = st.split('/')
>>> print l
['', 'WORKGROUP', 'COMPUTER', 'Samba Share']

```

---

### Post by ghostdog74 on 2007-10-17
> **nightfrost said:**
> 
The question is, how do I manipulate the text file into separate strings?

it depends on what you want to do with them, that's the whole point. storing into separate variables means nothing, until you use them for something.
Better to tell us what you intend to do with the ~/.smb/fusesmb.cache file.
with that much information , this is a way to do it ( in awk though). Assuming that file contains only /WORKGROUP/COMPUTER/Samba Share
```

#also, this assumes you know the positions of those strings you want to split
awk -F"/" '{print $2,$3,$4 }' ~/.smb/fusesmb.cache

```

---

### Post by ghostdog74 on 2007-10-17
> **jfinkels said:**
> The answer is, "Use python!":[code]

i would rather call it a suggestion.

---

### Post by jfinkels on 2007-10-17
> **ghostdog74 said:**
> i would rather call it a suggestion.

I was just being cheeky :D

---

### Post by Wybiral on 2007-10-17
> **jfinkels said:**
> I was just being cheeky :D

Looked like a good answer to me.

---

### Post by ghostdog74 on 2007-10-17
> **Wybiral said:**
> Looked like a good answer to me.
The "answer" is only as good as what the OP chooses it to be.

---

### Post by pmasiar on 2007-10-17
> **nightfrost said:**
> I'm playing around with bash a little (I'm no programmer, but one day soon I will dive into python, I'm thinking) 

Learning Python is good idea. You can do everything bash does (and more), with better syntax, and with Python shell to try code in a simple way. So you end up using bash only for the most trivial things.

But "Dive into Python" is book for experienced programmers, there are free online books better suited for a learner. See wiki in my sig for links.

processing a file in Python, line by line:
[php]
for line in open('path/to/file'):
     parts = line.split('/')
     # etc
[/php]

---

### Post by nightfrost on 2007-10-17
Wow, thank you all for amazingly fast answers. The thing I was trying to do was to write a simple gui frontend for fusesmb's config file in order to learn python (pygtk). I'm thinking a _really_ simple configuration gui. But for some reason, I thought I'd like to do it using bash + zenity first (almost as a mockup), and then move on to learn python. I have lots to follow up on now, especially the links in the last post will prove to be helpful, I'm sure. I think I'll just try to learn python.

(In fact, I wasn't aware that there was a book called 'dive into python'. I was just using the expresseion. Funny :-))

Once again, thanks a lot!

---

### Post by slavik on 2007-10-17
> **ghostdog74 said:**
> i would rather call it a suggestion.
You are correct. The answer would be Perl :)

---

### Post by pmasiar on 2007-10-17
> **slavik said:**
> You are correct. The answer would be Perl :)

If you are so eager to promote Perl, why you did not included simple code to read file and split on '/' to give OP idea what are promised Perl goods? And then let OP to decide if it is more obvious than Python?

Perl might be good for old admins with experience with bash, sed, awk, trained to line noise, but for beginner?

---

### Post by dwblas on 2007-10-17
> And then, I want to add each string between the slashes in different variables so that I have.

$WORKGROUP="WORKGROUP"
$SERVER="COMPUTER"
$SHARE="Samba Share"In Python, you do not have to split the line to replace text.
line.replace( "/$WORKGROUP", "/WORKGROUP")
or whatever you want to replace.

---

### Post by slavik on 2007-10-17
it pretty much looks like the Python version, except in Perl split is a not a method of the string class like in Java.

due to popular demand, here is code :)
array of hashes version
```

open $file, "smbsomething" or die $!;
while ($line = <$file>) {
  @arr = split /\//, $line # I think a better way is to use regex
  push @stuffs, {WORKSHOP => $arr[1], SERVER => $arr[2], SHARE => $arr[3]};
}
close $file;

```

---

### Post by ghostdog74 on 2007-10-17
> **slavik said:**
> You are correct. The answer would be Perl :)

see post #7

---

### Post by slavik on 2007-10-17
I did see it ... what about it? Looks like a fine post to me, nothing out of the ordinary ... Am I missing something?

---

### Post by ghostdog74 on 2007-10-17
> **slavik said:**
> Am I missing something?
nevermind if you can't understand. its ok.

---

