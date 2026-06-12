---
title: "php scripts for torrentflux?"
date: 2008-01-25
forum: Programming Talk
---

### Post by njparton on 2008-01-25
I have torrentflux installed on my ubnutu box (headless NAS device) and it works well, but is pretty limited in some areas.

I'd like to start writing some scripts (php?) that perform certain actions such as automatically restarting torrent downloads after a reboot. I'll probably use cron to control these.

I've started some reading into php and I have a lot of experience in writing shell scripts (c shell, korn shell, bash etc) and using awk, but I have absolutely no idea where to start when it comes to applying php to torrentflux.  Google has been no real help either.

Can anyone here give me some pointers on how to start writing php scripts to control torrentflux? Or even if php is the correct route to take?

Thanks in advance.

---

### Post by njparton on 2008-01-27
No-one can help me here?

---

### Post by LaRoza on 2008-01-27
> **njparton said:**
> No-one can help me here?

Look into Python. PHP can be used on the desktop, but is usually used for server side programming.

See my wiki.

---

### Post by fox_cream on 2008-09-25
Incase anybody is still looking for the answer....


Patch torrentflux with "overhacks" patch located here [http://www.torrentflux.com/forum/ind....html#msg12359](http://www.torrentflux.com/forum/ind....html#msg12359)

Instead of 

'http://localhost/~torrentflux/index.php?resumeall=now' 

in the script, i needed to use

'http://192.168.1.100/torrentflux/index.php?resumeall=now' 

where 192.168.1.100 is the static IP i've assigned to my NAS. (note the drop of ~, although I'm not sure if it's important).  

Create a script containing

wget -o /dev/null -O /dev/null --background --quiet --wait=3 --retry-connrefused --ignore-length --bind-address=127.0.0.1 'http://192.168.1.100/torrentflux/index.php?resumeall=now' &>/dev/null

make it executable (chmod a+x /path/to/script), and then make a cron entry for it to start at reboot i.e.

crontab -e
@reboot /path/to/script.sh

I used info about cron that i found here
[http://www.cyberciti.biz/faq/how-do-...-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-...-or-unix-oses/)

Sorted.

---

