---
title: "Variables in sh script"
date: 2009-07-22
forum: Programming Talk
---

### Post by bboston7 on 2009-07-22
I am currently writing an sh script to allow people to easily create a streaming queue for vlc, something that you can't do through the gui.  However, it appears that some of my user input variables don't work.  Here is the final command.

```
vlc -vvv $files --sout '#standard{access=http,mux=ogg,dst=$address:$port}'
```

The $files variable works great, however the $address and $port variables don't change over to the user inputed data.

Can someone help me understand why this is and what I can do to fix it?

Thankyou.

---

### Post by unutbu on 2009-07-22
Single quotes prevent variable expansion. Try double-quotes.
```

vlc -vvv $files --sout [COLOR="Red"]"[/COLOR]#standard{access=http,mux=ogg,dst=$address:$port}[COLOR="Red"]"[/COLOR]
```

---

### Post by bboston7 on 2009-07-22
That worked!

Thank you very much.

---

