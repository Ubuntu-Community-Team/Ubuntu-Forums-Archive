---
title: "Linux Programmer's Guide Man Pages"
date: 2004-12-22
forum: Programming Talk
---

### Post by Pink Floyd on 2004-12-22
I need them installed so I can use them trough the command line.
I searched them but I only found html, tex, pdf etc versions, but I need the "man" version.

Can someone help me? 
Thank you

---

### Post by Juergen on 2004-12-23
If it's not at tldp I'd think you have to try to convert this thing yourself.

But:
Can't you just use the html-version with a text-browser like lynx or links?

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=Juergen]But:
Can't you just use the html-version with a text-browser like lynx or links?[/QUOTE]
By far the easiest option, if you ask me.

---

### Post by yentingchen on 2004-12-25
[QUOTE=Pink Floyd]I need them installed so I can use them trough the command line.
I searched them but I only found html, tex, pdf etc versions, but I need the "man" version.

Can someone help me? 
Thank you[/QUOTE]
Hi, maybe this is what you needs:

cyt@ubuntu:~> apt-cache search manpages-dev
manpages-dev - Manual pages about using GNU/Linux for development

---

### Post by duff on 2005-01-10
[QUOTE=yentingchen]Hi, maybe this is what you needs:

cyt@ubuntu:~> apt-cache search manpages-dev
manpages-dev - Manual pages about using GNU/Linux for development[/QUOTE]
Thank you!

---

### Post by Viro on 2005-01-19
[QUOTE=yentingchen]Hi, maybe this is what you needs:

cyt@ubuntu:~> apt-cache search manpages-dev
manpages-dev - Manual pages about using GNU/Linux for development[/QUOTE]
 Good call. I've been looking for that package for some time now. thanks

---

### Post by sainter54 on 2006-08-15
The manpages-dev isn't on apt-get anymore. Is there something else I can download to get these Man Pages????

---

### Post by X.Cyclop on 2006-08-15
> **sainter54 said:**
> The manpages-dev isn't on apt-get anymore. Is there something else I can download to get these Man Pages????
[Add extra repos](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories) and try again ;)

---

### Post by sainter54 on 2006-08-18
That worked perfectly. Thanks for that... Sorry for being a noob...

---

### Post by X.Cyclop on 2006-08-19
> **sainter54 said:**
> That worked perfectly. Thanks for that... Sorry for being a noob...
There's no problem. Nobody's born knowing.:mrgreen:

---

### Post by driplock on 2008-01-11
Great! thanks..this thread helped me also...

---

### Post by imweiwei2 on 2008-01-30
For those total beginning, like myself couple days ago, this is what you type in a terminal:

sudo apt-get install manpages-dev

Thanks guys!

---

### Post by akkumaru on 2009-05-27
> **Pink Floyd said:**
> I need them installed so I can use them trough the command line.
I searched them but I only found html, tex, pdf etc versions, but I need the "man" version.

Can someone help me? 
Thank you

it's quite the opposite,,
i need the offline version either in html or pdf (or chm),
where can i find the latest version?

---

### Post by samjh on 2009-05-27
Wow, this thread has been unearthed three times since 2004.  Impressive. ;)

---

### Post by Atadam on 2012-05-05
Since you say "Nobody's born knowing"
I might tell that i do not understand!

  	 	 	 	 	 	   Vba = short for Visual Basic for Applications, a feature provided by Microsoft Office to get additional functionality for Excel and friends.
 Ubuntu = a Linux distribution used as base for Mint,Lubuntu and several other OS.
 OS = Operating System
 UI = User Interface. UI is the screen in a program where you click buttons to select your choice.
 grep = program used to search inside files (type man grep to get help or read rute)
rute = a description on how to use Linux referring to man pages


 Since 2 years i try to figure out how Linux is working in order to use it to reprogram  a excel table to open standards. Since i have made heavily use of vba (including a UI above Excel) capabilities and learned the whole stuff by using the implemented help file, I can say that help files are growing worse. With win98 you had all the things you need in one file you could rummage and find code examples to alter or to show you how it works. Later you got a search line that is as useful as the dash in ubuntu(you might just try to live within a computer).
 Then I recognized that vba will not be supported anymore.
 I thought that free software and open standards should be my solution but as long as help files are like this, i might just pee my pants and be happy with the result.
 

 With man pages it does not matter what language they are translated, you get all the time a non descriptive gibberish. Take a look at this:


 Das  Schlüsselwort  ist  gewöhnlich  ein regulärer Ausdruck und hat den 
        gleichen Effekt wie (-r). Es kann außerdem nach einer  bestimmten  Zei&#8208; 
        chenkette (-e) oder nach Zeichenketten mit Platzhaltern (Wildcards, -w) 
        gesucht werden. Bei Nutzung dieser Optionen kann es erforderlich  sein, 
        für  das  Schlüsselwort  und  Sonderzeichen eine Verarbeitung durch die 
        Shell zu vermeiden. Für Schlüsselwörter werden dafür  Anführungszeichen 
        und für Sonderzeichen Escape-Sequenzen (\) verwendet.
 

 No need to speak German, you will not understand it, even if English is your native language.
 It tells that the keyword has the same effect as -r and does not describe or refer to -r.
 -r = recursive, reproaching, rendering, rectal??? How many r words does the English language  have?
 You might search for strings (whatever they are) and refers to -e. Though, is -e a string is -e a program parameter to help you to refer to strings or is it just there to confuse a little more?
 And what type is the  string? I can not tell!


 &#304;t tells me that i might replace strings with Wild-cards => -w. Wow, i always thought i would search for words when i use grep???? Now it is a program parameter for wild cards like *?..


 ???....everybody will understand escape sequence like in "sequence", an order of events or symbols. Though escape sequence must be something like (\) where you have to put the symbols “(“ '\' “)” into a sequence in order to escape what???
            strg-c....????
 I can not tell!
 It might be easier to translate from hex to ascii than to understand any man page.
 46 55 43 4B 6D 41 6E 50 41 47 45 53 !!!!
  
Is there anything that allows a dummie like me to understand man pages in order to use Linux to rewrite a program or makes man pages understandable for people who have other things to do than to sleep with their computer???

your dummie M.Peters

PS:The vba code i created consists of over one million signs and about 30 sub functions with heavy math and not to forget the UI with help pages included.

---

