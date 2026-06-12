---
title: "Java actionPerformed and global variables"
date: 2007-12-20
forum: Programming Talk
---

### Post by DBQ on 2007-12-20
Hi everybody,
   I have a question.  In java I have a class which has global variables.  Also, in this class I have an actionPerformed method implemented, which is called everytime some event happens.  Now, in actionPerformed, I set these variables.  Although inside actionPerform their values do appear to change, after it is finished, the values go back to their old ones.  Why is this happening?  How do I get the values to stay?  Please help..

---

### Post by CptPicard on 2007-12-21
Post code, would be easier to tell what is wrong :)

What do you mean by "global variables"? Are they "public static" or something? Are you declaring new local ones in actionPerformed that mask class/object members?

---

### Post by DBQ on 2007-12-21
The variables are public static.  I do not mask the c lass.

---

### Post by Ramses de Norre on 2007-12-21
No one will be able to help you without seeing the actual code..

---

