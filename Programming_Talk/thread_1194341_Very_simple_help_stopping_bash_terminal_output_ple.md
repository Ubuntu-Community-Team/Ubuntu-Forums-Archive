---
title: "Very simple help stopping bash terminal output please"
date: 2009-06-22
forum: Programming Talk
---

### Post by Ojustaboo on 2009-06-22
My very simple bash for starting Lord of the rings online contains just the following 3 lines.

killall pulseaudio
export WINEPREFIX=/home/dad/.wine-lotro/
pylotro


This works fine, but how do I stop terminal windows opening
(eg saying: pulseaudio: no process killed) or failing that, how do I make them close straight away please?

thanks

---

### Post by Can+~ on 2009-06-22
How are you starting the script?

---

### Post by aesis05401 on 2009-06-22
Sounds like you are just wanting to 'background' the script. 

You can leave your original script in tact.  Create a custom launcher set to be a terminal application, and for your command simply enter the name of the lotr script with ' &' appended.  When you click this launcher a CLI will appear, your commands will run, and then the window will exit automatically.

Does this help?

---

### Post by soltanis on 2009-06-22
If you actually want to kill pulseaudio (if it's running and killall is failing) you should also try using pkill instead of killall.

Using the & will background the process but not suppress output. To do both, you would have to redirect the output data. So in the launcher command line you'd type

```

script.sh &> /dev/null &

```

Which redirects both standard output and error to the null device (discards all output).

---

### Post by Ojustaboo on 2009-06-22
Many thanks all, I am being stupid (for a change)

If I start the script from `create launcher` the problems non existent :D

soltanis's solution works if I start it from a terminal

thanks again

boo

---

