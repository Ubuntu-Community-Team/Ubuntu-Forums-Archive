---
title: "proxy for update manager"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by rajaram_s on 2008-05-24
Can anyone tell me how can I remove the proxy for my update manager? I removed the proxy settings in synaptic, and disabled the network proxy...

---

### Post by rajaram_s on 2008-05-24
I have also enabled the direct connection to internet in firefox

---

### Post by cwgatling on 2008-05-24
What does

```
echo $http_proxy 
```

return?

---

### Post by rajaram_s on 2008-05-24
returns nothing... just a blank line...

---

### Post by cwgatling on 2008-05-24
Weird. You could try

```
unset http_proxy
```

or maybe

```
export http_proxy=""
```

---

### Post by rajaram_s on 2008-05-24
Thank you it worked. Was probably coz, the updates it showed were from a proxy connection. It just showed the updates and I actually dint update. Now that I gave a check again, it works proper.....

---

### Post by cwgatling on 2008-05-24
Cool, good stuff :)

---

