---
title: "[SOLVED] How can I stop nohup'ing every command"
date: 2008-07-31
forum: Programming Talk
---

### Post by unutbu on 2008-07-31
When I run a script (in the background) from a gnome-terminal, it does not get killed when I quit gnome-terminal. It does not even quit when I log out and get back to the GDM login window. 

For example, I save this as 'test.sh'
```

#!/bin/sh
while true ; do
    echo "Hi!" >> ~/test/a;
    sleep 2
done
```

and I run it like this

```
test.sh &
```

(no nohup or disown). When I run pstree I get this:
```

     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;gnome-session&#9472;&#9516;&#9472;devilspie
     &#9474;                           &#9500;&#9472;fvwm&#9472;&#9516;&#9472;FvwmAuto
     &#9474;                           &#9474;      &#9500;&#9472;emacs-snapshot-&#9472;&#9472;&#9472;bash
     &#9474;                           &#9474;      &#9500;&#9472;firefox&#9472;&#9472;&#9472;run-mozilla.sh&#9472;&#9472;&#9472;firefox-bin&#9472;&#9472;&#9472;6*[{fi+
     &#9474;                           &#9474;      &#9492;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;ipython&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;less
     &#9474;                           &#9474;                       &#9500;&#9472;bash&#9472;&#9516;&#9472;pstree
     &#9474;                           &#9474;                       &#9474;      &#9492;&#9472;**test.sh**&#9472;&#9472;&#9472;sleep

```

Then I close all apps, log out, press Ctrl-Alt-F2, and run pstree from the virtual console and get:
```

init-+-NetworkManager
     |-NetworkManagerD
...
     |-system-tools-ba---dbus-daemon
     |-**test.sh**---sleep
     `-udevd
