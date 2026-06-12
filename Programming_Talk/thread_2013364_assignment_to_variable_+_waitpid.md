---
title: "assignment to variable + waitpid"
date: 2012-06-30
forum: Programming Talk
---

### Post by SilatDo on 2012-06-30
(Sorry, I forgot to put in the title, that this is about Bash)

Hi, I'm wondering why this doesn't work:

> #!/bin/sh
filename="xyz"
filename=$(zenity --entry --title "foo") &
sleep 0.1
wmctrl -r foo -e 0,500,500,100,200
wait $!
echo "filename: $filename"

In case you don't know what "zenity" is: it's a gtk-gui-version of "dialog". In this case, just a simple inputbox.

My understanding is, that this script should do the following:
1. assign "xyz" to "filename"
2. assign something to "filename" from the input of zenity, but send it to background, so that I can do stuff to the zenity window in the meanwhile.
3. sleep 1/10 of a second
4. move/resize the zenity window
5. wait until zenity resp. the assignment to "filename" is completed
6. echo "$filename"

However, the value of "filename" remains "xyz"
What am I missing?  Thanks in advance.

---

### Post by MadCow108 on 2012-07-01
I don't think something like that can work in bash

you can pipe the zenity result into a file or pipe and retrieve it later to get the same effect:
```
#!/bin/sh
filename="xyz"
zenity --entry --title "foo" > output &
pid=$!
sleep 0.1 
wmctrl -r foo -e 0,500,500,100,200
wait $pid
filename=$(cat output)
echo "filename: $filename"
```

---

### Post by SilatDo on 2012-07-01
Thanks, MadCow.  I, too, made a workaround:
```

#!/bin/sh

wmctrl_e ()  {
  sleep 0.1
  wmctrl -r foo -e 1,500,500,100,200
}

filename="xyz"
wmctrl_e &
filename=$(zenity --entry --title "foo")
echo "filename: $filename"

```

Both are ugly, mine just happens to be a little uglier ;)

However, I still believe there should be a way to make the whole assignment (filename=$(zenity)) a single process, which can be put into background.
We'll see.  Thanks again.

---

