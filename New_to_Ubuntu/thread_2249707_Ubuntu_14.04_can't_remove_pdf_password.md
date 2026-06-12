---
title: "Ubuntu 14.04 can't remove pdf password"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by Dactula on 2014-10-24
Hi All,

I am using Ubuntu 14.04. I tried to remove the password of a pdf file by using the option "forget password immediately". Then I typed the password and opened the pdf file. After I closed the file and tried to open it it again asked for password. Previously in Ubuntu 10.04 I could remove the password using this method. Please help.

---

### Post by vasa1 on 2014-10-24
Install qpdf from the software center. You can then use it like this:
```
qpdf --password=###### --decrypt input.pdf output.pdf
```

---

### Post by Dactula on 2014-10-26
It worked. Thanks for your prompt reply.

---

