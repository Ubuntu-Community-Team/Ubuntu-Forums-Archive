---
title: "Password prompt for installing apps and administration tasks"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wordmagic on 2008-11-15
Is there a way not to be prompted for password every time I want to install an application, etc?

---

### Post by halitech on 2008-11-15
yes


will you find the info here? no

---

### Post by shifty_powers on 2008-11-15
edit: as above...

---

### Post by bodhi.zazen on 2008-11-15
> **wordmagic said:**
> Is there a way not to be prompted for password every time I want to install an application, etc?

> **halitech said:**
> yes


will you find the info here? no

You are asking about how to change a "basic" security setting.

You can get a root shell with :

```
sudo -i
```

Beyond that you will need to use visudo. It is expected that you read the man pages and learn how to do this for yourself.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by SunnyRabbiera on 2008-11-15
There is a reason why you have the password prompt for administration tasks and installing apps, to keep you SAFE.
Wonder why windows XP has so many issues?
Because it automatically allows root access no questions asked, it offers no passwords by default so it doubles its issues by that alone.
Windows is so vulnerable because of what it has done to its system.
We encourage new users to keep the passwords here, I know its annoying and inconvenient but its why Linux is secure and windows is not.
I know it also seems silly when you are the only user on your computer too to type in the passwords but it is all there to keep your system safe.
Hey if you want to open your system to hackers and crackers then use windows.

---

### Post by wordmagic on 2008-11-16
Thank you for your answers. I do not want to open it to hackers and crackers but I think it is really annoying having to type a password all the time. As simple as that. I think Linux and Ubuntu specifically is focused not only on security, but on being user-friendly too ;) Correct me if I am wrong.

---

### Post by perlluver on 2008-11-16
Right it is focused on being user friendly, but at the same time secure.  I have yet to come across a Linux OS that hasn't asked me for my password when trying to install, or doing something dangerous.  If I had, I would have stopped using that system pretty quick.

---

### Post by Peter09 on 2008-11-16
Yes - but user friendly includes not having to run virus checkers and spam removers etc. All of which are a legacy of windows that we do not want. Running your system in admin mode is not recommended for good reasons.

---

### Post by bodhi.zazen on 2008-11-16
> **wordmagic said:**
> Thank you for your answers. I do not want to open it to hackers and crackers but I think it is really annoying having to type a password all the time. As simple as that. I think Linux and Ubuntu specifically is focused not only on security, but on being user-friendly too ;) Correct me if I am wrong.

The vast majority of users would disagree with that statement.

Entering a password is a minor inconvenience and offers a whole lot of protection. Once you enter a password there is a grace period so you should not be entering your password multiple times as you suggest, just once.

If you prefer, open a root shell with :

```
sudo -i
```

I think you should be asking yourself why it bothers you so much ?

---

### Post by wordmagic on 2008-11-16
> **bodhi.zazen said:**
> 
I think you should be asking yourself why it bothers you so much ?

Thank you for your answer.

Well, this is mostly a technical issue and not existential, let alone psychoanalytic ;)

Obviously, I am in the process of giving Linux a fair try, and my main focus is usability and user-friendliness (having to type a complex password for every program installation or minor administrative task is not negligible especially during a trial period where a lot of this is going on).

```
sudo -i
```
What does this code do?

---

### Post by shifty_powers on 2008-11-16
iirc it will grant you temporary admin privileges, not sure if it is just whilst terminal is open mind

---

### Post by Paqman on 2008-11-16
Security is always a tradeoff between usability and effectiveness. Personally, I think banging in my password every so often is a very small price to pay to get Linux's excellent level of security.

As for Ubuntu being usability focussed: that's exactly why you get 15mins of access after you use sudo. try entering several sudo commands in a terminal; you'll only be asked for your password after the first one.

---

### Post by wordmagic on 2008-11-16
> **shifty_powers said:**
> iirc it will grant you temporary admin privileges, not sure if it is just whilst terminal is open mind

Thanks!

---

