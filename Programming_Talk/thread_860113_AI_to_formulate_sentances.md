---
title: "AI to formulate sentances"
date: 2008-07-15
forum: Programming Talk
---

### Post by wepalm on 2008-07-15
So I was wondering how to make a program(chatterbot) formulate sentences?  What would be a good strategy on coding it? Also are there any suggesting languages I should use?

---

### Post by CptPicard on 2008-07-15
Is it because to make a program chatterbot formulate sentances what
would be a good strategy on coding it also are there any suggesting
languages you should use that you came to me?


:) Seriously speaking, you could try constructing some kind of a formal grammar for sentences and then just pretty much randomly generate from there, possibly keeping track of some keywords and guiding the generation using those. But it is of course a very difficult subject...

---

### Post by pmasiar on 2008-07-15
It was done 40 years ago: [http://en.wikipedia.org/wiki/ELIZA](http://en.wikipedia.org/wiki/ELIZA)

---

### Post by wepalm on 2008-07-15
> **CptPicard said:**
> :) Seriously speaking, you could try constructing some kind of a formal grammar for sentences and then just pretty much randomly generate from there, possibly keeping track of some keywords and guiding the generation using those. But it is of course a very difficult subject...

Well at the moment I don't really care about *what* words it chooses.  I just want to get sentence structure and patterns down first, after that I'll make word links (pet - cat, pet - dog).

---

### Post by wepalm on 2008-07-15
> **pmasiar said:**
> It was done 40 years ago: [http://en.wikipedia.org/wiki/ELIZA](http://en.wikipedia.org/wiki/ELIZA)

Yes, I know it was.  There's just a few problems with it.  1) it can't "learn".  2)There are so many versions it is almost impossible to find the original.  3)I want to create one myself(with your help ofcourse =)

---

### Post by scragar on 2008-07-15
you could program it with various rules of grammar(such as how to keep tense etc) and see how it goes, refining as required. Might take a while though.

---

### Post by Zugzwang on 2008-07-15
You might want to try out some software (also available as a "web service" that does something similar to what you want:

[SCIgen - An Automatic CS Paper Generator]("http://pdos.csail.mit.edu/scigen/")

You can download the source code and as far as I remember, they also use some formal grammar or so.

---

### Post by wepalm on 2008-07-15
> **scragar said:**
> you could program it with various rules of grammar(such as how to keep tense etc) and see how it goes, refining as required. Might take a while though.

Yeah thats what I was thinking.  I found this site ([http://www.towson.edu/ows/SentPatt.htm](http://www.towson.edu/ows/SentPatt.htm)) that has a list of the 10 most common Sentence Patterns.  The only thing I can think of is programming those in,  having a file for each part of the sp, reading the file and randomly choosing them.  Then for the learning part I could have it compare sentences that it reads to each structure if it fits one structure, it links two of the main words together(in a new "link" file).  Eventually to have sentences make sense it would find words that link and use those together in a sentence.  Would this work(That was just me going on about an idea formulating it as i went, so if it doesnt make sense im sorry)?

---

### Post by scragar on 2008-07-15
I'd do it with a DB of words, have an field for each match(so "past-sense verb" (eg: "ran" or "ordered") or whatever), then searching for a random result where that field is not empty.

---

### Post by wepalm on 2008-07-15
> **Zugzwang said:**
> [SCIgen - An Automatic CS Paper Generator]("http://pdos.csail.mit.edu/scigen/")

You can download the source code and as far as I remember, they also use some formal grammar or so.

That looks like it does exactly what I want.  Now just to download it and look at its code =)

---

### Post by wepalm on 2008-07-15
> **scragar said:**
> I'd do it with a DB of words, have an field for each match(so "past-sense verb" (eg: "ran" or "ordered") or whatever), then searching for a random result where that field is not empty.

This would probably be more helpful when trying to link words.

---

### Post by scragar on 2008-07-15
I can imagine future updates adding word linking though, so it could talk about at topic slightly better(the smarterchild MSN thing is forever asking "so what is so intresting about *programmed*" etc, which is fairly stupid).

---

### Post by wepalm on 2008-07-15
> **scragar said:**
> I can imagine future updates adding word linking though, so it could talk about at topic slightly better(the smarterchild MSN thing is forever asking "so what is so intresting about *programmed*" etc, which is fairly stupid).

Thats the exact reason why I want to do this.  That was the problem with ELIZA and ALICE.  Its always the same 5 responses. :popcorn:

---

### Post by Zugzwang on 2008-07-15
> **wepalm said:**
> Thats the exact reason why I want to do this.  That was the problem with ELIZA and ALICE.  Its always the same 5 responses. :popcorn:

Have you tried MEGAHAL? It uses a Markov chain model to generate sentences out of a given database of examples. It's in the repositories!

---

### Post by wepalm on 2008-07-15
> **Zugzwang said:**
> Have you tried MEGAHAL? It uses a Markov chain model to generate sentences out of a given database of examples. It's in the repositories!

I have tried MEGAHAL but I used the online version(there was no download that I could find).  Is it really in the repositories?  I must look into this.

---

### Post by pmasiar on 2008-07-15
[http://nltk.sourceforge.net/index.php/Main_Page](http://nltk.sourceforge.net/index.php/Main_Page) - Python's Natural Language Toolkit - has 6 chatbots sources: [http://nltk.org/nltk/chat/](http://nltk.org/nltk/chat/)

---

