---
title: "exporting environment variables from a program to the shell that called it."
date: 2009-07-21
forum: Programming Talk
---

### Post by Markhor on 2009-07-21
Exporting variables within a script scopes them to that script and its children.

  I'm wondering if it's possible for a program that is invoked at a terminal to export variables into that terminals environment?

---

### Post by slakkie on 2009-07-21
> **Markhor said:**
> Exporting variables within a script scopes them to that script and its children.

  I'm wondering if it's possible for a program that is invoked at a terminal to export variables into that terminals environment?

EXPORT also sets the scope outside of the script. Not exporting is only within the script (and its children).

---

### Post by Markhor on 2009-07-21
I was referring to setting the environment of the parent process from one of its child processes. 
For example:
                   at the terminal running: 
                      ```
`export test=test`
```
                   (or w/o backticks in a script)
                  followed by:
                   ```
printenv | grep test
```
shows that test is not moved into the (parent) terminal's environment by child process.

---

### Post by ratcheer on 2009-07-21
Try prefacing the export with the source operator, ".". E.g., 

```
. export test=test
```

Tim

---

### Post by Markhor on 2009-07-21
That works! Thanks for the replies.

---

### Post by ratcheer on 2009-07-22
You are welcome.

Tim

---

