---
title: "apt-get not working among other issues"
date: 2017-05-17
forum: New to Ubuntu
---

### Post by adhdluke on 2017-05-17
I attempted to install Spotify on Ubuntu 16.04 MATE
After what I did, it goes as far to tell me:

E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list
E: The list of sources could not be read.

I don't know how to fix this. I saw someone use some command called gedit, but I get the same error. 
I'm new to Linux, please help.

EDIT: Problem solved.

---

### Post by cc1984 on 2017-05-17
How did you try to install it? You might try [this]("http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10") as described in OMG!Ubuntu. It's not Unity in the example not Mate but should basically work the same.

---

### Post by deadflowr on 2017-05-17
Open a terminal and run 
```
cat /etc/apt/sources.list.d/spotify.list
```
then copy it and post the output here in this thread you started.
It's saying you have an error in that file, it seems like you added sudo into the file and it's causing the problem.

---

### Post by Bashing-om on 2017-05-17
adhdluke; Hello - Welcome to the forum .

I can not imagine how that line could have become malformed in such a manner.
Post back - Between code tags - the output of terminal command:
```

cat /etc/apt/sources.list.d/spotify.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and we fire up that text editor and fix the file ; as it must be in a specific format .. and sudo is not in that format !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by adhdluke on 2017-05-17
I did that. I think I see where I went wrong, but i don't know how to fix it.
When I was installing Spotify, where it wanted me to add the repository, the part where you type stuff in the terminal went blank. I dismissed it and tried to continue with the next step in installing Spotify, where the guide told me to do sudo apt-get update

So uh, here is the output from the command line:
sudo apt-get update
sudo apt-get update


That's it.

---

### Post by Bashing-om on 2017-05-17
adhdluke; Hey ..

Slow down and think ... read .
We asked to see the file so we can guide you to fix it .
```

cat /etc/apt/sources.list.d/spotify.list

```

By the way, what release is this ?
Is there a reason, as a new user, that you do not use the binary of skype provided in our software repository ?
> 
 sysop@x1604:~$ apt list skype
Listing... Done
skype/xenial 4.3.0.37-0ubuntu0.12.04.1 amd64
sysop@x1604:~$


[INDENT][INDENT]do as we can do
[/INDENT][/INDENT]

---

### Post by adhdluke on 2017-05-18
I don't understand the thing about Skype you just said. But when I run ```
cat /etc/apt/sources.list.d/spotify.list
``` the output from the console is 
sudo apt-get update
sudo apt-get update

I am running Ubuntu MATE 16.04 LTS

---

### Post by deadflowr on 2017-05-18
Remove the file.
It's wrong.
Easier to remove than try and edit it.
This line will remove the file
```
sudo rm /etc/apt/sources.list.d/spotify.list
```
Did you follow a guide to install spotify?
Could you add a link to it here.
So we can help properly add the spotify archives.

---

### Post by adhdluke on 2017-05-18
[https://www.spotify.com/us/download/linux/](https://www.spotify.com/us/download/linux/)
That's where I tried to get it.
```
 sudo rm /etc/apt/sources.list.d/spotify.list 
```
That also seems to have worked. apt-get update works fine now.

---

### Post by deadflowr on 2017-05-18
Okay to get spotify you need to do this in this order:
add the key
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
```
then add the archive,
```
echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
```
then run,
```
sudo apt-get update
```
thern install the spotify package,
```
sudo apt-get install spotify-client
```
that should be it.
Post if at any point it errors.

---

### Post by adhdluke on 2017-05-18
That worked! I have my terminal fixed and Spotify installed. Thanks!

---

### Post by deadflowr on 2017-05-18
cool
if you feel this issue has been fixed, please feel free to mark this thread as solved, so that others may happen upon it if they too get stuck
[How to mark a thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by howefield on 2017-05-18
Just as a for your information.. the spotify linux client is more than a couple of years old and unsupported, if it stops working or you have trouble with it there is always the webplayer at [https://play.spotify.com](https://play.spotify.com)

---

