---
title: "Have been trying for hours, any help for aircrack? I've tried EVERYTHING"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Abyssal Whim on 2012-11-18
Ok, so like the title says, I've been having a LOT of issues trying install aircrack-ng. I'm also having issues installing...well, anything. But that's a separate thread anyways.

Ok, so first off, I am new to the whole ubuntu scene. Or, to be more accurate, the linux scene. I've read numerous other threads, and tried following the directions of others who are ill fated with the same problem. What I have tried:

[FONT=Arial][SIZE=2]"sudo apt-get install build-essential
sudo apt-get install libssl-dev[/SIZE][/FONT][FONT=Arial][SIZE=2] 
wget [http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz) 
tar -zxvf aircrack-ng-1.1.tar.gz 
cd aircrack-ng-1.1 

In  the aircrack-ng-1.1 directory there is a file called common.mak, use  your favorite editor to open the file and scroll down till you see the  following line:  

CFLAGS ?= -g -W -Wall -Werror -O3  

Delete the -Werror variable, so that the line now looks like the following. Save and exit.  

CFLAGS ?= -g -W -Wall -O3  

Run make and make install to get aircrack-ng up and running.  

[/SIZE][/FONT]    [FONT=Arial][SIZE=2]try :[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]sudo make[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]and then :[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]sudo make install"

[SIZE=2]But every time I do so, I get an error[SIZE=2]:

"
[*] Run 'airodump-ng-oui-update' as root (or with sudo) to install or update Airodump-ng OUI file (Internet connection required).[SIZE=2]"

[SIZE=2]How do I get [SIZE=2]past this? [SIZE=2]I'm sure it's probably something I've overlooked, [SIZE=2]or something, but any help would [SIZE=2]be MUCH appreciated at this point. 


Note: Just using it to fu[SIZE=2]r[SIZE=2]ther my own knowledge[SIZE=2].

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by MG&amp;TL on 2012-11-18
Is there a good reason for you to compile aircrack?

If not:

```
sudo apt-get install aircrack-ng
```

---

### Post by GreatDanton on 2012-11-18
I think it's called aircrack-ng
```
sudo apt-get install aircrack-ng
```

You can also install it via Software center.

---

### Post by Abyssal Whim on 2012-11-18
I thought that'd work originally, but when I do try that, I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack

Which its preposterous, as I must have downloaded it at least 50 times by now...

---

### Post by Abyssal Whim on 2012-11-18
Also, I have tried aircrack, aircrack-ng, aircrack-ng-1.1.tar.gz, and they all end up doing the same thing on the end command. At this point, I am vexed. I keep trying to do SOMETHING about the issue with the airdump-ng, but so far, nothing has worked.

---

### Post by MG&amp;TL on 2012-11-18
> **Abyssal Whim said:**
> I thought that'd work originally, but when I do try that, I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack

Which its preposterous, as I must have downloaded it at least 50 times by now...

My bad, I got the wrong package name.

What happens when you try:

```
sudo apt-get install aircrack-ng
```

?

Btw, you might want to read up on package management: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) - whether you've downloaded something or not makes no difference whatsoever.

---

### Post by Abyssal Whim on 2012-11-18
> **MG&TL said:**
> My bad, I got the wrong package name.

What happens when you try:

```
sudo apt-get install aircrack-ng
```?

Btw, you might want to read up on package management: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) - whether you've downloaded something or not makes no difference whatsoever.

Sadly, the exact same thing. I figure I must have done SOMETHING wrong in my attempts at organizing the new system and messed up something I shouldn't have.

---

### Post by MG&amp;TL on 2012-11-18
I'm guessing you've managed to break APT somehow. Okay, try:

```
sudo apt-get update
```

Post the output and see if this fixes anything.

---

### Post by Abyssal Whim on 2012-11-18
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
aircrack-ng is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

I'm not QUITE sure if this means success, but I'm putting my money more on "no." Also, thank you for the patience. And to think I used to be so tech savvy. Now it seems I'm a noob again. ^_^

---

### Post by GreatDanton on 2012-11-18
I would try with Ubuntu software center. Type aircrack into search bar and let us know what you get.

---

### Post by MG&amp;TL on 2012-11-18
> **Abyssal Whim said:**
> "Reading package lists... Done
Building dependency tree       
Reading state information... Done
aircrack-ng is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

I'm not QUITE sure if this means success, but I'm putting my money more on "no." Also, thank you for the patience. And to think I used to be so tech savvy. Now it seems I'm a noob again. ^_^

In which case you appear to already have it. Well done! Now, what happens if you type:

```
aircrack-ng
```

?

---

### Post by Abyssal Whim on 2012-11-18
> **GreatDanton said:**
> I would try with Ubuntu software center. Type aircrack into search bar and let us know what you get.

That's actually where I started first, before trying to delve in myself. I couldn't get it to open up after I did it through there either. I keep wondering if maybe I just don't have something downloaded that I need or something. :/

---

### Post by Abyssal Whim on 2012-11-18
Wow....I feel rather stupid at the moment. Thank you very much! For some reason, I was more expecting some form of interface or something.... ^.^;;

---

### Post by coffeecat on 2012-11-18
Aircrack is not supported on these forums - thread closed.

**If** you have an ethical reason for wanting to use aircrack, then you would be better off with Backtrack and support on the Backtrack forums.

---

