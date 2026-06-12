---
title: "Python/Bash comand that call VLC."
date: 2017-10-16
forum: Programming Talk
---

### Post by dan882 on 2017-10-16
First of all, thank for this awesome forum.

So, i was writing a script in python that use **[SIZE=2]subprocess[/SIZE]** to start an audio file, using **[SIZE=2]vlc[/SIZE]**, i also want that at the end of the audio to close itself (**--play-and-exit**) and that dosen't show up all the usless info (**--quiet**). No problem so far, here is the command:

```
[SIZE=3]subprocess.check_call('vlc --quiet --play-and-exit "/home/foo/bar.mp3"', shell=True)[/SIZE]
```

This code work by stopping the script until vlc exit. If i try to close the audio it give me this message in the terminal "**QObject::~QObject: Timers cannot be stopped from another thread**". This is a problem for me since i need to continue using my script while the audio is still playing. I read that the problem is between the child program and the command that execute it but i can't find an easy solution :p


Here is my question, can i call vlc and have it not stop all my script until it has finished? There must be a simple way to start a program maybe a alternative to vlc (another media player)?

---

### Post by ian-weisser on 2017-10-16
check_call() specifically waits until completion.
If you don't want, that then look thrugh Popen() documentation for a call that doesn't wait for completion.

---

### Post by dan882 on 2017-10-22
> **ian-weisser said:**
> check_call() specifically waits until completion.
If you don't want, that then look thrugh Popen() documentation for a call that doesn't wait for completion.

Thank you, i used another way to start the program by add " &" at the end of the comand, i really don't know way i haven't think about before :confused:
I will read more about popen since i still i don't understand the "grammar", bye ):P

---

