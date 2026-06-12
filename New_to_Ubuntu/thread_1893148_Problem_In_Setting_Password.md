---
title: "Problem In Setting Password"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by Ashish_net on 2011-12-09
Sir, I am running ubuntu since last 6 months I am beginner to Linux OS but not very new, I am facing a very streng and irritating problem in my ubuntu 11.10 that ..

  WheneverI try to set Password of my ubuntu machine ... it gives me error that I have used wring syntax

Syntax I use is

sudo passwd <user_name> <new_password>


----
Actually It used to work fine in 11.04 but then I installed PAM Face-Recognization for using my face as my password ... initially it was working perfectly. But then I came to know ubuntu released itz 11.10 ver so I updated my os to 11.10 ... everything was fine but later I discovered that MY PAM face recognization is not working in ubuntu 11.10, so I tried to remove it but I could not remove it completely and during while something went wrong by my hands and since then I am not able to set password ..

Even I tried to use only : sudo passwd

But it says:
password updated successfully
---

But how can the password get updated without even entering it ?

Plz :( help me frndz....thanx in advance

---

### Post by collisionystm on 2011-12-09
sudo passwd <username>

it will prompt for you to enter a new unix password

---

### Post by mcduck on 2011-12-10
If you are already logged in as the user who's password you wish to change, then you don't need "sudo" or to specify the user name in the command. So the correct syntax would be as simple as this:
```
passwd
```

...also trying to run "sudo passwd" could very well have caused at least some of your problems, as doing that would set root password, while most of the tools in Ubuntu are configured to assume administration through the use of sudo instead. You can disable the root account again using this command:
```
sudo passwd -dl root
```

---

### Post by Ashish_net on 2011-12-10
Thank u guys for your immidiate replays but the soultions which u you guys are suggesting are already tried by me ...

When I use

sudo passwd <username>

It gives me o/p As

passwd: password updated successfully

[it do not prompt me for entering new password]

----

And when I try [without sudo]

passwd

It still gives me same o/p:
passwd: password updated successfully


I tried to use both d above comands even after using
sudo passwd -dl root

and I got o/p :[FONT=monospace] passwd: password expiry information changed.

But still problem persists continue as it was 


[/FONT]

---

### Post by collisionystm on 2011-12-10
No!! 

You do

Sudo passwd username

I.e sudo passwd Charles


Jeez.....

---

### Post by lolpenguin on 2011-12-10
> **collisionystm said:**
> No!! 

You do

Sudo passwd username

I.e sudo passwd Charles


Jeez.....

Did you read the post #4?
The usual output should be:
```
user@ubuntu:~sudo passwd user2
[sudo] password for user:
Enter new UNIX password:
Retype new UNIX password:
passwd: Password updated successfully
```

---

### Post by Ashish_net on 2011-12-11
Yes I know what should be my usual o/p, And I am not geting tat output (itz the problem) : And I am using exactly same sysntax, and I am damm sure itz not problem of syntax .. Becasuse same thing used to to work before ... But itz not working since the day I made few unusual changes with my notebook....

My user name is 'point'

so Im using sudo passwd point

Is there any way by which I can reset all my password related settinngs and files I mean these all things are due to what I have done wrongs or incompletae changes in my system

---

### Post by WasMeHere on 2011-12-11
Hi Ashish_net alias point :-)

Strange problem! I know cases when [FONT="Courier New"][SIZE="3"]passwd[/SIZE][/FONT] works while the GUI *users-admin* doesn't. One example is when I made a persistent USB boot stick and wanted a password for the default user.

Try this easy one: Could it be that it wants a longer new password (try with at least 8 characters)?

If it doesn't work, then you have to repair your login system. What about backup? Do you have a fairly recent backup of the system or at least of your personal files (documents, pictures, videos, music ...)?

Then maybe you dare remove and reinstall passwd.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge passwd
sudo apt-get install passwd
```

Let us hope that someone else can fill in here and suggest other things to reinstall!

---

### Post by lolpenguin on 2011-12-12
Hmm...you might have to run it from a different user account. When I change passwords I do it from root...but with sudo it should already be root...
Or try it without sudo, since it's your own account.

---

### Post by Ashish_net on 2011-12-12
ok ... Guys I do try to remove and reinstall passwd again as mentioned By olle wukllund
sudo apt-get update sudo apt-get upgrade sudo apt-get purge passwd sudo apt-get install passwdand yes, dear lolpenguine thanx 4 ur interest in my prob bt ur solution is already tried by me so feeling sory to say itz not not working

---

### Post by Ashish_net on 2011-12-13
no it did nt work still everythings is as it was ...

---

### Post by CoffeeRain on 2011-12-13
If you are logged in as yourself, and you just type passwd, it should work. Have you tried ```
which passwd
```Mine is in /usr/bin/passwd. In the man page it says that the -i option specifies which system to use, and the -l option specifies the location. You could try ```
passwd -l /etc/master.passwd
``` even though that is the default, it could have gotten changed.

---

### Post by Ashish_net on 2011-12-14
> **CoffeeRain said:**
> If you are logged in as yourself, and you just type passwd, it should work. Have you tried ```
which passwd
```Mine is in /usr/bin/passwd. In the man page it says that the -i option specifies which system to use, and the -l option specifies the location. You could try ```
passwd -l /etc/master.passwd
``` even though that is the default, it could have gotten changed.
when I used: which passwd

I got o/p As : /usr/bin/passwd

So it seems locatioin is also perfect as it should by default

---

### Post by CoffeeRain on 2011-12-14
Did you try ```
passwd -l /etc/master.passwd
```

---

### Post by Ashish_net on 2011-12-17
> **Ashish_net said:**
> ok ... Guys I do try to remove and reinstall passwd again as mentioned By olle wukllund
sudo apt-get update sudo apt-get upgrade sudo apt-get purge passwd sudo apt-get install passwdand yes, dear lolpenguine thanx 4 ur interest in my prob bt ur solution is already tried by me so feeling sory to say itz not not working

---

Ow Gr8 :)I found solution , Problem was due to that cancer software PAM-FACE recognization

I removed that using

sudo pam-auth-update --package face_authentication
sudo rm /usr/share/pam-configs/face-authentication
sudo apt-get remove pam-face-authentication




Now all my commmands are working perfectly :guitar::P

---

