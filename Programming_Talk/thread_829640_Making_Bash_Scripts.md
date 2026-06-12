---
title: "Making Bash Scripts"
date: 2008-06-15
forum: Programming Talk
---

### Post by MechWarrior001 on 2008-06-15
Is there a way to make a bash script disable Compiz Effects when I run a certain program & enable it when I exit that program?

For example, Tremulous. I have problems when Compiz is on. Anyway to make a script so when I run Tremulous, it automatically disables compiz  effects before & re-enables after I exit?

---

### Post by chewearn on 2008-06-15
To disable compiz, run:
```
metacity --replace &
```

To enable compiz, run:
```
compiz --replace &
```

Put these codes into a file in between the command to run the application you wanted.

.

---

### Post by bobbocanfly on 2008-06-15
```
metacity --replace &
tremulous && compiz --replace &
```

Should do the job. I cant test it (dont use Compiz) but if it works the way i think it should, compiz should only replace once tremulous is totally finished.

Place this in /usr/bin/ (~/bin is a better place if it is in your $PATH), chmod +x it and then edit your Tremulous menu item to run your new script.

---

