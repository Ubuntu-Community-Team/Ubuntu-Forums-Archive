---
title: "FYI - Mostly as Google Chrome is Unsupported"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-07-31
The day before UbuntuForums.org was broken into, the Update Manager installed some Google Chrome or Chromium Browser updates. I cannot recall which it was. The next day, upon a cold boot, Chrome and Chromium would no longer work. Firefox would not work either, but said the profile.ini was missing or corrupted. I deleted that and re-started FF. Now it's working. I next installed Opera as a safety backup browser.

After some netsearching, I find that there is little on the 'net about this problem. Next I found how to uninstall the two browsers. I was using sudo su - for some of it, and eventually removed all traces of those apps.

Next I tried re-installing them. That failed. Another uninstall and removing files with sudo su - . Another attempt at re-installing. No success.

As this Forum was down I could not post here, even though the Chrome is unsupported. And I don't know about support for Chromium.

Due to the timing of this, I (conspiracy theory) believed maybe my computer had been hacked. But as I have distinct passwords for this Forum, and all processes requiring a PW, it's unlikely that my computer had been infected with malware. Still, the timing made me think it possible.

Running chromium-browser from a terminal returns a "Aborted (core dumped)". A moment later, I get an Apport Msg. about SIGBART in () raise and try to report that. But as Chrome/Chromium is down, the report doesn't go through as the browser doesn't open the site that takes reports.  I also tried to report this problem at the Google+ site, but as the only error message I can give is the "Aborted (core dumped)", they think I'm the only person with this problem on the entire internet. And maybe I am, but I got another Google Chrome update today and it's not working, either.

Anyway, this is an FYI as I don't know what question to ask I've uninstalled and re-installed more than once, so maybe the problem is with Google.

---

### Post by Paqman on 2013-07-31
Have you tired running Chrome in another user account?

---

### Post by Mark_in_Hollywood on 2013-08-01
> **Paqman said:**
> Have you tired running Chrome in another user account?

I have created a new "user" with the name: chromeuser.

This was done with sudo adduser chromeuser

the same PW was used for myself and chromeuser

and chromeuser was give root privileges this way:

sudo /usr/sbin/visudo

# User privilege specification
root    ALL=(ALL:ALL) ALL 
chromeuser	ALL=(ALL:ALL) ALL

I logged off of user (me) mark

and tried to login as chromeuser and the login screen accepts the password, but does not go forward to the desktop.

If a Board Administrator is reading this, could you please move it to Abs. Beginner's?

---

### Post by cariboo on 2013-08-01
Moved by request.

---

### Post by Copper Bezel on 2013-08-01
This is not a solution to your problem, but I ran into it because of your post, and it does fill me with glee: there's actually [a workaround]("http://askubuntu.com/questions/5410/how-to-run-an-application-as-another-user/261799#261799") to run graphical apps from another user's account within yours. Doesn't work for the provided guest account, though (sadface.)

---

### Post by Mark_in_Hollywood on 2013-08-01
Ahhh, on rebooting the computer, the user: chromeuser is a workable user and Chromium ran without problem. Chrome would not run.

---

