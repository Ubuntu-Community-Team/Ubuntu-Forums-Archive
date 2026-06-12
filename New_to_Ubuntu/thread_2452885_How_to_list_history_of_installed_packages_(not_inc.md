---
title: "How to list history of installed packages (not include already removed)"
date: 2020-10-30
forum: New to Ubuntu
---

### Post by wugubee on 2020-10-30
I see on other references how to list it, but its still include removed packages,

such as this: ```
zgrep 'install ' /var/log/dpkg.log* | sort | cut -f1,2,4 -d' '
```

What is the best way to list installed packages, **but exclude removed ones**, of all users or specific user, perhaps with dates?

---

### Post by ActionParsnip on 2020-10-30
```

dpkg -l | grep ^ii | awk {'print $2'} > /tmp/packagelist.txt

```
Gives currently installed packages. Is this what you mean?

---

### Post by wugubee on 2020-10-31
no, but thanks anyway, im looking for something that include installation date, by whom,

---

### Post by Frogs Hair on 2020-10-31
The following will show manually installed packages without date. ```
apt-mark showmanual
``` I don't know if the results for each user would be displayed separately if run in the user profile.

---

### Post by rbmorse on 2020-10-31
Actually, I can see that knowing when and who installed a given package could be useful.  May be appropriate for feature request via Launchpad.

---

### Post by deadflowr on 2020-10-31
You can try to parse through the apt history.logs like
```
egrep "(Install|Start-Date|Requested-By)" /var/log/apt/history.log && zgrep -E "(Install|Start-Date|Requested-By)" /var/log/apt/history.log.*.gz
```
It will list the date, then the user who requested it and then what was installed.
The only issue I found is cutting those dates and user entries where only upgrades came about.

Edit: I forgot this part
> but exclude removed ones
You'd probably need to include removed packages and somehow run diff or something to compare and then leave those packages not listed as removed out.
Someone with far better scripting skills then me could probably do this.

---

