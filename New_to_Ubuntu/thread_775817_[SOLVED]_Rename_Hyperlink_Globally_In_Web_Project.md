---
title: "[SOLVED] Rename Hyperlink Globally In Web Project"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-04-30
Firstly, I used to use Dreamweaver, where it was possible to rename a file from say index.html to index.php; and all the instances of links to the renamed file would be amended.

Now that I don't use Dreamweaver, is there an application / way that I can do this.

Quanta doesn't seem to do it.
Neither do nvu or Bluefish.
Nor does Aptana.

Can anyone point out something that I've missed (?)

I don't feel like editing approx 500 files by hand to change one hyperlink.

Cheers.

---

### Post by master5o1 on 2008-04-30
Dreamweaver does work in Wine. If you want to use dreamweaver you can.

I know Dreamweaver Studio 8 (and all of Studio 8) work in Wine.

System > Administration > Synaptic Package Manager : Search "wine", mark + apply -> Install Dreamweaver :)



The reason why I give you this method is that I don't like using any wysiwyg software for web developing. It just makes my eyes bleed when I do use them.

---

### Post by Ek0nomik on 2008-04-30
I'm not sure if it does or not, but Eclipse is the only other IDE that I can think of possibly carrying that functionality.

---

### Post by WorldTripping on 2008-04-30
> **master5o1 said:**
> Dreamweaver does work in Wine. If you want to use dreamweaver you can.

I know Dreamweaver Studio 8 (and all of Studio 8) work in Wine.



Cheers, but I've only got a copy of Dreamweaver 4

And for the life of me I can't get it to run.

I too don't like WYSIWYG for coding, prefering to do it in a text editor. However DW did have a very good file management system (like drag 'n drop a file and all the references would be updated).

> **Ek0nomik said:**
> I'm not sure if it does or not, but Eclipse is the only other IDE that I can think of possibly carrying that functionality.

Cheers for that, I'll have a look now.

---

### Post by master5o1 on 2008-04-30
I thought Eclipse was for Java programming?

Another thing I can think of is that in gedit, you can do the find+replace option to change all instances of '/path/monkey/index.html' to '/path/monkey/index.php' in a file ... one file at a time.

How many files did you say you had to change?

---

### Post by WorldTripping on 2008-04-30
> **master5o1 said:**
> I thought Eclipse was for Java programming?

Another thing I can think of is that in gedit, you can do the find+replace option to change all instances of '/path/monkey/index.html' to '/path/monkey/index.php' in a file ... one file at a time.

How many files did you say you had to change?

I've just had a quick look at Eclipse, and you can load / amend <html> and php files, but no global find / replace that I can see.

Maybe I would be better off using the terminal.

I want to replace /name/index.html with /name/index.php in the html code.

Would there be a command script that I could use ?

---

### Post by master5o1 on 2008-04-30
Text Editor (Gedit) (command: gedit)

Has the find/replace that I was talking about. (alt+f2 and enter 'gedit', press enter -- or right click on your file click Text Editor)

Gedit is Linux's 1up on Windows' Notepad -> Gedit has Find & Find/Replace, syntax highlighting, line numbering, auto-indenting, brace highlighting (you have one bracket selected, it's pair is highlighted)

---

### Post by WorldTripping on 2008-04-30
YES !!!

[http://crunchbang.org/archives/2008/04/20/rpl-a-find-and-replace-terminal-tool/]("http://crunchbang.org/archives/2008/04/20/rpl-a-find-and-replace-terminal-tool/")

Had to install rpl

Took about 2 seconds to find / replace two strings over a whole directory.

That has just saved me a whole pile of work.

And I learnt something new today !

---

### Post by WorldTripping on 2008-04-30
And that is yet one more reason why I love working in Linux/Gnu.

Cheers for everyone's input.

Now how do I mark threads solved in this new forum ?

---

### Post by WorldTripping on 2008-04-30
> **master5o1 said:**
> Text Editor (Gedit) (command: gedit)

Has the find/replace that I was talking about. (alt+f2 and enter 'gedit', press enter -- or right click on your file click Text Editor)

Gedit is Linux's 1up on Windows' Notepad -> Gedit has Find & Find/Replace, syntax highlighting, line numbering, auto-indenting, brace highlighting (you have one bracket selected, it's pair is highlighted)


Thanks for that.

I use it a bit for manually coding html, but more handily I use the gedit plugins for encrypting / decrypting text to and from a GnuPG keyring.

---

### Post by master5o1 on 2008-04-30
There should be a 'mark as solved' somewhere... probably in one of the three links at the top right of the forum (just before the first post on each page)

---

### Post by Ek0nomik on 2008-04-30
> **master5o1 said:**
> There should be a 'mark as solved' somewhere... probably in one of the three links at the top right of the forum (just before the first post on each page)

The feature hasn't been implemented yet.

---

