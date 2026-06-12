---
title: "Cannot login to desktop after a reinstall with exact same credentials,etc."
date: 2015-04-09
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-04-09
thanks for reading. 

Background.
 I've had Xubuntu installed least 9-ish months now. No problems whats so ever. Including the times since I have had it "highly customized" (aka each sub-folder)----/(root) /boot /home etc. 

About 5-days ago I went to reinstall 14.4.02 (disk)---I was not paying attention and had misspelled the user name. AKA--"normal" is satUrn     I accidentally typed satrn  (missed the U)

Of course no problems with the install. Took about 48-hours befored I noticed (as I use the autologin feature--but DO have a root password). I noticed when I was saving desktop stuff---When I clicked "Home"--saw the 2-users sitting there. 


_THE PROBLEM_
So, when I noticed that I had created a wrong user, I tried looking up how to merge users (those instructions did not work for me as I could not login to satUrn (correct login)--as I was not given a choice. (had to to be logged out of user to rename). 
When I tried to change settings in the GUI "Settings" tree---with User management (didn't work)

So, I'm trying to reinstall---however, the user satUrn DOES exist--as always (everything is there that I want, etc.)----but once I reinstall (as I've always done successfully in the past)-----

BAD BEHAVIOR NOW?
It's stopping at the Login screen. (that shows "satUrn"--aka--correct login. 
It's the same screen you see (lightlocker kicks it on I think)--you leave computer too long, come back and need to log back in. 


"Succesful" (past)--it simply logs  in, straight to a black screen  pause about 1.5/2seconds then rolled to building out the desktop---panel icons, etc.etc. "Normal/Expected behavior"




I'm 1000000% positive I'm using the correct password to login (using the same as I've always used)

Put the correct password in it rolls "as if" it were to login, about 1.5/2-seconds of a black screen pause then POOF--back comes the login. 


I DO THINK it's recognizing my credentials as if I INTENTIONALLY use a bad password I immediately get the red box to pop up with check username/password. 

Suggestions? 

THANK YOU in advance! 
--------------------------------


Anomalies that may/may not be important. Mentioned above, I have my install "customized"--aka I am using every sub-folder that has a choice--to use it

```

aka---
/(root)
/boot
/usr
/srv
/home
/var
/usr/local
/opt


I did notice that when I created satrn (no U--"bad" login)--I *DID* use the customized install folders--as I always do (aka--remapped them before install) BUT, when I realized (bag loing/.no U)--installed
it has it's own folder for everything (aka--/home  /user /var    satrn (bad-no U)----

it did not follow the folder structure I had setup, it simply added a 2nd user--as "New" (it's Own user)---and completely "Left alone" (****PERFECT FOR ME*****)--the satUrn (correct)  folders, files, etc etc. 
I click "Home" (would go into a tree see both satUrn and satrn--I cllick on satUrn (desired login)--my desktop,etc. was exactly as expected

Click satrn (bad-no U)--just a blank desktop as if new login. 

-----Thus I do not *THINK*--I somehow tangled them up. 

satrn (bad-no U)--I made sure I had everything I wanted (not much) before deciding to reinstall (aka--I saved 1/2 dozen files to desktop, etc.)---The size of satrn(bad no U)--was only 4-GB--total. Thus what I'm assuming is about a "fresh install"


```  

I can't simply "reinstall" (a brand new instance on this box--it's a "Production" box and I have about 1/2 one TB home folder. yes, 500GB home folder. No where to off load that and save to "hold" to then move back. 

If I lose that, I have an Anxiety induced meltdown   *grin*

___________________________________________________

```

2nd (and this might the be issue?

----when using satrn (bad--no U)-----I installed the Google  Desktop  Two Step Authenticator. (course when failed to notice was bad)-
I HAD NOT set up with SSH yet, etc. But do have it installed. 

I know that (very rarely)--2-step has caused problems with site logins-etc. (aka--if I have 2-Step installed, but allow an app acess to gmail--*sometimes* does not work due to that 2-Step. 
--so tossing out there in case it might be a "Suspect"

I thought about deleting the "hidden" google-authenticator file inside of the root of satrn (bad no U)--before reinstalling but DO NOT delete that. 

Should I boot to a command line and do so? ----


```




If you have no clue what I"m speaking of

```


Google 2-Step
http://www.google.com/landing/2step/

Google Authenticator for Desktop (lightdm or gdm plugin)
http://askubuntu.com/questions/193248/google-authenticator-for-desktop-lightdm-or-gdm-plugin

Configuring two-factor authentication in Ubuntu 14.04 using Google Authenticator
http://wiki.vps.net/vps-net-features/cloud-servers/configuring-two-factor-authentication-in-ubuntu-14-04-using-google-authenticator/


```

---

### Post by whereismymindat2 on 2015-04-09
2nd--If it matters. I can still "see" that wrong user. I booted a Live USB and see both folders......I guess I could "delete" that user---but don't want to do so until this issue is cleaned up. It might be something necessary to login to satrn (bad-missing U)---???

---

