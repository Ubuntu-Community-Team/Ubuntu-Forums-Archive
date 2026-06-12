---
title: "Javascript to add tags to text box"
date: 2008-12-22
forum: Programming Talk
---

### Post by Bradosia on 2008-12-22
How do you create a button that when clicked will put tags like ```
[left][/left]
``` around the text that is currently highlighted in a text box. I am creating my own forum at [http://asodar.com/board/](http://asodar.com/board/)
Please do not ask me to go and download a pre-made forum and use it because I really want to do it myself. Thank you.

---

### Post by ufis on 2008-12-22
Many javascript wysiwyg editors exist already. Many of these are freely(*) available.

I believe this forum's software uses one of these.

Google "javascript wysiwyg editor"

It would be infinitely easier to download one of these, and edit it as you wish to change it than to write your own.

---

### Post by Reiger on 2008-12-22
But writing your own would be infinitely more rewarding/ would not incur the wrath of the person who is going to deal out the grades this season. ;)

Anyway since it is shove time: [http://csshtmltutorial.com/csshtmltutorial-htmlformcodetutorial.php](http://csshtmltutorial.com/csshtmltutorial-htmlformcodetutorial.php). This will give you all the basic GUI widgets/controls you'll ever need (you'll probably create more complex ones yourself, no doubt); but a word to the wise: input elements are not limited to being childs of form elements only, you can for instance put them into div or p elements -- which is entirely valid in XHTML. Now would maybe a good time to read up on 
(a) (Adding) event handlers with JavaScript
(b) The difference(s) between inline and block elements. For those who've never taken a look at the XHTML DTD: it is one of the key concepts in the entire DTD; a large amount of code is spent on regulatingthese two entities and definining these two entities -- essentially reducing the differences between XHTML elements to default style constraints/rules.
(c) Manipulating the DOM with JavaScript 

There are tons of guides, howtos and tutorials out there which cover those concepts sufficient to start some proof-of-concept coding with.

---

### Post by Wybiral on 2008-12-22
> **Reiger said:**
> But writing your own would be infinitely more rewarding

And infinitely more of a waste of development/testing time, more code to maintain, and more of an opportunity for bugs/browser compatibility issues.

---

### Post by Reiger on 2008-12-22
> **Wybiral]And infinitely more of a waste of development/testing time, more code to maintain, and more of an opportunity for bugs/browser compatibility issues.[/quote]

To quote the OP:

[QUOTE=Bradosia said:**
> Please do not ask me to go and download a pre-made forum and use it **because I really want to do it myself**. Thank you.

I think its about the reward of DIY-solutions thing, but... I may be missing something? :P

---

