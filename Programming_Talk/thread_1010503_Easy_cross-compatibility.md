---
title: "Easy cross-compatibility"
date: 2008-12-13
forum: Programming Talk
---

### Post by linuxguymarshall on 2008-12-13
I am just about to move on from my console/terminal/whatever you want to call it  C++ programs and start developing GUI apps. I would like to not have to do major rewrites of my code to compile it on Linux, OSX, and WinBlows as I constantly switch from OS to OS depending on the day and machine available.  So does anyone know of something that I can compile with the same source on all OSs and not have to rewrite. Thanks.


I thought about GTK+ but did not know if I would have to rewrite or not.

---

### Post by Epikuma24 on 2008-12-13
read [http://www.agner.org/optimize/](http://www.agner.org/optimize/)

---

### Post by linuxguymarshall on 2008-12-13
Not quite what I was looking for. I was more looking for some libraries but that is a start

---

### Post by snova on 2008-12-13
Qt. It's very comprehensive, as a widget toolkit, utility library (hashes, vectors, and whatnot), networking toolkit, IPC, OpenGL, scripting, SQL, HTML engine (WebKit), XML parser...

I like it. :)

---

### Post by CptPicard on 2008-12-14
Yeah, Qt might come closest, but in C++ you will in the general case more or less need to rewrite for each OS as you move away from the standard language and start using nontrivial libraries or OS dependencies... modularizing your code well will alleviate this somewhat though.

---

### Post by scourge on 2008-12-14
> **CptPicard said:**
> Yeah, Qt might come closest, but in C++ you will in the general case more or less need to rewrite for each OS as you move away from the standard language and start using nontrivial libraries or OS dependencies... modularizing your code well will alleviate this somewhat though.

Have you actually written Qt apps in C++ lately? I ask because Qt 4.x has great cross-platform libraries which effectively remove the need to write platform-dependent code. I'm working on a fairly large GUI project with a friend, and we only have one Windows-specific preprocessor macro (for exporting and importing a library), the rest is 100% cross-platform.

---

### Post by CptPicard on 2008-12-14
Ok, I take your word for it :) You still *are* essentially using Qt as all of your stdlib :)

---

### Post by Jonas thomas on 2008-12-14
> **linuxguymarshall said:**
> I am just about to move on from my console/terminal/whatever you want to call it  C++ programs and start developing GUI apps. I would like to not have to do major rewrites of my code to compile it on Linux, OSX, and WinBlows as I constantly switch from OS to OS depending on the day and machine available.  So does anyone know of something that I can compile with the same source on all OSs and not have to rewrite. Thanks.


I thought about GTK+ but did not know if I would have to rewrite or not.

I'm also very interested in cross-platform programming. I do/did a lot of vb6 programming on the MSW side and I wanted to move away from that and do something that was more cross-platform in C++.  After doing a fair amount of research I settled on Code::Blocks for an IDE,wxWidgets for the Gui and wxFormbuilder as a RAD tool.
To be honest, I'm still in the learning phase and it's taking me a lot longer than I would like to get productive, but so far I like what I'm seeing with the tutorials I'm working through.  I have loaded this up on an XP box, but most of what I've been doing has been on Linux.
Btw... I found a nice tutorial on wxWigets at [http://www.zetcode.com/tutorials/wxwidgetstutorial/]("http://www.zetcode.com/tutorials/wxwidgetstutorial/")

---

### Post by scourge on 2008-12-14
> **CptPicard said:**
> Ok, I take your word for it :) You still *are* essentially using Qt as all of your stdlib :)

That's a very clever wording. I can't think of many situations where Qt libs wouldn't be enough, unless I'd want to use some unique OS features like Keyring in OSX. But then I'd need platform-specific code no matter what language I use.

---

### Post by snova on 2008-12-14
> **CptPicard said:**
> Ok, I take your word for it :) You still *are* essentially using Qt as all of your stdlib :)

For which it more than suffices. The STL confuses me and I could never find good docs on it, but Qt makes perfect sense (and the HTML documentation is excellent, and local).

---

