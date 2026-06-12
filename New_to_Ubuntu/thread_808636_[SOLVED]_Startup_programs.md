---
title: "[SOLVED] Startup programs?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-26
Is there a way to start a program automatically using the terminal? I know how to do it with Sessions, but I want to do it in a script, which needs the terminal.

---

### Post by quelx on 2008-05-26
like an initialization script (/etc/init.d/)

There is a file, /etc/init.d/skeleton, which you can make a copy of and use it to create your own startup script.  These run before starting the windows manager (KDE, Gnome, XFCE, whathaveyou)

Telling us which application you are trying to start would help us help you.

---

### Post by slughappy1 on 2008-05-26
I am writing a script to install certain programs automatically for me. But for some of them to work properly I have to load the after Gnome loads. I would normally use the Sessions program, but the programs I want to run will either not load if I put them in Sessions, or they will not load correctly. For example, I want emerald --replace and conky to load. But when I put them in sessions, emerald didn't load and conky loaded improperly. So I wrote a quick little script ```
#!/bin/bash
sleep 20
emerald --replace &
sleep 5
conky

``` But I want to be able to use the terminal to to add the script to Sessions. 

I am trying to write a script that will install programs and my second script. But I want to make my first script able to put the second on a computer and then have it load during login using Sessions or a equivalent.

---

### Post by sam_delta on 2008-05-26
that script should work under sessions. make sure you make it executable
```
sudo chmod 777 ./your_script
```
then under sessions , add the path to your script 
/home/user/Desktop/script or wherever you have it

you may also consider adding more time to the sleep time, to let the whole desktop fully load
sam

---

### Post by quelx on 2008-05-26
If you create a new **Launcher** (right click on the Desktop and Create Launcher) you can change the **Type** to **Application in Terminal** then add that Launcher to your sessions file.  Not sure that would work, but it won't hurt to try.

---

### Post by slughappy1 on 2008-05-27
No sorry, I guess I didn't convey what I meant. I am making a script to install programs that I use, but in that script I want to copy a different script and make the second one load every time I login. The one I posted above already works. That is not the problem. The problem is getting the first script to copy the second one and make the second one load every time. I can rely on doing it myself after the first script makes the second. But I would like to make the whole process automatic.

---

### Post by sam_delta on 2008-05-27
ahh ok, try this

change the permissions of the second script by typing

```
sudo chmod 777 ./script2
```

NOTE this code will make the script executable to every user, therfore, you do not have to type sudo to run the second script. this is necesary, because you will not be typing any passwords, your first script will call the second one. unless you manually run the first script as sudo, you cant change the persmissions to something like(766)

then, in the first script, just type the path of the second script

```
/home/user/Desktop/script2
```

if it is in the same directory, just type 

```
./script2
```

if that doesnt work, try adding the word "sh" before the script so it would look like this:

```
sh ./script2
```

sam

---

### Post by Inxsible on 2008-05-27
Why would you want to call multiple scripts? Can't you embed everything that is in script2 in script1 itself??':confused:

---

### Post by slughappy1 on 2008-05-27
Well no, I want script one to execute a total of once. But I want script 1 to make script 2, and script 2 will execute every time I log in. Essentially I want script 1 to install programs and a script. So script 1 will install things, and script 2 will run the programs and script every login. Just as if I made script 2 and put it in Sessions, but I don't want to have to put it in Sessions myself. I want script 1 to do that. I don't know if I am making much sense, and I am sorry if I am not.

---

