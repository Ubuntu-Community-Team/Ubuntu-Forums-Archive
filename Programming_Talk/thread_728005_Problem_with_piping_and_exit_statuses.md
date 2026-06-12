---
title: "Problem with piping and exit statuses"
date: 2008-03-18
forum: Programming Talk
---

### Post by altonbr on 2008-03-18
```
rm -r $HOME/.Trash | zenity --progress --title="Secure Delete" --pulsate --auto-kill --auto-close ; echo $?
```

will return 0.
```

rm -r $HOME/.Trash ; echo $?
```

will return 1.

Is there anyway I can test the exit status ($?) of my 'rm' command while piping to zenity?

---

