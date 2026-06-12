---
title: "Removed path environment variable"
date: 2019-10-03
forum: New to Ubuntu
---

### Post by joseph+baliks on 2019-10-03
I was following a tutorial while installing ubuntu via the terminal.. somewhere i issued a command to change the path, now i cant login as am taken back to the same screen. please help.

---

### Post by Impavidus on 2019-10-03
Do you have a link to that tutorial? There must be thousands of tutorials out there and not all of them are good.

Do you remember the file you modified or the command you used? Can you login on the console? Try ctrl+alt+F2, login using your username and password. Then have a look at your PATH:```
echo $PATH
```It should have kept a record of your last commands too:```
tail .bash_history
```You can logout with the logout or exit command. Use ctrl+alt+F7 to get back to the GUI.

Do you still have your live disk? That will give you a GUI. Although it must be possible to solve this problem with the command line interface only, if you feel up to it.

---

