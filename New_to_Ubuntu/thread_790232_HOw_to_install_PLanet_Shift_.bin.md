---
title: "HOw to install PLanet Shift? .bin"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-11
hi guys,

I just downloaded planet shift.bin and i dont know how to install it any ideas? its a .bin file

---

### Post by sdowney717 on 2008-05-11
right click the file, goto properties - permissions, set it to allow execute as a program.

open up applications - accesories - terminal

navigate to the file type 'cd what directory etc...'
verify you are there by typing 'ls' to see the directory contents.
(you can back up by typing 'cd ..')

type in './namefile.bin' to run
(I believe this tells the os to run from this root location that file name)

---

### Post by appoloin on 2008-05-11
hi 

i tried to do what i think is right but i get a busy error

edward@Vlad:~$ /home/edward/Desktop/PlaneShift-v0.4.00-x86.bin
bash: /home/edward/Desktop/PlaneShift-v0.4.00-x86.bin: Text file busy

any idea?

---

### Post by appoloin on 2008-05-11
i took a screen shot of what i done.. hope this helps

---

### Post by fluteflute on 2008-05-11
You were almost there. You were right to do ```
cd Desktop
``` but now you should type ```
./PlaneShift-v
``` followed by a tab (the two arrows on the left of the keyboard) which will automatically fill in the rest for you.

---

### Post by appoloin on 2008-05-11
I dont get it

edward@Vlad:~$ ls Desktop 
PlaneShift.bin  Screenshot.png
edward@Vlad:~$ cd Desktop
edward@Vlad:~/Desktop$ ./PlaneShift-v
bash: ./PlaneShift-v: No such file or directory
edward@Vlad:~/Desktop$ ./PlaneShift.bin -v
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ./PlaneShift.bin-v
bash: ./PlaneShift.bin-v: No such file or directory
edward@Vlad:~/Desktop$ '/home/edward/Desktop/PlaneShift.bin'
bash: /home/edward/Desktop/PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ./PlanetShift.bin
bash: ./PlanetShift.bin: No such file or directory
edward@Vlad:~/Desktop$ ./PlanetShift.bin-v
bash: ./PlanetShift.bin-v: No such file or directory
edward@Vlad:~/Desktop$ ./PlanetShift.bin -v
bash: ./PlanetShift.bin: No such file or directory
edward@Vlad:~/Desktop$ ls
PlaneShift.bin  Screenshot.png
edward@Vlad:~/Desktop$ ./PlaneShift.bin 
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ./PlaneShift -v
bash: ./PlaneShift: No such file or directory
edward@Vlad:~/Desktop$ 


what am i doing wrong?

---

