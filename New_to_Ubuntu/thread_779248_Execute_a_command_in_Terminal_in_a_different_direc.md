---
title: "Execute a command in Terminal in a different directory"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by sjprice on 2008-05-02
I want to execute "python wuu.py" that is in a very deep directory. So I made a bash script in the directory and thought I could add a Launcher item pointing to the bash script to have it execute in Terminal. I get the error "There was an error creating the child process for this terminal"

Where did I go wrong? Is there an easier way?

---

### Post by wermeulen on 2008-05-02
Hi sjprice, I think I know this one.

For example, if wuu.py is in /home/sjprice/very/deep/directory/link/. Now, create a runme.bash script in that directory with following contents:
```
#!/bin/bash

cd /home/sjprice/very/deep/directory/link/
python wuu.py
```

Make the script executable either through command "chmox +x runme.bash" or by going to the permissions tab in the properties menu from when you right click on the file in nautolus.

Hope that solves your problem!

---

### Post by sjprice on 2008-05-02
yep, thats great and exactly what i want to do. Now take it a step further and tell me how to execute that bash script from the launcher, so I dont have to go to the directory every time :)


EDIT: so, after I read your bash script again, I figured out what you did. Change the directory, then run the script. I finally figured out to put that script in my home directory and added it to the launcher and added ./runwuu.sh to the command line. works like a charm!

Thanks wermeulen!

---

### Post by wermeulen on 2008-05-02
Kay :)

[LIST]
[*]Right click on the panel on an empty spot (the top bar where the applications, places, system and such are).
[*]Select Add to Panel...
[*]Select Custom Application Launcher and click Add
[*]Select as Type: Application in Terminal, give it a Name, browse to the file and select that as the Command. And Close.
[/LIST]

You know have a Launcher on your panel.

You can also put in your Applications Menu. Go to System -> Preferences -> Main Menu. Browse it for a good spot and select New Item. From there it is the same as last step in above list.

Is that it? :p

EDIT: Doh! You had it all figured out already :)

---

