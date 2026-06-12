---
title: "What a trouble! Every FF upgrade needs flash!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by nikosal on 2008-06-11
This is something that started from the beta versions of Firefox 3.0 and it is still here today, in every minor or major upgrade (from fixes to RC1, RC2 etc)

Every time the flash is not there and the auto way to get it is not working. I had spent hours of searching and the only thing that saved me was [that post from]("http://ubuntuforums.org/showthread.php?t=764844") stc77: 

> Re: Flash
After upgrading to Herdy, my flash stopped working too. But indeed it has been installed as stated above. The problem seems to be, that the correct links for firefox 3b are missing:
This solved the problem for me:

sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

Of course if you have just installed RC2, you have to correct to "3.0" instead of "3.0b5". 

Hey, any way that we can fix for good, so we don't run to the console each time?

---

### Post by pedro_orange on 2008-06-11
> **nikosal said:**
> 
Hey, any way that we can fix for good, so we don't run to the console each time?

Not upgrading your browser?
I've found this to be true with mine anyway ^^.

---

### Post by kerry_s on 2008-06-11
put the flashplayer.so in ~/.mozilla/plugins every firefox version will check there.
create the plugins folder.

---

### Post by nikosal on 2008-06-11
hmmmm I did a quick search. 
I have two libflashplayer.so files in my pc, but not a flashplayer.so. Do we speak about the same file? All are 7.7 MB and created in April 2008.

One is located at /usr/lib/firefox-addons/plugins
the other is at /usr/lib/mozilla-firefox/plugins

I guess non is in the correct place? 

Could you please write down the complete suggested path? 

Thanks

---

### Post by kerry_s on 2008-06-11
yes, libflashplayer.so is what i meant, i'm not using linux right now and couldn't remember the correct name.

you want to copy that file to your mozilla user settings folder.

in term:
```

mkdir ~/.mozilla/plugins
cp /usr/lib/mozilla-firefox/plugins/libflashplayer.so ~/.mozilla/plugins
```

that should get it to the right place, .mozilla is a hidden folder that contains all your settings for firefox. to see it open nautilus and press ctrl+h to show hidden files/folders.

---

### Post by nikosal on 2008-06-11
thanks, I just did so, will test it in the next upgrade!

---

### Post by nikosal on 2008-07-18
Hey... wtf!! Still, I have to 

sudo rm /usr/lib/firefox-3.0b5/plugins [enter]
sudo ln -s /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/ [enter]

(replacing with the correct ff edition) every time I do a big or minor upgrade!! The above tip didn't work. Any advice?? Am I the last man on earth with this strange problem??

---

### Post by gandaran on 2008-07-18
> **nikosal said:**
> Hey... wtf!! Still, I have to 

sudo rm /usr/lib/firefox-3.0b5/plugins [enter]
sudo ln -s /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/ [enter]

(replacing with the correct ff edition) every time I do a big or minor upgrade!! The above tip didn't work. Any advice?? Am I the last man on earth with this strange problem??

no, it won't work, these command are just wrong for what you want, and it's no strange problem, it's just you don't know what you doing.
it would be easier if you just copy/paste the libflashplayer.so file to /usr/lib/mozilla/plugins (use **sudo nautilus** for root permission to copy/paste on the file system) flash installed in this folder can be used by every mozilla firefox based browser and opera too!
may I ask if there's a particular reason you didn't install the flash available in synaptic package manager, it would have saved you from all this trouble.

---

### Post by bumanie on 2008-07-18
Feel as though I am butting in, but I have had terrible trouble with flash. Nothing in the way of fixes etc. would make it work. I tried every fix mentioned on this forum. However, yesterday success. I found out that adobe have released flash 10 for linux. I downloaded that from the adobe site and now flash works - even you tube. Flash 10 for linux may be worth a try.

---

### Post by nikosal on 2008-07-22
> **gandaran said:**
> 
it would be easier if you just copy/paste the libflashplayer.so file to /usr/lib/mozilla/plugins (use **sudo nautilus** for root permission to copy/paste on the file system) 

Thanks, but tt is already there, together with two other files (libjavaplugin.so and npwrapper.libflashplayer.so). But still, problem in every upgrade...

---

### Post by SunnyRabbiera on 2008-07-22
I think the main source of the issue came from the directory being different in the betas of firefox 3 as if i remember correctly the system would install things differently.
I dont have this issue now as I switched from the latest firefox 2 to 3.

---

