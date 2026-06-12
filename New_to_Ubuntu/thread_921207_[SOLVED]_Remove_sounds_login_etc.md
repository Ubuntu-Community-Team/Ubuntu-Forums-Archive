---
title: "[SOLVED] Remove sounds login etc"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by ctoaun on 2008-09-16
How do I, "_*[SIZE="4"]step by step[/SIZE]*_," remove the login sounds from user/sounds/share?

1) **Please do not say Preferences>sounds>disable>restart.**  
   There are far too many post here & at Google that indicate that this 
   does not work. Moreover, it's never worked for me. I refuse to have to logoff in mute because it's my frigging 
   computer.

2) sudo chmod 777 /usr/share/sounds/error.wav
   **Does not work either.** 
   This came from this [post]("http://ubuntuforums.org/showthread.php?t=858351&highlight=delete+sounds"):
 

chmod comes back as unknown ID in Ubuntu 8.04, assuming the system even prompts for a password.

I absolutely hate, hate, hate computer sounds other than a "low battery warning."

thanks

---

### Post by iaculallad on 2008-09-16
What about deleting the wav files directly from the terminal?

```
sudo rm /usr/share/sounds/login.wav
sudo rm /usr/share/sounds/logout.wav
```

---

### Post by mike1234 on 2008-09-16
> **ctoaun said:**
> How do I, "_*[SIZE="4"]step by step[/SIZE]*_," remove the login sounds from user/sounds/share?

1) **Please do not say Preferences>sounds>disable>restart.**  
   There are far too many post here & at Google that indicate that this 
   does not work. Moreover, it's never worked for me. I refuse to have to logoff in mute because it's my frigging 
   computer.

2) sudo chmod 777 /usr/share/sounds/error.wav
   **Does not work either.** 
   This came from this [post]("http://ubuntuforums.org/showthread.php?t=858351&highlight=delete+sounds"):
 

chmod comes back as unknown ID in Ubuntu 8.04, assuming the system even prompts for a password.

I absolutely hate, hate, hate computer sounds other than a "low battery warning."

thanks

 If you uncheck your sound preferences "play system sounds" and disable "login" and "logout" sound file, I guarantee you won't hear them anyomre. Other than that I'm not quite sure what it is you're asking.

M.

---

### Post by ctoaun on 2008-09-16
> **mike1234 said:**
> If you uncheck your sound preferences "play system sounds" and disable "login" and "logout" sound file, I guarantee you won't hear them anyomre. Other than that I'm not quite sure what it is you're asking.

M.

From your words, you accurately gleaned what I was asking.
Your proposed solution is precisely what I and others have tried on multiple occasions. Bottom line unchecking boxes will always fail some people, the that I started this thread.

Since you guaranteed results, I want my money back. I paid zero dollars for Ubuntu, which means you owe me $23,461.03

Seriously though,
Thanks anyway

---

### Post by mike1234 on 2008-09-16
> **ctoaun said:**
> From your words, you accurately gleaned what I was asking.
Your proposed solution is precisely what I and others have tried on multiple occasions. Bottom line unchecking boxes will always fail some people, the that I started this thread.

Since you guaranteed results, I want my money back. I paid zero dollars for Ubuntu, which means you owe me $23,461.03

Seriously though,
Thanks anyway

 You'll have to talk to someone in customer service department. I'm just a cashier. :)

M.

---

### Post by ctoaun on 2008-09-16
> **iaculallad said:**
> What about deleting the wav files directly from the terminal?

```
sudo rm /usr/share/sounds/login.wav
sudo rm /usr/share/sounds/logout.wav
```

_This does not work either. The alleged error is that there is no such file or directory_

Is there away to become root?


sudo rm /usr/share/sounds/startup3.wav

sudo rm /usr/share/sounds/generic.wav

sudo rm /usr/share/sounds/info.wav

sudo rm /usr/share/sounds/logout.wav

sudo rm /usr/share/sounds/question.wav

sudo rm /usr/share/sounds/shutdown.wav

sudo rm /usr/share/sounds/shutdown1.wav

