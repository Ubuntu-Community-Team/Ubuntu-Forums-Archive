---
title: "Nginx repository for Ubuntu/Debian"
date: 2009-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by CP1256 on 2009-06-08
**Edit**: I'm stopping with this.

[Nginx]("http://nginx.net/") is a lightweight server written by Igor Sysoev. Nginx is capable of running heavy websites with a lot less resources then Apache for example. Unfortunately nginx has frequent updates, making the package in the official repository age very quick. At this time of writing, the newest stable version of nginx is 0.7.59 while Debian Lenny provides 0.6.32 and Ubuntu Jaunty 0.6.35.
The packages have been compiled on Ubuntu and installed on both Ubuntu and Debian without a problem.

That's why I've set up a repository for the latest stable versions of nginx. Just add the following lines to '/etc/apt/sources.list' with your favorite text editor:

> deb [http://apt.avuc.nl](http://apt.avuc.nl) lenny stable
deb-src [http://apt.avuc.nl](http://apt.avuc.nl) lenny stable

And update your system with 'sudo aptitude update' or just 'aptitude update' as root. Now run 'sudo aptitude safe-upgrade' to upgrade nginx to the newest version. 

**Important:**
Install nginx from the official repositories first! Then update with my newer packages. The nginx executable from my packages is located somewhere else, so we need to make a symlink to the new location for '/etc/init.d/nginx' to work. Just do
> ln -s /usr/local/nginx/sbin/nginx /usr/sbin/nginx

And you're done! Restart nginx with '/etc/init.d/nginx' and if that doesn't work do 'killall nginx' as root. 

More information, like compile options, can be found [here]("http://apt.avuc.nl/all-versions/README-FIRST.txt").

Development and legacy version are now also available, just replace "stable" with "development" or "legacy" to get the corresponding packages.

---

### Post by Kyrra on 2009-06-21
Thanks for supplying your compile flags.  I have an x86-64 compiled system and your .deb packages only support i386.  I was able to get my own compiled using your flags.

---

### Post by CP1256 on 2009-06-22
I also have a 64 bit server now so I think I'm going to offer 64-bit packages soon. 

Glad I could help though!

---

### Post by denadai2 on 2009-07-20
i need the x84 version too ^^

thx :D

---

### Post by CP1256 on 2009-07-21
64Bit packages added, for all versions. You can now download 32 and 64bit packages.

---

### Post by aresnick on 2009-07-21
Everything seems to go swimmingly 'til I try to start nginx:

```

foo@bar:/usr/local/nginx/sbin$ sudo /etc/init.d/nginx start
Starting nginx: start-stop-daemon: Unable to start /usr/sbin/nginx: No such file or directory (No such file or directory)
nginx.

```

I installed nginx from the normal repo, added your repos to sources.list, ran apt-get update, then aptitude safe-upgrade.  The upgrade completed, and when I try to start nginx, I get the above error.

Running Jaunty on x86_64.

Any pointers would be appreciated.  Thanks!

-a.

---

### Post by CP1256 on 2009-07-22
> **aresnick said:**
> Everything seems to go swimmingly 'til I try to start nginx:

```

foo@bar:/usr/local/nginx/sbin$ sudo /etc/init.d/nginx start
Starting nginx: start-stop-daemon: Unable to start /usr/sbin/nginx: No such file or directory (No such file or directory)
nginx.

```

I installed nginx from the normal repo, added your repos to sources.list, ran apt-get update, then aptitude safe-upgrade.  The upgrade completed, and when I try to start nginx, I get the above error.

Running Jaunty on x86_64.

Any pointers would be appreciated.  Thanks!

-a.
The new nginx executable is located somewhere else, just run 'ln -s /usr/local/nginx/sbin/nginx /usr/sbin/nginx' and you'll be able to start it again.

I would also place this in '/etc/init.d/nginx', so you can upgrade to newer versions of nginx without downtime.

```
  upgrade)
        echo -n "Upgrading $DESC: "

        # See [http://wiki.nginx.org/NginxCommandLine](http://wiki.nginx.org/NginxCommandLine) for details
        # First, start a new process running the new binary
        kill -USR2 `cat /var/run/nginx.pid`
        sleep 1

        # Next, kill the old worker processes
        kill -WINCH `cat /var/run/nginx.pid.oldbin`
        sleep 1

        # Next, kill the old master processe
        kill -QUIT `cat /var/run/nginx.pid.oldbin`

        echo "$NAME."
        ;;
```

---

### Post by aresnick on 2009-07-22
Sorry, forgot to mention that I also made the symlink--I actually can verify that the nginx executable is there, as is nginx.old.  Strangely, even when I try to execute nginx from its directory, I get a "No such file or directory" error.

---

### Post by CP1256 on 2009-07-22
> **aresnick said:**
> Sorry, forgot to mention that I also made the symlink--I actually can verify that the nginx executable is there, as is nginx.old.  Strangely, even when I try to execute nginx from its directory, I get a "No such file or directory" error.

That is strange, try to remove nginx, then install the version from the repos, and see if it works. Then try again, maybe that will solve it. Currently I'm using version 0.8.6, which version are you using?

---

### Post by aresnick on 2009-07-22
No joy.  I'm currently using nginx 0.6.35.  To make sure we're on the same page about what I did:
[LIST]
[*] install nginx from official repos (yours aren't even in sources.list, yet)
[*] add your repos to sources.list
[*] sudo apt-get update && sudo apt-get upgrade
[*] sudo ln -s /usr/local/nginx/sbin/nginx /usr/sbin/nginx 
[*] sudo /etc/init.d/nginx restart
[/LIST]

and then things fall apart, as detailed above.  Any idea how to investigate the weird file's-here-but-i-can't-see-it syndrome?

Thanks!

-a.

---

### Post by CP1256 on 2009-07-23
> **aresnick said:**
> No joy.  I'm currently using nginx 0.6.35.  To make sure we're on the same page about what I did:
[LIST]
[*] install nginx from official repos (yours aren't even in sources.list, yet)
[*] add your repos to sources.list
[*] sudo apt-get update && sudo apt-get upgrade
[*] sudo ln -s /usr/local/nginx/sbin/nginx /usr/sbin/nginx 
[*] sudo /etc/init.d/nginx restart
[/LIST]

and then things fall apart, as detailed above.  Any idea how to investigate the weird file's-here-but-i-can't-see-it syndrome?

Thanks!

-a.

That is very strange, I've tested all packages (both 32 and 64bit) and for me they all seem to work fine. Are you sure the file permissions are correct, mine is -rwxr-xr-x. Did you try to launch it directly, doing '/usr/local/nginx/sbin/nginx'?

And where is the nginx executable located now?

---

### Post by aresnick on 2009-07-29
```

sprout@thesprouts:~$ sudo /etc/init.d/nginx restart
Restarting nginx: start-stop-daemon: Unable to start /usr/sbin/nginx: No such file or directory (No such file or directory)
nginx.
sprout@thesprouts:~$ ls -l /usr/local/nginx/sbin/nginx
-rwxr-xr-x 1 root root 652972 2009-07-21 15:08 /usr/local/nginx/sbin/nginx
sprout@thesprouts:~$ /usr/local/nginx/sbin/nginx
-bash: /usr/local/nginx/sbin/nginx: No such file or directory

```

So that's the crux of the issue; it's pretty baffling to me, since ls clearly says it is there =)

---

### Post by CP1256 on 2009-08-05
> **aresnick said:**
> ```

sprout@thesprouts:~$ sudo /etc/init.d/nginx restart
Restarting nginx: start-stop-daemon: Unable to start /usr/sbin/nginx: No such file or directory (No such file or directory)
nginx.
sprout@thesprouts:~$ ls -l /usr/local/nginx/sbin/nginx
-rwxr-xr-x 1 root root 652972 2009-07-21 15:08 /usr/local/nginx/sbin/nginx
sprout@thesprouts:~$ /usr/local/nginx/sbin/nginx
-bash: /usr/local/nginx/sbin/nginx: No such file or directory

```

So that's the crux of the issue; it's pretty baffling to me, since ls clearly says it is there =)
I'm very sorry for the late reply, put the following in '/etc/init.d/nginx' and it should restart properly and without downtime.

```
  upgrade)
        echo -n "Upgrading $DESC: "

        # See [http://wiki.nginx.org/NginxCommandLine](http://wiki.nginx.org/NginxCommandLine) for details
        # First, start a new process running the new binary
        kill -USR2 `cat /var/run/nginx.pid`
        sleep 1

        # Next, kill the old worker processes
        kill -WINCH `cat /var/run/nginx.pid.oldbin`
        sleep 1

        # Next, kill the old master processe
        kill -QUIT `cat /var/run/nginx.pid.oldbin`

        echo "$NAME."
        ;;
```

---

### Post by emyller on 2009-08-26
Same problem here. The file is **really** there, but the thing doesn't work.

---

