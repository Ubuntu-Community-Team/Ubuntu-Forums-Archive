---
title: "Array Declaration (BASH)"
date: 2008-10-07
forum: Programming Talk
---

### Post by blendmaster on 2008-10-07
Hello!

So, basically I'm new to bash (I have Java experience mostly, so I'm still a little off from scripting).

My problem lies in array declaration. Say I have an array *album_Data*, and I want to declare it with a certain amount of empty elements (say, for example, I want it to have $num_Of_Lines as the number for how big the array is).

After declaring it with empty elements, I want to begin initializing each element in a while loop. So, I have element $count being initialized in that array.

Finally, I want to then retrieve that data from the array.

As an example of the code (this is wrong, but may give a better picture):

```
num_Of_Lines=10
album_Data=album_Data[num_Of_Lines]
count=0
while read line3; do
if [ "$count" -le "4" ]; then
album_Data[$count]=$line3
((count++))
fi
done < Album.txt
mkdir /home/user/Music/"${album_Data[2]}"/
```

So basically, what am I doing (horridly, probably) wrong with my code?

Thank you!

---

### Post by stefanadelbert on 2008-10-07
As I understand it, you don't need to allocate space for an array in a Bash script. You declare an array and then populate it as you need to. If you need to iterate through an array there is a "for element in array" construct that is useful, or you could find the length of the array once it's populated and loop through the way you are in your example.

[http://www.tech-recipes.com/rx/635/bash-shell-script-declaringcreating-arrays/]("http://www.tech-recipes.com/rx/635/bash-shell-script-declaringcreating-arrays/")
[http://www.tech-recipes.com/rx/636/bash-shell-script-iterate-through-array-values/]("http://www.tech-recipes.com/rx/636/bash-shell-script-iterate-through-array-values/")

There are plenty of good Bash scripting resources out there. Good luck.
Stefan

---

### Post by blendmaster on 2008-10-07
That would explain it.

Thanks, I was really going crazy with that.

I was looking all over the place for a way to declare arrays, when its not even a standard part of the language lol.

---

### Post by gnusci on 2008-10-07
To recommend these two sites for Bash:

[http://en.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://en.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.tldp.org/LDP/abs/html/index.html](http://www.tldp.org/LDP/abs/html/index.html)

Give them a look if you are doing scripting.

---

### Post by ghostdog74 on 2008-10-07
> **blendmaster said:**
> Hello!

So, basically I'm new to bash (I have Java experience mostly, so I'm still a little off from scripting).

My problem lies in array declaration. Say I have an array *album_Data*, and I want to declare it with a certain amount of empty elements (say, for example, I want it to have $num_Of_Lines as the number for how big the array is).

After declaring it with empty elements, I want to begin initializing each element in a while loop. So, I have element $count being initialized in that array.

Finally, I want to then retrieve that data from the array.

As an example of the code (this is wrong, but may give a better picture):

```
num_Of_Lines=10
album_Data=album_Data[num_Of_Lines]
count=0
while read line3; do
if [ "$count" -le "4" ]; then
album_Data[$count]=$line3
((count++))
fi
done < Album.txt
mkdir /home/user/Music/"${album_Data[2]}"/
```

So basically, what am I doing (horridly, probably) wrong with my code?

Thank you!

if its not for practicing bash arrays, what you want to do is just 
```

var=$(awk 'NR==3' album.txt)
mkdir /home/user/Music/$var

```

tools like grep/sed/awk/cut/wc etc that are able to iterate files internally and faster than using bash's while loops.

---

