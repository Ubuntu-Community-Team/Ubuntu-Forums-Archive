---
title: "Installing gitosis for managing git repositories"
date: 2010-02-13
forum: Programming Talk
---

### Post by orengolan on 2010-02-13
I follow this post to install gitosis:
[http://www.markrichman.com/2008/06/16/installing-git-and-gitosis-on-ubuntu/comment-page-1/#comment-555](http://www.markrichman.com/2008/06/16/installing-git-and-gitosis-on-ubuntu/comment-page-1/#comment-555)

when I type this:
sudo -H -u git gitosis-init < /tmp/id_rsa.pub
I get this error:
env: -H: No such file or directory


any clues? (ubuntu 9.10)

---

### Post by orengolan on 2010-02-14
I found my issue.
I had alias in my .bashrc: alias sudo='sudo env PATH=$PATH'

after removing it, it's working.

Thanks!

---

