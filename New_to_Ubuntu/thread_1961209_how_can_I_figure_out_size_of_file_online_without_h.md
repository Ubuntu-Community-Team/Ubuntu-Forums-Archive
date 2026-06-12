---
title: "how can I figure out size of file online without having first downloaded it?"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-18
Hello,
We have limited bandwidth at our current location. How can we find out the size of www.somewebsite.com/foo.swf without having first downloaded it?

---

### Post by hanzj on 2012-04-18
i don't mind if it's a terminal/console command.

---

### Post by cortman on 2012-04-18
Would wget do it for you?

See 2nd comment on first response [here.]("http://stackoverflow.com/questions/6986085/get-file-size-of-a-file-to-wget-before-wget-ing-it")

---

### Post by hanzj on 2012-04-18
"2nd comment on first response". Do you mean
"wget [http://example.com](http://example.com) --spider --server-response -O - 2>&1 | sed -ne '/Content-Length/{s/.*: //;p}' "?

---

### Post by alphacrucis2 on 2012-04-18
One option is to start downloading the file and then the download window will show you the file size/ progress. If it looks too big just cancel the download.


Actually you don't even need to start the download. See attached FF screenshot

---

### Post by cortman on 2012-04-18
> **hanzj said:**
> "2nd comment on first response". Do you mean
"wget [http://example.com](http://example.com) --spider --server-response -O - 2>&1 | sed -ne '/Content-Length/{s/.*: //;p}' "?

Yeah.
I tested it. It works. I think it returns the file size in bytes, though.

---

### Post by hanzj on 2012-04-18
A simple command to run is 

```

curl -I http://somewebsite.com/foo.swf
```

Examine the Content-Length, which is given in bytes.

---

