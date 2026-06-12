---
title: "flash or sound crashes firefox on youtube"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-05-13
hey guys...

To crash firefox, i simply have to go to [www.youtube.com](www.youtube.com) and click on a video. firefox will immediately crash. 

Now I suspect either the flash player or the way sound is sent to the sound server (whatever the latter means). 

Here is the output of terminal when I run firefox from it:

```
ali@ali-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
```

When I run firefox, my homepage (google.com) is loaded. Then I browse to youtube and click on a video, and firefox crashes.

I have removed the following:
flashplugin-nonfree
libflash-mozplugin
libflash-swfplayer

yet, with all of them removed, I can still view flash content in firefox, which is strange.

I thought originally that by removing all the flash plugins and then reinstalling flashplugin-nonfree, it will solve the problem. however, I removed all the flash plugins (or at least I think so) yet i still can view flash content. 


How do I go about fixing this problem? any help is appreciated!

---

### Post by zenwalker on 2008-05-13
What? Even if u have removed flash libs, u can view flash. Is it not crashing now?

---

### Post by Xiong Chiamiov on 2008-05-13
Sad to say that Adobe doesn't care about us, so the official flash plugin is crap.  For some it works great, others it sucks terribly.

Do you have gnash installed?

---

### Post by KaliVoid on 2008-05-13
Hi

my firefox use to behave like your's
so what i did is install "[Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433")"
add-on ,it stop any flash from loading
and you can load the flash simply by
pressing a play button (you will see it...)

hope this will solve your problem

---

### Post by newbuntuxx on 2008-05-13
> **zenwalker said:**
> What? Even if u have removed flash libs, u can view flash. Is it not crashing now?


yes, i can still view flash content, strangely. Its still crashing. So, clearly a flash plugin is still lurking around some where. I dont know how to find it.

Any help on that?

---

### Post by newbuntuxx on 2008-05-13
> **Xiong Chiamiov said:**
> Sad to say that Adobe doesn't care about us, so the official flash plugin is crap.  For some it works great, others it sucks terribly.

Do you have gnash installed?


no, i dont have it. is it a flash plugin? can i install it using:

```
sudo apt-get install gnash
```

thanks

---

### Post by newbuntuxx on 2008-05-13
> **KaliVoid said:**
> Hi

my firefox use to behave like your's
so what i did is install "[Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433")"
add-on ,it stop any flash from loading
and you can load the flash simply by
pressing a play button (you will see it...)

hope this will solve your problem

i'll try that when i am home. i'll let you know if it works.

thanks...

---

### Post by reylafo on 2008-05-21
You can download and install Flash 10 directly from Adobe.

Available for Linux in a .tar pkg.

First remove the flash 9 plugin with synaptic.

Run the installer in a terminal and follow the instructions.

Worked great. Fixed a lot of crashing issues, using firefox 3 beta.

---

### Post by Promaster91 on 2008-05-21
If you are having problems with firefox 3 downgrade back to 2. That is what I did and I have had no flash problems!

---

### Post by purplepaint on 2008-05-22
I have this problem every other day or so too.

Is it likely to be solved when the final version of Firefox 3 is released?

---

### Post by shifty_powers on 2008-05-22
hopefully. some people seem to forget that the version of ff3 included in hardy is still a beta. what you think of that is another matter... ;)

---

### Post by Darkade on 2008-06-03
This is a known bug however there's a solution and it's quite easy just install libflashsupport
this library is the one that enables to play flash trough alsa sound server it's true that anyway your flash will crash but less, and i mean LESS, and you will be able to hear sound and flash at the same time without having to close one or the other.
hope it helps and as i've said it's a known bug and the developers are working really hard on it.

and by the way, sorry for the bad english:lolflag:

---

### Post by newbuntuxx on 2008-06-05
hey everyone, thanks for the replies,

I tried your solution Darkade, and firefox continues to crash. I then decided to downgrade to firefox two, and voila, that solved the problem.

Moral of the story: If you use beta software, dont complain :) though I must say that the features in firefox 3 beta were just amazing. I cant wait till a stable version is released.

---

