---
title: "Forgot password, trying to set a new one"
date: 2020-03-10
forum: New to Ubuntu
---

### Post by meebers2 on 2020-03-10
Running Ubuntu on a stand alone computer using an SSD.  Ubuntu 19.04 was just upgraded to it and I do not remember my password. :(  I can get it sign in by doing a restart and holding down the Shift key and it boots and says I am signed in, but still do not know my password and want to reset/change it because it is only 5 characters long..  Tried holding down the Shift key during reboot to get to the Menu? for selecting Root and then using passwd etc.  Tried the same with ESC key as well no luck.  Sorry for wording, as I am a novice at this. Tx

---

### Post by Bashing-om on 2020-03-10
meebers2; Hello - Welcome to the forum :)

These instructions have served well to reset the your user account access:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by TheFu on 2020-03-10
Support for 19.04 ended 2 months ago.  Move to 19.10 ASAP.  There isn't any other choice.

---

### Post by Bashing-om on 2020-03-10
Ouch !

+10

---

### Post by meebers2 on 2020-03-10
Tried to do an upgrade from the terminal, but 2nd line in asks for my PW :-(  OK Thanks..will be back in a while :-)

---

### Post by CelticWarrior on 2020-03-10
Upgrading an EoL release isn't worth the time and effort even if you knew the password...
If you can autologin somehow as you say, just backup your personal files and install a supported release from scratch.

---

### Post by DuckHook on 2020-03-10
Welcome to the forums, meebers2,

I'm not trying to be insensitive—truly I'm not—but there are so many red flags being raised by your approach to computing:

[list=1]
[*]Do not wait for releases to expire before upgrading.
[*]In your case, I would strongly recommend that you stay with LTS releases. They're good for up to five years so there's less risk of falling behind on the upgrade hamster wheel.
[*]Many new members bring their bad Windows habits along with them when first starting out. One of the worst of these habits is bypassing challenge/response authentication at login through activation of the autologin "feature". This is a very pernicious habit, as you have now discovered. It is not simply the trouble caused when you forget that password only to find that you really need it, it is a bigger problem because it leads to very shoddy security habits.
[*]A five letter password is, candidly, awful. May as well not have a password. It can be brute forced in milliseconds, promotes a false sense of security and is the worst of all worlds: not secure enough to matter, yet every bit as inconvenient as a good passphrase.
[*]The best compromise between security and convenience is a passphrase. It's not perfect, but it's far better than what you are doing now. For instructions and the theory behind it: [https://www.useapassphrase.com/](https://www.useapassphrase.com/)
[/list]
I know this doesn't help you with your immediate problem, but once that is solved using Bashing-om's instructions, you may find the above useful. For further reading on security, please click the link in my sig: "Security Basics"

---

### Post by meebers2 on 2020-03-11
Appreciate your comments ___Really I do _____.  I originally installed from scratch 1804.4 LTS and on the day of my original post, I was trying every 5 letter PW that I could think of for 2 days, No luck.  Tried my notes when I originally installed but none worked. So I attempted to shut down and got a warning message that I should not shut down because there was a download  in progress.  I waited until finished and that is when I found out that it had upgraded to 19.04..  Fu recommended I update ASAP to 19.10. (post #3).  I can only "assume" my PW is 5 characters long as it shows *****.  I have seen some others PW sign in software that may only show ***** but in reality there is many more characters.  Like I said in the beginning, I am new to this and thus far I have yet to learn how to save doc's/files etc.  ¯\_(&#12484;)_/¯ so nothing lost if I start from scratch again.    IF I re-install 18.04.4 LTS again, not sure what would prevent it from upgrading again to 19.04.  Tx for your comments.

Just tried a 13 character phrase in your link and got Approximate Crack Time: 14,187 centuries,  so that may be good enough :-)

---

### Post by yancek on 2020-03-11
> not sure what would prevent it from upgrading again to 19.04. 

Ubuntu doesn't automatically upgrade.  There is a difference between setting up automatic updates and  upgrading to a new version which is explained at the link below.

[https://askubuntu.com/questions/974455/will-ubuntu-auto-update-to-the-next-version](https://askubuntu.com/questions/974455/will-ubuntu-auto-update-to-the-next-version)

---

### Post by meebers2 on 2020-03-17
Update:  Sort of gave up on 19.04 because of the forgotten password.  Installed 19.10 and exercised it for 3 days and decided it was to slow and to me not friendly. :-(  So this time I installed Mint 19.3 and have been running it for 3 days now and am very happy with this installation.  It is so much faster than 19.10 and I can get "around" with it, besides it is an LTS version.  Thanks for all the help from the above posters.  p.s. Have PW written down in at least 3 places so being near 80 I believe I have my bases covered.

---

### Post by TheFu on 2020-03-17
> **meebers2 said:**
> Update:  Sort of gave up on 19.04 because of the forgotten password.  Installed 19.10 and exercised it for 3 days and decided it was to slow and to me not friendly. :-(  So this time I installed Mint 19.3 and have been running it for 3 days now and am very happy with this installation.  It is so much faster than 19.10 and I can get "around" with it, besides it is an LTS version.  Thanks for all the help from the above posters.  p.s. Have PW written down in at least 3 places so being near 80 I believe I have my bases covered.

Never write the full password down anywhere.  Keep 10 characters in your head and write down the other 20.

---

