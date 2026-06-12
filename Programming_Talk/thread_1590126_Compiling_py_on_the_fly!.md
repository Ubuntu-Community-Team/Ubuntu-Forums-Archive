---
title: "Compiling py on the fly!"
date: 2010-10-07
forum: Programming Talk
---

### Post by Sailor5 on 2010-10-07
Ahoy Sailors!

So, I'm currently in the midst of creating a nice Python driven application for windows, This application amongst other things will allow the user to specify options (Thus changing the script we're compiling) And then finally build our .py file using Py2Exe. But that's the fundamental problem, I don't really want to be leaving my source file on there PC, To my knowledge Py2Exe can't compile pyc files, Which is the only thing I can think of.

So how can I allow changes to be made to the compiling script whilst not allowing read access to the file?

Thanks Bye!

---

### Post by Queue29 on 2010-10-07
.pyc can be decompiled to .py files trivially (it's nothing more than bytecode, after all), so if you are that paranoid about people looking at your source code, you shouldn't be using python to begin with.

---

### Post by Sailor5 on 2010-10-07
> **Queue29 said:**
> .pyc can be decompiled to .py files trivially (it's nothing more than bytecode, after all), so if you are that paranoid about people looking at your source code, you shouldn't be using python to begin with.

So your saying there's no way to to do this? It doesn't matter if they can crack whatever route we take, So long as it doesn't just take five minutes to do such and steal my source I'm happy.

---

### Post by DanielWaterworth on 2010-10-07
In any language you can track down the logic, after all, machine code can be disassembled.

For your situation, I'd suggest using cython for as much of the source as possible after  obfuscating, [http://www.lysator.liu.se/~astrand/projects/pyobfuscate/]("http://www.lysator.liu.se/%7Eastrand/projects/pyobfuscate/")

edit: I feel like such a sell-out, teaching people to make non-open source python applications.

---

### Post by nvteighen on 2010-10-07
Wait a minute... do you want your script to modify itself in order to save configuration? Please clarify me that, because that's a very very impractical approach combined with Py2Exe-like compilation... 

I know some Perl programmers like to do that approach... CPAN's for instance... but uh, Perl's compilation is completely different.

---

### Post by DanielWaterworth on 2010-10-08
> **nvteighen said:**
> Wait a minute... do you want your script to modify itself in order to save configuration? Please clarify me that, because that's a very very impractical approach combined with Py2Exe-like compilation... 

I know some Perl programmers like to do that approach... CPAN's for instance... but uh, Perl's compilation is completely different.

I missed that too, put your configuration in a different place. An sqlite3 db for example.

---

