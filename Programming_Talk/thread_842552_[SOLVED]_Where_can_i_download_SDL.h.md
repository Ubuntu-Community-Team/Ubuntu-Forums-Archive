---
title: "[SOLVED] Where can i download SDL.h"
date: 2008-06-27
forum: Programming Talk
---

### Post by rraj.be on 2008-06-27
Where can i download SDL library.

i.e  SDL.h

---

### Post by LaRoza on 2008-06-27
```

sudo aptitude install libsdl1.2-dev 

```

---

### Post by rraj.be on 2008-06-27
I have already installed the above but i need SDl.h file to include it in my program which one of my friend is creating.

I said about SDL and he wish to use it.But we dont now where to get it for windows.

EDIT: For your kind information he is coding in windows using Borland c++ compiler.

---

### Post by LaRoza on 2008-06-27
> **rraj.be said:**
> I have already installed the above but i need SDl.h file to include it in my program which one of my friend is creating.

I said about SDL and he wish to use it.But we dont now where to get it for windows.

[http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)

---

### Post by rraj.be on 2008-06-27
What i got in the above is a DLL file.How can i use it as sdl.h file.

---

### Post by geirha on 2008-06-28
You've probably only gotten the runtime library then. Get the development library package. It should contain both the DLL and the SDL.h header file

---

### Post by rraj.be on 2008-06-28
could you please get me the link.
So sorry, i searched for it but i cant get that.

Please don't mistake me.

---

### Post by Sukarn on 2008-06-28
Go to [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php) and scroll down to "Development Libraries". Get the one needed by you (or your friend).

---

### Post by rraj.be on 2008-06-28
Got that.

Thank you.

---

### Post by kesten on 2011-10-14
> **LaRoza said:**
> ```

sudo aptitude install libsdl1.2-dev 

```

this should read 
sudo apt-get install libsdl1.2-dev
:)

---

