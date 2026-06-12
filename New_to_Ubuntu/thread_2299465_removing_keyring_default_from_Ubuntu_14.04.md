---
title: "removing keyring default from Ubuntu 14.04"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by oldhand2 on 2015-10-18
I have been searching all day for a means of removing (preferably) or at least deactivating the "keyring default" notice when attempting to connect to other networks.  So far I have seen and tried, if possible, numerous suggestions to do this without any results.  Most "solutions" relate to other versions of Ubuntu and there are no corresponding commands or windows in 14.04 to match with the shown instructions.  Has anyone had success in removing this feature  specifically for Ubuntu 14.04 ?(yes, I understand the purpose of the keyring feature as far as security is concerned) but right now I wish to toss security to the wind to connect to where I wish.  I have entered every password I have created since I started with Ubuntu about a week ago and still the keyring keeps telling me the password(s) is invalid.  My introduction to Linux is off to a rocky start but I really enjoy everything I have done thus far with the notable exception of the keyring.  Thanks

---

### Post by sandyd on 2015-10-18
Can you post the output of
```

ls -l ~/.local/share/keyrings
```

Thanks

---

### Post by oldhand2 on 2015-10-19
Thank you for your reply.  Entered command and output indicated "ls" invalid option. Try ls --help for more information.  Did this and received a long list of abbreviations for files, etc.  Greek to me.

(I just happened to return to another page by mistake when replying to your message and noted another user was having the same problem with keyring default.  He solved it by switching to Unbuntu Mint.  I will have to give this a try.)

---

### Post by vasa1 on 2015-10-19
> **oldhand2 said:**
> Thank you for your reply.  Entered command and output indicated "ls" invalid option. Try ls --help for more information.  Did this and received a long list of abbreviations for files, etc.  Greek to me.

(I just happened to return to another page by mistake when replying to your message and noted another user was having the same problem with keyring default.  He solved it by switching to Unbuntu Mint.  I will have to give this a try.)
When I run the command suggested by sandyd, I see this:```
04:39 PM ~ $ ls -l ~/.local/share/keyrings
total 0
04:39 PM ~ $ 
```
Maybe switching to Mint is a good idea. That should solve all your problems. All the best.

---

### Post by oldhand2 on 2015-10-19
My apologies Sandyd and Vasa1 -- I had entered two hyphens rather than one of wavey line things. (old eyes are not what they used to be.)  Here is the response received:

ls: cannot access -: No such file or directory
ls: cannot access l: No such file or directory
ls: cannot access /.local/share/keyrings: No such file or directory
/home/david:
DEBIAN        dnsmasq.conf.7z  etc                 opt       Templates
Desktop       Documents        Music               Pictures  usr
dnsmasq.conf  Downloads        NetworkManager.pid  Public    Videos

---

### Post by vasa1 on 2015-10-19
Please post the exact command you used, not just the output.

---

### Post by oldhand2 on 2015-10-19
Command used was:  ls - l ~ /.local/share/keyrings as suggested in post #2

---

### Post by howefield on 2015-10-19
> **oldhand2 said:**
> Command used was:  ls - l ~ /.local/share/keyrings as suggested in post #2

Try it without the space between - and l. Also remove the space after the ~ sign.

 ```
ls **-l** ~/.local/share/keyrings
```

---

### Post by vasa1 on 2015-10-19
> **howefield said:**
> Try it without the space between - and l. Also remove the space after the ~ sign.

 ```
ls **-l** ~/.local/share/keyrings
```

^^^ Whether you switch to Mint or something else, the terminal is very nearly the same and as tolerant (or intolerant). As you'll see when you run the command properly, spaces matter :)

---

### Post by oldhand2 on 2015-10-19
Shades of the 'ol DOS days!  Here's the latest response with your suggestions:

david@david-U210:~$ ls-l~/.local/share/keyrings
bash: ls-l~/.local/share/keyrings: No such file or directory

Got to go vote - the power-that-be is waiting.  Thanks you both for your help.

---

### Post by howefield on 2015-10-19
> **oldhand2 said:**
> Shades of the 'ol DOS days!  Here's the latest response with your suggestions:

david@david-U210:~$ ls-l~/.local/share/keyrings
bash: ls-l~/.local/share/keyrings: No such file or directory

Got to go vote - the power-that-be is waiting.  Thanks you both for your help.

Are you being deliberately obtuse ? :)

You weren't asked to remove all spaces, only the 2 that you inserted for some reason.

---

### Post by vasa1 on 2015-10-19
Just out of curiosity:```
05:37 PM ~ $  ls - l ~ /.local/share/keyrings
ls: cannot access -: No such file or directory
ls: cannot access l: No such file or directory
ls: cannot access /.local/share/keyrings: No such file or directory
/home/vasa1:
06_39rsync.log  Desktop    Downloads  Music  Pictures  Templates
bin             Documents  Dropbox    MyFox  Public    Videos
05:37 PM ~ $ 

```whereas OP got```
 ls: cannot access -: No such file or directory
ls: cannot access l: No such file or directory
ls: cannot access /.local/share/keyrings: No such file or directory
/home/david:
DEBIAN dnsmasq.conf.7z etc opt Templates
Desktop Documents Music Pictures usr
dnsmasq.conf Downloads NetworkManager.pid Public Videos
```Note the **etc**, **opt**, and **usr**!

