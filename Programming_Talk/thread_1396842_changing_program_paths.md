---
title: "changing program paths"
date: 2010-02-02
forum: Programming Talk
---

### Post by smdawson on 2010-02-02
I am writing shell scripts and want to be able to execute from the terminal by just entering the name.  i.e. 
```
smdawson@smdawson:~$ my_script
```

I am changing the searched paths like this
```
smdawson@smdawson:~$ export PATH=$PATH: /script_folder
```

This works for me and I can execute any shell script in the folder by typing the name in the terminal (i.e. my_script). However, if I close the terminal and come back, my changes are not saved. If I want to execute the shell script in the same way, I have to repeat the whole process of changing the searched paths, etc.

Any info on making these changes stick?

---

### Post by geirha on 2010-02-02
Add that line to ~/.profile . Then after you've logged out and back in, it should get sourced and $PATH will contain your script-folder.

```
echo "$PATH"
```

---

### Post by smdawson on 2010-02-02
I got it to save the changes. Thanks for the help.

---

