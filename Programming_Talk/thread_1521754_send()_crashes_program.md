---
title: "send() crashes program"
date: 2010-07-01
forum: Programming Talk
---

### Post by dawwin on 2010-07-01
I've got following code:
```

                while ((rbytes = read(filedesc, buffer, BUFFLEN)) > 0) {
                        if (send(dpack->cs, buffer, rbytes, 0) <= 0) {
                                perror("send");
                                close(filedesc);
                                return;
                        }
                }

```This is a part of simple HTTP server. I use pthread to handle connections after accept() . If I hold (for example) F5 in Firefox after few second my server crashes when calling send(). No error output, no return code, just crash

---

