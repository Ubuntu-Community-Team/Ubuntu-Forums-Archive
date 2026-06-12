---
title: "Geany 'problem'"
date: 2008-08-22
forum: Programming Talk
---

### Post by ruro on 2008-08-22
Hey everyone.

I've been hunting for a good editor/IDE the whole day today without finding the right one for me. The last one that I tried was Geany, and I actually really liked it. It's clean, and does what I need it to do and nothing more. However, there's just this one tiny thing that really irritates me!

The 'problem' is that there's a slight delay after I press return till I get a new line in the editor. It's not exactly something that makes the editor worthless, but it's really annoying with the delay.

I've tried turning off a lot of options thinking that the editor is doing something when I press return (checking indentation or something), but it didn't make any difference.

I also might add that if I open the same file in gedit and hit return, there's no delay at all... Therefore, I'm guessing that it's something with Geany that causes this (since I haven't experienced it anywhere else).

The reason for this post is that I'm hoping that someone else here have experienced the same thing, and found a solution for it. I'm guessing that the probability for that isn't that high though, since I find this problem rather odd, but it doesn't hurt to ask. :)

---

### Post by Zeotronic on 2008-08-22
I love Geany, and would love to help you, but I've never heard of this. Did you get it from the repos? If you did then I haven't a clue as to what could be wrong. Perhaps... which languages have you tried it in? I've only used it for C++ and Python, and I don't recall it doing anything like that in either. Does it do this all the time, or only some of the time?

---

### Post by ruro on 2008-08-22
> **Zeotronic said:**
> I love Geany, and would love to help you, but I've never heard of this. Did you get it from the repos? If you did then I haven't a clue as to what could be wrong. Perhaps... which languages have you tried it in? I've only used it for C++ and Python, and I don't recall it doing anything like that in either. Does it do this all the time, or only some of the time?
I got it through the terminal ('sudo apt-get install geany') and it installed without any problems. Well, I didn't get any error messages...

The languages that I've tried is both C and C++, but I haven't tried Python. I'm going to do that now... Hmm, no problem with Python. That makes it even more strange!

**After 5 minutes of messing around**

It seems that it's the GPL license that's causing the delay... If I move it from the top to somewhere else in the document, there's no delay. I even tried having the GPL license in my main() method and hitting enter, and there was no delay, but when I moved the license to the top again, it came back. Really odd if you ask me.

I found a way to remove the problem though: code folding! In C and C++ the license is a /* */ comment, so I can fold the section. When I fold it, the delay is gone.

So I can either:
[LIST]
[*]move the license
[*]remove the license
[*]fold the section
[/LIST]
**_-----------------------------------------------_**

I'm so slow sometimes! I'll just code, and when I'm done, I'll add the license. It works regardless of the language I'm coding in.

Take that! Problem solved. :D

---

### Post by Sinkingships7 on 2008-08-22
I would say remove the license. There's no reason to have it there if you're just practicing.

---

