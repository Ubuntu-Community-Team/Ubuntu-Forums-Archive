---
title: "How to remove config"
date: 2019-02-28
forum: New to Ubuntu
---

### Post by Impavidus on 2019-02-28
I don't know Lima.

Some tools can only have one instance running at a time. They can create a lockfile when starting and remove it when exiting. When the lockfile already exists, they don't start but give an error message. When such a tool is improperly terminated, the lockfile may remain and has te be removed manually.

Try```
rm .local/share/lima/config.lock
```

---

