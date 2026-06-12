---
title: "Best webeditor for ASP &amp; PHP"
date: 2007-09-18
forum: Programming Talk
---

### Post by larsdk on 2007-09-18
Hi there,

Since switching to Ubuntu I have been trying a couple of different solutions for webediting. I develop and maintain a couple of sites, some of which are in PHP and some in ASP. I need a simple editor that can recognize both ASP and PHP and do syntax highlight. Right now I am using quanta, but it feels quite heavy to work with so far...

Any suggestions?

Lars

---

### Post by Jon@bayleys.org.uk on 2007-09-18
try screem, or Kompozer. I think i tried Kompozer with php, and I'm not sure it picked up the formating, but that might be something which is changeable. Screem definitely worked.

---

### Post by larsdk on 2007-09-18
Sorry - forgot to write. I tried SCREEM as well. Did not work with ASP...

---

### Post by LaRoza on 2007-09-18
> **larsdk said:**
> Sorry - forgot to write. I tried SCREEM as well. Did not work with ASP...

I would use GEdit or Kwrite as usual, but I know for a fact Crimson Editor has ASP syntax highlighting (you can also make your own schemes) and runs in Wine.

---

### Post by pmasiar on 2007-09-18
SciTE has syntax higlighting for everyting I encoutered so far, including obscure languages like Baan and ABAP. It is relatively easy to define own styles, and it works on Windows too. My favorite simple editor.

---

### Post by Adicted on 2007-09-18
i like quanta, i don't have too much exprerience in ubuntu, but i like it

---

### Post by thesmartace on 2007-09-18
I do a lot of PHP and use Quanta+. I don't use ASP so I can't vouch for Quanta for that.

---

### Post by Mirrorball on 2007-09-18
Kate has syntax highlighting for PHP and ASP. I really love this editor, and whenever I'm using a more complicated IDE, I miss my Ctrl+I and Ctrl+D (indent and comment shorcuts).

---

### Post by altonbr on 2007-09-22
Notepad++ is a great Windows editor and will work in Ubuntu if you install wine.

[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)
```
sudo aptitude install wine
```
I personally prefer gEdit, especially in Gusty (Gnome 2.20).

---

### Post by pmasiar on 2007-09-23
> **altonbr said:**
> Notepad++ is a great Windows editor and will work in Ubuntu if you install wine.

Running wine just to run a windows-based editor? Kinda overkill, don't you think so? There are plenty of great cross-platform editors, like ie SciTE.

---

### Post by altonbr on 2007-09-25
> **pmasiar said:**
> Running wine just to run a windows-based editor? Kinda overkill, don't you think so? There are plenty of great cross-platform editors, like ie SciTE.

Yup, sure, Notepad++ was based on Scite, but Notepad++ has far surpassed it in my opinion. Anyway, I did say that I prefer gEdit, especially in Gusty.

---

### Post by medivh on 2007-10-02
I was using aptana in windows environment i will give it a try on ubuntu. Does anyone have experiences about it on linux? Its especialy an eclipse mod.

---

### Post by nick.tux on 2007-10-10
I use bluefish editor. you may try that one. i'm using php right now, haven't tried with asp yet.

---

### Post by RyanZec on 2007-10-10
> **pmasiar said:**
> Running wine just to run a windows-based editor? Kinda overkill, don't you think so? There are plenty of great cross-platform editors, like ie SciTE.

Note to me.  I have PhpED and i have not seen a single application for linux that comes with ALL the feature i need that it comes with(syntax highlighting, cold folding, syntax checking, code completion, code explorer to look at variables, functions, classes, etc...).  Grant you the first 2 feature are easy to find but that last 3 are not.  and i know some people might say that the last 3 make you a worst programmer or what not but the amount of time those features save me make them invaluable.

---

### Post by newsun on 2007-12-20
Quanta is awesome, although I like the svn integration on kdevelop better as it shows files edited and ready to be commited in the file tree, along with being able to commit from there easily, but the simple upload of files withing quanta is essential for php progarmming to me. no asp experience.

---

### Post by Sh@m@n on 2007-12-20
I use Eclipse PDT for PHP development.

It's a shame that, Ubuntu doesn't have an eclipse-pdt package available.

---

### Post by pcjunkie on 2008-08-19
There is a Linux one, I just have no plugin folder to place it in...still searching though.

---

### Post by rianjs on 2008-08-19
I'm a fan of EditPlus for Windows, and scite for Linux. Just my $0.02

---

### Post by nagaozen on 2009-01-06
> **larsdk said:**
> Hi there,

Since switching to Ubuntu I have been trying a couple of different solutions for webediting. I develop and maintain a couple of sites, some of which are in PHP and some in ASP. I need a simple editor that can recognize both ASP and PHP and do syntax highlight. Right now I am using quanta, but it feels quite heavy to work with so far...

Any suggestions?

Lars

Just add an ASP.lang to your GTKSourceView-2.0 and use GEdit.

Best Regards,
Fabio Zendhi Nagao (nagaozen)

---

### Post by hessiess on 2009-01-06
Personally I like Vim.

---

### Post by altonbr on 2009-01-09
If this goes down the pipes, gtksourceview-2 (gedit) will soon have native ASP syntax highlighting: [http://bugzilla.gnome.org/show_bug.cgi?id=139968](http://bugzilla.gnome.org/show_bug.cgi?id=139968)

---

### Post by bandish on 2009-01-09
hi

I am using netbeans 6.5 all in one but doesn't support ASP 

a bit heavy but is stable and good.

In windows deran weaber cs3

---

### Post by jaypoc on 2011-07-13
I use Eclipse with the Aptana and Eclipse Colorer plugins and it works for ASP and PHP if you're just looking for Syntax Highlighting. I haven't had much luck with code-hints, but I haven't tried to configure them either.

---

