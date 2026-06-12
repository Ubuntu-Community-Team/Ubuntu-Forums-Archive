---
title: "youtube ?"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by jbalazs on 2011-10-05
Youtube videos not playing ?? Ubuntu 10.4

Thanks

---

### Post by ubupirate on 2011-10-05
Could you please provide some more information on this issue? It's hard for people to help if they don't know what's wrong.

---

### Post by beew on 2011-10-05
Install the flash-aid addon for FireFox, run the script and restart FF and see if that works.

---

### Post by jbalazs on 2011-10-05
> **beew said:**
> Install the flash-aid addon for FireFox, run the script and restart FF and see if that works.

No it's not working

---

### Post by ubupirate on 2011-10-05
> **jbalazs said:**
> No it's not working

As I stated before:

> **ubupirate said:**
> Could you please provide some more information on this issue? It's hard for people to help if they don't know what's wrong.

How exactly is it not working?

---

### Post by AskTell on 2011-10-05
assuming your running 32bit, i dont remember what the beta 64bit package name is

paste the following command into the terminal located under applications/accessories/terminal

sudo apt-get install flashplugin-install

enter your password

press y to confirm installation and allow wait for it to finish, dont type anything while its installing.

once its finished type exit and hit enter, the terminal should close

restart mozilla and you should be good to go assuming your running 32bit

---

### Post by jbalazs on 2011-10-05
> **AskTell said:**
> assuming your running 32bit, i dont remember what the beta 64bit package name is

paste the following command into the terminal located under applications/accessories/terminal

sudo apt-get install flashplugin-install

enter your password

press y to confirm installation and allow wait for it to finish, dont type anything while its installing.

once its finished type exit and hit enter, the terminal should close

restart mozilla and you should be good to go assuming your running 32bit

this is the result 

foxhunter@foxhunter-laptop:~$ sudo apt-get install flashplugin-install
[sudo] password for foxhunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-install
foxhunter@foxhunter-laptop:~$

---

### Post by AskTell on 2011-10-05
are you running 64bit?

---

### Post by oldos2er on 2011-10-05
> **jbalazs said:**
> this is the result 

foxhunter@foxhunter-laptop:~$ sudo apt-get install flashplugin-install
[sudo] password for foxhunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-install
foxhunter@foxhunter-laptop:~$

The package name should be flashplugin-installer

Or click the FlashAid link in my sig.

---

### Post by amjjawad on 2011-10-06
What's the point for NOT providing MORE info?

Helping you blindly is what everyone here is doing because you are NOT providing more info. This is not the right way of asking for help.

1- You must be connected to the Internet
2- From Terminal run:

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

3- Restart Browser
4- See if it's work
5- If NOT, please provide MORE info.

And you welcome ;)

---

### Post by jbalazs on 2011-10-06
> **AskTell said:**
> are you running 64bit?

running 32bits

When I click on  to play youtube video just a black screen 

no video

---

### Post by thatguruguy on 2011-10-06
Here's how to fix.

---

### Post by Johnb0y on 2011-10-06
```
sudo apt-get install ubuntu-restricted-extras
```try that in a terminal and restart Firefox to see if it helps.

---

### Post by amjjawad on 2011-10-06
> **thatguruguy said:**
> Here's how to fix.

You forgot to add the link ;)

---

### Post by thatguruguy on 2011-10-06
No, I didn't.

---

### Post by Lars Noodén on 2011-10-06
You can play YouTube videos as [HTML5](http://www.youtube.com/html5) / WebM now and not worry about Flash.  If we are lucky, Flash is on the way out.

---

### Post by amjjawad on 2011-10-06
> **thatguruguy said:**
> No, I didn't.

Am I missing something? :/

---

### Post by audiomick on 2011-10-06
> **Lars Noodén said:**
> You can play YouTube videos as [HTML5]("http://www.youtube.com/html5") / WebM now and not worry about Flash.  If we are lucky, Flash is on the way out.
According to your link, you need Firefox 4. Ubuntu 10.10 is still on FF 3.xx

@amjjawad: I reckon thatguruguy is having a dig at the lack of info coming from the OP about his problem.;)

---

### Post by proxy.qtz on 2011-10-06
Here's how to fix it:

Step 1. Provide us with more information
Step 2. Update Firefox to FF4 or later
Step 3. Update/install Flash player
Step 4. Update/install Ubuntu restricted extras
Step 5. Enjoy youtube.

---

### Post by proxy.qtz on 2011-10-06
Also, you may want to let the video load before you play it. Also, your graphics drivers might not be new enough to play flash videos... Although i doubt it.

---

### Post by thatguruguy on 2011-10-06
> **amjjawad said:**
> Am I missing something? :/

Yes.  Meaningful information. None of us have received it, yet.

---

### Post by Lars Noodén on 2011-10-06
> **audiomick said:**
> According to your link, you need Firefox 4. Ubuntu 10.10 is still on FF 3.xx

@amjjawad: I reckon thatguruguy is having a dig at the lack of info coming from the OP about his problem.;)

Ok.  Firefox is not in backports for 10.10, but Oneiric is using FF7.

---

### Post by amjjawad on 2011-10-06
> **thatguruguy said:**
> Yes.  Meaningful information. None of us have received it, yet.

I didn't sleep for two days and got MANY bad news in these two days so I must log out but I got your point :)

---

### Post by amjjawad on 2011-10-06
> **audiomick said:**
> According to your link, you need Firefox 4. Ubuntu 10.10 is still on FF 3.xx

That in case the OP - who doesn't want to provide more info - has 10.10.

> 
@amjjawad: I reckon thatguruguy is having a dig at the lack of info coming from the OP about his problem.;)

Got it :)
Thanks!

---

