---
title: "scripting help in xubuntu 14.04"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-10-12
having problems when using notify-send or gxmessage in script. terminal stays open after running
#!/bin/bash    notify-send  (gxmessage) "hi"
the above is just an example. i just want the terminal to close and not stay open./tks

---

### Post by Lars Noodén on 2015-10-12
The script's parent process's id (that would be the shell in the terminal) is identified in the variable $PPID.  If you kill that at the end of your script, it will close the shell that ran the script and then that will close the terminal.  

```

#!/bin/sh
. . .
kill -HUP ${PPID}

```

That works in something launched manually from the terminal.  However, there might be a way that can get you in trouble if you launch it in some other way, I would guess.  But I am not sure about the drawbacks.

---

### Post by rburkartjo on 2015-10-12
lars that did the trick/tks

---