### Post by fluteflute on 2008-05-11
- No space between 'PlaneShift' and '-v'.
- Small 'v' rather than big 'V'.
- Press 'tab' after typing that ([http://www.7gadgets.com/wp-content/uploads/2007/09/il_fullxfull_11621271.thumbnail.jpg](http://www.7gadgets.com/wp-content/uploads/2007/09/il_fullxfull_11621271.thumbnail.jpg))


Or just try this (forget the tab thing) and put ```
./PlaneShift-v0.4.00-x86.bin
```.

---

### Post by appoloin on 2008-05-11
Nice TAB picture..
bash: ./PlaneShift: No such file or directory
edward@Vlad:~/Desktop$ ./PlaneShift -v
bash: ./PlaneShift: No such file or directory
edward@Vlad:~/Desktop$ ./PlaneShift-v
bash: ./PlaneShift-v: No such file or directory
edward@Vlad:~/Desktop$ ./PlaneShift-v
bash: ./PlaneShift-v: No such file or directory
edward@Vlad:~/Desktop$ ./PlaneShift-v
bash: ./PlaneShift-v: No such file or directory
edward@Vlad:~/Desktop$ ls
PlaneShift.bin  Screenshot.png
edward@Vlad:~/Desktop$ ./PlaneShift.bin-v
bash: ./PlaneShift.bin-v: No such file or directory
edward@Vlad:~/Desktop$ 


im getting no such file but if i do ls its there i dont get it

---

### Post by sdowney717 on 2008-05-11
you have to type it exactly lowercase uppercase etc....
you highlight the name copy and paste.

---

### Post by fluteflute on 2008-05-11
Push the tab button before pressing enter.

If that still doesn't work forget the tab and put: ```
./PlaneShift-v0.4.00-x86.bin
```.

---

### Post by appoloin on 2008-05-11
edward@Vlad:~/Desktop$ '/home/edward/Desktop/PlaneShift.bin'
bash: /home/edward/Desktop/PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ,/PlaneShift-v
bash: ,/PlaneShift-v: No such file or directory
edward@Vlad:~/Desktop$ ,/PlaneShift.bin
bash: ,/PlaneShift.bin: No such file or directory
edward@Vlad:~/Desktop$ ls
PlaneShift.bin  Screenshot.png
edward@Vlad:~/Desktop$ 

I did not put space on -v and i did us small v
i did type it as you advised but im still getting  No such file or directory
i even copy and paste so theres no typing mistake but still  No such file or directory

i think its just telling me to give it up lol...

thanks for the help anyway

---

### Post by atomkarinca on 2008-05-11
Just copy and paste these in the terminal:

```
cd ~/Desktop
chmod +x PlaneShift.bin
./PlaneShift.bin
```

---

### Post by fluteflute on 2008-05-11
I forgot about that stage! Except the file isn't called 'PlaneShift.bin'. So we need:
```
cd ~/Desktop
chmod +x PlaneShift-v0.4.00-x86.bin
./PlaneShift-v0.4.00-x86.bin
```

---

### Post by atomkarinca on 2008-05-11
> **appoloin said:**
> edward@Vlad:~/Desktop$ ls
PlaneShift.bin  Screenshot.png

Because of these lines I thought the filename was Planeshift.bin but the best thing is to type Plane and then hit tab button, it should be completed automatically.

---

### Post by appoloin on 2008-05-11
edward@Vlad:~$ cd Desktop
edward@Vlad:~/Desktop$ chmod +x PlaneShift.bin
edward@Vlad:~/Desktop$ ./PlaneShift.bin 
I hit enter
and i get this
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$

---

### Post by atomkarinca on 2008-05-11
Can you reboot and try those lines once more?

---

### Post by appoloin on 2008-05-11
Hi Guys,

I dunno what im doing wrong here but its just not doing it for me.

steps taken:
-cd Desktop
-ls
-PlaneShift.bin
- ./Plane => hit tab
-text file busy
edward@Vlad:~$ cd
edward@Vlad:~$ cd Deasktop
bash: cd: Deasktop: No such file or directory
edward@Vlad:~$ cd Desktop
edward@Vlad:~/Desktop$ ls
PlaneShift.bin
edward@Vlad:~/Desktop$ ./Plane
bash: ./Plane: No such file or directory
edward@Vlad:~/Desktop$
edward@Vlad:~/Desktop$ ./PlaneShift.bin
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ './PlaneShift.bin'
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ './PlaneShift.bin'
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ls
PlaneShift.bin
edward@Vlad:~/Desktop$ ./PlaneShift.bin
bash: ./PlaneShift.bin: Text file busy
edward@Vlad:~/Desktop$ ./PlaneShift-v0.4.00-x86.bin
bash: ./PlaneShift-v0.4.00-x86.bin: Text file busy
edward@Vlad:~/Desktop$ ./PlaneShift-v0.4.00-x86.bin
bash: ./PlaneShift-v0.4.00-x86.bin: Text file busy
edward@Vlad:~/Desktop$ './PlaneShift-v0.4.00-x86.bin'
bash: ./PlaneShift-v0.4.00-x86.bin: Text file busy
edward@Vlad:~/Desktop$ './PlaneShift-v0.4.00-x86.bin'
bash: ./PlaneShift-v0.4.00-x86.bin: Text file busy
edward@Vlad:~/Desktop$

either im getting really stupid her to suffering from fat fingers but im sure im following it right and just not working

---

### Post by housefly7k on 2008-06-01
I had the same error, it was because my torrent client was still uploading the file....atleast I think so, when I switched off the torrent I was able to install no problem using 

```
sudo ./PlaneShift-v0.4.00-x86.bin 
```

Goodluck with your installation.

---

### Post by djshag on 2008-08-02
I was having the same "text file busy" problem and closing the torrent client worked! Thanks!

---

