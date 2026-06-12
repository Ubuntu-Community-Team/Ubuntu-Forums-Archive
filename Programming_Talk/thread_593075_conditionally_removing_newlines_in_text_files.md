---
title: "conditionally removing newlines in text files"
date: 2007-10-26
forum: Programming Talk
---

### Post by DuplexEmotions on 2007-10-26
Howdy!

I have some text files from Project Gutenberg (a repository of public domain literature) that I'd like to print and bind. I hate reading on the monitor.

The issue I'm having is the txt files have, instead of word wrap, manual carriage returns. I'm attaching. It's a bit hard to explain, so I'll attempt to show it.


Here's the first paragraph of "Notes From the Underground" by Fyodor Dostoyevsky


I am a sick man. ...  I am a spiteful man.  I am an unattractive man.  I

believe my liver is diseased.  However, I know nothing at all about my

disease, and do not know for certain what ails me.  I don't consult a doctor

for it, and never have, though I have a respect for medicine and doctors. 

Besides, I am extremely superstitious, sufficiently so to respect medicine,

anyway (I am well-educated enough not to be superstitious, but I am

superstitious).  No, I refuse to consult a doctor from spite.  That you

probably will not understand.  Well, I understand it, though.  Of course, I

can't explain who it is precisely that I am mortifying in this case by my

spite: I am perfectly well aware that I cannot "pay out" the doctors by not

consulting them; I know better than anyone that by all this I am only

injuring myself and no one else.  But still, if I don't consult a doctor it is

from spite.  My liver is bad, well--let it get worse!

See what I mean? the line wraps are manually inserted with a carriage return. This is causing me no small amount of trouble while I reformat it for printing. I have found some code snippets such as 

tr "\n" " " <input_file >output_file

that will remove the newlines, but the paragraphs are separated by new lines as well. What I would like to do is write a script that removes a new line unless it has another new line before or after it. Unfortunately, I'm a bit over my head here. Does anybody have any suggestions, bash scripts, or advice?

---

### Post by kast on 2007-10-26
Hey I'm far from an expert, but what would happen if you used **tr** to remove the carriage returns?

**tr -d '\15' < file**

---

### Post by DuplexEmotions on 2007-10-26
I tried that but for some reason it doesn't do anything. I've tried 

tr -d '\15' < notestest.txt > notestest2.txt

as well.

---

### Post by LaRoza on 2007-10-26
'10' is the newline character I think, but it will strip all of them.

---

### Post by kast on 2007-10-26
how about 
[B]
tr -d '\n'[/B] < file

---

### Post by kast on 2007-10-26
Sorry i believe you have done something like that, removes all new lines, not really a good idea :)

---

### Post by DuplexEmotions on 2007-10-26
exactly.

---

### Post by LaRoza on 2007-10-26
Found the answer!

I did it on Windows, so you'll have to do it with another tool probably.

Here is what I did.

