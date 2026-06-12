---
title: "launcher not found"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by CycloneChen on 2012-04-23
hello,everybody ,i am a freshman . yesterday ,i used the wubi to install the ubuntu11.10 , which selected the ubuntu desktop environment ,on F disk. it went without any error. after it finished,i restart my pc,then came the welcome interface. but ,here ,i can't see the input field for login account or password, then i press the ctrl+alt+f1, enter the command_line and then run the "sudo apt-get update && sudo apt-get upgrade" ,at last ,4 packages fail to update..(can't remenber exactly what are they now)

then i swicth back to the xwindows.here ,i can't see the launcher, but a bar including the "file","edit","go","bookmarks","help" on the top of the  screen.

anybody can tell me what happened ,how can i solve it ?? thx

---

### Post by d4m1r on 2012-04-23
1) Welcome to Ubuntu!

2) Can you get us the specific name of those packages that won't update? apt-get update was a good try, but those 4 packages are probably related to your problem.

---

### Post by NikTh on 2012-04-23
hello , 
wubi its not good choice. Ubuntu not works well under a fully restricted operating system as MS windows. I know that is just for testing the Ubuntu , a virtual install , but the best choice to test Ubuntu is via liveCD. (IMHO). 
First time i tested Ubuntu was via wubi. Disappointed. To slow , to crashy . 
Second time was via LiveCD . Surprised !! to fast and stable. 
I decided to install it alongside widows. Yes i surprised more ! From speed , responsive , shutdown and startup speed. 
Today windows are only for games in my machine. 

If i didn't convince you to switch on dual-boot with windows , then
from virtual terminal (ctrl+atl+F2) try following commands 
```
sudo service lightdm stop 
sudo dpkg --configure -a 
sudo apt-get install -f 
sudo service lightdm start
``` 
if problem not solved then from desktop enviroment , open terminal (ctrl+alt+t) and try this 
```
unity --reset
``` 

good luck :)

---

### Post by CycloneChen on 2012-04-23
> **d4m1r said:**
> 1) Welcome to Ubuntu!

2) Can you get us the specific name of those packages that won't update? apt-get update was a good try, but those 4 packages are probably related to your problem.

hn ,seems that it start with "ib"

---

### Post by CycloneChen on 2012-04-24
> **NikTh said:**
> hello , 
wubi its not good choice. Ubuntu not works well under a fully restricted operating system as MS windows. I know that is just for testing the Ubuntu , a virtual install , but the best choice to test Ubuntu is via liveCD. (IMHO). 
First time i tested Ubuntu was via wubi. Disappointed. To slow , to crashy . 
Second time was via LiveCD . Surprised !! to fast and stable. 
I decided to install it alongside widows. Yes i surprised more ! From speed , responsive , shutdown and startup speed. 
Today windows are only for games in my machine. 

If i didn't convince you to switch on dual-boot with windows , then
from virtual terminal (ctrl+atl+F2) try following commands 
```
sudo service lightdm stop 
sudo dpkg --configure -a 
sudo apt-get install -f 
sudo service lightdm start
```if problem not solved then from desktop enviroment , open terminal (ctrl+alt+t) and try this 
```
unity --reset
```good luck :)


thank you so much !  i tried as you said ,reconfiguring the lightdm, but after i run the first comand, sys turned into the command_line interface and stay there for almost 20 mins,....can't stand any more~ then i restart pc,and tried the " unity --reset", it worked ! now ,the launcher shows up again~~ thx, NikTh:guitar:

---

