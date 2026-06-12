---
title: "Locked myself out of Gnome. Need help"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Deeta on 2008-04-28
Hiya friends,

I just had the bright idea to share my home directory, which was then set by nautilus to be read by other people.

It seems this permission change causes me to be unable to log back into Gnome after a reboot.

So right now I am stuck in the recovery Console with a german keyboard layout but an US International Keyboard.

Could anyone tell me how

1. I can switch the recovery console keyboard layout to US INTL
2. to set the permissions in my home folder
3. what the normal permissions for my home folder are

Thanks :)

Deeta

---

### Post by bluefrog on 2008-04-28
dpkg-reconfigure console-setup  to fix the keyboard.

chmod -R 775 /home/your-user
chown -R your-user.your-user /home/your-user

usually home permissions are 770 (nothing for the rest of the world)

---

### Post by tamoneya on 2008-04-28
the typical permissions for /home/username are 755.  If you want to set these yourself just type```
sudo chmod -R 755 /home/username
```

---

### Post by dioukf on 2008-04-28
Let me sugest another way: 

Just create another user! useradd <newuser> -g admin (if you use this group you will have a new sudo power user). 

When you have the new user you can copy your files, see the default permissions...

---

### Post by Guilden_NL on 2008-04-28
> **dioukf said:**
> Let me sugest another way: 

Just create another user! useradd <newuser> -g admin (if you use this group you will have a new sudo power user). 

When you have the new user you can copy your files, see the default permissions...

Small problem - how do you set up the password?  I set up a new user and am locked out for lack of a password.  I tried the PWD used with the account to set up the second account - no go.

---

### Post by Deeta on 2008-04-28
> **bluefrog said:**
> dpkg-reconfigure console-setup  to fix the keyboard.

chmod -R 775 /home/your-user
chown -R your-user.your-user /home/your-user

usually home permissions are 770 (nothing for the rest of the world)


Thank you so much :) (subsequent posters may feel thanked too ^-^)

It worked like a charm. (Though the 'dpkg-reconfigure console-setup' routine asked some esoteric questions I seem to have guessed correctly and now in addition to having fixed my problem, my keyboard layout is correct and the terminal font looks far nicer :)

Toodles,
Deeta

---

### Post by Guilden_NL on 2008-04-28
> **Guilden_NL said:**
> Small problem - how do you set up the password?  I set up a new user and am locked out for lack of a password.  I tried the PWD used with the account to set up the second account - no go.
Answered it myself thanks to Google:

# sudo passwd newuser
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

Crazy stuff happening with the Cruddy Cowpie distro aka Hardy Heron.  I believe that it went backwards, hence the "C" designation by me.

---

