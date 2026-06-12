---
title: "Can anyone help me with emacs + ange-ftp?"
date: 2010-11-08
forum: Programming Talk
---

### Post by melsen on 2010-11-08
Hey guys,

I've been trying desperately to get my emacs configured to use ange-ftp to an ftp server.

My shell-box is behind a firewall, and as such I have my .emacs file looking like this:

```

(require 'tramp)
(setq tramp-default-method "ftp")
(setq ange-ftp-ftp-program-name "pftp")

```

And then I've tried to set up my .netrc file as this to be able to use autocompletion on host name.. and this I can't even get to work either....

```

machine server-host-name port-no
        login <my-user>
        password <my-password

```

And I just can't get it work... it won't autocomplete the servername.. and if I try to open the ftp connection manually by

ctrl-x, ctrl-f and then typing:

/username:password@servername#port:~/

.. it just says it's not a valid tramp file...

What am I doing wrong... can anyone please explain how this is to be set up.. I've read pages up and down on wiki's on how to do this.. but to no prevail.

Does anyone perhaps have an example .emacs file they can supply me with where they know that ftp works in emacs.


Best regards,

- Allan
Denmark

---

