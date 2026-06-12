---
title: "home folder encryption"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Viva on 2011-11-10
I chose to encrypt my home folder while installing oneireic. On the first boot, a window popped up telling me to do something important to complete the encryption process, but I overlooked it and closed the window. Was it related to setting up the pass phrase and key? How do I go about completing the process? Sorry for the lack of clarity about the actual message, it was late in the night and I overlooked it except for the fact that it was related to encryption of the home partition.

---

### Post by orange2k on 2011-11-10
It is a message telling you to write down the decryption key for your now encrypted home folder if case you ever had system brake down and want to retrieve the data from the home folder...

I also don't know how to make the system repeat that message...

---

### Post by Mark Phelps on 2011-11-10
If the encryption completed successfully, and you did not write down the passphrase, or otherwise remember what you entered -- you're HOSED!

Don't bother asking if there's any way to "crack" the password because there isn't.  And, it is not stored anywhere such that you can find it.

Basically, if you don't know what you're doing, you should not be messing around with encryption.

Don't use this myself, so my guess would be that you would have to reinstall to get access back.  And this time, reconsider your need for an encrypted /home folder.

---

### Post by Viva on 2011-11-10
Couldn't I just reinstall ubuntu? I can still log in to ubuntu btw.

---

### Post by dFlyer on 2011-11-10
If you can login and have access to your home folder you have nothing to worry about. Just write down your passcode and move on.

---

### Post by Rex Bouwense on 2011-11-10
You can always re-install, but unless you can back up any data, pictures,etc. that is on home, it will be lost.

---

### Post by Viva on 2011-11-10
> **dFlyer said:**
> If you can login and have access to your home folder you have nothing to worry about. Just write down your passcode and move on.

How do I find out the passcode?

---

### Post by U-Ren on 2011-11-10
If you used encryption, there is no way that your home folder will open unless you know the pass code or log on with your account. Trust me, I tried (lol-poor me!)
Do not re install without backing up the data, in fact, that will end any chance for you to access your files. Keeping your home folder encrypted has no problems unless your system dies as you won't be able to back them up say, with a Ubuntu live cd. Basically, you'll have to keep your files backed up at all times. 

I always use home encryption and I also tend to lose my pass codes. Back up is the only way to be sure that your stuff will be there no matter what.

---

### Post by Mark Phelps on 2011-11-10
> **Viva said:**
> How do I find out the passcode?

Basically ... you DON'T!

What would be the point of encryption if you could simply find out the passcode?

---

### Post by dFlyer on 2011-11-10
> **Viva said:**
> How do I find out the passcode?

If your home folder opened when you logged in you know the passcode because you would have had to use it. Otherwise your home folder isn't encrypted.

---

### Post by orange2k on 2011-11-11
> **dFlyer said:**
> If your home folder opened when you logged in you know the passcode because you would have had to use it. Otherwise your home folder isn't encrypted.

Thats not true. You still need that long password to recover data from the home folder if a system breakdown occurs. If the system works fine then you only need the login password, but only then. It is wise to write down that long password...

---

### Post by SlugSlug on 2011-11-11
that box that pops up asking to create a recovery code, -- mine popped back up after a reboot & I also noticed there is a command to run to force it to come back up... but i didn't take note sorry

---

### Post by Viva on 2011-11-11
Looks like the drive wasn't encrypted after all. I could simply mount it from the live cd.

---

### Post by Viva on 2011-11-18
Just checked my log messages and found this.
> pam_ecryptfs: pam_sm_authenticate: /home/main is already mounted

Is this related to home folder encryption?

---

### Post by Viva on 2011-11-19
Bump

---

### Post by Viva on 2011-11-20
I need your help guys. Should I just re-install? I don't have any important data on the drive yet.

---

