---
title: "[SOLVED] Firefox 3 puzzle - won't display schedule"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by dansan on 2008-06-18
This is very minor, but I'll ask anyway.

Firefox 3 in Hardy doesn't display the TV schedule at eurosport.com, while the version of Firefox in Gutsy does, and so does Opera 9.5. What do I need to fix this hole in FF3?

Daniel

---

### Post by steve101101 on 2008-06-18
make sure the have the necessary plugins to display all the web content.

---

### Post by dansan on 2008-06-18
> **steve101101 said:**
> make sure the have the necessary plugins to display all the web content.

There are very few plugins for FF3. I've got Java. What else could be involved with display of a tv schedule?

Daniel

---

### Post by monkey56657 on 2008-06-18
It looks to me that the website will have to update to make this work in firefox 3. It doesn't look like a plugin issue just a general issue with ff3's rendering engine. 

Contact the site and advise them it doesn't work correctly in firefox 3, otherwise wait for them to realise and update themselves.

---

### Post by dansan on 2008-06-19
monkey56657

Thanks for the tip. Could you tell me how you figured this out -- what to check about websites?

---

### Post by monkey56657 on 2008-06-20
I used firebug an addon for firefox and found the code responsible for the tv schedule. There was nothing in the code that suggested a plugin was required. The only thing used is html/css/javascript. I had javascript enabled and no changes were made to how my browser renders html/css so I came to the conclusion that the page needed fixing.

---

