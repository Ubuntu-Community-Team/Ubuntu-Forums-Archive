---
title: "Which licence is better"
date: 2009-05-23
forum: Packaging and Compiling Programs
---

### Post by checkersland on 2009-05-23
Hi

I'd like to submit a new program into Ubuntu repository and I can't select an appropriate licence for the program. There are a lot of licences and I can't select one...

I'd like to see the next rules in that licence: nobody should decompile, change and sell the program. I don't publish the sources, but the program is free for use and doesn't include any fees.

Which common used licence is the best for my requests?

Thanks, Pavel

P.S. Sorry if select inappropriate forum section...

---

### Post by lisati on 2009-05-23
You might want to look into ["Creative Commons"]("http://creativecommons.org/")

---

### Post by checkersland on 2009-05-28
> **lisati said:**
> You might want to look into ["Creative Commons"]("http://creativecommons.org/")
I've never heard about this licence. What about GNU GPL or GNU LGPL? It's really difficult to catch all nuances of such licences...

---

### Post by zolookas on 2009-05-28
You program is not open source so you can't licence it under GPL. LGPL is suitable only if your main program is open source and you need to provide closed source plugins or addons.

---

### Post by soltanis on 2009-05-28
Yeah, just FYI your model is not free/open-source based on your restrictions, so GPL/LGPL/BSD/Zlib/Apache would not apply to you.

---

### Post by checkersland on 2009-05-28
> **zolookas said:**
> You program is not open source so you can't licence it under GPL. LGPL is suitable only if your main program is open source and you need to provide closed source plugins or addons.

Thanks! As I understand BSD licence is good enough, but I'd like to deny modification of my program and selling of it... As I know apache licence is also permit to modify source (and crack it if possible).

---

### Post by checkersland on 2009-05-28
> **soltanis said:**
> Yeah, just FYI your model is not free/open-source based on your restrictions, so GPL/LGPL/BSD/Zlib/Apache would not apply to you.
Hmm. As I remember there are no any obligations about source publishing in BSD licence... Am I right?

As I know there are a lot of proprietary code in Ubuntu repositories. What kind of licences do they use?

---

