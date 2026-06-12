---
title: "Open source"
date: 2013-04-25
forum: Programming Talk
---

### Post by Tesseract007 on 2013-04-25
I just had a question. How can I take a peek at the open source code and if I wanted to modify it a little how do you do that? What programing language would I use.

---

### Post by ki4jgt on 2013-04-26
For which project?

---

### Post by codemaniac on 2013-04-26
there is launchpad, where you can find many opensource projects with their source code available for browsing.

[http://launchpad.net](http://launchpad.net)

find your favorite project and start the feast. :)

---

### Post by ki4jgt on 2013-04-26
Then there's sourceforge.net, code.google.com, github.com, koding.com, and several others in numerous langauges.

---

### Post by Tesseract007 on 2013-04-26
I have Ubuntu 12.10. I will soon be upgrading to 13.0. I have another dumb question. Is it possible to see closed source programs? I know its technically not legal to mess with it. I'm just asking if it's possible just to look at it.

---

### Post by trent.josephsen on 2013-04-26
Is it possible to read a book? Well, yeah, but only if you have a copy of the book. Having the movie on DVD isn't enough.

Is it possible to read source code? Well, yeah, but only if you have a copy of the source code. Having a compiled program isn't enough.

It's not possible to take a program distributed in binary format and extract the source code: you can't just open an .exe file and view the source for Photoshop. But if some disgruntled Adobe employee leaked the Photoshop source code onto TPB or something, you could download it (though doing so might be illegal, depending on the license and where you live).

---

### Post by Tesseract007 on 2013-04-26
[SIZE=4]What I was thinking was that I would be able to view closed source code with some text viewing program. But I thought it would be encrypted or something like that or just unviewable. I'm new at this stuff that's why I'm asking.[/SIZE]

---

### Post by nidzo732 on 2013-04-26
> **Tesseract007 said:**
> [SIZE=4]What I was thinking was that I would be able to view closed source code with some text viewing program. But I thought it would be encrypted or something like that or just unviewable. I'm new at this stuff that's why I'm asking.[/SIZE]
No, you can't do that. You would just get a lot of gibberish. The source code is not saved in the executable files. The compiler translates it to machine language. It's a language that a computer can execute but it's not human-readable. You can try and see for yourself```
gedit *executable_file*
```

---

### Post by Virtuality314 on 2013-04-27
You would have to reverse engineer and decompile the proprietary executable, which would be highy illegal and probably violate at least 35 laws (give or take a few 30). Then, you would be able to view the source code, although it would probably still not make sense.

---

### Post by lykwydchykyn on 2013-04-27
...Unless the proprietary program is written in an interpreted language, which they usually aren't because it's hard to keep it proprietary in that case.  But viewability really depends on whether the language is compiled or interpreted.

---

### Post by shawnhcorey on 2013-04-27
> **Tesseract007 said:**
> [SIZE=4]I just had a question. How can I take a peek at the open source code and if I wanted to modify it a little how do you do that? What programing language would I use.[/SIZE]

You would have to use the language the project was written in. Find would where the community for the project resides on the net and make your queries there.

> **Tesseract007 said:**
> [SIZE=4]I have Ubuntu 12.10. I will soon be upgrading to 13.0. I have another dumb question. Is it possible to see closed source programs? I know its technically not legal to mess with it. I'm just asking if it's possible just to look at it.[/SIZE]

Most closed-source projects do not publish the source, so no, it's not possible to view it, legally or otherwise.

---

### Post by Tesseract007 on 2013-04-28
If I wanted to modify my GUI for Ubuntu what program could I use to do that? And what would be step #1,2,3,4 etc..

---

### Post by Tesseract007 on 2013-04-28
If I wanted to modify the GUI for my desktop what program could I use. And what would be like step #1,2,3 etc? Ops I double posted sorry. You can delete one if you want I dont know how?

---

### Post by lykwydchykyn on 2013-04-28
> **Tesseract007 said:**
> [SIZE=4]If I wanted to modify my GUI for Ubuntu what program could I use to do that? And what would be step #1,2,3,4 etc..[/SIZE]

#1: Decide which component you want to modify
#2: Download the source code to that component
#3: Modify it in whatever language it's written.
#4: Compile the code if necessary
#5: Replace what you've got with that code.

You're asking a very very vague question, there's no way to give you specific instructions.

---

### Post by ofnuts on 2013-04-29
> **Tesseract007 said:**
> [SIZE=4]If I wanted to modify my GUI for Ubuntu what program could I use to do that? And what would be step #1,2,3,4 etc..[/SIZE]

If you are asking this question you very likely haven't got the beginning of the skills required... If you want to do that you have to:

- become fairly proficient in C/C++ (6months minimum)
- become very proficient with UI programming (and the relevant UI libraries, Qt, Gtk or other, depending on desktop manager used)(another 6 months)
- become familiar with the build tools
- become familiar with the Linux software installation setup

Then grabbing the source code of your desktop and modifying it to suit your needs becomes doable.

---

### Post by lykwydchykyn on 2013-04-29
If you just want to rearrange your desktop a bit, try a desktop environment like KDE.  You can do considerable customization without having to code anything.  Unity wasn't designed to be flexible, really.

---

