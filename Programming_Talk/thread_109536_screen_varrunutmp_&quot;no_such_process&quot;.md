---
title: "screen: /var/run/utmp &quot;no such process&quot;"
date: 2005-12-28
forum: Programming Talk
---

### Post by rosslaird on 2005-12-28
I figured I'd post this here, since I have the best chance, in this forum, of finding command-line junkies.

When I use screen, either in an X terminal or a console, it works but I get this error:

Could not write /var/run/utmp: No such process.

I tried "touch /var/run/utmp" to no avail. Same error.

Hints, anyone? I tried googling this without success.

Thanks in advance,

Ross

---

### Post by Crazy Man on 2006-01-10
I'm having the same thing. However, it doesn't seem to affect my screen actitvities, it does affect the time it takes to reattach after a detattchment.

*bump*

---

### Post by ape on 2006-01-10
make sure that /usr/bin/screen is still owned root:utmp and that the permissions are rwxr_sr_x.

---

### Post by rosslaird on 2006-01-11
[QUOTE=ape]make sure that /usr/bin/screen is still owned root:utmp and that the permissions are rwxr_sr_x.[/QUOTE]

Yup, all is set as above on my system.
Still no dice.

---

### Post by Crazy Man on 2006-01-12
Make sure that your screen session is actually on a terminal physically on your server machine (the machine you're screening from). In my case, it was "on the fly", and it's what caused that problem for me.

It might not work for ya'll, but it's a theory...

---

### Post by ubuntujonez on 2006-06-10
Yeah I have the same deal. I don't really mind the error message. It can be surpressed by adding -ln to your screen command line. But creating new screens does the same thing. I'm sure there's probably a screen setting that could be added to ~/.screenrc.

For me the bother is that I'd like to see my screen entries with the 'who' command. The 'w' shows nothing ever either... probalby a worse problem. 

My /usr/bin/screen executable was sgid. As per the screen man page, I changed it to suid and then it complained about /var/run/screen needs to be 755 (it was 775). I changed that too, but same problem.

Woe.

-uj

---

### Post by pestilence4hr on 2006-11-16
I had this problem, and doing the following fixed it:

```

sudo -s
cat /dev/null > /var/run/utmp
reboot

```

I think /var/run/utmp was corrupted due to an improper shutdown (power failure).  Perhaps because I had screen running on the machine when the power went out...I don't know.

---

