---
title: "alias command"
date: 2011-03-03
forum: Programming Talk
---

### Post by jmg158 on 2011-03-03
okay, so I'm trying to essentially write a script that will allow me to play songs with a keystroke. I tried to test the waters tonight for the first time and I had some issues. I'll copy and paste.... first my script... and then an excerpt from the command prompt screen where it was run.



/* Here I will assign aliases to play these files */
alias w='aplay "Aquabats- The Fury of the Aquabats- 9.wav" &'
alias e='aplay "Aquabats- The Fury of the Aquabats- 8.wav" &'
alias r='aplay "Aquabats- The Fury of the Aquabats- 7.wav" &'
alias t='aplay "Aquabats- The Fury of the Aquabats- 6.wav" &'
alias y='aplay "Aquabats- The Fury of the Aquabats- 5.wav" &'
alias u='aplay "Aquabats- The Fury of the Aquabats- 4.wav" &'
alias i='aplay "Aquabats- The Fury of the Aquabats- 3.wav" &'
alias o='aplay "Aquabats- The Fury of the Aquabats- 2.wav" &'
alias p='aplay "Aquabats- The Fury of the Aquabats- 1.wav" &'
alias q='aplay try.wav &'
alias 
q
-----------------------------------------------------------------

john@john-RC684AA-ABA-SR2002X-NA640:/media/Expansion Drive/John's Music/The Aquabats!/Fury of the Aquabats$ ls
Aquabats- The Fury of the Aquabats- 10.wav
Aquabats- The Fury of the Aquabats- 1.wav
Aquabats- The Fury of the Aquabats- 2.wav
Aquabats- The Fury of the Aquabats- 3.wav
Aquabats- The Fury of the Aquabats- 4.wav
Aquabats- The Fury of the Aquabats- 5.wav
Aquabats- The Fury of the Aquabats- 6.wav
Aquabats- The Fury of the Aquabats- 7.wav
Aquabats- The Fury of the Aquabats- 8.wav
Aquabats- The Fury of the Aquabats- 9.wav
Aquabats-The Fury of the Aquabats- L.wav
Aquabats-The Fury of the Aquabats- S.wav
Aquabats- The Fury of the Aquabats-.wav
sampler.exe
try.wav
john@john-RC684AA-ABA-SR2002X-NA640:/media/Expansion Drive/John's Music/The Aquabats!/Fury of the Aquabats$ bash sampler.exe
sampler.exe: line 1: /bin: is a directory
alias e='aplay "Aquabats- The Fury of the Aquabats- 8.wav" &'
alias i='aplay "Aquabats- The Fury of the Aquabats- 3.wav" &'
alias o='aplay "Aquabats- The Fury of the Aquabats- 2.wav" &'
alias p='aplay "Aquabats- The Fury of the Aquabats- 1.wav" &'
alias q='aplay try.wav &'
alias r='aplay "Aquabats- The Fury of the Aquabats- 7.wav" &'
alias t='aplay "Aquabats- The Fury of the Aquabats- 6.wav" &'
alias u='aplay "Aquabats- The Fury of the Aquabats- 4.wav" &'
alias w='aplay "Aquabats- The Fury of the Aquabats- 9.wav" &'
alias y='aplay "Aquabats- The Fury of the Aquabats- 5.wav" &'
sampler.exe: line 13: q: command not found


am I overlooking something completely obvious in not being sure why this isn't found? I've defined the alias... i've even echoed it to prove that it has saved the command correctly... 

what am I missing?

---

### Post by Vox754 on 2011-03-04
> **jmg158 said:**
> okay, so I'm trying to essentially write a script that will allow me to play songs with a keystroke. I tried to test the waters tonight for the first time and I had some issues. I'll copy and paste.... first my script... and then an excerpt from the command prompt screen where it was run.

...

john@john-RC684AA-ABA-SR2002X-NA640:/media/Expansion Drive/John's Music/The Aquabats!/Fury of the Aquabats$ bash sampler.exe
**sampler.exe: line 1: /bin: is a directory**
alias e='aplay "Aquabats- The Fury of the Aquabats- 8.wav" &'
alias i='aplay "Aquabats- The Fury of the Aquabats- 3.wav" &'
...


It seems to me that your script actually starts in the first line with this:
```

/* Here I will assign aliases to play these files */

```

This, of course, causes bash to expand "/*" to a list of files that start with "/" and are followed by any number of characters (*):
```

/bin
/boot
/cdrom
/dev
... etcetera.

```

This is crazy, because this expansion does not result in any valid command and it creates an error.

I suggest you start the script with:
```

#!/bin/bash

# Investigate the meaning of "shebang" to understand the first line
# The hash or pound is the comment character in many scripting languages

# Here I will assign aliases to play these files
alias w='aplay "Aquabats- The Fury of the Aquabats- 9.wav" &'

```

Also, giving the extension ".exe" is just plain ugly. In Linux, the extension is just part of the name of the file, it doesn't matter. However, it is tradition that executables don't have extension, but if you want an extension for your bash script, you may as well use ".sh", so "sampler.sh" it is.

---

### Post by jmg158 on 2011-03-04
alright, what you say definitely makes sense to me. Guess Googling isn't the best way to find 100% verified information on linux commenting. 

Who knew the internet had bad data on it?

funny that you mention the first line, I had it included initially but took it out for some reason I can't recall. Either way, I would really understand if every command failed after the first line, however, I'm now perplexed by some commands failed "q" and some commands "alias" worked fine. 

whatever. when I get home i'll get to try it and will hopefully have learned something.

---

### Post by m_duck on 2011-03-04
You don't need to use a script for alias definitions. You can shove them in ~/.bashrc (or another file sourced from ~/.bashrc) and then log out/in or source ~/.bashrc.

You can see which aliases are currently defined by running ***alias*** in the terminal.

---

### Post by jmg158 on 2011-03-04
well, haha this is embarassing, but i'm using the script because this is part of making a bigger program I'm writing. I guess its embarassing because of how early I ran into problems haha.

---

### Post by Kirboosy on 2011-03-04
> **m_duck said:**
> You don't need to use a script for alias definitions. You can shove them in ~/.bashrc (or another file sourced from ~/.bashrc) and then log out/in or source ~/.bashrc.
 
You can see which aliases are currently defined by running ***alias*** in the terminal.
 
+1 Its much easier this way. :)

---

### Post by Vox754 on 2011-03-04
> **jmg158 said:**
> well, haha this is embarassing, but i'm using the script because this is part of making a bigger program I'm writing. I guess its embarassing because of how early I ran into problems haha.

By the way, I had forgotten about this, but in general, aliases are a very bad idea. It's a rather primitive way of saving some typing time.

Aliases should be used sparingly, such as shortening "ls -lhF" to "ll".

But for more complex uses, functions are the way to go.

[http://mywiki.wooledge.org/BashFAQ/080](http://mywiki.wooledge.org/BashFAQ/080)

---