sudo rm /usr/share/sounds/startup.wav

sudo rm /usr/share/sounds/startup3.wav

sudo rm /usr/share/sounds/login.wav

Thanks though

Why the hell is this so difficult? Makes no sense
It should not be this difficult to delete some stupid sound files.

---

### Post by cariboo on 2008-09-16
I just tried Alt-F2:

```
gksu nautilus
```

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

---

### Post by ctoaun on 2008-09-16
> **cariboo907 said:**
> I just tried Alt-F2:

```
gksu nautilus
```

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

> **cariboo907 said:**
> I just tried Alt-F2:

```
gksu nautilus
```

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

I bet this would have worked.
I just followed you advice, and nautilus did let me create a folder in /usr/share/sounds, which is something it would not allow me to do before.

Had you posted earlier, All evidence indicates that this would've worked, so thanks

Apparently, since at least November 2005, for whatever reason or reasons, Ubuntu will complete ignore the "no sound choice" in "event sounds." There are literally 200,000 Google entries for "disable event or login/logout sounds in Ubuntu, obviously a huge bug problem.


[COLOR="Red"][SIZE="3"]However, here is another solution that works and worked for me:[/SIZE][/COLOR]

[SIZE="6"]**$ sudo apt-get remove ubuntu-sounds**[/SIZE]

[SIZE="4"]This problem is solved

thanks, everyone [/SIZE]

---

### Post by ctoaun on 2008-09-16
Did someone put a red "thumbs down" on this without having the courage to identify themselves or offer a better & more timely solution?  Cowardice is what some would call such actions. The solution does not harm the system or Ubuntu and it most definitely fixes a problem that has been ignored by Ubuntu for at least three year old problem, a problem shared by more than 100,000 Ubuntu users

---

### Post by billgoldberg on 2008-09-16
> **ctoaun said:**
> Did someone put a red "thumbs down" on this without having the courage to identify themselves or offer a better & more timely solution?  Cowardice is what some would call such actions. The solution does not harm the system or Ubuntu and it most definitely fixes a problem that has been ignored by Ubuntu for at least three year old problem, a problem shared by more than 100,000 Ubuntu users

What tumbs down?

There are multiple solutions in the thread on how to disable the system sounds.

What's the problem?

You are coming over a bit aggresive buddy. This is a forum of volunteers.

If you want to yell at someone because you have a problem with Ubuntu, stand in front a mirror.

Also, there is no need for the large text. Such things are agains the CoC, I believe.

---

### Post by ctoaun on 2008-09-16
**[SIZE="3"]Uhm...yeah..wow!? You've taken my words out of context**, and have construed negativity where there was none. [U]Did you read this thread, or did you just skim portions of it? Although I loathe to do so, on the off chance that there are a few others who are just as confused as you, I will explain all herein.[/SIZE] 
[/U]

> **billgoldberg said:**
> What tumbs down?



There is a little red "thumbs down" icon at response no# 8. Either, I am the only one who can see it, or you're the only one who can't see it.
I simply wanted to know who would put it there and not identify themselves. This is called being human and normal.

> **billgoldberg said:**
> ...

There are multiple solutions in the thread on how to disable the system sounds.

What's the problem?



I would think that the problem would be obvious since I identified the problem when I first posted this thread. *[SIZE="3"]Moreover, other than you,[/SIZE]* the response from others indicated that it was understood by several people. What was or is your problem? No matter,no need to risk a scrolling error, for your convenience, here is the original question, again. 


> **ctoaun said:**
> How do I, "_*[SIZE="4"]step by step[/SIZE]*_," remove the login sounds from user/sounds/share?

1) **Please do not say Preferences>sounds>disable>restart.**  
   There are far too many post here & at Google that indicate that this 
   does not work. Moreover, it's never worked for me. I refuse to have to logoff in mute because it's my frigging 
   computer.

2) sudo chmod 777 /usr/share/sounds/error.wav
   **Does not work either.** 
   This came from this [post]("http://ubuntuforums.org/showthread.php?t=858351&highlight=delete+sounds"):
 

