---
title: "include a define file in arm asm code which doesn't conform to assembly defines"
date: 2014-07-18
forum: Programming Talk
---

### Post by mayankmehta83 on 2014-07-18
Hi,

I have a define file which has defines in the form "`define <name> <value>"; but assembly would have defines in the form ".equ <name>, <value>" ("#define <name> <value>" didn't work for me); now is there a way I can include define file in a way it converts "`define <> <>" to ".equ <>, <>" while including in asm so that asm would recognize these defines?

Thanks in advance.

---

### Post by ofnuts on 2014-07-18
No, but you can write a quick script to transform your available file into something the assembler will accept. Sed is your friend. You can also include a rule in your make file to run the script on your original define file whenever it changes.

---

