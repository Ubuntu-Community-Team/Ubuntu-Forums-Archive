---
title: "Keyring not unlocking when logging in (Firefox?)"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-08
Hello all

Is there any way for this to stop coming up? I'm the only person who uses this machine and I'd like this to auto unlock on my log-in or just be unlocked by default.

Sometimes I can browse around for like 20 minutes before it appears.

[[IMG]http://s29.postimg.org/6egxhc2ub/IMAG1700.jpg[/IMG]]("http://postimg.org/image/6egxhc2ub/")

Please excuse the camera-phone picture of the screen. This prompt prevents me clicking on anything else, including not allowing me to screenshot the message.

---

### Post by ian-weisser on 2014-05-09
You usually get this prompt if your keyring password doesn't match your login password.
Are the passwords identical?

---

### Post by Drowz0r on 2014-05-09
Yeah the passwords are the same.

---

### Post by Drowz0r on 2014-05-12
Is there some kind of "registry" update or something I need to do?

---

### Post by grumblebum2 on 2014-05-12
I believe the login keyring is not unlocked when you set your user account to automatically login.
Chrome saves passwords here so it is probably asking to unlock.
I think the only way to change the behaviour is to set your account not to autologin
and just login manually.
Either way you need to manually login once but at least this way it's not random.

It is also possible to set a blank password for the login keyring
which will leave any passwords unencrypted.
ie **~/.local/share/keyrings/login.keyring** will be accessible as a plain text file.

Personally I would just spend the extra couple of secs to login manually.

---

### Post by squakie on 2014-05-13
When I was running 13.xx I didn't get this request even though I was set for auto-logon.  With 14.04, I've tried logging out, logging in, power cycle, etc. - still comes up with this same request.  Didn't something like PAM handle this previously?  Is there some option we need to set with it (or it's replacement)?

---

### Post by Drowz0r on 2014-05-13
Yeah on 12.04 LTS I didn't have this prompt and I've always had auto-log in running...

I'm curious to know if there is a way to stop it but keep the encryption.

---

### Post by mcduck on 2014-05-13
> **squakie said:**
> When I was running 13.xx I didn't get this request even though I was set for auto-logon.  With 14.04, I've tried logging out, logging in, power cycle, etc. - still comes up with this same request.  Didn't something like PAM handle this previously?  Is there some option we need to set with it (or it's replacement)?

PAM handles it automatically, but it can only do so once you have already confiremd you really are yourself (by logging in with a password).

If you use automatic login, the only way to avoid the popup for unlocking the keyring is to not have a keyring password. Which of ocurse doesn't make much of a difference any more, if you are OK with leaving your whole user account unsecured then doing the same for the keyring shouldn't be a problem either (and of course you can't have security without any kind of password confirmation anyway).

So, if you prefer using automatic login, the solution is to open the "Passwords and Keys" application, right-click on the "Login" keyring, select "Change Password", and once asked for new password leave the fields empty & click "Continue" to unset the keyring password.

---

### Post by mcduck on 2014-05-13
> **Drowz0r said:**
> Yeah on 12.04 LTS I didn't have this prompt and I've always had auto-log in running...

I'm curious to know if there is a way to stop it but keep the encryption.

What use would the encryption be, if anyone can just open your account and access the data without any kind of password confirmation?

---

### Post by Drowz0r on 2014-05-13
> **mcduck said:**
> What use would the encryption be, if anyone can just open your account and access the data without any kind of password confirmation?

I assume that the password would be parsed from the OS I am on to the browser so someone would have to be using my computer in some way in order to use my browser. If someone copied all the information my browser stored, the information would be encrypted and not unlocked until the password would be parsed from my OS, for instance.

---

### Post by mcduck on 2014-05-14
that someone would be able to get the keys needed to unencrypt the data just as easily as he'd be able to get the browser data itself if there isn't any confirmation (password) required from the user to access the encryption key.

---

### Post by squakie on 2014-05-14
I was rather stupid just using automatic login the last 2 times I've installed releases.  Talk about leaving the system wide open - anyone could access my PC since mine is the only log on, which means anyone could access EVERYTHING on the PC - and BTW Drowz0r I don't think encryption would help at all if anyone can have full access to your system because of auto-logon.

I'm not sure why I ever changed to auto-logon - I think it was about the time I was setting up an old laptop to "rescue" my brother in-law until I got his laptop reloaded, and I made that auto-logon for him - probably was just in my mind.

At any rate, I've gone back to requiring logon.

---

