---
title: "Google Chrome won't open"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by CMac12 on 2013-02-15
I accidentally used to run 32 bit Ubuntu on my 64 bit Laptop. I recently fixed this by backing up my files and then re-downloading Ubuntu and all was good, however when I tried to download Google Chrome and open it I got this message

'The profile appears to be in use by process 18732 on host cameron-Dell-System-Inspiron-N7110. If you are sure that no other processes are using this profile, delete the file /home/cameron/.config/google-chrome/SingletonLock and restart Google Chrome'

The process and file that the error message give don't seem to exist on my Laptop. Can anyone Help?

[CENTER]Thanks
[/CENTER]

---

### Post by sleash78 on 2013-02-15
32 bit works on 64 bit processor computers.  commands i'd try to use are  sudo apt-get --yes purge chromium-browser && sudo apt-get --yes install chromium-browser  that will reinstall chrome basically.  also u might want to see if it's your personal settings, so i'd move the chrome folder and try it like u just freshly installed it.  first make sure you close chrome  try  mv /home/$USER/./.config/chromium/ /home/$USER/./.config/old_chromium/ ; mv /home/$USER/./.cache/chromium /home/$USER/./.cache/old_chromium  restart chrome  good luck

---

### Post by DuckHook on 2013-02-16
> **CMac12 said:**
> The process and file that the error message give don't seem to exist on my Laptop

Are you sure of this? Do:```
ps -ef | grep 18732
```...being mindful that next time, you will have a different process number, so replace 18732 with whatever the new process is.

Also, make sure you are seeing all hidden files in Nautilus by doing <Ctrl>+<h>. Hidden files begin with a dot as in .config, so drill down to make sure that .../google-chrome/SingletonLock is really not there.

---

### Post by VeeDubb on 2013-02-16
One option, which usually works provided you have a google account and previously had chrome set to sync everything with that account, is to simply delete your profile for chrome.  It's found at ```
/home/YourUserName/.config/google-chrome
```

Whenever I've had to delete mine, I'll get an error that it was unable to delete because a file is in use, but it deletes everything except ```
/home/YourUserName/.config/google-chrome/Default/User StyleSheets/Custom.css
```

Even if you force delete it through the terminal, that file will re-create itself almost instantly.


Anyway, that's worked for me any time I've had any problems with chrome and profile errors.  As soon as you log back into your google account all of your bookmarks, settings, saved passwords, and plugins will be restored within a matter of minutes (although you won't see some of the plugins until you restart chrome).

Again, that only works if you set chrome up to sync everything to your google account.  If not, you'll loose anything that isn't kept in sync.

---

### Post by CMac12 on 2013-02-16
Tried the Ctrl h and the hidden files came up fine, deleted it like it said and now it works fine

Thanks very much!

---

