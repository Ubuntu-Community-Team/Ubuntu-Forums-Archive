---
title: "Shell/Bash Script"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by SWGraphics291 on 2013-03-22
I have made a shell script with a wait function. When i click run in terminal the terminal comes up for 0.1 ish seconds and then goes, can someone tell me how to fix this. It has'nt done it before?

---

### Post by papibe on 2013-03-22
Hi starwars29.

This keeps the terminal open for 5 seconds.
```
#!/bin/bash
sleep 5

```

Could you post your script?
Regards.

---

### Post by SWGraphics291 on 2013-03-22
```
echo My text
wait 1
echo My text
wait 5

```

---

### Post by SWGraphics291 on 2013-03-22
I just tried it with #!/bin/bash at the top as well.

---

### Post by papibe on 2013-03-22
Thanks.

'wait' it is not a pause command, use sleep instead:
```
#!/bin/bash
echo My text
sleep 1
echo My text
sleep 5
```

Let us know how it goes.

P.S.: 'wait' is used to wait for commands that have been sent to the background. It takes optional arguments, but not seconds (process ids actually).

---

### Post by SWGraphics291 on 2013-03-23
Oops I forgot it was sleep. I was thinking of Lua.

---

