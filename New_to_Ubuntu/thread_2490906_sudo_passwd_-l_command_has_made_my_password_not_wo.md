---
title: "sudo passwd -l command has made my password not work in terminal"
date: 2023-09-20
forum: New to Ubuntu
---

### Post by ChrisMacor on 2023-09-20
I wanted to stop having to enter my password every time the screen went to sleep so I used the sudo passwd -l  username command.
Now my password does not work in terminal.
Any suggestions?
Thanks for your help,
Christopher
[COLOR=#F8F8F2][FONT=Hack]
[/FONT][/COLOR]

---

### Post by rudratrivedi on 2023-09-20
Hello Chris,

`passwd -l` locks your account by changing to an impossible value.
This prevents the specified account from being able to login. 
Usually you would run `passwd -u` to unlock it, but this won't work in your case.

You might need to boot from Live media and edit the `/etc/shadow` file, and remove the "!" in front of your hashed password. Save and reboot.

Man page for passwd: [https://manpages.ubuntu.com/manpages/jammy/en/man1/passwd.1.html](https://manpages.ubuntu.com/manpages/jammy/en/man1/passwd.1.html)

---

### Post by TheFu on 2023-09-20
> **ChrisMacor said:**
> I wanted to stop having to enter my password every time the screen went to sleep so I used the sudo passwd -l  username command.
Now my password does not work in terminal.
Any suggestions?


From the passwd manpage:

```
       -l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a ´!´ at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH
           key). To disable the account, administrators should use usermod
           --expiredate 1 (this set the account's expire date to Jan 2,
           1970).
           Users with a locked password are not allowed to change their
....

```

Best not to run commands without understand what the options do.  Always check the manpage, preferably the manpage ON YOUR COMPUTER, since things change from time to time and the local manpage will match the version of the program you have installed.

Basically, you have 4 options:
[LIST]
[*]Use another account that can change user's passwords - do you have another account on the system that has sudo rights?
[*]Use recovery mode, from the Advanced Grub Boot option, get a root shell, change the password for your userid. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[*]Boot from alternate media, setup a chroot so use the passwd and desired passwd DB, then change the password that way. [https://www.howtogeek.com/1292/reset-your-ubuntu-password-easily-from-the-live-cd/](https://www.howtogeek.com/1292/reset-your-ubuntu-password-easily-from-the-live-cd/)
[*]Do a fresh install, overwriting the existing OS, settings, users, etc AND the current passwd DB
[/LIST]

I trust you can google for how to do each of those, if you need more help.

What's that old saying .... "look before you leap."

There's a website that will accept a command and options, then use the generic manpages to show relevant parts.  Explainshell.something, I think.

---

### Post by MAFoElffen on 2023-09-20
+1 for option #2 of TheFu's answer.That is what I would recommend...

---

### Post by ChrisMacor on 2023-09-21
Thanks everyone for your input.
I'll try option #2.
Christopher

---

### Post by ChrisMacor on 2023-09-21
Ok, I'm in recovery mode, in my root account.
When I do passwd -u command it gives me 
Usage passwd [options]  [Login}
and a list of 15 options.
When I try the passwd -u again it doesn't return with the password unlocked.
When I try the passwd -d it doesn't return with the password deleted.
When I do passwd -S it returns
root L 09/16/23 0 99999 7 -1

Am I in the correct directory?
Am I using the correct commands?
Again, thank you for your help!
Christopher

---

### Post by MAFoElffen on 2023-09-21
LOL. Okay

Read this first (from man passwd)
```

       -u, --unlock
           Unlock the password of the named account. This option re-enables a
           password by changing the password back to its previous value (to
           the value before using the -l option).

```
See where that says "of the named account"? you have to specify the name of the account you want to unlock...

The format of the command in that, from a root prompt, would be
```

passwd [option] <user_name>

```
So, lets say the username of the account your locked was "fred123", then an example of unlocking fred123's account from a root prompt would be
```

passwd -u fred123

```
Is that enough information to do that, or do you have other questions?

EDIT -- After that is done, then I'll explain how to set your account up to do an autologin, which is what you were trying to do, when this happened...

---

### Post by ChrisMacor on 2023-09-22
That's great MAFoElffen!
I'm back into my Ubuntu installation.
Thanks so much for your help with this!
Yes I'm ready to know how to do autologin.
Christopher

---

### Post by MAFoElffen on 2023-09-22
Great. Glad that goal #1 is achieved. 

Now for goal #2...

In the upper right of the task bar, Click on the icons, then open Settings from the drop down menu. In the left panel of Settings, open "Users". In the upper right where it says "Add Users and change settings", select the Unlock button. Once it unlocks the settings there, in the middle of that panel in the User that you want to modify, select the radio button there for "Automatic login". Select the button that says Lock.

Reboot and test.

Tell me how that goes.

---

### Post by TheFu on 2023-09-22
First, learn to read the man pages on your system.  You can avoid most of these things by doing that BEFORE you enter commands.

---

### Post by ChrisMacor on 2023-09-22
I'm still getting an Keyring authentication request on reboot. Is that expected, MAFoEllffen?

---

### Post by ChrisMacor on 2023-09-22
And it's asking for a password after the screen goes blank.
thx again,
Christopher

---

### Post by ChrisMacor on 2023-09-22
Did the user automatic login button and reboot but Ubuntu is still asking for a password on login and after the screen goes blank.
Thx again,
Christopher

---

### Post by TheFu on 2023-09-22
[https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en) might help according to google.

---

### Post by MAFoElffen on 2023-09-22
For the Lock screen: From the Settings menu, select Privacy, and then select Screen Lock. On the Screen Lock page, toggle the Automatic Screen Lock switch from On to Off.

@TheFu -- The instructions I gave him are using the same panel in Settings with the same On/Off control...

@ChrisMacor --- You are saying that with the "Automatic Login" control set to "On" that is still will not login without a password?

If not, I could probably lead you through manually creating a SystemD Getty over-ride, but I that makes me vervous letting you loose with that, I would feel better if you were not "New to Ubuntu". Because that would involve manually entering in commands, and manually editing a systemd service file with elevated permissions. I do it, but I have a few skills. You, being unskilled, things could go wrong with that. And if it goes south, you would have to chroot into it to back off the override. Just saying, the alternate method has some risks.

---

