---
title: "Problems with rc.local"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by protargol on 2008-10-15
I'm trying to run a process (firestarter) on startup and it needs root privileges so I tried putting it into the /etc/rc.local file, but it's not loading when I log in.  This is what the end of the file looks like.  I'm not sure what is wrong and why it's not running.  Any suggestions?  Thanks.

> 
...
#
# By default this script does nothing.

/usr/sbin/firestarter

exit 0


---

### Post by Rocket2DMn on 2008-10-15
rc.local doesn't execute commands when you *log in*, it executes them right at the end of the boot process itself (after other init scripts).  If you want a program to open when you login to the GUI, try System->Preferences->Sessions.

---

### Post by protargol on 2008-10-15
> **Rocket2DMn said:**
> If you want a program to open when you login to the GUI, try System->Preferences->Sessions.

Oh ok, I was afraid of that.  The problem is that this program requires root privileges so it complains when started via System->Preferences->Sessons

---

### Post by Rocket2DMn on 2008-10-15
I have not tried this approach, but it may be worth looking into: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by Nepherte on 2008-10-16
Why would you want to run firestarter on startup? The firewall is still active, whether you run firestarter or not.

---

