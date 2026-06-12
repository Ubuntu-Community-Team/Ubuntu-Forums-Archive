---
title: "can login, but it reloads the login screen?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Sarannen on 2008-06-19
I installed Ubuntu Desktop Edition "into" Windows XP Home Edition SP2. The install went fine, the computer rebooted just fine. I choose Ubuntu from the boot menu. It went through it's additional installation features there.

When it was done, it displayed the login screen. I entered the username and password that I had previously chosen. I heard music playing, the screen was replaced by a plain orange-ish background, then the login screen reappeared. I tried using the GNOME GUI instead of the default with the same results.

I've done a quick search through the forums via Google, but have not found anything similar to this.

Any help would be very much appreciated!

---

### Post by tjwoosta on 2008-06-19
hmmm...

is it possible that your password somehow got mixed up?

cuz thats what normally happens when you have the wrong info, it will just start to load and go right back to the login screen

---

### Post by Duck2006 on 2008-06-19
What video card are you running. It sound like it may not have installed right.

---

### Post by markbuntu on 2008-06-19
Did you try the gnome safe mode?

---

### Post by Sarannen on 2008-06-19
Ahh, that could be. I figured it would show an error that there was a wrong password?

(Yup, complete newb here.)

Thanks :) I'll try that and let ya know how it goes! :)

---

### Post by Sarannen on 2008-06-19
Ack, a ton of replies showed up all of a sudden. My first post was to tjwoosta.

Duck2006: My video card is ATI Radeon Xpress 200 series.

markbunto: No, I haven't tried safe mode. Will try that after the password thing.

---

### Post by Duck2006 on 2008-06-19
If it is your pass word (you have forgotten), then your have to start up in recovery mode and reset it. From the promp type

sudo passwd <user name>
type the new pass word in and retype it in and then,

reboot

---

### Post by markbuntu on 2008-06-19
I had this problem and it was some missing files. If gnome safe mode gets you in look in the System/Adminstration/System Log files for a message like

authentication failed, blah blah blah could not open... missing file blah blah blah

I wrote down what was missing and installed them with synaptic and that fixed my login problem.

---

### Post by Sarannen on 2008-06-19
I had the password right apparently. When I intentionally typed a wrong one, it gave me an error.

Logging in via GNOME failsafe mode worked great.

So, now that I'm in safemode...is there something in particular I should do to fix my little issue?

Thanks!!

---

### Post by Sarannen on 2008-06-19
Ok, working on that now, mark. Thanks :)

---

### Post by Sarannen on 2008-06-19
markbuntu: I can't seem to find anything quite like that. The closest I can see is:
Jun 19 20:21:41 sora-desktop gdm[5635]: WARNING: Couldn't authenticate user 

I've gone through all the logs; no luck finding anything that's missing.

---

### Post by markbuntu on 2008-06-19
OK then, we have made some progress. Go to System/Administration/User Profile Editor and see if your password works there.

---

### Post by Sarannen on 2008-06-19
System/Administration/Users and Groups is what I've got. I tried it there, and it worked. It also worked upon downloading some updates (decided to see if maybe they help me out at all).

The updates are almost done installing.

---

### Post by markbuntu on 2008-06-19
Sorry, it has been a few months since I has this problem and I had to find my notes.

 Not all the logs are shown. in the System Log Viewer so go back to the log and go to File Open and open the auth.log

Look in there.

If you see a message like:

May 23 17:09:36 mark-desktop gdm[5479]: pam_smbpass(gdm:auth): unrecognized option [missingok]

Then you can fix it by using Synaptic to install

libpam_smbpass

just use the search function in Synaptic and click install and then apply.

---

### Post by Sarannen on 2008-06-19
Ok, I have to wait for the updates to finish before it will let me use Synaptic.

Thanks for your patience and help!

---

### Post by markbuntu on 2008-06-19
Logout and then try to login. If it doesn't work then go back in with gnome safe mode  and look for this in one of the logs

May 23 18:36:43 mark-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

You can fix this by installing nscd with Synaptic and then you should be able to login normally.

It is a weird thing. It happened to me and a few other people when we first installed 8.04. After your updates just try to login normally before you do these things. The updates may have the fixes already.

Does your computer have an AMD64 xx00+ cpu?

---

### Post by Sarannen on 2008-06-19
Restarted, same problem.

Going to try reinstalling packages now :)

---

### Post by Sarannen on 2008-06-19
No luck. Installed, restarted. I did, however, get a new popup... "User Sarannen added"

and it then proceeded to send me back to the login screen.

---

### Post by Sarannen on 2008-06-19
Oh, and the CPU is AMD Sempron 3400+.

---

### Post by Sarannen on 2008-06-19
Hey, sorry to dip out on you like this when you're being so helpful, but it's my bedtime. Early workdays kinda kick my **** :(

I'll be online again at the latest of Saturday.

---

### Post by markbuntu on 2008-06-19
OK. Send me a message when you get back on.

---

