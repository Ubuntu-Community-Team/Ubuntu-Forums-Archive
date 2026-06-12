---
title: "HOWTO: Change your forgotten password"
date: 2006-02-19
forum: Outdated Tutorials &amp; Tips
---

### Post by majikstreet on 2006-02-19
What?! You forgot your password? What are you going to do now? You can't reinstall; you have all your critical files on your machine!

No big deal. Don't sweat it. We can change your password so easily it's not even funny. 

**The Howto:**
1. Boot up your computer, and when you see the screen that says something like "Press ESC to enter grub," press ESC (the escape key) as soon as you can. 

2. Now you should see a menu with many options. Use the arrow keys to navigate to the newest kernel (the one with the highest number) that has "(recovery mode)" written next to it. Now, hit enter (return).

3. Next, your system should boot up normally. BUT, you WILL NOT see the boot splash. Don't worry about that. Lots and lots of text WILL fly past you.

4. Now you are at a root shell. 

5. Type
```

passwd username

```
replacing username with your username

6. Now a little thing will come up and say "New UNIX Password" or similar. Type the new password that you want. Hit enter. Type it again. Hit enter

7. Then, your password has been changed! Type
```

shutdown -r now

```

8. Your system is now rebooting. Once it comes back up, login with your new username and password.

9. There is no step nine.


That was easy, too easy. Congratulations! \\:D/ 

Hope to help,
majikstreet

---

### Post by welsh_spud on 2006-02-19
My God! That's just plain scary...


...but it will come in useful. Thanks majikstreet

---

### Post by majikstreet on 2006-02-19
:D

yeah, it's really scary..

but it's a great feature..

**That's why you should physically secure a computer that has sensitive/important stuff on it, folks.**

---

### Post by welsh_spud on 2006-02-19
I remember something like this on the old Apple iBooks. When they were booting up you could hold down ctrl-c and it would drop you into a root shell, letting you do whatever you want to the computer.

---

### Post by Iandefor on 2006-02-20
Interesting. Thanks, majik.

---

### Post by majikstreet on 2006-02-20
[QUOTE=Iandefor]Interesting. Thanks, majik.[/QUOTE]
no problem :D

---

### Post by bored2k on 2006-02-20
[QUOTE=welsh_spud]My God! That's just plain scary...


...but it will come in useful. Thanks majikstreet[/QUOTE]
That's why people set up passwords for GRUB.

---

### Post by cronholio on 2006-02-20
It seems scary. However, the logic behind that is: If someone has physical excess to a computer, they have access to your data anyway (and be it by means of taking along the HD). UN*X was built when people used to login remotely.

---

### Post by imagine on 2006-02-20
It's not about Unix, this works in every OS, also Windows.
If you need to secure your data against people who have physical access to it, encryption is your friend.


Btw, "reboot" is shorter than "shutdown -r now". Just for the people who are really lazy.

---

### Post by dvarsam on 2006-02-20
Dear "majikstreet"

After your reply to my post, I blended your post to Mine, and here is the FULL version:


How to change a User's or ROOT's Password (before Booting):

To Log in in your Ubuntu, simply use your "user name" (you gave during the installation) & the "password" (you specified at that time).


If you have Forgotten your User's "password":

	What?
	You forgot your password?
	What are you going to do now?
	You can't reinstall; you have all your critical files on your machine!

No big deal.
Don't sweat it.
You can change your password very easy. 


There are two ways to go on this:

