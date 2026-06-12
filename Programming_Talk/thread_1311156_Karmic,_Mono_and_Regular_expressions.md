---
title: "Karmic, Mono and Regular expressions"
date: 2009-11-02
forum: Programming Talk
---

### Post by vancheese on 2009-11-02
Hi people

I'm using a new install of Karmic 64bit and have install mono and monodevelop from main/universe. However my issues arise when I try to use standard C# regex libs. The majority of web informations suggests that I should use

using System.Text.RegularExpressions;

However, The compiler borks that the regular expressions doesn't exist in the namespace of System.text and I can't locate RegularExpressions on my computer?

Any Suggestions/help?

Andy

---

### Post by directhex on 2009-11-02
Um, it ought to be fine, it's in System.dll

---

### Post by vancheese on 2009-11-03
Can you give a simple example of code which you know works with Mono on Karmic? Then I can work out if its my code or computer causing the problem!

---

### Post by vancheese on 2009-11-03
Please ignore my muppetdom - I had not included the correct references -

---

