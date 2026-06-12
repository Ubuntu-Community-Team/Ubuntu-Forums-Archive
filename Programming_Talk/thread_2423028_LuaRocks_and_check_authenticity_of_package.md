---
title: "LuaRocks and check authenticity of package"
date: 2019-07-16
forum: Programming Talk
---

### Post by jason.jackal on 2019-07-16
I am new to Lua, and I have started using it since a number of network devices I support use it as a scripting language. However, I have started using it for some general scripting. Due to the latter, I found LuaRocks, but I am unsure. How do I check the authenticity of the packages that I install?

thank you

---

### Post by norobro on 2019-07-16
I have some experience with Lua but have never used LuaRocks. 

In checking it out I found this:> Here’s what we’re working on now:
    
[LIST]
[*]Implementing package signing and integrity verification of package files
[LIST]
[*]This will enable us to verify that files have come directly from package maintainers, preventing any future issues concerning tampering
[/LIST]
[/LIST]
From here: [https://luarocks.org/security-incident-march-2019](https://luarocks.org/security-incident-march-2019)

HTH

---

### Post by jason.jackal on 2019-07-16
> **norobro said:**
> I have some experience with Lua but have never used LuaRocks. 

In checking it out I found this:From here: [https://luarocks.org/security-incident-march-2019](https://luarocks.org/security-incident-march-2019)

HTH

Oh.... this is good that they want to introduce it; however, makes me second guess the direction of the ecosystem since it did not have it from start.

How have you liked using Lua? What do you use Lua for? I am just starting in it. Coming from Perl and Python. For some odd reason, I do not like coding in Python; however, it appears to be the industry standard these days.

Thank you for the link and the post.

---

### Post by norobro on 2019-07-16
You're welcome.

I probably should have emphasized "some". Years ago I was helping create/maintain a website that used Lua for its cgi scripts so I was forced to learn the basics. I liked it very much but have hardly used it since. Here is the tool that we used (I notice that it is available through LuaRocks): [https://github.com/keplerproject/cgilua](https://github.com/keplerproject/cgilua)

I agree about Python being the accepted standard.  I come from a C/C++ background but use Python, almost exclusively, for scripting.

---

### Post by jason.jackal on 2019-07-16
> **norobro said:**
> You're welcome.

I probably should have emphasized "some". Years ago I was helping create/maintain a website that used Lua for its cgi scripts so I was forced to learn the basics. I liked it very much but have hardly used it since. Here is the tool that we used (I notice that it is available through LuaRocks): [https://github.com/keplerproject/cgilua](https://github.com/keplerproject/cgilua)

I agree about Python being the accepted standard.  I come from a C/C++ background but use Python, almost exclusively, for scripting.

Very interesting... thank you for sharing. I have started learning C... again!!! I had it many years ago in college as my programming language, since Commodore Basic nor MOS6502 assembly was offered, and I had no clue what this new language called Java was; however, never did anything with it since I am not a programmer by trade, yet I see benefit in learning it due to memory management and static typed.

Most of what I do is script driven: Perl, Python, Tcl, Lua, etc. Funny, I never get a sense of enjoyment when I use Python as I do with Tcl and Perl. Call me odd..

---