1. To Change your current User's Password:

    a. Restart Ubuntu in Recovery Mode.
        To do this, Boot up your computer & when you see the screen that says 
        "Press ESC to enter grub", press "ESC" (the Escape Key) as soon as you can.

    b. Now you should see a Menu with many options.
        Use the arrow keys to navigate & select the newest Kernel (the one with the 
        highest number) that has "(Recovery Mode)" written next to it.

    c. Press the key named "Enter" (return) & your System will Boot and will take 
        you to the Command Line (the bash Shell's $ or # prompt).

    d. Type:

	passwd username

    e. A window will launch  & will ask you to enter your "New UNIX Password".
        Enter your NEW "password".

    f. Then Reboot your Ubuntu (by typing "reboot" or "shutdown -r now") & Log in 
       with your "username" & the NEW "password" you specified.

2. To Create a NEW User Account:

    a. Restart Ubuntu in Recovery Mode.
        To do this, Boot up your computer & when you see the screen that says 
        "Press ESC to enter grub", press "ESC" (the Escape Key) as soon as you can.

    b. Now you should see a Menu with many options.
        Use the arrow keys to navigate & select the newest Kernel (the one with the 
        highest number) that has "(Recovery Mode)" written next to it.

    c. Press the key named "Enter" (return) & your System will Boot and will take 
        you to the Command Line (the bash Shell's $ or # prompt).

    d. Type:

	useradd -m new_user_name

    e. Type:

	passwd new_user_name 

    f. Enter the NEW User's Password twice.

    g. Then Reboot your Ubuntu (by typing "reboot" or "shutdown -r now") & Log in 
        with your NEW "username" & "password" you specified.


IF Ubuntu does NOT let you type ANY of the above commands & requests a ROOT Password, do the following:

    Note:
    By default, there is NO "root" Password in Ubuntu (the ROOT Password is NOT 
    set).
    Once you Set a ROOT Password in Ubuntu, it requires it when you are in the 
    "Recovery Mode".
    You can use an Ubuntu Install CD to Reset the ROOT Password.

1. Insert the Install CD & at the CD Boot Prompt, type:

	rescue

2. Follow the instructions & when you are in the "Terminal", type:

	passwd root

3. Enter the ROOT Password twice in there & Add a NEW User account with:

	adduser

4. Enter your NEW User info & when your finished, type:

	adduser your_new_user_name admin

    Note:
    This is performed so that the NEW User can access System Tools as ROOT.

5. Then remove your InstallCD, Reboot your Ubuntu (by typing "reboot" or 
    "shutdown -r now") & Log in with your NEW User account.


Have Fun !!!

---

### Post by majikstreet on 2006-02-20
[QUOTE=imagine]It's not about Unix, this works in every OS, also Windows.
If you need to secure your data against people who have physical access to it, encryption is your friend.


Btw, "reboot" is shorter than "shutdown -r now". Just for the people who are really lazy.[/QUOTE]
I know that reboot is shorter.. For some reason I felt like putting shutdown -r now

dvarsam thanks :)

**A lesson to all: if you have valuble data on your machine, always encrypt and physically secure your machine. That is all.**

---

### Post by dvarsam on 2006-02-21
[QUOTE=majikstreet]

**A lesson to all: if you have valuble data on your machine, always encrypt and physically secure your machine. That is all.**[/QUOTE]

Dear "majikstreet"

What you said above is **THE** most important advice to the Ubuntu Community:

1. To Encrypt your Work

2. To Physically secure your Machine.


I agree with you Totally !!!


Let me explain why:


_Case 1_: To Encrypt your Work

It is NOT good for ANYBODY that knows your username, to be able to change YOUR Username's Password & access all YOUR files with YOUR user rights.

It would be better, if Ubuntu FORCED you to Boot as Root (in such a case).

_Result_:
So, if you are concerned with Security it is good to create a Root account.

This way, if somebody wants to break in YOUR PC:

1. They need to know your root Password,

OR:

2. They need to Boot from CD & change your Root Password from there


In the 2nd case, you MUST Restrict Ubuntu to Boot from a CD.
So, enter the BIOS & do NOT let Ubuntu Boot from a CD.
Then secure your BIOS with a password...

_Result_:
So somebody who wants to see your Stuff, needs to know YOUR BIOS password...

But then, make sure you do NOT forget your BIOS password!

But, even in such a case, there is a way to overcome that lock:

1. They can Flash your BIOS & (voilla !!!) there is NO BIOS password!

     OR:

2. Physically remove YOUR Hard Drive from your PC & plug it in a different PC to 
    sneak into your work...

But if your **Encrypt** your Files with a Password?

Then, they would have to "crack" your Password or find another way to SEE your files.

That means:
Whoever tries to SEE your stuff, MUST be a good "Hacker"!


_Case 2_: To Physically secure your Machine.

IF somebody breaks-in your house & steals YOUR Hard Drive, you' ve lost it ALL !!!

However, that does NOT mean that he will know how to SEE your files unless he is an Expert...

_Result_:
...in the end (if they are willing SO much), they WILL find a way to see your stuff, in any way...

_Word of Advice_:

Anything that is "Locked" can be "Unlocked"....

... and it is a matter of "How much Time" is needed for somebody to Break-in your Ubuntu...

So, all you can do is to "Slow them down" a little...

Have fun !!!

---

### Post by engla on 2006-02-21
Adapting The HOWTO for PPC (yaboot) users

That's right, us on PPC machines can't use GRUB, we use something called yaboot instead. Should be no problem though, just replace step 1 and 2 with this:

1. Reboot your PPC machine. If you have dual-boot or cdboot or such configured, the first you will see is a menu to choose either linux, macosx or cd-boot. You want linux of course; press 'L'.
2. Now, you are sent to the second yaboot screen. If you type tab you get a list of the different kernels you can boot to, but normally you just want to use the one called "Linux". To boot to single user mode you have to follow your desired kernel with 'single', so at this stage we type```
Linux single
```Make sure it's exactly like "Linux single", caps matters.
The rest is just the same.

---

### Post by Thetha on 2009-09-01
Thanks a lot... I was about to reinstall ubuntu :)

---

### Post by Hellene Atheist on 2009-12-25
Thanks,  majikstreet. That was very easy.
I've been looking for an easy way to change my password.=D>

---

### Post by GoBrandiRanger on 2010-07-18
Thank you so much! I'd been neglecting updates for about 8 months now, due to my lost password. lol

---

### Post by andorthekid on 2013-01-09
it doesnt work :(

---

### Post by andorthekid on 2013-01-09
iam stuck at step one :(

---

### Post by steeldriver on 2013-01-09
Hello and welcome

This is a very old thread and some things have changed - please follow these instructions instead

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sisco311 on 2013-01-09
Thread moved to Outdated Tutorials & Tips.

---