chmod comes back as unknown ID in Ubuntu 8.04, assuming the system even prompts for a password.

I absolutely hate, hate, hate computer sounds other than a "low battery warning."

thanks

**Again, with the exception of you, all who responded understood me. What was or is your problem? Other than you, none reported feeling offended**


> **billgoldberg said:**
> ...

You are coming over a bit aggresive buddy. This is a forum of volunteers.



1) I thanked all who responded, and I even gave a brief explanation as to 
   why their solution did not work. This is called common courtesy by 
   most; however, apparently to you, common courtesy is a form of 
   aggression.

2) [B]In response 5, One person guaranteed that there solution would
    work. 
   When it failed, I jokingly replied that the guaranteeing party owed me 
   several thousand dollars since Ubuntu was free to me.

This person, user name Mike1234, responded in a joking fashion. If I was aggressive, would you please be so kind as to explain to him and I where & how I was I aggressive?
[/B]
3) **If you had read my thread you would have learned...**

> **ctoaun said:**
> 
...Apparently, since at least November 2005, for whatever reason or reasons, Ubuntu will complete ignore the "no sound choice" in "event sounds." There are literally 200,000 Google entries for "disable event or login/logout sounds in Ubuntu, obviously a huge bug problem...



**See? I quoted myself to make the following point:**

It is quite normal for one to be frustrated with a problem that should not exist; causes more than an hour's worth of work; annoys people by the thousands and has existed for years unfixed by Ubuntu.

Not once did I direct a negative comment towards a volunteer, yet you would have the audacity to imply otherwise? 

I make no apology for saying that if someone has the courage to place a "thumbs down" Icon on my response, they should have the morale fortitude to admit to doing it. This is called being human. 
  

> **billgoldberg said:**
> ...


Also, there is no need for the large text. Such things are agains the CoC, I believe.

According to the code of conduct, font and coloring may be used to highlight portions of a post. It is not to be used for an entire post.

Also again, according to the code of conduct, the maximum font size for signatures is "10." In other words, I shall continue to highlight as I deem necessary. See below

> **billgoldberg said:**
> ...

If you want to yell at someone because you have a problem with Ubuntu, stand in front a mirror.



[COLOR="Red"][SIZE="3"]First of all, I never implied a negative thought towards anyone much less yelled at anyone.[/SIZE][/COLOR]

**[SIZE="3"]Please refrain from making or implying indefensible accusations and or statements that are not supported by the context.[/SIZE]**

[COLOR="Red"]When people respond to forum threads at 4am EST, 8AM UTC, the hour of your response, it is not inconceivable that said person may have been under the inebriating influence of alcohol. If that describes you, then please cease and desist.[/COLOR] 

**I have thanked people on this forum even after they admitted to steering me in the wrong direction for hours.** God people make mistakes, and I could never attack such people. Honest mistakes are ok, but if thee desires to joust with me, then thy should come prepared.

[SIZE="4"]Regardless of what you do, for the sake of the forum of which you purport to care so much about, please refrain from making or implying indefensible accusations and or statements that are not supported by the context, much less the text. [/SIZE]

---

### Post by ctoaun on 2008-09-16
I just want to reiterate a heartfelt thanks to all who responded to this post with the intent to help. 
>
Read the post again and one will see that any expressed frustration was directed to the problem not the respondents.
>
Thank you

Obviously, this thanks is not extended to one person in particular, respondant #10.

---

### Post by shoot2kill on 2008-09-16
yeah.. good luck in getting an answer mate... :/

i know i got put off from helping out somewhere up there ^^^

---

### Post by dhtseany on 2008-09-16
Wow chill people. It's only an OS. God.

---

### Post by ctoaun on 2008-09-16
> **shoot2kill said:**
> yeah.. good luck in getting an answer mate... :/

i know i got put off from helping out somewhere up there ^^^

Actually, I received one very helpful answer.

Here it is  

Re: Remove sounds login etc
I just tried Alt-F2:

Code:

gksu nautilus

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

Also, this one, which came from Google

