---
title: "I'm a newbie"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by DogDragonsm31 on 2008-07-18
Hi, I Just put Ubuntu on a machine and I want to put
realplayer on. I know it has apps to veiw videos,
But I have a membership to the realplayer superpass for
BigBrother.
So how do I put it on Ubuntu?
I had a membership to your forum for awhile cause I was
going to put it on a machine before, But it kept freezing
trying to do the update.
So I tried it again with 8,04 and the updates went with
no problems. So I'm going to try this for awhile, You know
take it for a test drive. :)
Thanks for looking and Thanks for any help :)

---

### Post by overdrank on 2008-07-18
> **DogDragonsm31 said:**
> Hi, I Just put Ubuntu on a machine and I want to put
realplayer on. I know it has apps to veiw videos,
But I have a membership to the realplayer superpass for
BigBrother.
So how do I put it on Ubuntu?
I had a membership to your forum for awhile cause I was
going to put it on a machine before, But it kept freezing
trying to do the update.
So I tried it again with 8,04 and the updates went with
no problems. So I'm going to try this for awhile, You know
take it for a test drive. :)
Thanks for looking and Thanks for any help :)

HI and welcome and I would start here
[https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)

---

### Post by DogDragonsm31 on 2008-07-18
ok Thanks

---

### Post by hyper_ch on 2008-07-18
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by sharks on 2008-07-18
+1 for hyper_ch

---

### Post by bhadotia on 2008-07-18
Please mark the thread as solved if you have solved your problem- to do that use thread tools on the top right corner.
Cheers!

---

### Post by sharks on 2008-07-18
and please thank the person who helped u by pressing the star button at his end of post.

---

### Post by hyper_ch on 2008-07-18
> **sharks said:**
> and please thank the person who helped u by pressing the star button at his end of post.

Thank only if you feel it appropriate ;) there is no obligation or "must" to do so :)

---

### Post by Canis familiaris on 2008-07-18
> **hyper_ch said:**
> thank Only If You Feel It Appropriate ;) There Is No Obligation Or "must" To Do So :)
+1

---

### Post by DogDragonsm31 on 2008-07-18
Ok I'm lost Like I said I'm a newbie but this is what happen
root@sm31-desktop:/home/sm31# $ sudo aptitude install libstdc++5
bash: $: command not found
root@sm31-desktop:/home/sm31# $ cd ~/desktop
bash: $: command not found
root@sm31-desktop:/home/sm31# $ sudo ./RealPlayer11GOLD.bin
bash: $: command not found
root@sm31-desktop:/home/sm31# 

so I'm doing something wrong, But don't know what
and realplayer is on my desktop

---

### Post by bhadotia on 2008-07-18
> **DogDragonsm31 said:**
> Ok I'm lost Like I said I'm a newbie but this is what happen
root@sm31-desktop:/home/sm31# $ sudo aptitude install libstdc++5
bash: $: command not found
root@sm31-desktop:/home/sm31# $ cd ~/desktop
bash: $: command not found
root@sm31-desktop:/home/sm31# $ sudo ./RealPlayer11GOLD.bin
bash: $: command not found
root@sm31-desktop:/home/sm31# 

so I'm doing something wrong, But don't know what
and realplayer is on my desktop
This is because you are using the $ in front of very command .  When you run 'sudo su', the $ is replaced by the # , so that now you don't need the 'sudo' in front of 'aptitude install libstdc++5' or './RealPlayer11GOLD.bin'. I think you forgot about the 'chmod +x ..'.
$ basically means you are logged in as a normal user and can't perform administrative tasks such as installing software (like you are doing at present)- only super user can do such tasks. So we use the sudo command to log-in as superuser (su) temporarily and do admin work. But by doing sudo su we log in as superuser permanently for the terminal session and that is indicated by the #.
If you don't understand anything, please ask.

---

### Post by vikramaditya on 2008-07-18
> **DogDragonsm31 said:**
> I have a membership to the realplayer superpass for
BigBrother.
My, that sounds disturbing. :???:  Are you sure Big Brother isn't watching?

---

### Post by overdrank on 2008-07-18
> **DogDragonsm31 said:**
> Ok I'm lost Like I said I'm a newbie but this is what happen
[COLOR="Red"]root@sm31-desktop:[/COLOR]/home/sm31# $ sudo aptitude install libstdc++5
bash: $: command not found
root@sm31-desktop:/home/sm31# $ cd ~/desktop
bash: $: command not found
root@sm31-desktop:/home/sm31# $ sudo ./RealPlayer11GOLD.bin
bash: $: command not found
root@sm31-desktop:/home/sm31# 

so I'm doing something wrong, But don't know what
and realplayer is on my desktop

Hi and it appears you are already root. Did you sudo i or sudo su to become root in the terminal?
Edit to slow and looks like you have the help and it is time for sleep. :)

---

### Post by nikloleta on 2008-07-18
these posts are very good for me too! Thanks guys!

---

### Post by DogDragonsm31 on 2008-07-18
> **bhadotia said:**
> This is because you are using the $ in front of very command .  When you run 'sudo su', the $ is replaced by the # , so that now you don't need the 'sudo' in front of 'aptitude install libstdc++5' or './RealPlayer11GOLD.bin'. I think you forgot about the 'chmod +x ..'.
$ basically means you are logged in as a normal user and can't perform administrative tasks such as installing software (like you are doing at present)- only super user can do such tasks. So we use the sudo command to log-in as superuser (su) temporarily and do admin work. But by doing sudo su we log in as superuser permanently for the terminal session and that is indicated by the #.
If you don't understand anything, please ask.

