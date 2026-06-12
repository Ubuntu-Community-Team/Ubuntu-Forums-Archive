---
title: "Revert to default settings on Gnome tweak crash"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Keral on 2012-06-19
Hello, I have this issue when i was trying to play around with the Gnome tweak tool, it ended awkwardly(some themes ended up being too off and out of sync for some reason). I ended up trying to purge it in terminal midway(Bad idea...) hoping it would revert. But when i reinstalled everything...


It ended up 

-Trying to log in via gnome doesnt display the UI and ubuntu crashes as it opened(you can still shut down via power button though)

-I cant open the Gnome tweak tool using the unity layout(So im basically stuck using ) it just changes colours but window isnt showing anymore


I just wanted to pretty much forget the whole ordeal and revert everything in its default settings. but im stuck with a terrible UI in ubuntu(unity) and i cant access Gnome without spazzing itself. Assistance would be helpful..(im at work so ill do the solutions tonight) :(

---

### Post by HiImTye on 2012-06-19
log into Ubuntu using Unity then open a terminal and enter
```
gnome-shell --replace
```
it should output some errors giving you an idea of what to fix

---

### Post by Keral on 2012-06-20
Gevening sorry for the late reply.

I tried the code but it causes the the terminal to crash for some reason and completely destroy the UI.

-I have docky, a black horizontal screen filled almost 1/3 of the screen

-The top and application launcher bars disappeared

-Any window opened are minimized and cannot be resized nor modified(as if it froze as well)

---

### Post by Keral on 2012-06-20
Ive been trying to find any solutions in an hour and nothing, as much as possible im avoiding to use the terminal before i cause any more damage. Tried to input the code as well, it still crashes the same way sorry. x___x

as much as possible i just want to restore everything back to normal without reformatting(last resort...).

---

### Post by Keral on 2012-06-20
A quick update

I reinstalled both the gnome tweak and shell properly. Gnome tweak is still unresponsive, but i managed to access the gnome UI via log in and it feels responsive so far.

Used code mentioned in ubuntu(unity) and it pointed out an error to /usr/bin/gnome-shell with via "force close"

I hope this helps.

---

### Post by HiImTye on 2012-06-20
GS refusing to open is usually indicative of user extensions that are broken or not properly installed. check to see if there are any errors that point to your home folder.

better yet, run this command. it will make a log and you can attach that log to your reply
```
unity --repace > $HOME/Desktop/GSOutput.log
```
once youre confident that it has fully crashed, hit Ctrl+C and then type the following to switch back to Unity:
```
Unity --replace
```
then attach the log that is output to your desktop to your next reply

---

### Post by Keral on 2012-06-21
> **HiImTye said:**
> GS refusing to open is usually indicative of user extensions that are broken or not properly installed. check to see if there are any errors that point to your home folder.

better yet, run this command. it will make a log and you can attach that log to your reply
```
unity --repace > $HOME/Desktop/GSOutput.log
```
once youre confident that it has fully crashed, hit Ctrl+C and then type the following to switch back to Unity:
```
Unity --replace
```
then attach the log that is output to your desktop to your next reply

Hello :)

Sorry the analysis was getting exceedingly long and the log file was getting repetitive so i have to cut it(ill still keep it long though), since it didnt crash(fortunately) i wont be doing the second one then. But heres the GS log file :)

---

