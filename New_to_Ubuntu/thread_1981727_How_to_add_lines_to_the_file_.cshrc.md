---
title: "How to add lines to the file .cshrc"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Ashotti on 2012-05-17
I need to add a line (to creat an alias) to the file .cshrc : how can I do this?

As far as I understood I should do this from the C shell, but I am using a bash shell.

Because I always use the bash shell, does it make sense to modify also the file .bashrc?

I am sorry if the question sounds confusing (or a bit stupid), but I am not an expert with Ubuntu.

Thanks a lot!

---

### Post by codemaniac on 2012-05-17
Add your alias into the .cshrc file , something like below.
```
alias grep='grep --color=auto'
```

---

### Post by Ashotti on 2012-05-17
How can I open the file to insert the line?

Thanks

---

### Post by Lisiano on 2012-05-17
You can use gedit to open in a graphical editor or use Nano or Vi to edit in a terminal
```
gedit .cshrc
```

---

### Post by Ashotti on 2012-05-17
Done!

Thanks!

---

### Post by codemaniac on 2012-05-18
Thats a good news .Well done . : )

---

