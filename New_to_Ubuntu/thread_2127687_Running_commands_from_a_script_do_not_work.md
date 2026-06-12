---
title: "Running commands from a script do not work"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by mjohnston on 2013-03-20
Hi all!

I am having some issues with a script, this is my first foray into Ubuntu and have read many guides, tutorials etc, so please be gentle!

My script (copyword.sh) is as follows:


    ```
#!/bin/sh
rm -rfv /home/user/Documents/Exercise/*
cp -rfv /home/user/Documents/ExerciseShare/ExerciseFiles/Word/Advanced/ /home/tp3/Documents/Exercise/

```

If i was to run these commands individually via Terminal they run ok. I have put them in a script (as above) and when I attempt to tun the script the Terminal windows flashes (opens as if it is about to do something and then closes) for about a second and nothing happens.


My attempts at solutions:


 1. Adding `wait` to the end of the script - no luck
 2. Right Click Script > Properties > Permissions > Execute - set
 3. Attempted to `Run` and `Run in Terminal` - no luck

When I attempt to run the script via terminal as below I get an error:
```
/home/user/Desktop/copyword.sh
```

Error:
```
bash: /home/user/Desktop/copyword.sh: /bin/sh^M: bad interpreter: No such file or directory
```

Any help would be much appreciated!

Cheers,
Mitchell

---

### Post by AlecJ on 2013-03-20
try putting a full stop in front i.e.

./home/user/Desktop/copyword.sh

or if in the folder

./copyword.sh

---

### Post by steeldriver on 2013-03-20
> **mjohnston said:**
> 
```
bash: /home/user/Desktop/copyword.sh: /bin/sh[COLOR=#ff0000]^M[/COLOR]: bad interpreter: No such file or directory
```


It looks like you have Windows-style line terminations (CR-LF) in your file - you will need to run the file through dos2unix or use a text editor to remove them - see similar problem / solution here --> [http://ubuntuforums.org/showthread.php?t=2125559&p=12557331#post12557331](http://ubuntuforums.org/showthread.php?t=2125559&p=12557331#post12557331)

---

### Post by mjohnston on 2013-03-20
> **steeldriver said:**
> It looks like you have Windows-style line terminations (CR-LF) in your file - you will need to run the file through dos2unix or use a text editor to remove them - see similar problem / solution here --> [http://ubuntuforums.org/showthread.php?t=2125559&p=12557331#post12557331](http://ubuntuforums.org/showthread.php?t=2125559&p=12557331#post12557331)

Perfect,

This is the answer. Thank you very much!

---

