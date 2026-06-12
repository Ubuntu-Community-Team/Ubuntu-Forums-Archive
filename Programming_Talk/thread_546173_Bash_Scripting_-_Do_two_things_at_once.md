---
title: "Bash Scripting - Do two things at once"
date: 2007-09-08
forum: Programming Talk
---

### Post by bobbocanfly on 2007-09-08
I am writing a script that grabs images from a movie file then creates a montage of them. I am using Zenity as a GUI Front-end and have hit a problem. I need some way of forking the script so that i get a pulsating zenity progress bar while the first fork grabs the images. Does anyone have a solution?

---

### Post by colo on 2007-09-08
Start all programs needed to perform task A in a subshell, and background that subshell.

```
(task A) &
task B
task B+1
```

---

