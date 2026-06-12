---
title: "Problem with phpmyadmin"
date: 2021-12-11
forum: New to Ubuntu
---

### Post by gale85 on 2021-12-11
I tried to install phpmyadmin with the command ```
sudo apt update && sudo apt install phpmyadmin php-mbstring
```, first I got an error Could not get lock / var / lib / dpkg / lock then I typed the command in the terminal
```
[COLOR=#404040][FONT=monospace]sudo dpkg --configure -a[/FONT][/COLOR]
``` in terminal.
After that, the installation was somehow completed, but now when I type 127.0.0.1/phpmyadmin in chrome, it won't open that login window, but will show me the php code.
How do I handle this?

---

### Post by gale85 on 2021-12-14
I installed php and now I get a login window but I can't log in even though I know which username is set and my password, the window throws out 4 errors, with the second error being displayed twice
> 
Cannot log in to the MySQL server
mysqli::real_connect(): (HY000/2002): No such file or directory
Connection for controluser as defined in your configuration failed.


---

### Post by gale85 on 2022-01-13
I solved the problem. I deleted all the packages related to php, mysql, apache and phpmydmin and did everything as in the [clip]("https://www.youtube.com/watch?v=8mUqaGe54nY&list=LL&index=7&ab_channel=AlejandroMV") and now everything is working properly.

---

