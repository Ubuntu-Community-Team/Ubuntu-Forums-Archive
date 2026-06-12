---
title: "scripting help -notify when done"
date: 2020-05-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-05-20
i have a script #!/bin/bash clamscan -r /. i want to use notify send or similar command to notify me script is finish and completely run. what should i add to my script/tks

---

### Post by ActionParsnip on 2020-05-20
Run:
```

sudo apt-get install notify-osd

```

You can now run:
```

notify-send Test "Hello World"

```

HTH

---

### Post by rburkartjo on 2020-05-20
found this
[https://www.ostechnix.com/get-notification-terminal-task-done/](https://www.ostechnix.com/get-notification-terminal-task-done/)

---

