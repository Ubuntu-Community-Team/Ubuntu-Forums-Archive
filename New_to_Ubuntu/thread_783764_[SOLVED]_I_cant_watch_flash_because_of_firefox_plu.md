---
title: "[SOLVED] I cant watch flash because of firefox plugin problems"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by gumpontheweb on 2008-05-06
Everything worked fine yesterday. Foxyproxy(an add on) updated and caused me to re-install firefox. After re-installing I had to get the missing plugins. THIS IS WHERE THE PROBLEM IS!
When it asked which plugin to use I clicked on the wrong one by accident and now I cant get it to ask me again. I installed the newest flash player(i think,9.0 r115 instead of the old one that seems to be the one working ,9.0r100) That's all greek to me.
When I use to get to a flash video I would see a picture from the video with a small play button in the middle of the window the video would play.
Now I see a large play button that takes up the whole video box, there also is no picture from the video behind the button.
Is there a way to get rid of EVERYTHING that is firefox plugins or even all of firefox. live help was helping me untill it was cut off. he got me to install the newest adobe flash update but I dont think it worked. The old one didn't let it play or something?
What can I do? I would like to watch stuff!!!

---

### Post by phidia on 2008-05-06
How was foxyproxy installed? If it was through the package manager you could uninstall and reinstall that. You could also try uninstalling firefox using  the package manager and then reinstall it.

---

### Post by trekguy on 2008-05-06
> **gumpontheweb said:**
> Everything worked fine yesterday. Foxyproxy(an add on) updated and caused me to re-install firefox. After re-installing I had to get the missing plugins. THIS IS WHERE THE PROBLEM IS!
When it asked which plugin to use I clicked on the wrong one by accident and now I cant get it to ask me again. I installed the newest flash player(i think,9.0 r115 instead of the old one that seems to be the one working ,9.0r100) That's all greek to me.
When I use to get to a flash video I would see a picture from the video with a small play button in the middle of the window the video would play.
Now I see a large play button that takes up the whole video box, there also is no picture from the video behind the button.
Is there a way to get rid of EVERYTHING that is firefox plugins or even all of firefox. live help was helping me untill it was cut off. he got me to install the newest adobe flash update but I dont think it worked. The old one didn't let it play or something?
What can I do? I would like to watch stuff!!!

I'm trying to learn this stuff too. I had grey "play" buttons where the flash movie was supposed to be playing.  Although, in my case, there was a movie behind the button.  This worked for me.

> Originally posted by tjwoosta

Re: Flash on Hardy 64bit
if you see grey boxes that you have to click on to make them play, it is because you have the swfdec player instead of the prefered flashplugin-nonfree

to remove the swfdec player do this
Code:

sudo apt-get purge swfdec-mozilla

then install the working flashplayer like this
Code:

sudo apt-get install flashplugin-nonfree

this works on hardy 64 bit fine, no need to install any 32 bit java or librarys or anything 

---

### Post by smo0th on 2008-05-06
A quick solution should be going to Applications>>Add/Remove..>>search for firefox>>unselect and apply changes, firefox should be uninstalled, then you make a clean install and do your best with your plugins =)

---

### Post by gumpontheweb on 2008-05-06
> **trekguy said:**
> I'm trying to learn this stuff too. I had grey "play" buttons where the flash movie was supposed to be playing.  Although, in my case, there was a movie behind the button.  This worked for me.
I use to be able to see a screenshot of the movie with a tiny play button in the middle. Now it doesn't have the movie pic, just black behind it.

---

### Post by gumpontheweb on 2008-05-06
> **smo0th said:**
> A quick solution should be going to Applications>>Add/Remove..>>search for firefox>>unselect and apply changes, firefox should be uninstalled, then you make a clean install and do your best with your plugins =)

That dont work. Itried but the wrong pugin or something wrong stays!!!
I am gonna try the solution above

---

### Post by gumpontheweb on 2008-05-06
> **trekguy said:**
> I'm trying to learn this stuff too. I had grey "play" buttons where the flash movie was supposed to be playing.  Although, in my case, there was a movie behind the button.  This worked for me.

YOU HAD IT EXACTLY!!!!
you have given me the absolute best help on this board!!!
Thank you soo much
the live mozilla dude couldn't figure it out that quick.
TREKGUY IS AWESOME!!!

---

### Post by whitefort on 2008-05-06
> **trekguy said:**
> I'm trying to learn this stuff too. I had grey "play" buttons where the flash movie was supposed to be playing.  Although, in my case, there was a movie behind the button.  This worked for me.

Trekguy, MANY thanks - this has been driving me nuts since I installed Hardy, and you fixed it for me!

(THough I have to wonder why Thunderbird by default installs the wrong one...)

---

### Post by trekguy on 2008-05-06
Woohoo, glad I could help someone.  I only been running Ubuntu for a couple weeks, and I'm a little lost, too.

To be honest, I didn't figure it out...I found the fix from a post by tjwoosta... that's how this place works.... eventually, you find what you're looking for.  :)

It sure does feel good when you get something to work!

---

### Post by Ichido on 2008-05-14
> **trekguy said:**
> Woohoo, glad I could help someone.  I only been running Ubuntu for a couple weeks, and I'm a little lost, too.

To be honest, I didn't figure it out...I found the fix from a post by tjwoosta... that's how this place works.... eventually, you find what you're looking for.  :)

It sure does feel good when you get something to work!

I am having the same problem with a friend's PC.
My PC works fine and my friend's does not.
I have compared every thing possible and both of our systems are identical except for his Firefox has a Flashplayer ver.8 that is Not Enabled.
Where or how this Flashplayer 8 got there is a mystery.
I have tried everything in the above posts and his Video still does not work.
I will try a Ubuntu Re-install.
Do you still have the link to the Post by tjwoosta?
Thanks.

---

### Post by shs123 on 2008-07-05
Thanks Trekguy for the post. I recently updated my system from Gutsy to Heron and this "big play button" thing had been driving me crazy. Rather than going through the way that was described to you, I simply went into the Syanaptic Package Manager, searched for "swfdec-mozilla" (yes, it was installed), marked it for "complete removal" and now all is well!
thanks again..

---

### Post by spartan1011 on 2009-04-30
this helped alot... especially since I upgraded to jaunty. thanks.

---

### Post by Bijuno on 2009-09-11
I´ve had the same problem... Three months ago it started. And until today, I was able to fix it because I found this thread.  **Thank You VERY MUCH!!**

:P

---

