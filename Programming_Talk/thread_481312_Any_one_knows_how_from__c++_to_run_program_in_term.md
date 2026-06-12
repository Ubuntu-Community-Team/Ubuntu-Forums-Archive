---
title: "Any one knows how from  c++ to run program in terminal"
date: 2007-06-22
forum: Programming Talk
---

### Post by marcha23 on 2007-06-22
[SIZE="4"]Hallo, so I am making a graphical project with wx widgets. The problem is tath I have to show some graphs an therefor I need to run gnuplot-terminal program to show this graphs. As it is a terminal program there is pause option till you press enter in terminal, that i want to use, so how I can run program in terminal from c++?[/SIZE]

I can write script that runs gnuplot and open file and then with system(" bash script_name"), but then there appears no terminal window and the pause is not controlable.

Any suggestions.

---

### Post by Soybean on 2007-06-22
Uh... well, one option would be something like 
```

system("gnome-terminal -x bash script_name");

```
Which would launch in a terminal, but specifically a gnome-terminal. So if your user doesn't use gnome-terminal or have it installed, that wouldn't work. I suspect there's a better way, but I don't do much GUI-based programming.

---

### Post by marcha23 on 2007-06-22
Thanks it is really working.

---

