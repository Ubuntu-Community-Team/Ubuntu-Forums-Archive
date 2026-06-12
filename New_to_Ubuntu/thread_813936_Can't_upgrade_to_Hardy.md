---
title: "Can't upgrade to Hardy"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-31
I get the error message: could not calculate the upgrade. Doesn't make any difference if I use terminal or the update manager.

---

### Post by shifty_powers on 2008-05-31
what version of ubuntu are you currently using?

and do you have a separate /home partition?

---

### Post by captgadget on 2008-05-31
I'm running 7.1 and yes I do have a serpate home partion set up as per psychocats.

---

### Post by bwhite82 on 2008-05-31
Are you able to 'upgrade' rather than 'dist-upgrade'?

---

### Post by sayakb on 2008-05-31
Since you do have a /home, go for a clean install rather than upgrading. Chances of successful upgrades are less, so it's better to have a clean install instead.

---

### Post by shifty_powers on 2008-05-31
well, not come across that particular problem before, but there is a reason why psychocats recommends a separate home partition.

what you can do, is just do a clean install of 8.04 from the live-cd, but use the manual partitioning option. when you do, format and mount the other partitions but DON'T format the home parttiion.

that way you will have a clean install of 8.04 but will also keep all of your personal data.

also use this beofre installation

[http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync](http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync)

to generate a list of all installed software and reintsall it on 8.04 ;)

---

### Post by captgadget on 2008-05-31
shifty_powers, I'll do the clean install. When I click on the link you provided, copy an paste in terminal: dpkg --get-selections > installed-software, nothing shows in terminal. Is that correct or do you know?

Thanks

---

### Post by shifty_powers on 2008-05-31
that's fine.

if you read the link, it will output a list of all you installed packages into a file in your home directory, which you won't format.

so, when you do the cleaninstall, the file will still bbe there and you can run:

```
dpkg --set-selections < installed-software
```

;)

---

### Post by captgadget on 2008-05-31
Thanks - I did find it in the home folder. Will get it started here shortly.

---

### Post by shifty_powers on 2008-05-31
heh good luck ;)

as previously stated, a clean install is generally favoured over upgrade's ;)

just don't fomrat your home partition ;)

---

### Post by captgadget on 2008-05-31
OK, after the install I think I need to redirect Hardy to the partion containing the Home folder right?

---

