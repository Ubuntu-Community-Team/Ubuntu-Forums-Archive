---
title: "Rich text or Html text editor control in Linux"
date: 2011-07-26
forum: Programming Talk
---

### Post by jeff.biggeek02 on 2011-07-26
Hey guys,

I've been an Ubuntu user for about 1.5 years now with no usage of Windows except for my job where I have to. :) I have decided to dabble in Mono and GTK Sharp a bit, just to see what it takes to whip up a simple application in Ubuntu.

I am looking for some kind of a "desktop" (read, "not web") control that lets me give the user features such as:

- Bullet points
- Tables
- Bold, Italics, Underlining
- Left, Center, Right, Fully justified
- Etc

Ideally, if I was in Windows land, I would use Microsoft's OLE controlss to drop a word document editor in my app and be done with it.  Can I do something like that with OpenOffice?  Or perhaps there is another control that would provide richer features than a text box?  I found Mono.TextEditor, but that is geared towards code editing and not note taking.

Thanks for any ideas!

---

### Post by jeff.biggeek02 on 2011-07-29
And we have a winner.  In the case of Mono, I'm using Webkit-Sharp, which is just a CLI binding for the popular Webkit.

This GTK based widget has a set_editable(true) function that automatically builds an HTML WYSIWYG editor into your control (similar to the one I'm typing into right now).  Excellent!

---

