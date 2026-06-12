---
title: "[SOLVED] anyone familiar with libcurl?"
date: 2008-12-01
forum: Programming Talk
---

### Post by StOoZ on 2008-12-01
im trying to get the http status from some pages....
now , as I noticed, libcurl downloads the page / pdf / anything in the link before providing the status , this is not good , since , in case I want to test if a link which includes a 50MB pdf is still valid , then I need to wait too much time...
any idea how to tell it not to download stuff , and just return the status?

I looked at the API , didnt find anything useful , so I guess im missing something here.

thanks,

---

### Post by mmix on 2008-12-01
[http://stackoverflow.com/questions/290996/http-status-code-with-libcurl](http://stackoverflow.com/questions/290996/http-status-code-with-libcurl)

HTH

---

### Post by StOoZ on 2008-12-01
this exactly how I get the response , the problem is , as I said , it first downloads the page (direct link) , and then provide the response.. I dont want to have this behavior.

---

### Post by Cracauer on 2008-12-01
It doesn't have any http HEAD capabilities?

---