I opened the file in a hex editor, [http://mh-nexus.de/hxd/](http://mh-nexus.de/hxd/), which probably runs in Wine.

Use the search and replace function to replace the hex code "0D 0A 0D 0A" to something you can change later, like "AA AA AA AA". Then change all the "0D 0A" to blank (delete them). Now change the "AA AA AA AA" to "OD 0A 0D 0A".

"0D 0A" is a Windows CR-NL.

I realize this isn't the fancy script that I haven't taken time to write, but it works...

(The data type is "Hex" not "string")

---

### Post by kast on 2007-10-26
**nawk -v ORS='' '1' file > file2**

---

### Post by DuplexEmotions on 2007-10-26
nawk generated a new file but didn't have any changes. this is starting to get somewhat frustrating.

---

### Post by kast on 2007-10-26
really? that's what i get

I am a sick man. ... I am a spiteful man. I am an unattractive man. Ibelieve my liver is diseased. However, I know nothing at all about mydisease, and do not know for certain what ails me. I don't consult a doctorfor it, and never have, though I have a respect for medicine and doctors.Besides, I am extremely superstitious, sufficiently so to respect medicine,anyway (I am well-educated enough not to be superstitious, but I amsuperstitious). No, I refuse to consult a doctor from spite. That youprobably will not understand. Well, I understand it, though. Of course, Ican't explain who it is precisely that I am mortifying in this case by myspite: I am perfectly well aware that I cannot "pay out" the doctors by notconsulting them; I know better than anyone that by all this I am onlyinjuring myself and no one else. But still, if I don't consult a doctor it isfrom spite. My liver is bad, well--let it get worse!

I am a sick man. ... I am a spiteful man. I am an unattractive man. I

believe my liver is diseased. However, I know nothing at all about my

disease, and do not know for certain what ails me. I don't consult a doctor

for it, and never have, though I have a respect for medicine and doctors.

Besides, I am extremely superstitious, sufficiently so to respect medicine,

anyway (I am well-educated enough not to be superstitious, but I am

superstitious). No, I refuse to consult a doctor from spite. That you

probably will not understand. Well, I understand it, though. Of course, I

can't explain who it is precisely that I am mortifying in this case by my

spite: I am perfectly well aware that I cannot "pay out" the doctors by not

consulting them; I know better than anyone that by all this I am only

injuring myself and no one else. But still, if I don't consult a doctor it is

from spite. My liver is bad, well--let it get worse!

---

### Post by kast on 2007-10-26
first part being the new file after the 

**nawk -v ORS='' '1' file > file2**

---

### Post by DuplexEmotions on 2007-10-26
this is certainly odd, I dont' seem to be getting any changes with any of these commands. very unusual. I really do appreciate all your help thus far.

edit: also, in your example it doesn't append a " " after it takes out the new line so some words are stuck together.

---

### Post by kast on 2007-10-26
ahh.. missed that, sorry. ill keep looking :)

---

### Post by kast on 2007-10-26
I'm wondering if just copying from the post isn't the same as what your working with, could you send me a clip of it in a doc?


[email]eratcliff@inbox.com[/email]

---

### Post by DuplexEmotions on 2007-10-26
Here's the exact .txt file as I got it from gutenberg. it's all of Notes from the Underground. I have a lot of these but I'd like to get this one done first.

EDIT: use this link instead, direct linking is mean. It's the plain text version
[http://www.gutenberg.org/etext/600](http://www.gutenberg.org/etext/600)

---

### Post by DuplexEmotions on 2007-10-26
a friend of mine wrote this script that works pretty well.

#!/usr/bin/perl -w

while (<>) {
  $_ =~ s/
$//g;
  if ($_ =~ /^$/) { print "\n\n"; }
  else { $_ =~ /(.*)\n/; print "$1 "; }
}


it works!

---

### Post by LaRoza on 2007-10-26
> **DuplexEmotions said:**
> 
#!/usr/bin/perl -w

while (<>) {
  $_ =~ s/
$//g;
  if ($_ =~ /^$/) { print "\n\n"; }
  else { $_ =~ /(.*)\n/; print "$1 "; }
}


it works!

Who here says Perl is readable? :)

---

### Post by ghostdog74 on 2007-10-27
not sure if its what you want
```

awk -v RS=="\n\n"?"\n":"" '1' file

```

---

### Post by slavik on 2007-10-27
> **LaRoza said:**
> Who here says Perl is readable? :)
right here buddy!!! :)

```

$_ =~ s/
$//g;

```

perl will not strip away the \n after the s/ ;) it will remove every \n at the end of the line :) (\n\n becomes \n)

then it will skip over empty lines (/^$/) and print all text that is followed by a newline without it (space is appended instead), making the entire file into a single line, which pasted into OOo Writer works very well for printing (same with gedit) since they do wordwrap now.

edit: re-read the source code, it prints \n\n when encountering an empty line ...

---

### Post by kast on 2007-10-27
Well after more scripting on the Shell its off to Perl, good to see that it looks easy :(

hey DuplexEmotions hopefully what you have there will do, i must have ran command after command on that txt you sent the link to, with  no luck!

---

### Post by DuplexEmotions on 2007-10-27
the perl script works really well, does precisely what I needed. Thanks for all the help, everyone.

---

