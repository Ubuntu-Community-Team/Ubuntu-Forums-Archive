---
title: "cscope + emacs issue, programmers out there, pls respond"
date: 2007-11-28
forum: Programming Talk
---

### Post by maindoor on 2007-11-28
I am trying to use cscope on emacs built like this:
                 1) find ./ -name "*.[csSh]" -type f -print > cscope.files
                 2) cscope -k -q -b
                 generates four files cscope.files , cscope.in.out, cscope.out,
                 cscope.po.out

                 When I run cscope.el on emacs, any cscope operation 
                 gives me this output in the cscope emacs buffer

                 cscope: -q option mismatch between command line 
                             and old symbol database
                 cscope: removed files cscope.out.in and cscope.out.po

                 But there was no cscope.out.in and cscope.out.po 
                 created originally. Then Why do I get this message ?

Thanks,
Sanjeev.

---

### Post by maindoor on 2007-11-28
found the problem. -d option was not being read by xcscope.el properly. tested the fix too.

---

### Post by saisairpi on 2008-09-01
I met the same problem. Could you tell me how you solve it? Thanks a lot.

---

