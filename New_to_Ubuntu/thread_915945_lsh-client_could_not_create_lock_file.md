---
title: "lsh-client could not create lock file"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by integralrootcosxdx on 2008-09-10
I've Hardy Heron installed and I want to use ssh2 client. i installed lsh-client and lsh-utils using synaptic pacgake manager. 

and tried using lsh client

hemant@T6017D:~$ lsh -l hkulkarni3 yamsrv1.ece.gatech.edu
Could not create lock file `/home/hemant/.lsh/yarrow-seed-file.lock' (errno = 2): No such file or directory
Could not lock seed-file `/home/hemant/.lsh/yarrow-seed-file'
lsh: No randomness generator available.


Can any tell me what is this error and how to resolve this problem?

-integralrootcosxdx

---

### Post by Pro-reason on 2008-09-11
I've just installed lsh-client myself to help you, and I do indeed get exactly the same error.  It seems to be broken.

Let's look at the error message.  It is complaining that it can't edit “~/.lsh/yarrow-seed-file”.  This is because “~/.lsh” does not exist.

I can create it with “mkdir ~/.lsh”, and then try again.  It now tells me:
```

No seed file. Please create one by running
lsh-make-seed -o "~/.lsh/yarrow-seed-file".
lsh: No randomness generator available.

```

OK, I run that command and it creates a seed file.

I try again.

It tells me:
```

lsh: Failed to open `~/.lsh/host-acls' for reading (errno = 2): No such file or directory
lsh: Server's hostkey is not trusted. Disconnecting.
lsh: Protocol error: Bad server host key

```

OK, so I try creating that file with “touch ~/.lsh/host-acls”.  I try again.

It tell me:
```

lsh: Server's hostkey is not trusted. Disconnecting.
lsh: Protocol error: Bad server host key

```

I tried putting in the names for my own server, and got the same result.

I don't know where to go from here.  Anyone?

---

### Post by goobersmootcher on 2009-01-03
Sorry for the necro but I ran into the same problems and found this page.  After more google searches I found my answer.  I wanted to post a link to a page that helped me solve the problem:

[http://www.lysator.liu.se/~nisse/lsh/lsh.html](http://www.lysator.liu.se/~nisse/lsh/lsh.html)

Search for the word "sloppy" (without quotes) in that page and it will tell you about using --sloppy-host-authentication to be able to accept the key from the host you're trying to connect to.  I did that and now all is fine in my lsh world.

---

### Post by Ruyuk on 2009-01-03
I don't think you should post other links to to other websites on here. Just letting you know.

---

### Post by goobersmootcher on 2009-01-03
Hmm, really?  I didn't see anything about that in the code of conduct (only about posting obscene links and such).  I'd think the site would be open to sharing knowledge and thus links even if to other sites, but if that's officially a "don't do that" type of thing then I guess it's good to know.

---

