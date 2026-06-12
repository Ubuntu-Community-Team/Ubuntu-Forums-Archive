---
title: "Help needed with bash script"
date: 2009-04-06
forum: Programming Talk
---

### Post by Nevon on 2009-04-06
I've rewritten a script to burn Xbox 360 ISOS, originally written by a guy called Wicked, as well as added a GUI to it. The GUI version seems to be working fine, but the CLI option is giving me an error that I can't seem to track down. I was hoping someone here could help me see if they can find it.

The script is available here: [http://ubuntuforums.org/showthread.php?p=7024970](http://ubuntuforums.org/showthread.php?p=7024970)

The error message I'm getting is [: 146: ==: unexpected operator

Note that this is using the --no-gui option.

---

### Post by sisco311 on 2009-04-06
```
elif [ **"$1"** == "--no-gui" ]; then
```

---

### Post by Nevon on 2009-04-06
> **sisco311 said:**
> ```
elif [ **"$1"** == "--no-gui" ]; then
```

Still gives me the same error.

---

### Post by sisco311 on 2009-04-06
oh ok, i was able to reproduce the error with sh:
```
sh script --no-gui
```
the script works fine for me in bash:
```
script --no-gui
bash script --no-gui
```

if you change == to = in the if statements the script will  work in both sh and bash:
```
elif [ $1 = "--no-gui" ]; then 
  blablabla

``` 

HTH

---

### Post by Nevon on 2009-04-06
> **sisco311 said:**
> oh ok, i was able to reproduce the error with sh:
```
sh script --no-gui
```
the script works fine for me in bash:
```
script --no-gui
bash script --no-gui
```

if you change == to = in the if statements the script will  work in both sh and bash:
```
elif [ $1 = "--no-gui" ]; then 
  blablabla

``` 

HTH

Awesome, man! Now it is working! A thousand thanks to you! :D

---

