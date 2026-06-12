---
title: "quick BASH(ish) question"
date: 2011-06-19
forum: Programming Talk
---

### Post by cmwhidmore on 2011-06-19
At my day job, I spend most of my time reading through long, tedious, timestamped, almost log-looking files, where the only part of real concern are the last few words of the line. I am trying to write a script that, given a text-only input file, it will get rid of that (largely) unimportant junk at the beginning, and leave behind an easier to read version in a seperate file.

I have most of the script figured out, but currently I am hung up on one thing- I cannot think of a command, or string of commands, that would either delete the leading (pattern-following) text on a line OR select just the last group of words (non-pattern-following) and move it to a new file.

Any ideas?

************************************************
EXAMPLE- (not actual usage)
Sample input
```
Jun 13 09:51:16 MXX0200GTP-HP-PC dbus-daemon: [system] Reloaded configuration
Jun 13 09:51:23 MXX0200GTP-HP-PC dbus-daemon: [system] Reloaded configuration
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: Successfully dropped root privileges.
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: avahi-daemon 0.6.27 starting up.
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: Successfully called chroot().
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: Successfully dropped remaining capabilities.
Jun 13 19:41:12 MXX0200GTP-HP-PC avahi-daemon[609]: No service file found in /etc/avahi/services.
```Desired result:: ```

dbus: Reloaded configuration
dbus: Reloaded configuration
avahi: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
avahi: Successfully dropped root privileges.
avahi: avahi-daemon 0.6.27 starting up.
avahi: Successfully called chroot().
avahi: Successfully dropped remaining capabilities.
avahi: No service file found in /etc/avahi/services.
```

---

### Post by luvshines on 2011-06-19
LOL !! Came up with this code, haven't even checked if it works on all possible inputs, but works for this one atleast

Assuming all the logs in a file /tmp/junk

```
sed -e "s/.*[[:blank:]]\(.*-daemon.*:.*$\)/\1/g" -e "s/-daemon.*:/:/g" -e "s/:[[:blank:]]*\[.*\]/:/g" /tmp/junk
```

Better wait for some bash guru to comment ;)

---

### Post by geirha on 2011-06-19
Removing the first four whitespace separated fields, and removing "-daemon*" from the fifth, should get you close to the desired output:
```

while read -r _ _ _ _ name message; do
    printf '%s: %s\n' "${name%-daemon*}" "$message"
done <inputfile >outputfile

```
See [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001) and [http://mywiki.wooledge.org/BashFAQ/100](http://mywiki.wooledge.org/BashFAQ/100)

---

