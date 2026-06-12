---
title: "compile windows code for ubuntu"
date: 2011-01-14
forum: Programming Talk
---

### Post by evan54 on 2011-01-14
hi,

Situation
- I have a program that runs in windows that I want to run in linux from a server.
- Basically provide remote access from a server that runs a linux based OS.
- I also have the source code
- The program is called PC1D and can be found here:
[http://www.pv.unsw.edu.au/links/products/pc1d.asp](http://www.pv.unsw.edu.au/links/products/pc1d.asp)

Things I know:
- The program was written in Microsoft Visual Studio (because there is a .vcproj)
- I need to recompile it somehow...


please let me know what else I could do / how to compile it.

thanks

---

### Post by lisati on 2011-01-14
*Thread moved to **Programming Talk**.*

Hmmmmm, Visual Studio. Chances are you're in for a lot of work to get an Ubuntu-friendly version compiled. Perhaps someone who has more experience at doing this kind of conversion than myself can offer some tips.

---

### Post by worksofcraft on 2011-01-14
> **evan54 said:**
> hi,

Situation
- I have a program that runs in windows that I want to run in linux from a server.
- Basically provide remote access from a server that runs a linux based OS.
- I also have the source code
- The program is called PC1D and can be found here:
[http://www.pv.unsw.edu.au/links/products/pc1d.asp](http://www.pv.unsw.edu.au/links/products/pc1d.asp)

Things I know:
- The program was written in Microsoft Visual Studio (because there is a .vcproj)
- I need to recompile it somehow...


please let me know what else I could do / how to compile it.

thanks

I have had a quick look at some of the code and it appears to date back to windows 3.1 origins... full of Macros like DECLARE_MESSAGE_MAP and using header files like afxwin.h... TBH I do not think you will succeed to make this into a native Linux app and IMO you would have less work and get a better result if you can simply find the algorithms and  code it from scratch.

Alternatives might be to run the ready built executable under Windows Emulator, "wine" or in a virtual box that runs some form of Windows.

---

### Post by evan54 on 2011-01-14
I heard that there are dangers of running things using wine because windows viruses can get access through it? Is this true or is there a suggested way I should make this work?

Also, I don't have an available windows CD installer to install windows on a virtual machine (I assume I'd need this.. but I'm just guessing)

thanks again

---

### Post by fct on 2011-01-14
The virus-through-wine risk is low enough to consider it as an option.

The other option is basically rewriting the source code for it to be multi-platform (linux compatible at least). Which, considering it's an MFC project, means lots of pain.

---

### Post by worksofcraft on 2011-01-14
> **evan54 said:**
> I heard that there are dangers of running things using wine because windows viruses can get access through it? Is this true or is there a suggested way I should make this work?

Also, I don't have an available windows CD installer to install windows on a virtual machine (I assume I'd need this.. but I'm just guessing)

thanks again

That's a good point about viruses and come to think of it there isn't a single Windows application I've ever used since switching to Ubuntu. I might just save myself some disk space and avoid the risk by removing Wine :D

As for virtual machines... you can get ready configured "appliances" with Windows on them available on the internet however you probably will be breaking Microsoft licensing terms if you actually use them: Quite most Microsoft Windows EULA will **not allow** you to run Windows on a virtual machine at all even if you do have the installation disk :shock:

So I had another look at these 132 source files and I conclude it is **not** structured in a way that will facilitate isolation of the actual program logic from the user interface or be amenable to any kind of conversion.

Thus my advice is to try and get the algorithms and formulas from elsewhere (e.g. a text book) and encapsulate them in modules that are self contained with NO system dependencies. Then most programmers will know how to write you a user interface :)

---

### Post by evan54 on 2011-01-14
Hey guys,

you're awsome! Thanks for all the responses!

I downloaded wine ran it (it runs fine :D) and then removed wine to avoid the risk of windows viruses.

In light of the virtual machine talk, I think the safest option (if my assumption that virtual machines can't effect files on the original machines by default) is to make a virtual machine running ubuntu with wine on it allowing all windows programs to run there.

Otherwise yes ideally I would rewrite the whole thing.. which at the moment I don't think I have the time for.

thanks again

---

### Post by evan54 on 2011-01-14
Hey guys,

you're awsome! Thanks for all the responses!

I downloaded wine ran it (it runs fine :D) and then removed wine to avoid the risk of windows viruses.

In light of the virtual machine talk, I think the safest option (if my assumption that virtual machines can't effect files on the original machines by default) is to make a virtual machine running ubuntu with wine on it allowing all windows programs to run there.

Otherwise yes ideally I would rewrite the whole thing.. which at the moment I don't think I have the time for.

thanks again

---

### Post by worksofcraft on 2011-01-14
> **evan54 said:**
> Hey guys,

you're awsome! Thanks for all the responses!

I downloaded wine ran it (it runs fine :D) and then removed wine to avoid the risk of windows viruses.

In light of the virtual machine talk, I think the safest option (if my assumption that virtual machines can't effect files on the original machines by default) is to make a virtual machine running ubuntu with wine on it allowing all windows programs to run there.

Otherwise yes ideally I would rewrite the whole thing.. which at the moment I don't think I have the time for.

thanks again

Windows viruses are of course not very effective on Linux systems because they don't recognize the native executable file format, they won't find many of their favorite system files to infect and they only have read access to most of your installation anyway, unless you are running with superuser status. ;)

---

### Post by wmcbrine on 2011-01-14
Part of the Wine package is WineLib, which allows you to rebuild Windows apps as native Linux apps (if you have the source, which you do). This may be of interest to you.

---

