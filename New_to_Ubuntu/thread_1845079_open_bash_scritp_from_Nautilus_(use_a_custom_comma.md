---
title: "open bash scritp from Nautilus (use a custom command?)"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by jmgl on 2011-09-16
Hello all,

I am trying to make a bash script to deal with some files selected and opened from Nautilus. Simplifying my problem I created a file called "callFromNautilus.sh" with the next content:

```

#!/bin/bash
echo "hello Wolrd" > files.txt

```This script is expected to create a file called "files.txt" with the content hello World in it. I make sudo chmod 700 callFromNautilus.sh and the file works as expected when called either from the Terminal or from Nautilus (double clicking callFromNautilus and selecting "Run in terminal").

What I would like to do is to open it automatically each time I double click a file with extension, for instance, *.cft (So then I could start playing with the NAUTILUS_SCRIPT_SELECTED_FILE_PATHS and so on). To do it I right-clicked one file that I created, file_1.cft, and selected "Open with other application". Then "Use custom command" and browsed for my script callFromNautilus.sh. For some reason this does not seem to work since the file "files.txt" that I was expecting is no created each time I double click a file with extension *.cft (not even the first time, when I select the option Open).

I would appreciate if someone could tell me what I am doing wrong here.

Thank you in advance for your help!

jmgl

---

### Post by SavageWolf on 2011-09-16
Are you sure the working directory is set? Change your script to include `cd ~/Desktop/`, and see if the file is created on your desktop.

---

### Post by jmgl on 2011-09-16
Oh my... you are completely right.
still many things to learn in linux!

---

