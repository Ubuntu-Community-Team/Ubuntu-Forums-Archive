---
title: "New to linux, my sub is not working and I need some help with Terminal"
date: 2016-06-10
forum: New to Ubuntu
---

### Post by roidingoldman on 2016-06-10
I'm brand new to linux and upon running it for the first time I noticed my speakers are working fine but my sub is doing nothing. I've found the solution to my problem right here: (reply #2) [http://ubuntuforums.org/showthread.php?t=1155761](http://ubuntuforums.org/showthread.php?t=1155761) but I lack the basic knowledge of Terminal to actually accomplish it.

I can use the linux version of File Explorer to find the find and edit the line of code, but it won't let me save it because it needs me to be the admin. Apparently I need to use Terminal to do this. I need specific, step by step instructions of what to enter into Terminal. Thanks for your responses and your time.

I am running ubuntu 16.04 LTS 64-bit.

---

### Post by Habitual on 2016-06-10
Try ```
gksudo gedit /etc/pulse/daemon.conf
```

If /etc/pulse/daemon.conf is the file in question.
Sub other graphical editor for gedit if different (kate/pluma)

Or using the command-line
```
sudo vi /etc/pulse/daemon.conf
```
and then in vi
press the forward slash "/" character and type in remixing and press <enter>
1st hit may not be it so press / again to continue searching.

When you find the correct entry to edit from the /remixing search you will be on the line needing to be edited.
press the $ symbol to goto the end of line and press the letter "a"
backspace over No and press "I" and then make No into Yes
Press escape twice and type ZZ and it's saved and you are out.

---

### Post by roidingoldman on 2016-06-10
> **Habitual said:**
> Try ```
gksudo gedit /etc/pulse/daemon.conf
```

This worked. First I had to install gksudo. Then restart, then do it again, but then it worked.

I appreciate your help with this. The sub is still not working :(, but at least I was able to modify the file. Now I just need to try another solution.

---

### Post by DuckHook on 2016-06-10
*vi* is very powerful and versatile, but not very intuitive for newer users unaccustomed to modal editors.

For the command line, I would recommend:```
sudo nano
```...which is a lot like gedit or any other simple text editor.

@roidingoldman

The thread you are following is more than 7 years old and there have been 14 releases since then. Many things have changed over that time. I have very little knowledge of audio issues, so cannot help, but hopefully, more knowledgeable people will soon notice this thread.

---

### Post by roidingoldman on 2016-06-10
Fixed it. Took an absolutely crazy amount of effort. But I figured it out. I appreciate all your input. Not just in this thread but overall. I wouldn't have known what to do without the crazy amount of information yielded by Google and this forum.


Step 1, open Terminal. Step 2:

```
gksudo apt-get install alsa-tools
```

and

```
gksudo apt-get install alsa-tools-gui
```

Search computer for HDAJackRetask and open
Select codec Conexant CX20641

Green Headphone, Front side > Headphone
Pink Mic, Front side > Microphone
Pink Mic, Rear side > Line in
Green Line Out, Rear side > Line out (Front)

Apply now

UPDATE: I've noticed that while this works, I need to do it again every time I restart the computer. I fixed that by pressing the "Install boot override" button right below "Apply now" and it fixes that.

---

### Post by DuckHook on 2016-06-10
Congratulations! Good for you. I wasn't much help, but I know that sometimes, nothing feels more rewarding than figuring it out yourself.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by Habitual on 2016-06-11
> **roidingoldman said:**
> Fixed it. Took an absolutely crazy amount of effort

"effort" is just inexperience with new tools. ;)
Good job and well done.

---

