---
title: "GNU license information in C program"
date: 2009-07-16
forum: Programming Talk
---

### Post by e24ohm on 2009-07-16
Folks:
I am reviewing the GNU license information at [http://www.gnu.org;](http://www.gnu.org;) however, i am very confused on the documentation. What do I need to place in my C program to be in compliance with GNU?

thank you
E

---

### Post by Tibuda on 2009-07-16
Read "[How to use GNU licenses for your own software]("http://www.gnu.org/licenses/gpl-howto.html")". In few words, you should include the license in text format and add this statement in a comment of your source code:
>     This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

---

### Post by e24ohm on 2009-07-16
> **danielrmt said:**
> Read "[How to use GNU licenses for your own software]("http://www.gnu.org/licenses/gpl-howto.html")". In few words, you should include the license in text format and add this statement in a comment of your source code:
hey thanks.

---

### Post by nvteighen on 2009-07-16
It's all about common sense :) Place it somewhere everyone could locate it, in binary or source. 

In source, in each source file, so no matter what module you're looking at, you know which license it is. Think that being Free Software, your module could be suddenly chopped off the original project and published separately somewhere else.

In binary, well... what I do is to put a text file called COPYRIGHT that shows what licenses apply to the different parts of the program. Then, I put the license texts. Also, if the program shows some output, a notice during execution will always be useful and nice. But any way that makes clear what terms apply will be ok.

---

### Post by wmcbrine on 2009-07-16
Usually the file is called "COPYING"... in fact, if I see a "COPYING" file, I tend to just assume that it's the GPL, and not read it. :D (Of course I do check it if I actually plan to redistribute it.)

Theoretically you're supposed to put boilerplate like danielrmt showed at the top of each source file. But in one project, I just put a one-line notice in each file, directing people to the COPYING file. In other projects, I've put the three-paragraph notice in each file, but ended it with this:

```
# You didn't receive a copy of the license with this library because 
# you already have dozens of copies, don't you? If not, visit gnu.org.
```

and didn't include COPYING. I believe all of these are fine -- after all, copyright is automatic, and if someone ever did decide that your GPL notice was inadequate, all that would mean would be that the code would revert to the default copyright condition: "You have no permission to copy this." So potential copiers are strongly motivated to find your notice adequate. :)

I have never bothered to put GPL notice in a program's output.

---

