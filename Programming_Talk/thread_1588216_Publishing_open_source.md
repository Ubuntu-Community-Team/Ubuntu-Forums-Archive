---
title: "Publishing open source"
date: 2010-10-04
forum: Programming Talk
---

### Post by eckeroo on 2010-10-04
Hello,

In a month or so, I should have some Python code ready. I would like to share it with the rest of the world. The code is for engineering and my intention is for other engineers that I work with and beyond to help themselves and hopefully add more code.

How do I go about formally making my code open-source with the GNU General Public License?

Where can I upload/manage my code for the world to access? I only know a bit of Python and I cannot do html or any web stuff.


Regards

---

### Post by worseisworser on 2010-10-04
[http://github.com/](http://github.com/)

---

### Post by SoftwareExplorer on 2010-10-04
How the fsf says to use the GPL3: (taken from [[COLOR="DeepSkyBlue"]http://www.gnu.org/licenses/gpl.txt[/COLOR]]("http://www.gnu.org/licenses/gpl.txt")).
>             How to Apply These Terms to Your New Programs

  If you develop a new program, and you want it to be of the greatest
possible use to the public, the best way to achieve this is to make it
free software which everyone can redistribute and change under these terms.

  To do so, attach the following notices to the program.  It is safest
to attach them to the start of each source file to most effectively
state the exclusion of warranty; and each file should have at least
the "copyright" line and a pointer to where the full notice is found.

    <one line to give the program's name and a brief idea of what it does.>
    Copyright (C) <year>  <name of author>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

Also add information on how to contact you by electronic and paper mail.

  If the program does terminal interaction, make it output a short
notice like this when it starts in an interactive mode:

    <program>  Copyright (C) <year>  <name of author>
    This program comes with ABSOLUTELY NO WARRANTY; for details type `show w'.
    This is free software, and you are welcome to redistribute it
    under certain conditions; type `show c' for details.

The hypothetical commands `show w' and `show c' should show the appropriate
parts of the General Public License.  Of course, your program's commands
might be different; for a GUI interface, you would use an "about box".

  You should also get your employer (if you work as a programmer) or school,
if any, to sign a "copyright disclaimer" for the program, if necessary.
For more information on this, and how to apply and follow the GNU GPL, see
<http://www.gnu.org/licenses/>.



By the way, if you are wondering how you get a copyright so you can license the program under the GPL, it's simple:It's copyrighted as soon as you write it. 

For code hosting, you might use bzr and launchpad. I'll see if I can find a good how to on that.

---

### Post by eckeroo on 2010-10-05
Thanks,

What about google code?  like this:

[http://code.google.com/p/pyeuclid/](http://code.google.com/p/pyeuclid/)

I like the simple and straight forward layout.

---

### Post by SledgeHammer_999 on 2010-10-05
Google Code uses [Subversion](http://en.wikipedia.org/wiki/Apache_Subversion) as it's revision control which is IMHO not the best approach for collaboration. 

Git allows to create and merge branches of your code really easily. Also github has a neat feature. If someone "forks" your code in github then you can track it's commits as a separate branch and merge back the changes you want. So every other engineer can fork it on github and everyone(you included) can monitor the changes and help each other out.(of course the code can be forked somewhere not only on github).
An example of this is here-->[http://github.com/emesene/emesene/network](http://github.com/emesene/emesene/network)
(the graph shows all the branches and merges that have happened. also it shows the branches that have changes but are not merged back on the original).

Note: Bazaar(bzr) works in a similar manner(regarding the easyness of creating and managing branches) but I haven't worked with it much.

---

### Post by SoftwareExplorer on 2010-10-06
Ok, the promised bzr howto:
[[COLOR="DeepSkyBlue"]Bazaar in five minutes[/COLOR]]("http://doc.bazaar.canonical.com/latest/en/mini-tutorial/")
It covers both using bazaar and putting your code on launchpad in a branch.

---

### Post by ad_267 on 2010-10-06
Google code can also use Mercurial which I like better than Subversion. It's a distributed version control system like Git. I set up a Google code page yesterday and it took about a minute from loading the page to having a repository to push to.

Once you've got your code up there it's just a matter of marketing to get more people involved.

---

### Post by ssam on 2010-10-06
there is also sourceforge which do pretty much all the major revision control systems (also gives you forums, bug tracker, wiki etc).

---

