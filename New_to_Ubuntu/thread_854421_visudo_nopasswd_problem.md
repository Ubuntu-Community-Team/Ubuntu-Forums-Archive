---
title: "visudo nopasswd problem"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by peter_babeone on 2008-07-09
hi everyone, 

I'm using ubuntu Hardy and have a problem with visudo. I added a NOPASSWORD new line at the end of the file, so that the default password of group admin doesn't override it. And it should be worked, but I don't know why it doesn't. I have searched but can't figure out the problem. Please help me !

> Here is the content of "sudo visudo".

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# by Duc
duc ALL=NOPASSWD: /usr/sbin/vpnc,/usr/sbin/vpnc-disconnect,/usr/bin/killall,/bin/kill

Any help will be appreciated ,

Peter

---

### Post by bodhi.zazen on 2008-07-09
just to be clear, what do you mean it does not work ? You get an error message when editing , you get an error message when running the applications, or you still are asked for a password ?

If the latter, move the line to here (position seems to matter) :```
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
**duc ALL=NOPASSWD: /usr/sbin/vpnc,/usr/sbin/vpnc-disconnect,/usr/bin/killall,/bin/kill**                      

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by peter_babeone on 2008-07-09
hi bodhi.zazen,

thanks lots for your answer. What I meant is, I'm asked for the password, when I use those programs. I changed the file like you showed me but it's still unsuccessful. I got

> duc@vn:~$ sudo vpnc
[sudo] password for duc:

Here are the content of the current configuration file for "sudo visudo" and some information about my  log-in user.

> # See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
**duc ALL=NOPASSWD: /usr/sbin/vpnc,/usr/sbin/vpnc-disconnect,/usr/bin/killall,/bin/kill**

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


> duc@vn:~$ groups
duc adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev


---

### Post by bodhi.zazen on 2008-07-09
Sorry, my mistake.

In sudoers the LAST line matched takes precedence, so move it back :)

Other then that I do not see a syntax error, do any of those command call or rely on others ?

---

### Post by spiderbatdad on 2008-07-09
please try this synatax:

```
duc 	ALL=(ALL) NOPASSWD: /usr/sbin/vpnc, /usr/sbin/vpnc-disconnect, /usr/bin/killall, /bin/kill

```

---

### Post by bodhi.zazen on 2008-07-09
> **spiderbatdad said:**
> please try this synatax:

```
duc     ALL=(ALL) NOPASSWD: /usr/sbin/vpnc, /usr/sbin/vpnc-disconnect, /usr/bin/killall, /bin/kill

```

Nice thought (bodhi keeps toes crossed).

On my system, I do not need the (ALL) or s p a c e s in the list of commands.

Also, if there is a syntax error, and you are using visudo like you should :lolflag: 

visudo checks for syntax errors :twisted:

---

### Post by peter_babeone on 2008-07-09
@spiderbatdad

thanks so much, it work like a charm with :popcorn:

> duc 	ALL=(ALL) NOPASSWD: /usr/sbin/vpnc, /usr/sbin/vpnc-disconnect, /usr/bin/killall, /bin/kill


@bodhi.zazen
> Other then that I do not see a syntax error, do any of those command call or rely on others ?

No, I just made some examples :guitar:

Thanks again & wish you all the best :lolflag:

Peter

---

