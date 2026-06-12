---
title: "Wget loop not working"
date: 2019-12-21
forum: Programming Talk
---

### Post by lilipop on 2019-12-21
hi,
i have this script
```

#!/bin/bash
for i in {1..4}
do
     wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/$i https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/$i/
done

```

it does not work

but when i execute only this;
```

wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/2 [https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/2/](https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/2/)

```
so, what is wrong with my loop?
can smb help me please?

thanks

---

### Post by TheFu on 2019-12-21
Did you try putting an "echo" in front of the wget command?

I use scripts to build scripts - all-the-time.  BTW, I'd write it this way:
```
#!/bin/bash
OPT1=" --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru"
OPT2="https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q"
for i in {1..4} ; do
   echo wget     $OPT1/$i     $OPT2/$i/
done
```

I didn't verify all the options. Output is:
```
$ bash /tmp/t
wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/1 https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/1/
wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/2 https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/2/
wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/3 https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/3/
wget --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/4 https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/4/

```
Whether any of this works, I don't know.

---

### Post by lilipop on 2019-12-21
hello,
thanks for trying to help me
```

#!/bin/bash
OPT1=" --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru"
OPT2="https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q"
for i in {1..4} ; 
do
   echo OPT1     $OPT1/$i   
   printf "\n"
   echo OPT2 $OPT2/$i/
   printf "\n"
done

```

got this output:
```

OPT1 --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/{1..4}


OPT2 https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/{1..4}/



```

maybe there is something wrong with my system?

---

### Post by TheFu on 2019-12-21
The exact code I posted generated the exact output I posted.
I didn't mean that it didn't work, just the the resulting output wasn't tested.
I started by select/pasting your code.

I use vim as my editor, no Linux. If you are doing this using a non-Unix editor, EOL might be wrong.  Also, I get that ** for .... ; do** is a style choice, but mine is working on the single line.  I changed the temp file to be
```
for .... 
do
```
it still worked.

---

### Post by lilipop on 2019-12-21
i have also tried this version:

```

#!/bin/bash
OPT1=" --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru"
OPT2="https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q"


counter=1
while [ $counter -le 4 ]
do
   echo OPT1     $OPT1/$counter   
   printf "\n"
   echo OPT2     $OPT2/$counter
   printf "\n"
   ((counter++))
done

```

and it seems also not to work. the counter for some reason is not increasing :'(

---

### Post by lilipop on 2019-12-21
[COLOR=#000000]so, why then from the same code i get one output and u got another?[/COLOR]
[COLOR=#000000]i use ubuntu with all the updates[/COLOR]

> **TheFu said:**
> The exact code I posted generated the exact output I posted.
I didn't mean that it didn't work, just the the resulting output wasn't tested.
I started by select/pasting your code.

I use vim as my editor, no Linux. If you are doing this using a non-Unix editor, EOL might be wrong.  Also, I get that ** for .... ; do** is a style choice, but mine is working on the single line.  I changed the temp file to be
```
for .... 
do
```
it still worked.

---

### Post by lilipop on 2019-12-21
i use Kate as my editor

> **TheFu said:**
> The exact code I posted generated the exact output I posted.
I didn't mean that it didn't work, just the the resulting output wasn't tested.
I started by select/pasting your code.

I use vim as my editor, no Linux. If you are doing this using a non-Unix editor, EOL might be wrong.  Also, I get that ** for .... ; do** is a style choice, but mine is working on the single line.  I changed the temp file to be
```
for .... 
do
```
it still worked.

---

### Post by lilipop on 2019-12-21
[https://stackoverflow.com/questions/21370059/why-is-this-simple-for-loop-in-my-linux-bash-not-working](https://stackoverflow.com/questions/21370059/why-is-this-simple-for-loop-in-my-linux-bash-not-working)

i was running my code as "sh guru.sh" but i should run it as bash guru.sh.

thanks anyway for the help. 
maybe you can help me also a bit with my other question?  ([https://ubuntuforums.org/showthread.php?t=2433584](https://ubuntuforums.org/showthread.php?t=2433584))

thanks

---

### Post by TheFu on 2019-12-21
But the code isn't the same.  

The code above is a little different. Sure, those differences shouldn't matter, but it seems they do.  I'm hardly an expert at bash.  I just have lots of experience and write my scripts in a specific way to avoid issues and make them easier to update over time.

If you seek a *why* answer, I don't know. Maybe someone else will?
BTW, I select/pasted that last code.
```
$ /tmp/t
OPT1 --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/1

OPT2 [https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/1](https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/1)

OPT1 --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/2

OPT2 [https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/2](https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/2)

OPT1 --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/3

OPT2 [https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/3](https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/3)

OPT1 --no-clobber --convert-links -nH -nd -p -E -e robots=off -U mozilla -P /home/jousr/Desktop/KitGuru/4

OPT2 [https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/4](https://www.kitguru.net/lifestyle/mobile/notebook/dominic-moass/dream-machines-p960rn-laptop-review-9750h-2080-max-q/4)
```

Looks like an issue on your side.

---

