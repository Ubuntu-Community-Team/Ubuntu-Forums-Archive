---
title: "Bash general redirection question"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by Myoldmopar on 2013-06-18
I realize this is not Ubuntu specific question, but I like UbuntuForums the most and it's probably a simple question anyway.

I have a script that does a number of operations which all spew output.  I redirect these using the standard [FONT=courier new]"> /dev/null 2>&1"[/FONT] approach.  No big deal.  However, I'd like to clean up all this and redirect them without having to repeat this on every command.  I tried setting a variable: [FONT=courier new]TOBITBUCKET=' > /dev/nu ...'[/FONT], and append this to each command, but this didn't work--even in single quotes.  Bash was presumably trying to evaluate the variable and something was getting messed up.

Is there a great way to do what I am trying to do?  I still want the script itself to spew informative/progress messages, I just don't want any of the sub-processes to spew anything.  It would be great to have it as a verbose option that I could quickly turn on or off for debugging.

Thanks!

---

### Post by prodigy_ on 2013-06-18
```

#!/bin/bash
exec 1>/dev/null # redirect STDOUT
exec 2>/dev/null # redirect STDERR

# your code

```

---

### Post by Myoldmopar on 2013-06-18
That's great, I knew there were some tricks.  However, that seems to muffle everything, including my own information (which makes sense as it is just redirecting everything within this script).  Could be useful, but in my case, I'm looking to be able to report my own echoes.  As I mentioned, it would be really great to have a shorthand variable that I could append to each command which implies the redirection.  This would clean up all the /dev/null repeating, and allow me to turn it on and off for debugging/verbosity.  I think it's probably possible, I just don't have the right combination of quotes and ticks...

Thanks!

---

### Post by prodigy_ on 2013-06-18
> **Myoldmopar said:**
> I'm looking to be able to report my own echoes.
```
exec 1>$(tty)
echo "something"
```

---

### Post by SeijiSensei on 2013-06-18
> **Myoldmopar said:**
> TOBITBUCKET=' > /dev/nu ...'[/FONT], and append this to each command, but this didn't work--even in single quotes.

You don't want single quotes in this case as '$TOBITBUCKET' returns the identical string.  But you should be able to append your variable like this:

```
echo 'This is a test' $TOBITBUCKET
```

Does that not work for you?

---