Ok I tried a couple times and still messing up. So I think I have to be spoon feed.
So I'm going to the beginning and start at [http://ubuntuforums.org/showthread.php?t=848814](http://ubuntuforums.org/showthread.php?t=848814)
and read the post there and try to get a handle on what I doing.
I know Linux is better than windows, But it is going to take me a 
little to learn how to use it.
Sorry windows spoiled me so now I have to learn the right way.
I'll deal with realplayer at a later time.
Thanks for the help But I have to start with baby steps.
I not going to give up did that the last time this time I will
get a working idea on how to use this OS.

---

### Post by overdrank on 2008-07-18
> **DogDragonsm31 said:**
> Ok I tried a couple times and still messing up. So I think I have to be spoon feed.
So I'm going to the beginning and start at [http://ubuntuforums.org/showthread.php?t=848814](http://ubuntuforums.org/showthread.php?t=848814)
and read the post there and try to get a handle on what I doing.
I know Linux is better than windows, But it is going to take me a 
little to learn how to use it.
Sorry windows spoiled me so now I have to learn the right way.
I'll deal with realplayer at a later time.
Thanks for the help But I have to start with baby steps.
I not going to give up did that the last time this time I will
get a working idea on how to use this OS.

Yea look at the sticky's and read and ask questions. It will take a little time and once you get it going your way it's great. :)

---

### Post by bhadotia on 2008-07-18
> **DogDragonsm31 said:**
> Ok I tried a couple times and still messing up. So I think I have to be spoon feed.
So I'm going to the beginning and start at [http://ubuntuforums.org/showthread.php?t=848814](http://ubuntuforums.org/showthread.php?t=848814)
and read the post there and try to get a handle on what I doing.
I know Linux is better than windows, But it is going to take me a 
little to learn how to use it.
Sorry windows spoiled me so now I have to learn the right way.
I'll deal with realplayer at a later time.
Thanks for the help But I have to start with baby steps.
I not going to give up did that the last time this time I will
get a working idea on how to use this OS.

Alright but first lets us get your realplayer working:). I will now try to explain it from the beginning:
[LEFT]1. Open a  **fresh  **terminal (this means new terminal window) (Applications>Accessories>Terminal) and copy and paste the following command:
```
sudo aptitude install libstdc++5
```2. Now I think you already have the RealPlayer11GOLD.bin , so place it on your desktop and in the terminal do this (just copy and paste):
```
cd ~/Desktop
```3. Now this:
```
chmod a+x RealPlayer11GOLD.bin
```[/LEFT]

4. And finally:
```
sudo ./RealPlayer11GOLD.bin
``` You should now see the RealPlayer 11 in the Applications>Sound & Video. If it still does not work put your error here. If it does work go to preferences in tools menu in RealPlayer and configure it .

---

### Post by DogDragonsm31 on 2008-07-18
> **bhadotia said:**
> Alright but first lets us get your realplayer working:). I will now try to explain it from the beginning:
[LEFT]1. Open a  **fresh  **terminal (this means new terminal window) (Applications>Accessories>Terminal) and copy and paste the following command:
```
sudo aptitude install libstdc++5
```2. Now I think you already have the RealPlayer11GOLD.bin , so place it on your desktop and in the terminal do this (just copy and paste):
```
cd ~/Desktop
```3. Now this:
```
chmod a+x RealPlayer11GOLD.bin
```[/LEFT]

4. And finally:
```
sudo ./RealPlayer11GOLD.bin
``` You should now see the RealPlayer 11 in the Applications>Sound & Video. If it still does not work put your error here. If it does work go to preferences in tools menu in RealPlayer and configure it .

But it looks like a basic media player.
Not what I'm use to, I download the file for the superpass
and saved it to my desktop. But when I open it says
" the player does not have the capabilities to play back this 
content," I tried to check for updates and it takes me back
to when I download realplayer from.
So If I can get to the sign in part I think it will work.
but now I'm lost again

---

### Post by DogDragonsm31 on 2008-07-18
Ok I took the update and it was realplayer 10-5GOLD.exe
and tried to install it and got this
[sudo] password for sm31:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
sm31@sm31-desktop:~$ cd ~/Desktop
sm31@sm31-desktop:~/Desktop$ chmod a+x RealPlayer10-5GOLD.exe
sm31@sm31-desktop:~/Desktop$ sudo ./RealPlayer10GOLD.exe
sudo: ./RealPlayer10GOLD.exe: command not found
sm31@sm31-desktop:~/Desktop$ chmod a+x RealPlayer10-5GOLD.exe
sm31@sm31-desktop:~/Desktop$ sudo ./RealPlayer10-5GOLD.exe
./RealPlayer10-5GOLD.exe: 1: MZ&#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;: not found
./RealPlayer10-5GOLD.exe: 2: Syntax error: word unexpected (expecting ")")
sm31@sm31-desktop:~/Desktop$

---

### Post by DogDragonsm31 on 2008-07-18
Ok I called RealPlayer support 
I told them that Realplayer 11 is install, But I can't 
sign into it.
RealPlayer support said " Ubuntu is not a compatible OS
for realplayer"
I said it's installed and does play
They said "yes but it doesn't allow all the tabs in realplayer to show
so you won't be able to sign in."
So I just watch it on my Laptop. 
No biggie just one less thing that will be put on my machine.
Just letting you know what realplayer support said.

---

