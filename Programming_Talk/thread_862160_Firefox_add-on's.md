---
title: "Firefox add-on's"
date: 2008-07-17
forum: Programming Talk
---

### Post by LoneWolfJack on 2008-07-17
Hi folks,

I'm currently looking into the possibility of developing a firefox add-on, yet I can't seem to find any relating page on mozilla.org.

So far, I found out that they're working with several XML files for GUI customization and meta data, and they seem to be crazy enough do let the entire programming be done in JavaScript (still can't believe this).

Yet some projects I've seen use Perl as the main programming language, probably compiling the code before adding it to the xpi file thingy.

So before spend two more hours trying to figure out what's going on, I though I'd give it a try asking for ideas here... so does anyone have experience in add-on programming with firefox? Do you know any good resources?

I'd like to use C or PHP for the backend programming of my add-on because I consider JavaScript to be too bug-prone and time consuming to debug. Also, I'd like to program the essentials in a way that will allow me to use them for converting the add-on to a IE add-on.

Any ideas?

---

### Post by mssever on 2008-07-17
> **LoneWolfJack said:**
> Hi folks,

I'm currently looking into the possibility of developing a firefox add-on, yet I can't seem to find any relating page on mozilla.org.

So far, I found out that they're working with several XML files for GUI customization and meta data, and they seem to be crazy enough do let the entire programming be done in JavaScript (still can't believe this).

Yet some projects I've seen use Perl as the main programming language, probably compiling the code before adding it to the xpi file thingy.

So before spend two more hours trying to figure out what's going on, I though I'd give it a try asking for ideas here... so does anyone have experience in add-on programming with firefox? Do you know any good resources?

I'd like to use C or PHP for the backend programming of my add-on because I consider JavaScript to be too bug-prone and time consuming to debug. Also, I'd like to program the essentials in a way that will allow me to use them for converting the add-on to a IE add-on.

Any ideas?
By add-ons, do you mean extensions, plugins, themes, languages, or something else?

I haven't written any extensions for Firefox, but I'm guessing that you're pretty much restricted to Javascript. Firefox has a built-in Javascript interpreter; it almost certainly doesn't have one for PHP. To write a C extension, you'd probably have to statically link everything to make it run everywhere people might want to install it without making them compile from source. And that's assuming that Firefox even allows you to use C, which I doubt.

As far as Javascript debugging goes, try the Firebug extension. At least there's a debugger for Javascript, unlike PHP (last I checked, at least).

---

### Post by LoneWolfJack on 2008-07-17
Even Mozilla isn't clear what they consider extensions and what they consider plugins so I have no idea.

There's a tool called addblockplus ([http://adblockplus.org]("http://adblockplus.org") which is mainly written in Perl and which will remove ads from websites. 

So my guess is that you can use compiled code but I can't seem to find any resource on this topic.

I'm intending to build something that is remotely similar to that addblockplus thingy bu I don't want to implement it in Perl and I also don't feel like taking the addblock code apart just to learn how the mozilla API works.

Any further ideas?

---

### Post by mssever on 2008-07-17
> **LoneWolfJack said:**
> Even Mozilla isn't clear what they consider extensions and what they consider plugins so I have no idea.The delivery mechanism is different. There aren't many common plugins. Examples include the Adobe Reader plugin, and various media player plugins. I think that plugin authors have a lot more freedom than extension writers.

It's annoying that Mozilla is trying to replace meaningful terms such as *extension* with the less meaningful term *add-on*.

> There's a tool called addblockplus ([http://adblockplus.org](http://adblockplus.org) which is mainly written in Perl and which will remove ads from websites.
AdBlockPlus is written in Javascript, XUL, and the rest of the standard extension development stack. There's no Perl whatsoever in there. I just looked.

---

### Post by LoneWolfJack on 2008-07-17
um... did you check out the web CVS?

in src you'll find plenty of pl files with perl code in it...

---

### Post by mssever on 2008-07-17
> **LoneWolfJack said:**
> um... did you check out the web CVS?

in src you'll find plenty of pl files with perl code in it...
No, I looked in the extension files as they're installed in Firefox. Perhaps they use Perl to generate some/all of the extension files, but that would mean that the build system is Perl, not the extension itself. What actually gets distributed is as I described above.

EDIT:By the way, even if you generate the Javascript code, you still have to ensure that it's correct.

---

### Post by LoneWolfJack on 2008-07-17
Ok, you're perfectly right. It never even occured to me that they may have been using Perl to generate the JS code because I didn't expect anyone to use JS for something like this. 

For me, Mozilla/FF just took a heavy blow to their reputation.

But thanks to you for helping me getting that straightened out.

---

### Post by Can+~ on 2008-07-17
[http://developer.mozilla.org/en/docs/Building_an_Extension](http://developer.mozilla.org/en/docs/Building_an_Extension)

---

### Post by mssever on 2008-07-17
> **LoneWolfJack said:**
> Ok, you're perfectly right. It never even occured to me that they may have been using Perl to generate the JS code because I didn't expect anyone to use JS for something like this. 

For me, Mozilla/FF just took a heavy blow to their reputation.
Consider this from another angle. Suppose you're building a browser similar to Firefox. Which language(s) do you support? There are two broad categories to choose from.

First is languages that compile to native code, such as C. If you go that route, you have cross-platform issues. Extensions will probably have to be compiled for each OS and hardware platform. Plus, they're more likely to unnecessarily use OS-specific stuff--particularly when written by Windows users who don't care about, e.g., Linux. So compiled-to-native languages are out.

The other option is an interpreted language such as Python, Perl, etc. (including Java and other bytecode-interpreted languages). Of course, if you use such a language, you have to have an interpreter running anytime an extension is running. It just so happens that every modern browser must already include a Javascript interpreter in order to do its job of rendering websites. Consider that Firefox is already quite large, and that it already uses a lot of memory. Why make matters worse by adding one or more additional interpreters?

Javascript isn't my favorite language, but it isn't terrible, either. IMHO, it's worst problem is poor documentation.

EDIT: I'm guessing that extensions use a superset of Javascript to provide features impossible in standard JS due to security concerns.

---

