---
title: "force wget to use a different file name for what it downloads?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-29
Hi
Thank you for reading my post
Is it possible to force wget to use a custom file name when it download a file?

for example to download the [www.aaa.com/file55.zip](www.aaa.com/file55.zip) to /home/legolas/f55.zip ?

Thanks.

---

### Post by aheckler on 2008-04-29
You could just do something like this in terminal, downloading and renaming it in one command:

```
wget http://www.aaa.com/file55.zip && mv file55.zip f55.zip
```

---

