---
title: "set unique titile for each terminal tab from bash in 16.04"
date: 2016-12-13
forum: New to Ubuntu
---

### Post by lnux12 on 2016-12-13
I want to open multiple terminal tab, run command and set title. I can open multiple tab with this command:
  gnome-terminal --tab -e "command1" --tab -e "command2" 
  but cannot use --title option as it is not available in this version. 
  I know mate-terminal is the solution but i do not want to apply this.  Also applied following solutions:
  [http://unix.stackexchange.com/questions/177572/how-to-rename-terminal-tab-title-in-gnome-terminal](http://unix.stackexchange.com/questions/177572/how-to-rename-terminal-tab-title-in-gnome-terminal)
  set-title worked for me but i do not know how to do it in bash script.
  Following script can open terminal tab but i want to set unique title for each tab too.
  ```
#!/bin/bash

tab=" --tab"

for i in 2 3; do
  options+=($tab -e "bash -c 'ping 192.168.8.$i; bash'" )          
done

gnome-terminal "${options[@]}"
```

What i want to do is 1. open terminal tab 2. set title and run command

---

### Post by lnux12 on 2017-01-31
I had solved my issue answer provided at here :  [http://askubuntu.com/questions/860145/set-title-for-each-terminal-tab-in-gnome-terminal-using-a-bash-script#860484](http://askubuntu.com/questions/860145/set-title-for-each-terminal-tab-in-gnome-terminal-using-a-bash-script#860484)

---

### Post by parkado on 2017-01-31
And one shall mark the thread [SOLVED] after! : ) Admins seem to dig it : )

---