---

### Post by oldhand2 on 2015-10-19
Hello once again.  Sorry to drag this on for so long -- run the command again and received the following:

david@david-U210:~$ ls -l ~/.local/share/keyrings
total 8
-rw-rw-r-- 1 david david  15 Oct 13 20:46 default
-rw------- 1 david david 687 Oct 13 22:56 Default_keyring.keyring
-rw------- 1 david david   0 Oct 14 07:23 user.keystore

Doesn't make a great deal of sense to me but must mean something.  A bit of a learning curve for me. (Son-in-law installed Linux for me [at my request] but he is not too well-versed in the system either.

---

### Post by VMC on 2015-10-19
> **vasa1 said:**
> ...
Maybe switching to Mint is a good idea. That should solve all your problems. All the best.

I'd like to know how Mint addresses the keyring issue. What are they doing that stops the keyring password. I wonder if they pass on the login password to keyring somehow.

---

### Post by vasa1 on 2015-10-19
> **VMC said:**
> I'd like to know how Mint addresses the keyring issue. What are they doing that stops the keyring password. I wonder if they pass on the login password to keyring somehow.
Oh, that was inspired by OP:> (I just happened to return to another page by mistake when replying to your message and noted another user was having the same problem with keyring default. He solved it by switching to Unbuntu Mint. I will have to give this a try.) 
I don't know anything about Mint, Unbuntu or otherwise, or about keyrings.

---

### Post by Geoffrey_Arndt on 2015-10-19
Here is a link to a very short article that explains what often causes keyring issues, and what to do about it.   Suggest you read and see if this helps your situation.

By the way, in Linux, as in any other OS including Windows, it's NEVER a good idea to have "automatic" logins (e.g., logins should always require a password).   And if you don't know or can't remember the login password, all kinds of bad things can happen when you try to reset or change it.  Note the article was written for Ubuntu 13.10, but, it still applies to later versions including 14.04, 14.10, 15.04 and 15.10.

[URL="http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/"]http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/


[/URL]

---

### Post by sandyd on 2015-10-20
> **oldhand2 said:**
> Hello once again.  Sorry to drag this on for so long -- run the command again and received the following:

david@david-U210:~$ ls -l ~/.local/share/keyrings
total 8
-rw-rw-r-- 1 david david  15 Oct 13 20:46 default
-rw------- 1 david david 687 Oct 13 22:56 Default_keyring.keyring
-rw------- 1 david david   0 Oct 14 07:23 user.keystore

Doesn't make a great deal of sense to me but must mean something.  A bit of a learning curve for me. (Son-in-law installed Linux for me [at my request] but he is not too well-versed in the system either.

Type the following to remove your keyrings. Once they are deleted, there is **no** going back....

Please copy and paste, do not add any spaces unless you want to take out all your user settings.
```

rm -rf ~/.local/share/keyrings

```
Your keyrings are now all deleted.
New prompts will be created when you open an app that requires or wants you to enter a keyring password.
Please do not use a blank password.

---

### Post by vasa1 on 2015-10-21
> **sandyd said:**
> Type the following to remove your keyrings. Once they are deleted, there is **no** going back....

Please copy and paste, do not add any spaces unless you want to take out all your user settings.
```

rm -rf ~/.local/share/keyrings

```
Your keyrings are now all deleted.
New prompts will be created when you open an app that requires or wants you to enter a keyring password.
Please do not use a blank password.

Given the history of this thread, won't it be safer if OP **first** navigates to *~/.local/share/keyrings* and then issues a simpler *rm* maybe even with *-i*?

---

### Post by mcduck on 2015-10-21
> **VMC said:**
> I'd like to know how Mint addresses the keyring issue. What are they doing that stops the keyring password. I wonder if they pass on the login password to keyring somehow.

That's what Ubuntu does as well by default. Assuming you are using login password (so no automatic login) and haven't changed your password or the keyring password at any point (the keyring pasword is set to same as login password during the install, but after that I don't think it's updated automatically if you change your login password, so you'd have to do it yourself).

[https://wiki.gnome.org/Projects/GnomeKeyring/Pam]("https://wiki.gnome.org/Projects/GnomeKeyring/Pam")

Using automatic login or login without a password would mean there's no authentication at that point,  so the keyring isn't opened automatically either, and instead it'll ask you for the keyring password as soon as any application tries to access it. And same will happen if the login & keyring passwords are different, or if you have additional keyring with different password.

So why would moving to Mint change this? I actually think it wouldn't, or rather that since it's supposed to work correctly by default, having any problems means something has broken at some point. So probably a reinstall of Ubuntu itself would have given the same result. The again there could always be some issues between the display managers, Gnome guys of course have GDM as their highest priority, while Ubuntu uses LightDM and Mint uses MDM. The again, it would still have to be some local conflict or something broken on that user's specific system, as the automatic unlock is working correctly for most users on all of those display managers...

---

