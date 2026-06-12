---
title: "[SOLVED] Any XML Validators?"
date: 2007-11-12
forum: Programming Talk
---

### Post by Dannik on 2007-11-12
Hey guys, please suggest some nice XML Validators. I couldn't get XMLStarlet to work.

---

### Post by LaRoza on 2007-11-12
[http://www.getdeb.net/search.php?keywords=XML](http://www.getdeb.net/search.php?keywords=XML)

Should be what you want.

---

### Post by stylishpants on 2007-11-13
xmllint and xmlstarlet both work well for me.  I use them for validating against both xml schema and RELAX NG.

---

### Post by Dannik on 2007-11-13
Thank you for the link above. Well, I dont know why, but XMLStarlet just doesn't work. Whenever I type in "xml" in console, it says "bash: xml: command not found". Any ideas why?

---

### Post by meatpan on 2007-11-13
Consider using firefox for a quick & dirty XML validation.  There are also a  few plug-ins that have some bells & whistles.

---

### Post by LaRoza on 2007-11-13
> **meatpan said:**
> Consider using firefox for a quick & dirty XML validation.  There are also a  few plug-ins that have some bells & whistles.

I know XML aware browser can check for well formed XML, but I don't if any can validate against an XML Schema or DTD, like the app I linked above.

---

### Post by Dannik on 2007-11-13
How can I use firefox for validation? I thought all it does is show if document is well-formed. I need to validate it based on DTD.

---

### Post by LaRoza on 2007-11-13
> **Dannik said:**
> How can I use firefox for validation? I thought all it does is show if document is well-formed. I need to validate it based on DTD.

Locally, you can't as far as I know (as I stated). You can use the app I linked to, it works.

---

### Post by tbfr on 2007-11-13
> **Dannik said:**
> Thank you for the link above. Well, I dont know why, but XMLStarlet just doesn't work. Whenever I type in "xml" in console, it says "bash: xml: command not found". Any ideas why?

type in 'xmlstarlet' instead of 'xml', that should be the only difference from the websites documentation. it's a great tool.

---

### Post by Dannik on 2007-11-13
Yes, Laroza the program does validate xml.
Tbfr, whenever I type "xmlstarlet" it tells me to use "xml". I still wonder why doesn't "xml" works. It seems like I'm the only one who has this problem.

---

### Post by tbfr on 2007-11-13
> **Dannik said:**
> Yes, Laroza the program does validate xml.
Tbfr, whenever I type "xmlstarlet" it tells me to use "xml". I still wonder why doesn't "xml" works. It seems like I'm the only one who has this problem.

don't worry, just use xmlstarlet :) if you call xmlstarlet without parameters it shows a help page, unfortunately with the wrong command name.

there are two debian bug reports about this:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=398267](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=398267)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373167](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373167)

---

### Post by Dannik on 2007-11-13
lol, wow thank you so much. I did use "xmlstarlet" instead of "xml" and it worked! Strange, I was so sure that I tried it before and it didn't work.

---

