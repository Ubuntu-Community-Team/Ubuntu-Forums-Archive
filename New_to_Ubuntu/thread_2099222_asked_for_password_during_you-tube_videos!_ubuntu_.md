---
title: "asked for password during you-tube videos?! ubuntu 12.04"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by dulce on 2012-12-28
*warning i know nothing and shouldn't have an ubuntu system but... *:redface:

just upgraded to 12.04.  was inundated with requests for my password but i think i fixed that mostly, by disabling it.

but can't watch you-tube movies because every 10 minutes or so the screen saver comes on with another request for the password. we loose the visual but the audio continues.

what is this craziness and what can i do about it? *:-|*

---

### Post by chadk5utc on 2012-12-29
ok goto  I believe its in System -> Preferences -> Screensaver and change the time

---

### Post by kejava on 2012-12-29
Hi Dulce,

Go to the top, right corner of your Ubuntu desktop.  Click on the spoked wheel looking thing and get the pull down menu.  Click on "System Settings ...".  This can also be found as one of the icons in the launcher on the left of the desktop (cog and wrench).  When the interface opens, select the "Brightness and Lock" icon (in the top left row/column).

Have you tried changing these settings? (see attachment).

---

### Post by cariboo on 2012-12-29
This is actually a bug, in gnome-screensaver, that our friends upstream at gnome haven't seen fit to fix as of yet.

There is a fix for it though, have a look at [this]("http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/") blog post.

---

### Post by dulce on 2012-12-29
thanks so much guys. this will give me something to do today. :) also, i see i still have to sign in at start-up what do i do about that?

> **chadk5utc said:**
> ok goto  I believe its in System -> Preferences -> Screensaver and change the time

of course i am familiar with S->P->S but can you tell me where to find it in 12.04? and change the time to what?

> **kejava said:**
> Hi Dulce,

Go to the top, right corner of your Ubuntu desktop.  Click on the spoked wheel looking thing and get the pull down menu.  Click on "System Settings ...".  This can also be found as one of the icons in the launcher on the left of the desktop (cog and wrench).  When the interface opens, select the "Brightness and Lock" icon (in the top left row/column).

Have you tried changing these settings? (see attachment).

ok looked at that. turned the lock off. 'require my password' was not checked and i did not check it.

> **cariboo907 said:**
> This is actually a bug, in gnome-screensaver, that our friends upstream at gnome haven't seen fit to fix as of yet.

There is a fix for it though, have a look at [this]("http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/") blog post.

that makes sense (the bug). would like to install caffeine but can you tell me where to find a terminal in 12.04?

---

### Post by audiomick on 2012-12-29
> **dulce said:**
> ...tell me where to find a terminal in 12.04?

Either with the key combination

ctrl+alt+t

or type "terminal" in the search box in the dash.

---

### Post by kejava on 2012-12-29
> **dulce said:**
> thanks so much guys. this will give me something to do today. :) also, i see i still have to sign in at start-up what do i do about that?

For auto-login at start-up:
Go back into the "System Settings" --> "User Accounts".  Then select the account of interest and toggle the "Automatic Login" switch.

Is that what you were looking for?

---

### Post by dulce on 2012-12-29
> **kejava said:**
> For auto-login at start-up:
Go back into the "System Settings" --> "User Accounts".  Then select the account of interest and toggle the "Automatic Login" switch.

Is that what you were looking for?

it says that there is only one account, mine as administrator and the toggle is off.

i just 'logged out' (by the way i haven't seen  'restart' anywhere) and started up again. it brings up a 'guest account' with my name and i have to sign in.

---

### Post by dulce on 2012-12-29
> **cariboo907 said:**
> This is actually a bug, in gnome-screensaver, that our friends upstream at gnome haven't seen fit to fix as of yet.

There is a fix for it though, have a look at [this]("http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/") blog post.

entered the first command 'Adding the Caffeine repo' and got this:

[I]Cannot access PPA ([https://launchpad.net/api/1.0/~caffeine/+archive/developers/ppa](https://launchpad.net/api/1.0/~caffeine/+archive/developers/ppa)) to get PPA information, please check your internet connection.

[/I] i got something similar and 'please check your internet connection' on some (but not all) of the  ubuntu softwareyesterday.it works, what would i check?i'm in Mexico by the way.

---

### Post by rrich1974 on 2012-12-29
i want to think about something besides caffeine. 
open vlc and play a long music file or a low bitrate audio stream, mute the vlc. 
vlc will prevent the screensaver. 
go to prefernces, general setting, choose all setting and in the general setting (first option) and check "prevent power management during playback"
that will do the trick. 
caffeine is a solution but from my experience it not work quite well. 
not to mention that you need to add a ppa, this i am not recommending!

---

### Post by dulce on 2012-12-29
> **rrich1974 said:**
>  
open vlc and play a long music file or a low bitrate audio stream, mute the vlc. 
vlc will prevent the screensaver.  

thanks for your help. but i have no idea what this means (see my disclaimer in the OP)

> go to prefernces, general setting, choose all setting and in the general setting (first option) and check "prevent power management during playback"
that will do the trick.again,  i no longer know where 'preferences, general setting' is.  12.04. is a different setup with different terms. there are no general settings in System Settings

> caffeine is a solution but from my experience it not work quite well. 
not to mention that you need to add a ppa, this i am not recommending!ahh its the ppa! i will let caffeine go then.

---

### Post by dulce on 2012-12-29
was it a mistake for someone like me to upgrade? a local expert (unfamiliar with ubuntu) told me to go ahead, it wouldn't screw things up.

actually i like it. just need some help. i know this is minor stuff. you guys always come thru for me, thanks. :)

---

### Post by dulce on 2012-12-29
> go to prefernces, general setting, choose all setting and in the  general setting (first option) and check "prevent power management  during playback"
that will do the trick. 			 		

have looked thru all the settings for this but didn't find it.

---

### Post by rrich1974 on 2012-12-30
open vlc, tools-prefernces-(in the down-left corner choose "all") - click first option "advanced" - check "inhibit power management...."
i have vlc 2.0.3

---

### Post by dulce on 2012-12-30
my local expert (unfamiliar with ubuntu) told me to set the screen saver on 'never'. i did that and it solved the video sign in problem.

i can live with this, its at my level of functioning, so thats thats. thank you for all your input everyone.

---

