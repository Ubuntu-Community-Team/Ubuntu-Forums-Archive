---
title: "Changing the default 644 ownership of your home dir."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Roasted on 2008-05-12
So, I just did that. I changed it to 777 like an idiot. Now whenever I try to log in, it prompts me with an error. I logged into terminal failsafe and did a chown 644 (like it should be) to my home dir, yet I still get the errors. I'm reinstalling as we speak, but I'd like to know what I should have done to fix it for future reference.

---

### Post by jnorth on 2008-05-12
> **Roasted said:**
> So, I just did that. I changed it to 777 like an idiot. Now whenever I try to log in, it prompts me with an error. I logged into terminal failsafe and did a chown 644 (like it should be) to my home dir, yet I still get the errors. I'm reinstalling as we speak, but I'd like to know what I should have done to fix it for future reference.

LOL - been there done that.  Remember what the error was?  I'm betting something like "$Home directory must be owned by user and not writable by other users."

Anyway, I found it easier to just back up my entire /home/user directory to a usb drive and reinstall, then copy files back over (which defaulted them to the correct permissions).

You could log in with another sudo-capable user if you have one, or if not, boot up from a livecd and change the permissions on that file to get you back in, but fixing everything else is more than I care to get into.

Something like ```
chown -R user:user /home/user
chmod 644 /home/user/.dmrc
```

---

