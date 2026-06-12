---
title: "permission denied and unable to do anything in terminal"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by kewinh0727 on 2013-02-17
hey i got a really big problem! i have dualbooted windows 7 and ubuntu 12.04

2 partition for the windows 7 OS and 2 partitions for ubuntu where i have 4096MB for swap and 130GB for ubuntu..

its a bit laggy when im dragging windows around the desktop ... but that is ot my main problem right now..

the problem is that i cant do anything in the terminal...  i can't open

/etc/apt/sources.list to edit so i can install spotify... it only says permission denied.

and when im trying to log in as root through

su

is says Authenicating Failure.

i have no idea why it is like that... when i used 10.04 i didnt have that problem at all so im wondering why now in 12.04 ? thnx.

---

### Post by snowpine on 2013-02-17
Welcome to the forums!

In Ubuntu we use 'sudo' (not 'su'), for example:

```
sudo nano /etc/apt/sources.list
```

Be **very** careful editing this important system file! A significant % of support requests on these forums relate to mangled sources.list problems.

---

### Post by kewinh0727 on 2013-02-17
> **snowpine said:**
> Welcome to the forums!

In Ubuntu we use 'sudo' (not 'su'), for example:

```
sudo nano /etc/apt/sources.list
```Be **very** careful editing this important system file! A significant % of support requests on these forums relate to mangled sources.list problems.

i know that we use sudo :)

it was just an example... so why can't i log in to su in terminal ?

and thanx i finaly got into the ''list'' :)..

---

### Post by snowpine on 2013-02-17
'su' is disabled in Ubuntu. We use 'sudo' instead. The comparable command to 'su' is:

```
sudo -i
```

More info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kewinh0727 on 2013-02-18
hey im new to this forum and pretty new in ubuntu. i have used ubuntu 10.04 lts just a little bit.

well now i have a little problem...  i feel lika i have more administrator acces if you can call it that, when im typing commands in the terminal i was able to do more things in 10.04 lts but now in 12.04.2 i can't to much at all i cant for example install spotify like the exact way i did in 10.04 i feel locked down or something or is it supposed to be like this ?

plz tell me if it has changed or anything and which codes i can type to like get ''permission acces'' because now all i get is permission denied and no file or directory and so on.. 

thnx !

---

### Post by QIII on 2013-02-18
***Threads merged.***

Please do not start new threads on the same topic.  In this case, it would have been better to simply bump this thread by adding another post with a simple message like "bump".

However, don't bump more often than once in 24 hours.

Thanks.

---

### Post by kewinh0727 on 2013-02-18
> **QIII said:**
> ***Threads merged.***

Please do not start new threads on the same topic.  In this case, it would have been better to simply bump this thread by adding another post with a simple message like "bump".

However, don't bump more often than once in 24 hours.

Thanks.

yeah i was looking for the first one but i couldnt find it :/ thnx ^^and sorry

---

### Post by QIII on 2013-02-18
No problem.

If you want to find your previous posts, use the "Search" button in the tool bar and select "Find All Your Posts."

Good luck with your issue!

---

### Post by rnerwein on 2013-02-18
> **kewinh0727 said:**
> i know that we use sudo :)

it was just an example... so why can't i log in to su in terminal ?

and thanx i finaly got into the ''list'' :)..
hi
for using "su" in a terminal:
1. type sudo -i (gives you a root shell)
2. passwd root (give root a password)
3. now you can run su in a terminal
ciao

---

### Post by ooleyguy on 2013-02-18
You can temporarily become su by typing sudo su in the terminal. You will keep root access (so far as I can tell) as long as you keep that terminal open.
 
Not exactly sure you really need to do that. I've only been using linux and ubuntu for two weeks and typing the 4 letter phrase sudo has become second nature, just like slamming my hands on my keyboard every time windows did something stupid did. sudo doesn't ask for your PW every time. I guess it knows that you are the same user that was using sudo 5 seconds ago.

---

### Post by sudodus on 2013-02-18
Use sudo when you want to perform administration tasks. Do not use it when it is not necessary. Do not leave a terminal window or a browser with administration privileges when the task has finished, because of the risk of destroying the system or removing files by mistake.

---

### Post by kewinh0727 on 2013-02-18
sorry for being so slow in understanding xD.. is it supposed to be like this that i cant do as much in terminal im going crazy in not understadning why

it feel more open to use terminal in 10.04 and in 12.04 i cant..

i cna install spotify in 10.04 and i CAN't in 12.04 by the way that the spotify seite has its guide on the linux preview installing guide..

---

### Post by ooleyguy on 2013-02-18
I've never used Spotify myself, but a quick search on Google makes it appear that Spotify is a Windows/Mac program. Perhaps using Wine would work for you.

I don't know if this is the "Hoyle Rules" way of doing things, but so far in my Ubuntu usage, tweaking, etc., when I find something new I want to install that isn't located in the software center, these three steps are taken:

sudo add-apt-repository ppa:<some place on the net where the installation files are located>

sudo apt-get update to update your repository cache

sudo apt-get install <whatever program you are installing>

Doing it this way achieves at least two goals I am aware of:

1) When the author of the program releases an upgrade, Ubuntu will automatically see that and upgrade it for you with all the other upgrades of system and Ubuntu supported software.

2) Most repositories look like they've gone through a bit of inspection by the folks at launchpad, so you can be reasonably assured that the programs do not contain malware.

---

### Post by arpanaut on 2013-02-18
This should work:
[http://www.webupd8.org/2011/12/how-to-install-native-spotify-linux.html](http://www.webupd8.org/2011/12/how-to-install-native-spotify-linux.html)

---

