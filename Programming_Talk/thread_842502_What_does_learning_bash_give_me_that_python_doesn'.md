---
title: "What does learning bash give me that python doesn't?"
date: 2008-06-27
forum: Programming Talk
---

### Post by GammaPoint on 2008-06-27
A lot of people seem to know bash fairly well. I give in to peer pressure easily so I was wondering if I should learn it as well :) 

But what does bash allow me to do that python doesn't? Or is it just simpler to use 'cd blah blah, etc' in a script than 'os.system(cd blah blah etc)'?

---

### Post by diaa on 2008-06-27
Personally, I'm on the Python side, the *only* advantages I see with bash are

[LIST=1]
[*]Speed, bash should be faster but I'm not sure how faster.
[*]More user base, definitely the number of distros with bash is more than the number of distros with Python, yes Python is getting more and more standard as a part of linux distros but I suspect you'll find it on small distros such as SysRescueCd and so on, so if you want your script to run on those you have to use bash.
[/LIST]
However I'll choose Python over bash for everything I want to do(except bash 2-3 liners) because of maintainability and because I already know Python :)

I hope this doesn't turn into a flame war *duck* but I'm anxious to know what the bash guys have to say :)

---

### Post by pmasiar on 2008-06-27
@diaa: exactly.

But I do not see any reason to worry about the speed difference, if any: you don't use bash for speed, speed for 5-lines is not significant, and I would not use bash for anything bigger. And Python is present on all but the most limited distros, I would not worry about that until you focus specifically on those.

There are couple of useful tricks in bash to manipulate environment, but I prefer to use Python for anything beyond trivial bash. 

People who are bash expert learned it before Python and keep it that way - but Python has many significant advantages over the bash, one of them being decent **universal** programming language :-)

---

### Post by LaRoza on 2008-06-27
> **GammaPoint said:**
> A lot of people seem to know bash fairly well. I give in to peer pressure easily so I was wondering if I should learn it as well :) 

But what does bash allow me to do that python doesn't? Or is it just simpler to use 'cd blah blah, etc' in a script than 'os.system(cd blah blah etc)'?

I haven't taken the time to sit down and learn bash. I learn it as I use it. (You will learn quite a bit that way)

In a python script, you wouldn't want to be using system(cd...), you would want to use the inbuilt modules that are cross platform and standard.

os.chdir() would be used. [http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)

---

### Post by nvteighen on 2008-06-27
> **GammaPoint said:**
> 
But what does bash allow me to do that python doesn't? Or is it just simpler to use 'cd blah blah, etc' in a script than 'os.system(cd blah blah etc)'?

Excuse my ignorance: but doesn't "os.system(cd blah)" actually call "cd blah" the default system shell?... Aren't both exactly the same!?

---

### Post by diaa on 2008-06-27
> **nvteighen said:**
> Excuse my ignorance: but doesn't "os.system(cd blah)" actually call "cd blah" the default system shell?... Aren't both exactly the same!?

On Windows and Linux yes, but what about BeOS or Symbian or another new XYZ OS where Python is available, it's not guaranteed so it's better to use the Python-provided function which will be implemented approrpiately depending on the platform.

---

### Post by Quikee on 2008-06-27
IMHO Bash is tuned for working with files (things like questions if file does exist, is file executable, for i in *.exe), calling binaries and storing the result, stdin, stdout, pipes - gluing like this just can't be done so nicely in python as it can be done with bash. 

For anything else python is superior.

---

### Post by CptPicard on 2008-06-27
Bash is a system shell (and a fairly good one at that), Python is a general-purpose programming language.

Two completely differen things. You are comparing apples and oranges.

---