However, here is another solution that works and worked for me:

$ sudo apt-get remove ubuntu-sounds

This problem is solved

thanks, everyone

---

### Post by ctoaun on 2008-09-16
> **dhtseany said:**
> Wow chill people. It's only an OS. God.

Yeah, that's what I was thinking.
Then along came billgoldberg

---

### Post by ctoaun on 2008-09-16
> **mike1234 said:**
> You'll have to talk to someone in customer service department. I'm just a cashier. :)

M.

Noted LOL

---

### Post by shoot2kill on 2008-09-16
ok, so you can stop triple posting now, and mark as solved.

---

### Post by ctoaun on 2008-09-16
Actually, I received one very helpful answer.

Here it is

Re: Remove sounds login etc
I just tried Alt-F2:

Code:

gksu nautilus

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

Also, this one, which came from Google

However, here is another solution that works and worked for me:

$ sudo apt-get remove ubuntu-sounds

This problem is solved

thanks, everyone

---

### Post by dhtseany on 2008-09-16
> **ctoaun said:**
> Yeah, that's what I was thinking.
Then along came billgoldberg

Hahaha Bill Goldberg. That's just funny on it's own lol

---

### Post by ctoaun on 2008-09-16
**[COLOR=Red][SIZE=4]For those who see that this thread is marked as solved, here is the answer.[/SIZE][/COLOR]**

Sounds are located in /usr/share/sounds

when one goes to sound events, and deactivates sounds, sound is still heard at login. This has been an Ubuntu problem since at least November 2005.
You are not alone. 200,000 Google post about disabling sound in Ubuntu cannot be all wrong.

 Re: Remove sounds login etc
Actually, I received two very helpful answers.

Here it is

**Solution 1 of 2**
Re: Remove sounds login etc
I just tried Alt-F2:

Code:

gksu nautilus

and navigated to /usr/share/sounds, I deleted everything in the directory. I looged out, then back in agian. No login or logout sounds.

Jim

**Solution 2 of 2**, from Google

This solution that works and worked for me:

$ sudo apt-get remove ubuntu-sounds

This problem is solved

thanks, everyone

[I][COLOR=Lime]PS: ch mod 777 may not work, didn't for me.

Neither did sudo rm <filepath><name>[/COLOR][/I]

---

### Post by pumrum on 2008-10-28
hate to bump a dead horse but...

in Intrepid there's a new "guest user". any idea how to completely disable login/logout sounds ETC for the guest user? If you run **sudo apt-get remove ubuntu-sounds** in 8.10 it will also force you to uninstall **ubuntu-desktop**, which you obviously don't want to do.

> user@laptop:~$ sudo apt-get remove ubuntu-sounds
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  **ubuntu-desktop** ubuntu-sounds
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1147kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
user@laptop:~$


i've also been using the following to disable the login bongos (the 1sec clip that plays when the logon screen is ready)... is that what ya'll have been looking for? i mean... for every version through 7.10 i've used the following and my laptop never made a PEEP unless i told it to do so:

> Disable Annoying Ubuntu Sounds

---1. Click System > Preferences > Sound
---2. Click the Sounds tab
------1. Uncheck Play system sounds 
---3. Click the System Beep tab
------1. Uncheck Enable system beep 
---4. Click Close
[B]---5. Click System > Administration > Login Window
------1. Click the Accessibility tab
------2. Uncheck Login screen ready [/B]
---6. Click Close


and occasionally you need the following to disable the system beep:


       

> 
Disable the System Beep
Note: in Gutsy 7.10 the following is needed due to Ubuntu Bug 162719
Note: in Feisty 7.04 the following was not needed

---1. Disable the system beep for the current session
------1. Type sudo modprobe -r pcspkr and press Enter
---2. Disable the system beep for all subsequent sessions
------1. Type sudo gedit /etc/modprobe.d/blacklist and press Enter
------2. Append the following to the end of the file
-
#Disable the PC speaker
blacklist pcspkr
-
------3. Save the file and exit
---------1. Note: this permanent change will take effect on the next restart

---

