---
title: "Prgramming hacking tools with C++"
date: 2005-06-24
forum: Programming Talk
---

### Post by ron126 on 2005-06-24
Can C++ be used to program hacking tools like nmap, nessus, 'ettercap', 'ethereal' or john the ripper ? 

Or is it better to program a hacking tools with other programming language such as C, Perl or Python ? Which is best? Or does it depends?

---

### Post by circussideshow on 2005-06-25
Since when are the apps you mentioned classified officially as "hacking tools?"

---

### Post by dmccarney on 2005-06-25
Now I'm not sure whether you are talking about automating those tools in a script or something or if you actually want to make your own variant. 

If its the latter then (not meaning to sound trollish) but you would need considerable knowledge in the area that you are wishing to exploit, and generally speaking, if you had that knowledge you would probably know which language would apply best to your problem. 

You would most definately need to give more information though about what you want to accomplish because the programs you listed are quite different and are used to audit different things.

---

### Post by ron126 on 2005-06-25
> If its the latter then (not meaning to sound trollish) but you would need considerable knowledge in the area that you are wishing to exploit, and generally speaking, if you had that knowledge you would probably know which language would apply best to your problem.

Ok, so that's depend.

And i seldom see some security tools being programmed by C++ (i may be wrong) Why? Let say i want to program a password cracking tool like john the ripper with C++, is it right to say it's possible, though there may be a better programming language out there which can do a better job?

In conclusion, what type of programs does C++ suits best ? Can anyone gave me some great programs done by C++?

---

### Post by thumper on 2005-06-25
[QUOTE=ron126]Ok, so that's depend.

And i seldom see some security tools being programmed by C++ (i may be wrong) Why? Let say i want to program a password cracking tool like john the ripper with C++, is it right to say it's possible, though there may be a better programming language out there which can do a better job?

In conclusion, what type of programs does C++ suits best ? Can anyone gave me some great programs done by C++?[/QUOTE]
Any tool can really be written in any language (well almost any).

C++ is often used for larger, server side systems.  Particularily in banking (which is the sector where I work most).  I'd say that C++ suits larger type systems rather then smaller ones, as it is often quicker and easier to use something like python (or insert scripting language of choice).

C++ is also used for computationally intensive work.  Where much number crunching is needed.  Modern C++ approaches fortran for speed.

---

### Post by buffbikedude on 2005-06-26
[QUOTE=ron126]Can C++ be used to program hacking tools like nmap, nessus, 'ettercap', 'ethereal' or john the ripper ? 

Or is it better to program a hacking tools with other programming language such as C, Perl or Python ? Which is best? Or does it depends?[/QUOTE]

To me, "hacking tool" means "programming tool". To me, "hacker" is my preferred way of saying programmer. It has nothing to do with breaking into people's systems. See [http://www.catb.org/~esr/faqs/hacker-howto.html](http://www.catb.org/~esr/faqs/hacker-howto.html) and [http://www.paulgraham.com/gh.html](http://www.paulgraham.com/gh.html) .

If you want to write an attacking tool, any general-purpose programming tool that provides programs access to the network will suffice. C++, C, Perl, and Python are all good. I prefer Python. Others may prefer Java or scheme, even. Everyone is entitled to their opinions. Some languages are probably a bit better than others, but I am not in a position to inform you what is best; I can only tell you what's worked so far for me. Some very smart people actually have formed strong opinions on the matter. I'll leave it up to you to seek them out.

Happy hacking! 

Ben

---

