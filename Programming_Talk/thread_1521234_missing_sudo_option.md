---
title: "missing sudo option?"
date: 2010-06-30
forum: Programming Talk
---

### Post by RobertL on 2010-06-30
I invoke a bash script from a python script and the bash script contains  a sudo line. I would like the user to have only 1 chance to supply the  correct password to sudo. If she doesn't give the right pw I want sudo  to exit with a non-zero exit code. Is there a way to make sudo do that?   I don't want the user to have to type control-C to get out of sudo if  she doesn't know the pw. I expected sudo to have an option to specify how many times the user can give the wrong password but I can't find it. Am I missing something?

This description of the situation is simplified to make the  question clear.

---

