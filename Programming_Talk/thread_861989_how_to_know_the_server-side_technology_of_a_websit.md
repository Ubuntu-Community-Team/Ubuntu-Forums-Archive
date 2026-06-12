---
title: "how to know the server-side technology of a website"
date: 2008-07-17
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-17
how do i know what server-side technology (like jsp / asp), a server uses, if all the pages are opened by forwarding (eg. by jsp:forward tags), so that the url of the page doesnt change at all.

---

### Post by dexter.deepak on 2008-07-17
anyone ???:(

---

### Post by Tony Flury on 2008-07-17
I don't think you can - why do you need to know ?

---

### Post by dexter.deepak on 2008-07-17
just to know, if someone/i can attack the website by knowing the drawbacks of the used technology.

---

### Post by Tony Flury on 2008-07-17
One way to find out is to maybe look at the headers - might be some clues in there.

---

### Post by mssever on 2008-07-17
You can look for things that are common to a particular technology, such as headers, URL extensions, etc. But remember that all that stuff can be forged. A URL ending in php doesn't always mean that PHP is used on that site. It could be a trick.

---

