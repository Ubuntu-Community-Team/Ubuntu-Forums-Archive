---
title: "Git over http not working"
date: 2007-07-11
forum: Programming Talk
---

### Post by chrono325 on 2007-07-11
I have been driving myself crazy trying to get [git]("http://git.or.cz/") working over http using Apache. I am using feisty but have recently upgraded to gutsy's git versions using Prevu.

Anyway, neither pushing to a git repository or pulling from one works. The server I am using works just fine for other things, including hosting Mediawiki and gitweb. The native Git server works fine, but I am often behind a firewall and need http(s) support.

Anyway, I followed the instructions given [here]("http://www.kernel.org/pub/software/scm/git/docs/howto/setup-git-server-over-http.txt") and litmus successfully passed all the tests and visiting the address [https://git.haxney.org/git/emacs.git/](https://git.haxney.org/git/emacs.git/) for example worked fine.

I have run up "git-update-server-info" and looking at the "info/refs" and "objects/info/packs" files I can see that there is info there, but I still get the following:
```

$ git clone https://git.haxney.org/git/emacs.git/
Initialized empty Git repository in /tmp/gitty/emacs/.git/
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?

```

Trying to push to an empty repository gives the following:

```

$ git push upload master
Error: no DAV locking support on remote repo https://git.haxney.org/git/test-repo.git/
error: failed to push to 'https://git.haxney.org/git/test-repo.git/'

```

Any thoughts?

---

### Post by antono on 2008-01-11
> 
```

$ git push upload master
Error: no DAV locking support on remote repo https://git.haxney.org/git/test-repo.git/
error: failed to push to 'https://git.haxney.org/git/test-repo.git/'

```

Any thoughts?

Yep. You should enable DAV locking. 
Change permissions on /var/run/apache2 

chown www-data:www-data /var/run/apache2/

koz apache cant write Dav lock info there

cat  /etc/apache2/mods-enabled/dav_fs.conf
DAVLockDB /var/lock/apache2/DAVLock

---

### Post by antono on 2008-01-11
> **chrono325 said:**
> 
```

$ git push upload master
Error: no DAV locking support on remote repo https://git.haxney.org/git/test-repo.git/
error: failed to push to 'https://git.haxney.org/git/test-repo.git/'

```

Any thoughts?

And... Show me please your ~/.netrc :) 
I think you have to enable your host username and pass there if you use authenticated http connection.

---

