---
title: "embedding python into JavaScript"
date: 2010-02-02
forum: Programming Talk
---

### Post by skizofrenito on 2010-02-02
Hello all,

is there a way to embed python code into JavaScript? Or even to call a whole python script that you can loaed from a .py file in Javascript?

Thank you in advance

---

### Post by myrtle1908 on 2010-02-02
Never used it but ...

"Skulpt is an entirely in-browser implementation of Python."

[http://www.skulpt.org/](http://www.skulpt.org/)

---

### Post by era86 on 2010-02-03
> **skizofrenito said:**
> Hello all,

is there a way to embed python code into JavaScript? Or even to call a whole python script that you can loaed from a .py file in Javascript?

Thank you in advance

Are you saying you want to run a Python script from Javascript on the client side?  I guess I'm speculating the context, but I would make a request to the server, run the code, then fetch the response...  that's just me though... :)  Goodluck

---

### Post by skizofrenito on 2010-02-03
@ myrtle1908: Yes this seems like what I wanted,  and helped me found and other sources like pyjamas and pypy! :D

@ era86: Yeah, you are totally right!! I think this is the best solution, but my question was made to find a way to avoid the client - server overhead.. Finally, I think that I will implement my application so that to communicate with the server running the python code, as you said, because it seems to be more simple! ;)

Thank you both!

---

