---
title: "copying songs (first real program)"
date: 2007-06-30
forum: Programming Talk
---

### Post by MiCovran on 2007-06-30
Interested in commenting a simple (but useful) new program?

I realized that it's very tiring collecting manually all music from your hard disk and copying it to (for instance) an mp3 player. So, since I use rhythmox with playlists I thought it would be nice if you could just make "cp" use all songs listed in an exported playlist and copy them to a given directory. So, since I have never programmed anything "real" outside algorithm competitions, I decided to make this program on my own for practice: "m3ucp". :) It uses .m3u playlists (m3u is the simplest playlist format IMO, maybe I'll add other formats later) to "cp" songs to given directories. Source is attached to this post (I needed to add .txt to upload), it's a small program.

Anyway, I would like to hear comments about the program. Anything: idea, code readability, performance, features that could be added (just don't complicate too much ;)), what I must do... The only bug I know for now is strings' bound checking.

Remember, I'm a n00b in practical coding and I'm still learning, so just post all your critics, good or bad.
BTW, this is the first time I used C, not C++ (thought I should practice it too).

---

### Post by kidders on 2007-07-01
Hi there,

A C app might be a little overkill for this particular task ... you may be making life more complicated than it needs to be. For instance, if you knew an m3u only contained absolute references to local files, the same task could be performed with a single shell command...```
for i in $(sed  '/^\s*$\|^#.*/d' test.m3u); do cp $i /dest/path; done
```

In reality of course, there are lots of reasons why something *that* simple would break, so a short shell script would be required (to properly handle URLs, relative paths, and files with odd characters in the filenames). Personally, I would be tempted to go that route, for simplicity's sake.

---

### Post by MiCovran on 2007-07-01
[QUOTE=kidders]A C app might be a little overkill for this particular task[/QUOTE]
The problem is that I only know BASIC, Pascal and C++. I never tried to learn shell scripting (now I see even more that I should). Maybe I should have used C++ (for simplicity's sake :)) because it makes strings easier. But I wanted this to be a practice of coding too. I think I'll rewrite it to C++ soon.

[QUOTE=kidders]to properly handle URLs[/QUOTE]
I never thought of URLs, thanks.

[QUOTE=kidders]files with odd characters in the filenames[/QUOTE]
That's why I use quotation marks for directories from m3us and use '\' for quotation marks that are part of the directory only. I think this should work. Does it? Are quotation marks only one to worry about if filename is written inside quotation marks?
This is confusing to explain. For instance, I use: ```
"/home/user/some new directory/a file with \"quotes\""
``` instead of: ```
/home/user/some\ new\ directory/a\ file\ with\ \"quotes\"
```

Thanks for reply.

Oh, I noticed a bug in line 52: there's something missing at the beginning of the line: ```
if( i > 0 )
```Relative path handling was done in a hurry. Without this "if" the program will not work when it is executed in the same directory as a playlist :(.

---

### Post by kidders on 2007-07-01
Hey again,

> **MiCovran said:**
> Are quotation marks only one to worry about if filename is written inside quotation marks?I wonder how characters like '$', '[', '>', '&', and so on would be treated. The results could be quite dangerous if your "cp" command arguments aren't properly escaped.

---

### Post by dwblas on 2007-07-04
I would suggest learning Python first.  Just my opinion.  You want to start with something that will allow you to do everything you want instead of several languages, bash does this, C/C++ does that, etc.  Sometime down the road you can decide if you want to learn other languages as well.

---

### Post by MiCovran on 2007-07-05
> I wonder how characters like '$', '[', '>', '&', and so on would be treated.
I just can't seem to find any info about these '\' and '"' symbols for linux command line on the internet. I'm not brilliant in internet browsing, so if anyone knows where I can find something about this topic, could you post it, please?

> The results could be quite dangerous if your "cp" command arguments aren't properly escaped.
What do you mean?

---

### Post by kidders on 2007-07-05
Hey again,

Dwblas's suggestion is a good one! :-) Having said that, I get the impression that C's difficulty level, or suitability (or unsuitability!) for the task at hand aren't particularly important to you ... ie you just want to take C on a test drive for a while. I'm all in favour of that. :-)

With any language though, the problems start when you have to start interfacing the the environment you're running in. The answer to both of your questions, I suppose, is "Proper escaping is pretty critical". Consider these, as simple (albeit unrealistic) examples:

**I - Linux shell**
For some reason, you write a script (or for that matter, any program that executes an "mv" command) to move files to a user-specified location. You ask the user for $DEST, and do...```
mv (.. long list of files here ..) $DEST
```
Now, imagine $DEST is "dev/null; rm -Rf ~". If the semicolon isn't handled correctly, the result could be...[LIST]
[*]The list of files are moved into oblivion ... ie essentially deleted.
[*]The entire home directory of the user running the command is erased.
[/LIST]
Naturally, no matter how silly (or malicious) a user is when he specifies his target location, there should simply be no way to persuade a program to have this effect.

**II - SQL**
Imagine you'd written a login script for a website that uses the following SQL to match a user-provided username & password to an existing account...```
SELECT * FROM account WHERE username='<username>' AND password='<password>' LIMIT 1
```
By specifying a username of "  ' OR TRUE OR '  ", a user could manipulate the query into returning results it shouldn't, possibly leading to a successful login.

Again, there should of course be no way for a user to manipulate a website into this kind of behaviour.



In more realistic terms, the point is that certain characters/symbols invariably have special meanings in a given context. For instance, you can't often call variables things like "for", "if" or "case", in many programming languages. If you fail to handle "special" symbols properly, even completely innocent use of any program can lead to disaster.

One common technique, used to replace special characters with substitutes that don't have any special meaning, is called "escaping" (that word should help with web searches). As a simple illustration:

```
touch 1;rm 1
```

**Question:** Does the user mean "Touch a file called '1' and then delete it", or "Touch a file called '1;rm 1'"? The above does the former; the below does the latter.

```
touch 1\;rm\ 1
```

I hope that helps.

---

### Post by Note360 on 2007-07-05
I would suggest learnign python ruby or perl for this. THis is just one of those things though that perl is made for, but seriously I would suggest python or ruby, maybe perl later on when it upgrades to perl 6.

(sorry perl was my first language so i have a slight fondness for it and ruby)

---

### Post by AlexThomson_NZ on 2007-07-05
> **Note360 said:**
> I would suggest learnign python ruby or perl for this. THis is just one of those things though that perl is made for, but seriously I would suggest python or ruby, maybe perl later on when it upgrades to perl 6.

(sorry perl was my first language so i have a slight fondness for it and ruby)

While that may be the case, wouldn't that defeat the whole purpose of him wanting to practice with C?

I am sure there are 100s of ways to do this program, each way would be 'best' in some aspect, ie: 
 - a one line shell script
 - a 200 byte executable stripped-assembly program
 - a native, standalone and distributable C program
 - a python program a n00b can whip up in 2 minutes
 - a robust multi-platform Java application

I think this would be a useful little program to brush up on your C skills

---

### Post by Note360 on 2007-07-05
> **AlexThomson_NZ said:**
> While that may be the case, wouldn't that defeat the whole purpose of him wanting to practice with C?

I am sure there are 100s of ways to do this program, each way would be 'best' in some aspect, ie: 
 - a one line shell script
 - a 200 byte executable stripped-assembly program
 - a native, standalone and distributable C program
 - a python program a n00b can whip up in 2 minutes
 - a robust multi-platform Java application

I think this would be a useful little program to brush up on your C skills


You are right in all respects. All languages could or should be able to do this task (idk if Javascript can). Any way, I like that you did it in C I like C better than C++ even though I am a object oriented man, mainly for syntax reasons (which is why I like C# with Mono). Good luck with this. Actually this would be a fun programming challenge for all of us (what happened to that series of threads)

---

### Post by AlexThomson_NZ on 2007-07-05
> **Note360 said:**
> You are right in all respects. All languages could or should be able to do this task (idk if Javascript can). Any way, I like that you did it in C I like C better than C++ even though I am a object oriented man, mainly for syntax reasons (which is why I like C# with Mono). Good luck with this. Actually this would be a fun programming challenge for all of us (what happened to that series of threads)

Just to clarify, I wasn't doing the project, just defending the guys decision to use C ;)

Hate to thread-jack, but I agree with you about the coding challenges, I am new here and have been dying to get into a fun coding challenge (pref. gtk + C + OpenGL as that's what I am brushing up on myself...).  Anyone want to start one?

---

### Post by Note360 on 2007-07-05
> **AlexThomson_NZ said:**
> Just to clarify, I wasn't doing the project, just defending the guys decision to use C ;)

Hate to thread-jack, but I agree with you about the coding challenges, I am new here and have been dying to get into a fun coding challenge (pref. gtk + C + OpenGL as that's what I am brushing up on myself...).  Anyone want to start one?

I know that you weren't doing the project and yeah ill start one. I have to think of one to do (maybe we should do it in a different way, like monthly ones where we all band together into groups (based on language preference) and we as groups try to solve a specified problem that is bigger than the old ones. Hence the month long periods). I will start a topic for planing that.

Oh and for the guy who is making this program best of luck. If you want to see the differences between programming languages a good way to see them is to write the same program in different languages. I did that with a simple Fahr to Celcius converter which kept ono getting more feature packed.

Best of luck

---

### Post by MiCovran on 2007-07-06
> One common technique, used to replace special characters with substitutes that don't have any special meaning, is called "escaping" (that word should help with web searches). I found this page ([http://steve-parker.org/sh/escape.shtml](http://steve-parker.org/sh/escape.shtml)) and found out I still have to worry about '&', '`' and '\' besides '"'.

Thank you all for help and understanding.

Oh, Note360, I'm about to rewrite this to C++ now, but only because of strings. I don't like some things about C++ too, (like iostream) so I'll still use cstdio and cstdlib instead.

---

