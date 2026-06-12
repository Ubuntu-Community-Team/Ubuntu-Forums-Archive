---
title: "Single on/off switch for conky"
date: 2006-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by kerry_s on 2006-08-01
Here's a simple script to turn conky on and off. Just copy the script to a empty text file and make it executable(properties>permissions)->

```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky

fi
```

Then just create a single launcher for it(right click panel/desk) and point it to what ever you named your file, add a icon and your all set. I use mine so i can change my .conkyrc to try things and skip using the terminal to kill conky and start conky, clicking on the icon is way faster. ;)

---

### Post by diskotek on 2007-01-07
i couldn't understand how to make it exactly...
how you name the file and how you make it executable.

i paste it to the mousepad(text file) and save it..uh i couldnt go so far :(

---

### Post by diskotek on 2007-01-07
ok i did it..the problem was: i save it to the desktop and i couldnt change the permissions. i moved it to home folder and make it executable. it works great. now i can configure my .conkyrc in a practical way :)
thanks again

---

### Post by amadeus266 on 2008-01-15
see this

[http://ubuntuforums.org/showthread.php?p=4138450#post4138450](http://ubuntuforums.org/showthread.php?p=4138450#post4138450)

---

### Post by NovaAesa on 2008-02-01
Awsome!! Thanks!

---

### Post by Harii on 2008-09-27
Looks like the one in Antix-mepis--
works really good too!
You can change it to work with wbar or any app. as well.

---

### Post by tromort on 2008-10-27
sweet! ROX!

---

### Post by o0Chris0o on 2009-05-13
This is great! I find this so much easier now. Thanks so much for your contribution

---

