---
title: "A second bash to auto-run as non-root user"
date: 2009-03-06
forum: Programming Talk
---

### Post by flylehe on 2009-03-06
Hi,
These days I have to install a higher version of bash under my $HOME on my office server. I hope to make the new bash automatically run both when I ssh to my server and when I boot into my office computer which loads my $HOME on the server. So I added into ~/.bash_profile that:
```

SHELL='${HOME}/bin/my_new_bash/bin/bash'                                                                                                      
exec $SHELL

```

The new bash starts automatically if I ssh to the server, however, if I try to login into my office computer, I will not be able to with the following error:
> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.
I can login successfully if the line "exec $SHELL" in .bash_profile is commented. 

I was wondering if there is some way to make the new bash start automatically without the login error when login into my office computer?
Thanks!

---

### Post by &#956; . on 2009-03-06
To be honest, I don't know much about bash. I'm guessing that bash is just being weird; try this:

```

sleep 11
SHELL='${HOME}/bin/my_new_bash/bin/bash'
exec $SHELL

```

---

