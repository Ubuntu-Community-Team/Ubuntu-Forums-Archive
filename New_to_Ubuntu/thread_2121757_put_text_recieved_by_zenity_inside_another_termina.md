---
title: "put text recieved by zenity inside another terminal command for nautilus scripts"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-02
I am making a command that deletes text except the file extencion and the first set of numbers, up until now I have this ```

rename -v 's/[^0-9]*([0-9]+)[^0-9].*/$1.**mp4**/' *
```
I am looking for how to make a zenity command that shows and input box and replace the bolded extencion for the one inputed in the zenity box, I prefer to use YAD but I am willing to use whatever can make the trick

---

### Post by Froylan on 2013-03-03
bump

---

### Post by Froylan on 2013-03-03
forget it, I fixed it, here is what I did ```
don=$(zenity --entry --text "input text here" --entry-text "yes, here")
rename -v 's/[^0-9]*([0-9]+)[^0-9].*/'$(echo $don)'/' *


```

---

