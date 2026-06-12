---
title: "cd Documents to cd Pictures"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by mferarri on 2012-09-13
Hi,

I'm a complete ubuntu noob and I would like to know how to change directories in the terminal from "Documents" folder to "Pictures" folder. I want to do this all in one command.

Thanks.

---

### Post by wojox on 2012-09-13
```
cd ~/Pictures/
```

---

### Post by mferarri on 2012-09-13
thanks it works, but what does the tilde mean?

---

### Post by cortman on 2012-09-13
The tilde stands for your home/username directory. Therefore, /~ means / (root directory) home/current_user_home_directory.

---

### Post by wojox on 2012-09-13
> **mferarri said:**
> thanks it works, but what does the tilde mean?

It is the value of $HOME.

```
wojox@wojox-testing:~$ $HOME
bash: /home/wojox: Is a directory
```

---

### Post by mferarri on 2012-09-13
Thanks guys for your very prompt responses! ):P

---

