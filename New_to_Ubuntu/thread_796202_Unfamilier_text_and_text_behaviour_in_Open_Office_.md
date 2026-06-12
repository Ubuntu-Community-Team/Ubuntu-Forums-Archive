---
title: "Unfamilier text and text behaviour in Open Office 2.4"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by a.v.l on 2008-05-16
Having typed out a document using Open Office 2.4 word processor in Ubuntu 8.04 I find that when I print out the document the text doesn't appear as it does on the screen. For example several lines of text appears in a  different font than appears on screen.  Making changes to the text has no effect.

Another point is that I don't have the options of choosing familier font types like Arial and Times Roman etc. A Screen shot shows the fonts options available which are unfamilier to me. How do I correct this problem  please?

---

### Post by Joeb454 on 2008-05-16
Those fonts are actually Microsoft fonts, can you open a terminal and type or copy/paste ```
sudo apt-get install msttcorefonts
``` or search Synaptic (System > Administration > Synaptic Package Manager) for it :)

That should give you some of those fonts to use :)

---

### Post by a.v.l on 2008-05-16
> **Joeb454 said:**
> Those fonts are actually Microsoft fonts, can you open a terminal and type or copy/paste ```
sudo apt-get install msttcorefonts
``` or search Synaptic (System > Administration > Synaptic Package Manager) for it :)

That should give you some of those fonts to use :)



Thanks that seems to have helped.

---

### Post by Joeb454 on 2008-05-16
No problem, it includes Verdana which used to be one of my favourite fonts in Office :) That's how I know ;)

---