### Post by oldos2er on 2008-11-16
You might want to read this: [http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

 Also, the 15 min. timeout value for sudo can be changed.

---

### Post by Mardoct909 on 2008-11-16
It's a bit annoying, I agree... But try Vista's attempt at doing the same thing. It's far worse, and similarly can only be removed at the cost of security, and a lot of it. Most OSes have already noticed that it's a bad idea to allow unfettered access to root regardless of who's asking for it.

Also, you do want a secure password, but you don't need it to be s95JkER4529Iit or anything. Just make it something simple but still hard to guess. I just take a word and a number and alternate between the word and number. Ex. scourge and 5289 becomes s5c2o8u9rge. Or sc52ou89rge. Etc. It's relatively easy to remember for the level of security it offers, and I find it can be typed quickly after the first few times you enter it.

---

### Post by sirjoebob on 2008-11-16
I, too, got annoyed by this and found a solution by adding myself to the /etc/sudoers file. I have done this for a while and it makes things a lot easier for me. 



This is a safety feature and removing it is not advised for new users.

---

### Post by jimmy the saint on 2008-11-16
Plus, there is nothing less user friendly than having a system that you are able to completely bork without having the faintest idea what you have done and how to fix it.  The root password promtp, if it does nothing else, serves as a warning that what you are about to do has the potential to break something.  One thing that linux is good at is making sure that if an action can break something, you have to be a superuser, or at least have the password to do it.

---

### Post by jimmy the saint on 2008-11-16
It was noted by a forum staff member earlier in this thread that this type of information is not shared here. There is a  reason information like that is not to be shared in these BEGINNER SUPPORT FORUMS.  If a user is to new to know that, or research it independently, they are certainly to inexperienced to have unfettered access to every nook and cranny of the OS without so much as a warning when they can break something.

---

### Post by sirjoebob on 2008-11-16
Good point and I apologize for putting that here. I use an RSS aggregator to check the Ubuntu forums and did not realize this was under absolute beginner. Obviously, I would not recommend using this unless you are aware of the risks. Again, I would NOT use this. 

Sorry for posting that here to begin with.

---

### Post by jimmy the saint on 2008-11-16
No worries, but I would edit the post and remove the instructions to prevent them from causing headaches for new users in the long run!

---

### Post by SunnyRabbiera on 2008-11-16
> **Peter09 said:**
> Yes - but user friendly includes not having to run virus checkers and spam removers etc. All of which are a legacy of windows that we do not want. Running your system in admin mode is not recommended for good reasons.

Indeed, I find running addware/spyware and virus checks to be against user friendliness.
You just type in a password with linux, with windows you have to open up a application and scan the drive for hours.

---

### Post by bodhi.zazen on 2008-11-16
> **jimmy the saint said:**
> It was noted by a forum staff member earlier in this thread that this type of information is not shared here. There is a  reason information like that is not to be shared in these BEGINNER SUPPORT FORUMS.  If a user is to new to know that, or research it independently, they are certainly to inexperienced to have unfettered access to every nook and cranny of the OS without so much as a warning when they can break something.

Thank you, yes that is the point exactly. While you are free to run your box the way you wish, we prefer to teach new users how to use their system rather then circumvent security features that protect all of us.

Basically, if they have to ask, please give "standard" but safe answers. If they understand the OS , they will not need to ask.

---

### Post by Buggsy787 on 2008-11-18
Hi,
The forum description fits me exactly. 6 weeks and struggling with 8.04 and 8.10 as i am not prompted for password when trying to do the 80+ updates needed. Moved to 8.10 for this reason and after a week was back where I started. All that happens in Update Manager is the list appears with descriptions, click on install, status bar shows starting administrative... then disappears and update manager does nothing even if left for hours.
What should I do to make the password request reappear.

By the way it's the same with partition editor, samba, synaptic etc

Thanks
Buggsy

---

### Post by Peter09 on 2008-11-18
Check that the prompt for password is not appearing behind the original window. Have you set your windows up so that the in focus window is not brought to the front?

---

### Post by Buggsy787 on 2008-11-18
Good question, shall investigate. Thanks Peter

---

### Post by Buggsy787 on 2008-11-18
Hi Peter, There is no window for the password prompt appearing, although there is a box in the task bar it won't maximise when clicked and then just disappears. I had all windows minimised. I don't know how to set the windows up to automatically get focus. I thought, and it seems normally to happen, that new windows get focus immediately. I have to kill the Update Manager to get rid of it. Strangely System Monitor is quite happy to let me kill the process without a password! Not a lot of consistency here.
Any other thoughts?
Cheers
Frank

---

### Post by Buggsy787 on 2008-11-18
Have been reading the top 10 tips for newbies and checked the update/upgrade. As I write apt-get is updating my system having asked for the password in the terminal. Perhaps I will promote myself to a terminal user rather than a typical Windows Vista approach:)
Frank

---

### Post by Buggsy787 on 2008-11-18
Well now updated but still doesn't let me input password when doing anything not in terminal

---

### Post by handydan918 on 2008-11-18
This is totally a SWAG, so you might want to wait for more feedback, but what about trying

```
sudo dpkg-reconfigure gksu
```

or, failing that, 
```
sudo apt-get remove gksu && apt-get install gksu
```

---

### Post by Peter09 on 2008-11-18
The only other thing I can think of is that you have some unusual setting in compiz - in the window management section.

---

### Post by Buggsy787 on 2008-11-18
Thanks PC. How do I check that? Having done the other suggestions I now  only get a TTY when I boot - how do I get back to my desktop?
Frank

---

### Post by Peter09 on 2008-11-18
does the command 
```
startx
```

give you a GUI

---

### Post by Buggsy787 on 2008-11-19
Thanks Peter, got a gui but no packages as before, reported no image and still no admin rights so going to do a reinstall! Thanks for all your help

---

### Post by Paqman on 2008-11-19
> **Mardoct909 said:**
> 
Also, you do want a secure password, but you don't need it to be s95JkER4529Iit or anything. Just make it something simple but still hard to guess. I just take a word and a number and alternate between the word and number. Ex. scourge and 5289 becomes s5c2o8u9rge. Or sc52ou89rge. Etc. It's relatively easy to remember for the level of security it offers, and I find it can be typed quickly after the first few times you enter it.

Another good way to achieve a strong password that's easily remembered is to use a phrase. For example "My son's name is Liam, and he is 12" becomes "msniLahi12", which is plenty strong.

---

### Post by edwardtilbury on 2010-04-21
I wish it was more like windows 7 in that sense.. I mean I don't mind the screen diming and waiting for me to click yes, it's faster than having to move the other hand from the mouse and enter my case sensative alpha-numeric password all the time.
 
Once I'm logged in and I have a locking screen saver I'm pretty safe, it's really only me using the computer, so a quick windows 7 style of security "yes / no" dialoge box would be just fine for me.

---

