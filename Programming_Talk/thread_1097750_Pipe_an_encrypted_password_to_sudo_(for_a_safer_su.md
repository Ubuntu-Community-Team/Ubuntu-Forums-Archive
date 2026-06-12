---
title: "Pipe an encrypted password to sudo (for a safer sudo -S)"
date: 2009-03-16
forum: Programming Talk
---

### Post by mlambie on 2009-03-16
Hi everyone,

I have an Applescript I use to manage a few dozen Ubuntu servers. It currently prompts for my sudo password in a dialog box (on the Mac) and then opens a Terminal tab to each server listed in an array. I then execute:

```
echo myPassWordZ0r | sudo -S clear && sudo aptitude ...
```

This means that for split second my password is visible in the terminal, and I presume ps would show it too. I'd prefer it capture the password via the dialog box on the Mac, encrypt it locally and send that encrypted password to sudo instead, like this:

```
echo 8ff2d30cff8abcf875a62338a2158567 | sudo -<X> clear && sudo aptitude ...
```

Does anyone know if sudo can be coerced into accepting an already-encrypted password via STDIN instead of just plain text, or will I need to roll my own sudo (which I'm really not wanting to do).

Alternatively, does anyone have any better ideas (other than adding the commands I want to run to sudoers in such a way that I no longer need a password)?

Thanks,

Matt

---

### Post by geirha on 2009-03-16
What's wrong with adding the command to sudoers? Anyway, you could set up ssh host based authentication, and log in directly as root with no password ... [http://www.ssh.com/support/documentation/online/ssh/adminguide/43/Host-Based_User_Authentication.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/43/Host-Based_User_Authentication.html)

---

### Post by imdano on 2009-03-16
The newest version of sudo has an option that may be of interest:
> -A

    Normally, if sudo requires a password, it will read it from the current terminal. If the -A (askpass) option is specified, a helper program is executed to read the user's password and output the password to the standard output. If the SUDO_ASKPASS environment variable is set, it specifies the path to the helper program. Otherwise, the value specified by the askpass option in sudoers(5) is used.


edit: Actually this may not be very helpful, because you're running the sudo command multiple times.  Your best bet is probably host-based authentication, though you could look into using [expect](http://en.wikipedia.org/wiki/Expect) instead of reading from stdin.

---