```

I believe test.sh should get killed when the gnome-terminal is closed. Why is my shell acting like this? How can I fix it?

---

### Post by daimaru on 2008-07-31
(EDIT AND DELETED] nevermind... I guess i did not read your post carefully enough since you did restart xserver it seems weird that the script is still  running. eventhough wireless lan scripts keep running too, even if you restart x. maybe theres a connection

---

### Post by mssever on 2008-07-31
Not everything gets killed when you log out. I don't know why, and I don't like it, but that's the way it has been as long as I've noticed. I often explicitly kill things from a console or failsafe terminal between sessions. What's particularly annoying is that gvfs-fuse-daemon refuses to die under any circumstances unless I send SIGKILL--which is the messiest way to kill a process.

---

### Post by unutbu on 2008-07-31
Vor says that when he tried my script, the script was killed when he closed his terminal. [http://ubuntuforums.org/showpost.php?p=5484543&postcount=8](http://ubuntuforums.org/showpost.php?p=5484543&postcount=8)

So there seems to be some possibility for configuration, though I don't know where to look.

---

### Post by mssever on 2008-07-31
> **unutbu said:**
> Vor says that when he tried my script, the script was killed when he closed his terminal. [http://ubuntuforums.org/showpost.php?p=5484543&postcount=8](http://ubuntuforums.org/showpost.php?p=5484543&postcount=8)

So there seems to be some possibility for configuration, though I don't know where to look.
It must have something to do with what signals are being sent. I ran a script very similar to your test script and learned something interesting:

When I type exit to close the terminal, the script keeps running. When I close the terminal via the close button on the title bar, the script gets killed.

---

### Post by damis648 on 2008-07-31
Do not run it with "&".

---

### Post by unutbu on 2008-07-31
> **mssever said:**
> 
When I type exit to close the terminal, the script keeps running. When I close the terminal via the close button on the title bar, the script gets killed.

Yes, this is how mine behaves as well. Perhaps there is nothing abnormal about my setup; this may just be the way the terminal was coded to behave.

Thanks, mssever!

---

### Post by mssever on 2008-07-31
It might be interesting to find out which signals are being sent, if any. You could try trapping various signals and see what happens...

---

### Post by unutbu on 2008-07-31
I'm afraid I probably don't understand what you mean  due to my very limited understanding of shell scripting.

I used a perl script to generate these commands, LOL:

```
#!/bin/sh
trap 'echo "I trapped signal 1" >> ~/test/a; exit' 1
trap 'echo "I trapped signal 2" >> ~/test/a; exit' 2
trap 'echo "I trapped signal 3" >> ~/test/a; exit' 3
trap 'echo "I trapped signal 4" >> ~/test/a; exit' 4
trap 'echo "I trapped signal 5" >> ~/test/a; exit' 5
trap 'echo "I trapped signal 6" >> ~/test/a; exit' 6
trap 'echo "I trapped signal 7" >> ~/test/a; exit' 7
trap 'echo "I trapped signal 8" >> ~/test/a; exit' 8
trap 'echo "I trapped signal 9" >> ~/test/a; exit' 9
trap 'echo "I trapped signal 10" >> ~/test/a; exit' 10
trap 'echo "I trapped signal 11" >> ~/test/a; exit' 11
trap 'echo "I trapped signal 12" >> ~/test/a; exit' 12
trap 'echo "I trapped signal 13" >> ~/test/a; exit' 13
trap 'echo "I trapped signal 14" >> ~/test/a; exit' 14
trap 'echo "I trapped signal 15" >> ~/test/a; exit' 15
trap 'echo "I trapped signal 16" >> ~/test/a; exit' 16
trap 'echo "I trapped signal 17" >> ~/test/a; exit' 17
trap 'echo "I trapped signal 18" >> ~/test/a; exit' 18
trap 'echo "I trapped signal 19" >> ~/test/a; exit' 19
trap 'echo "I trapped signal 20" >> ~/test/a; exit' 20
trap 'echo "I trapped signal 21" >> ~/test/a; exit' 21
trap 'echo "I trapped signal 22" >> ~/test/a; exit' 22
trap 'echo "I trapped signal 23" >> ~/test/a; exit' 23
trap 'echo "I trapped signal 24" >> ~/test/a; exit' 24
trap 'echo "I trapped signal 25" >> ~/test/a; exit' 25
trap 'echo "I trapped signal 26" >> ~/test/a; exit' 26
trap 'echo "I trapped signal 27" >> ~/test/a; exit' 27
trap 'echo "I trapped signal 28" >> ~/test/a; exit' 28
trap 'echo "I trapped signal 29" >> ~/test/a; exit' 29
trap 'echo "I trapped signal 30" >> ~/test/a; exit' 30
trap 'echo "I trapped signal 31" >> ~/test/a; exit' 31
trap 'echo "I trapped signal 32" >> ~/test/a; exit' 32
trap 'echo "I trapped signal 33" >> ~/test/a; exit' 33
trap 'echo "I trapped signal 34" >> ~/test/a; exit' 34
trap 'echo "I trapped signal 35" >> ~/test/a; exit' 35
trap 'echo "I trapped signal 36" >> ~/test/a; exit' 36
trap 'echo "I trapped signal 37" >> ~/test/a; exit' 37
trap 'echo "I trapped signal 38" >> ~/test/a; exit' 38
trap 'echo "I trapped signal 39" >> ~/test/a; exit' 39
trap 'echo "I trapped signal 40" >> ~/test/a; exit' 40
trap 'echo "I trapped signal 41" >> ~/test/a; exit' 41
trap 'echo "I trapped signal 42" >> ~/test/a; exit' 42
trap 'echo "I trapped signal 43" >> ~/test/a; exit' 43
trap 'echo "I trapped signal 44" >> ~/test/a; exit' 44
trap 'echo "I trapped signal 45" >> ~/test/a; exit' 45
trap 'echo "I trapped signal 46" >> ~/test/a; exit' 46
trap 'echo "I trapped signal 47" >> ~/test/a; exit' 47
trap 'echo "I trapped signal 48" >> ~/test/a; exit' 48
trap 'echo "I trapped signal 49" >> ~/test/a; exit' 49
trap 'echo "I trapped signal 50" >> ~/test/a; exit' 50
trap 'echo "I trapped signal 51" >> ~/test/a; exit' 51
trap 'echo "I trapped signal 52" >> ~/test/a; exit' 52
trap 'echo "I trapped signal 53" >> ~/test/a; exit' 53
trap 'echo "I trapped signal 54" >> ~/test/a; exit' 54
trap 'echo "I trapped signal 55" >> ~/test/a; exit' 55
trap 'echo "I trapped signal 56" >> ~/test/a; exit' 56
trap 'echo "I trapped signal 57" >> ~/test/a; exit' 57
trap 'echo "I trapped signal 58" >> ~/test/a; exit' 58
trap 'echo "I trapped signal 59" >> ~/test/a; exit' 59
trap 'echo "I trapped signal 60" >> ~/test/a; exit' 60
trap 'echo "I trapped signal 61" >> ~/test/a; exit' 61
trap 'echo "I trapped signal 62" >> ~/test/a; exit' 62
trap 'echo "I trapped signal 63" >> ~/test/a; exit' 63
trap 'echo "I trapped signal 64" >> ~/test/a; exit' 64

while true ; do
    echo "Hi!" >> ~/test/a;
    sleep 2
done

```

But all I was able to determine was that SIGHUP (signal 1) is sent to the script when the terminal window is closed, and no signal is sent to the script when 'exit' is typed at the terminal prompt.

---

### Post by mssever on 2008-07-31
> **unutbu said:**
> But all I was able to determine was that SIGHUP (signal 1) is sent to the script when the terminal window is closed, and no signal is sent to the script when 'exit' is typed at the terminal prompt.
I think you did understand what I meant. And it looks like you have the answer. The exit command doesn't send any signals to Bash's children.

---

