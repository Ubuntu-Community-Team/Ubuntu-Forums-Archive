---
title: "Lubuntu: Returning to first installed version without loosing emails"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by rods on 2014-01-10
Hi, I installed Lubuntu 13.10 in my Asus EeePC a few months ago and love it. I've been using it as my main computer for emails and web browsing. I've been trying to understand a bit more about ubuntu/lubuntu. When trying (install and uninstall) new applications and tweeks I lost the configuration I had and got the main theme look like ubuntu but without lots of applications and shortcuts.
Is there a way to install everything again but without loosing my emails? Can I copy them to an external  drive and put them again in the same place after a new install?
Thanks
Rodolfo

---

### Post by Dave_L on 2014-01-10
How do you access your email?  With Thunderbird? From a web page?

If it's Thunderbird, you can save a copy of your profile folder (probably /home/USER/.thunderbird), which contains the email messages, settings, etc., and after the reinstall, copy the folder back into place.

---

### Post by rods on 2014-01-10
Thunderbird

---

### Post by TheFu on 2014-01-10
It depends on which email program you are using.  I use thunderbird and migrate everything ... data, settings, preferences, gpg stuff between systems all the time.  Thunderbird settings are binary compatible across Windwos, OSX, and Linux OSes.  Anyway, those settings are in somewhere like
~/.thunderbird/ or ~/.mozilla-thunderbird/ - so if you "backup" those areas only, then you can restore them later.

Also, you could just create a new userid (make a new account on the same machine) to get fresh settings, then copy over the email settings.  Almost everything, including user settings AND user data is relative to the "HOME" for each user. That means it is trivial to migrate all your personal settings and data between systems, since EVERYTHING related to an individual user's settings are in 1 place for a system.

I use the shell almost exclusively, so I can't explain how to accomplish these things using a GUI. Sorry.

---

### Post by rods on 2014-01-10
I'll try that. Thank you very much

---

### Post by oldfred on 2014-01-10
I regularly copy profiles for both Thunderbird and Firefox from Desktop to laptop & back when travelling.
I find in new install I need to go into program once to create new profile and then copy over old profile. I then edit profile.ini with old profile.

 new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

