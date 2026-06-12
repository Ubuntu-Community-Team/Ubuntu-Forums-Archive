---
title: "Ubuntu Proxy Settings Question Firefox Browser"
date: 2023-10-22
forum: New to Ubuntu
---

### Post by bhubunt on 2023-10-22
Hi there,
I have a question about proxy settings for my Firefox browser which I am using on an Ubuntu 22.04 OS.

I just checked the general settings of the browser and under network settings, configure how Firefox connects to the internet, I noticed the entry "Use system proxy settings" was checked off. 

I don't understand why that's the case. Isn't "no proxy" the default setting? I did not click on "Use system proxy settings."

Are there any bash commands you can suggest to check why system proxy settings is turned on?

Thanks.

---

### Post by ActionParsnip on 2023-10-23
Try:
```

env | grep -i proxy

```

---

