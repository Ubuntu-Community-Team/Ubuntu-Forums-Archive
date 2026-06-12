---
title: "Keeping ubuntu secure during programming"
date: 2010-07-05
forum: Programming Talk
---

### Post by techguy7 on 2010-07-05
I am new to ubuntu, and programming. I would like to learn to program in ubuntu, but I just have one question.  Can a virus infect the program I am developing because it is located in my home directory.  Thanks

---

### Post by CptPicard on 2010-07-05
If you're at that level of development, no. You're secure.

---

### Post by nvteighen on 2010-07-05
> **techguy7 said:**
> I am new to ubuntu, and programming. I would like to learn to program in ubuntu, but I just have one question.  Can a virus infect the program I am developing because it is located in my home directory.  Thanks

That's fear based on magical thinking.

Viruses propagate themselves by infecting key system components. Think about it: if you were someone wanting to write a virus, you'll obviously try to write something that maximizes danger and replication rates but also keep it as most undetectable as possible. So, the attack would be driven against a subtle vulneraibility in the OS or in a very well-known utility associated to a target OS, because that would show more harm potential than something that checked for applications hosted in a home directory which you don't know how the users uses them or whatever. A really hardcore malware that just infects every single executable binary it finds would be very something very silly to do as it couldn't run undetected. (Very old MS Word 6.0 Macro viruses had this issue: they usually tried to rename all opened .doc files into macros... something one can easily detect by just looking at one's directory).

So don't worry. Also, be aware that GNU/Linux is designed in a way that makes it really difficult to a virus to be succesful **if** you follow basic security practices and just don't go installing whatever you find on the web (always use certified trusted sources) and have no server installed and running without configuration.

---

### Post by techguy7 on 2010-07-06
Thank you, You have been a great help.

---

### Post by NoBugs! on 2010-07-07
It depends on what the code does. Some code may seem harmless, like this example:
os.system("programname "+ some_data_from_internet)
It is harmless in most cases, but if some_data_from_internet is "data; rm importantfiles" it could be disastrous.
It's important to keep untrusted data (such as from internet) from taking control. Also, it's generally good to not run programs as root, since that has the possibility of messing up the whole system, not just home directory.

---

### Post by juancarlospaco on 2010-07-07
See LXC, or other SandBoxing thing

---

