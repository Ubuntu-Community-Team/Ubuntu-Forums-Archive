---
title: "Loading shared objects from application directory"
date: 2010-07-04
forum: Programming Talk
---

### Post by _Dan on 2010-07-04
Hello,

I'm making a commercial software (a game), distributed as binary, so I want to include some shared objects with the binary, as is suggested by the GameDev.net Linux game dev tutorials. Specifically OpenAL and Alut but that is really irrelevant.

Now initially I tried just dropping the .so files in the same directory with the app binary but that didn't work, with the common "cannot find such and such.so" messages.

After much trial and error I've got it to work by setting the compiled binary rpath to "."

But since I found this out more or less by trial and error, I have to ask, is this the correct way of doing this? And will this work on all distros? (I hadn't heard of "rpath" until today)

---

### Post by pbrane on 2010-07-04
One alternative is
```

export LD_LIBRARY_PATH=$PWD

```
use a shell script to set this and then run the executable, several binary only games are done like that under GNU/Linux, This way it should run in any directory your users decide to install it in.

Have a look at this if you haven't already:
[URL="http://en.wikipedia.org/wiki/Rpath_%28linking%29"]http://en.wikipedia.org
/wiki/Rpath_%28linking%29[/URL]

---

