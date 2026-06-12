---
title: "Kill method"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Niloc on 2008-08-14
If I have an application which has 'frozen', is there some way of 'killing' it from the command line?

---

### Post by Locutus_of_Borg on 2008-08-14
killall application_name

---

### Post by ad_267 on 2008-08-14
If you don't know the application name you can use:
ps -e | less
to get a list of all the processes running. Then use:
kill psid
where psid is the process id number.

Also you can run the program xkill and then just click on the window of the program you want to kill.

---

### Post by iaculallad on 2008-08-14
Or, using the process ID of your application.

```
ps aux | grep app_name
```

And using the ProcessID to terminate the application:

```
sudo kill -9 ProcessID_from_ps_aux
```

---

### Post by ice60 on 2008-08-14
to get the process id you can run this -
```
pidof *process_name*
```
then to kill the process you can run this -
```
kill -9 *the pid you got*
```
kill with the 9 option will kill anything, sometimes without the 9 not everything will be killed. running **info kill** will tell you more.

that's what i normally do, maybe there's a better way??

---

### Post by bryncoles on 2008-08-14
you can also open the terminal (i have mine mapped onto the shortcut 'super key +t).  type 'top' to open a task manager, showing what processes are running. then press 'k' and type in the number in the PID column to close that task. 

if the offending program is listed as being a root program, you will have to use 'top' as root too. exit by pressing 'q' and type 'sudo top'.

thats what i do anyway!

---

### Post by kaboodle_fish on 2008-08-14
Another alternative is to right click on a panel, select Add to Panel and add "Kill Application"* 
 
Then you can click this which will turn your cursor into a crosshair which you can put over the application you want to kill. 
 
 
*It may not be called this, but you will recognise it.

---

### Post by hakimaki on 2008-08-14
Also can use top or htop in terminal, highlight the app and press F9 I believe it will be for Kill.

---

### Post by starcannon on 2008-08-14
pstree

locate name of process

pkill process

---

### Post by Bachstelze on 2008-08-14
> **ice60 said:**
> to get the process id you can run this -
```
pidof *process_name*
```
then to kill the process you can run this -
```
kill -9 *the pid you got*
```
kill with the 9 option will kill anything, sometimes without the 9 not everything will be killed. running **info kill** will tell you more.

that's what i normally do, maybe there's a better way??

[FONT="Courier New"]kill -9[/FONT] should ony be used in last resort (i.e. when the process won't terminate when you try to [FONT="Courier New"]kill[/FONT] it normally). So you should first try

```
kill pid
```

and if that doesn't work you can use [FONT="Courier New"]kill -9[/FONT]. Another option is to use [FONT="Courier New"]killall[/FONT], that will kill all the processes that run a given app, for example:

```
killall firefox
```

or

```
killall ssh
```

---

### Post by Paqman on 2008-08-14
As mentioned there's the panel applet, but you can also hit Alt-F2 and type:
```

xkill

```
and then just click on the unresponsive window. You can also end any process you want from within the System Monitor.

---

### Post by danny_galaga on 2008-08-14
probably a dumb question, but can you not just use 'system monitor' to kill an application?

---

### Post by starcannon on 2008-08-14
> **danny_galaga said:**
> probably a dumb question, but can you not just use 'system monitor' to kill an application?

+1 to danny_galaga

lol what and take the fun out of it

I've been up to long sheesh hehe.

*smacking myself in the head, doh, I usually go for the gui option first*

/sigh, i'm tired, and not thinking right.

*wobbles off to bed*

---

