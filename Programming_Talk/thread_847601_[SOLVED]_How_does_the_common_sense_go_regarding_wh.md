---
title: "[SOLVED] How does the common sense go regarding what $VARIABLES should be Global or L"
date: 2008-07-02
forum: Programming Talk
---

### Post by jingo811 on 2008-07-02
How does the common sense go regarding what $VARIABLES should be Global or Local?  
I don't have any pirate's guideline to live by.  Should like 80% be Local or how should I balance it?

---

### Post by LaRoza on 2008-07-02
> **jingo811 said:**
> How does the common sense go regarding what $VARIABLES should be Global or Local?  
I don't have any pirate's guideline to live by.  Should like 80% be Local or how should I balance it?

They should all be local.

---

### Post by henchman on 2008-07-02
Does local mean "no object-scope variables, only function-scope variables"?

---

### Post by LaRoza on 2008-07-02
> **henchman said:**
> Does local mean "no object-scope variables, only function-scope variables"?

It means no global variables.

---

### Post by jingo811 on 2008-07-02
> **LaRoza said:**
> They should all be local.

Allrighty matey then 100% local $VARS will be my future pirate's guideline to live by then.

---

