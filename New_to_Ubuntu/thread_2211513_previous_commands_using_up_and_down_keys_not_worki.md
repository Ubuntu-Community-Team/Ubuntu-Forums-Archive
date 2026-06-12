---
title: "previous commands using up and down keys not working"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-03-16
I am using a CLI only server, and when I log in as a standard user, it puts me in $.  when I use the up and down keys, I get the "^[[A" or  "^[[B".  Why does it not work?

---

### Post by steeldriver on 2014-03-16
What kind of server? Probably you are not in a bash shell, remember that in Ubuntu (and some others) /bin/sh is a symlink to the dash shell

---

### Post by sniper8752 on 2014-03-16
I checked in my /etc/passwd file, and the shell was set to /bin/sh, so I changed it to /bin/bash and it works now.

---

