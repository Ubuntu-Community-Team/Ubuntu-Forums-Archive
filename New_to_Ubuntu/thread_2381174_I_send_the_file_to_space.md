---
title: "I send the file to space"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-27
For mistake I execute this command:
```

mv file.txt user@1985.168.1.52

```

Where can I find the file "file.txt"?
Thanks

---

### Post by vasa1 on 2017-12-27
You've renamed file.txt. It doesn't exist under that name any more. See *man mv*.

---

### Post by Impavidus on 2017-12-28
It should have renamed the file to user@1985.168.1.52.

That's a strange name. Maybe you wanted to send the file to a different computer with that IP address? In that case, use rsync or scp. mv can't operate over a network.

---

