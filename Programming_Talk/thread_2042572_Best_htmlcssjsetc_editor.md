---
title: "Best html/css/js/etc editor"
date: 2012-08-14
forum: Programming Talk
---

### Post by subtlebreath on 2012-08-14
Not positive if this is the right place to post this question, but what is the best web code editor?

I usually use Dreamweaver or Notepad++ on my Windows 7 system, but I'm totally new to Linux so I don't know what's good.

---

### Post by slooksterpsv on 2012-08-14
I love using BlueFish for a Notepad++ like program.

BlueGriffon is coming along, so I'd look into that one as well.

---

### Post by ads52 on 2012-08-15
There is a nice new version of Bluefish: 2.2.3 which is well worth a look.

---

### Post by trent.josephsen on 2012-08-15
jEdit. Emacs. Vim. In order of which one I'd suggest you try first, and in reverse order of my personal preference.

This is a recurring discussion and no different from any of the other "best editor" threads out there.

---

### Post by subtlebreath on 2012-08-15
I tried installing Bluefish using the process outlined here:
[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.2.3_on_Ubuntu_12.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.2.3_on_Ubuntu_12.04_or_newer)

But when I run it I get:
error reading list 1 Error opening file: No such file or directory

** (bluefish:3067): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directory error reading list 1 Error opening file: No such file or directory

---

### Post by na5h on 2012-08-15
I recommend [Aptana Studio]("http://www.aptana.com/"). Bluefish, Komodo Edit, Netbeans and Eclipse are a few other popular alternatives...

---

### Post by subtlebreath on 2012-08-15
Since Bluefish was giving me trouble I installed Aptana using this guide:
[http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/](http://www.samclarke.com/2012/04/how-to-install-aptana-studio-3-on-ubuntu-12-04-lts-precise-pangolin/)

When I run it though I get this:
(Aptana Studio 3:8055): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed.

---

### Post by phrak on 2012-08-15
vim...

but I agree with others here, there isn't really a "best" just ones that touch a soft spot in our collective personal prefrences..

---

### Post by trent.josephsen on 2012-08-15
> **phrak said:**
> just ones that touch a soft spot in our collective personal prefrences..

Eloquent :)

---

### Post by ads52 on 2012-08-15
> **subtlebreath said:**
> I tried installing Bluefish using the process outlined here:
[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.2.3_on_Ubuntu_12.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.2.3_on_Ubuntu_12.04_or_newer)

But when I run it I get:
error reading list 1 Error opening file: No such file or directory

** (bluefish:3067): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directory error reading list 1 Error opening file: No such file or directory

Seems a little odd, perhaps have a look at this page on the Ubuntu Community Docs:

[https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

---

### Post by subtlebreath on 2012-08-15
> **ads52 said:**
> Seems a little odd, perhaps have a look at this page on the Ubuntu Community Docs:

[https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

I uninstalled Bluefish and reinstalled it following that guide, and I still get that same error. So frustrating...

---

### Post by ads52 on 2012-08-16
> **subtlebreath said:**
> I uninstalled Bluefish and reinstalled it following that guide, and I still get that same error. So frustrating...

Can I suggest that you close Bluefish down, back up your config files:

```

mv -v ~/.bluefish ~/.bluefish_bak

```

and then restart bluefish?

---

### Post by na5h on 2012-08-16
Installing Java, unpacking the file downloaded from Aptana.com and double clicking on "Aptana Studio" inside the unpacked folder should be enough to run Aptana Studio...

---

### Post by vasa1 on 2012-08-16
> **trent.josephsen said:**
> jEdit. Emacs. Vim. In order of which one I'd suggest you try first, and in reverse order of my personal preference.

This is a recurring discussion and no different from any of the other "best editor" threads out there.

+1.

Might as well toss in Geany.

---

### Post by DarkAmbient on 2012-08-16
You've most likely already used gedit (being the default texteditor in Ubuntu) but perhaps you haven't tried coding in it? It has plenty of built-in functionality for coding-purposes (syntax-highlighting, auto-indentation etc)  as well as plug-ins to extend it, such as code-snippets or a built-in terminal among else.

So in case you haven't give gedit a shot for some coding. It's sort of the only tool I use now a days for coding.

---

### Post by subtlebreath on 2012-08-16
> **DarkAmbient said:**
> You've most likely already used gedit (being the default texteditor in Ubuntu) but perhaps you haven't tried coding in it? It has plenty of built-in functionality for coding-purposes (syntax-highlighting, auto-indentation etc)  as well as plug-ins to extend it, such as code-snippets or a built-in terminal among else.

So in case you haven't give gedit a shot for some coding. It's sort of the only tool I use now a days for coding.

Haven't tried coding with gedit yet. I'll see how I like it. Really all I care about in a web editor is that it color codes, so if it has that then I'm set.

PS. Moonsorrow is awesome.

---

### Post by DarkAmbient on 2012-08-17
> **subtlebreath said:**
> Haven't tried coding with gedit yet. I'll see how I like it. Really all I care about in a web editor is that it color codes, so if it has that then I'm set.

PS. Moonsorrow is awesome.

Cool, and yea coding + metal is solid stuff!

---

### Post by trestevenson on 2013-02-26
I hadn't thought to try gedit before downloading netbeans.  I hope to get some time with both of them this evening to see which I prefer.

---

