---
title: "[SOLVED] Displaying shell script lines when executing"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by NormR2 on 2008-06-02
Is there a flag/switch that you can turn on in a shell script that will display the lines of the script as they are being executing?
When executing a script, I'd like to see the line/command that is being executed on stdout, followed by the output from that command.

In other words how do you debug a script?

---

### Post by hyper_ch on 2008-06-02
never tried it but how about:
```

sh -v scrip.sh

```

-v is normally verbose mode... not sure if that works but might be worth a try.

---

### Post by sisco311 on 2008-06-02
You also can set the verbose mode in the script:
> #!/bin/bash -v
...
commands....

---

### Post by hyper_ch on 2008-06-02
I knew there must be a way ;)

---

### Post by NormR2 on 2008-06-02
thanks to both of you.

Also the -x option shows me the line after variable substitution has taken place!

---

