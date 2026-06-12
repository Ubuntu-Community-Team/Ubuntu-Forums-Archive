---
title: "CLI user/password is &quot;incorrect&quot; but actually isn't"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by 2muchcoffeeman on 2012-03-04
The values in this message are fake, but the situation is real:

My Ubuntu account name (the name that appears on the login screen when booting up Ubuntu) is XXXX
My password is YYYYYYYY.

But when my browser freezes (seems to be a common experience, first with Chrome and now with FF), and I hit ctrl-alt-F1 to invoke Command Line Interface, the login procedure will not accept these same credentials.

On the CLI screen, I am prompted with "login." I enter XXXX.
Then, I am prompted with "password." I enter YYYYYYYY.
Ubuntu then tells me the password is incorrect.

No, it's not. 

So, why do I get that error message?

---

### Post by fleamour on 2012-03-04
Have you checked Caps Lock?

---

### Post by 2muchcoffeeman on 2012-03-04
Yes. Caps lock is not engaged when trying to enter login/password combo in CLI. Thanks.

---

### Post by presence1960 on 2012-03-04
> **2muchcoffeeman said:**
> Yes. Caps lock is not engaged when trying to enter login/password combo in CLI. Thanks.

Don't use the numeric keypad if you have one for numbers in your password in this situation, instead use the keys above the qwerty keyboard for numbers. Example for "1" use the key with "1 and !", for 2 use the key with "2 and @".

---

### Post by 2muchcoffeeman on 2012-03-04
My computer does not have a numeric keypad. I use the numbers that run left-to-right above the qwerty keyboard. Thank you.

---

### Post by fleamour on 2012-03-04
Does it work when entering password for, say, updates?  The freezing may pre-empt the trouble you are having.

---

### Post by 2muchcoffeeman on 2012-03-04
Thank you, yes, when I am asked to "authenticate" when running updates or installing a new package, the password is accepted. No Issues.

The irony here is that I am needing to resort to the CLI to *fix* the browser freezing, as instructed elsewhere in the forums.

---

### Post by Lokireloaded on 2012-03-04
does ctrl + alt + t not work?

---

### Post by fleamour on 2012-03-04
A system that unstable is bad news! :(

Has it always done this?  I can only suggest re-setting password, but all in all that is most probably of no help.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by 2muchcoffeeman on 2012-03-04
> **Lokireloaded said:**
> does ctrl + alt + t not work?

I'm using ctrl-alt-f1 per the instructions of [this post]("http://ubuntuforums.org/showpost.php?p=11612865&postcount=3") elsewhere in the forums. Occasionally the entire system, and not only the browser, would freeze up. On those occasions, the indicator light on the computer that signifies the CPU is in use would light up, and would remain lighted. No blinking, no on-and-off, but a steady light. The computer would not respond to any input -- keyboard or mouse. This happened when I would be running Chrome for a long time, meaning many hours consecutively. During those episodes, the computer would not respond to the ctrl-alt-T command. During those same episodes, it *would* respond to ctrl-alt-f1, but then it would not accept my login credentials. 

The problem appears to have abated now that I've begun to use FF instead of Chrome. But FF did freeze up tonight (other programs were not frozen and the computer responded to key/mouse input), and I tried ctrl-alt-f1 command, only to run into the login roadblock again.

---

### Post by winh8r on 2012-03-05
This may or may not apply to you , but make sure that your username does not have any spaces in it.

For instance , if the username you see in the login window is Bob Smith, then Ubuntu will shorten this to bobs as it does not allow empty spaces in usernames.

This becomes apparent when trying to login using the console as it WILL NOT authenticate with anything other than the shortened name, no combination of bobsmith, Bob_Smith will do it it will only work if the correct shortened form is used.

Best way to check what name is being used is the command:

```
whoami
```


I believe that a lot of confusion has arisen over this as people may have written down their username and password as they entered it when they installed Ubuntu, but may be unaware of the system removing spaces like this.


If this is not the cause of your problem them I apologise for crashing in like this , but it may come in useful someday to someone reading this thread.

---

### Post by Diametric on 2012-03-05
What kind of hardware are you running?

---

### Post by 2muchcoffeeman on 2012-03-06
**winh8r**: Thank you, yes, my account name is four letters long, with no spaces, like this: Dave

I checked [FONT="Courier New"]whoami[/FONT], and the result of the query was: Dave

So, it appears the potential spacing issue is not what's going on here.

**Diametric**: Pretty basic rig:
[INDENT]Dell Latitude D630
64 bit
2.0 GB memory
Intel Core 2 Duo CPU T7300 @ 2 GHz x 2
[/INDENT]

---

### Post by yetiman64 on 2012-03-06
> **2muchcoffeeman said:**
> **winh8r**: Thank you, yes, my account name is four letters long, with no spaces, like this: **D**ave

I checked [FONT=Courier New]whoami[/FONT], and the result of the query was: **D**ave

So, it appears the potential spacing issue is not what's going on here....
If your username has a capital letter, this like the spacing can cause issues. User names are best all lower case with no spacing or special characters.

Below link is a bug report (although marked as invalid, please read the reply #2, mentions mail systems that automatically lower case your username, I'm thinking in your case the tty terminal might be doing the same thus mismatching the user name - case sensitive)

[[COLOR=Blue]Ubiquity bug link[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/127967") (invalid as a bug, but reply #2 possibly explains the problem with a tty terminal.)

The capital D may be fine for normal use but the tty terminal (ctrl + alt + F1) may be choking on the capital letter (maybe because it lowercased it automatically).

I'm actually surprised you managed to make an account with capitalization, I tried to recently and the installer put up a warning (Ubiquity is the installers application - same situation for me as in the bug linked).

---

### Post by 2muchcoffeeman on 2012-03-06
**yetiman64**: Aha! Yes! The capitalization was the issue. When I used a lower-case letter on the name in response to the "login" prompt, and then entered the password, Ubuntu approved the credentials and I was in business.

I don't know how to explain why, when I boot up Ubuntu under normal circumstances, the login screen shows my user name with a capital first letter. (Also, when invoking the whoami command, the result is the name with a capital first letter).
[B] 
Thank you[/B].

---

### Post by yetiman64 on 2012-03-06
> **2muchcoffeeman said:**
> **yetiman64**: Aha! Yes! The capitalization was the issue. When I used a lower-case letter on the name in response to the "login" prompt, and then entered the password, Ubuntu approved the credentials and I was in business.

I don't know how to explain why, when I boot up Ubuntu under normal circumstances, the login screen shows my user name with a capital first letter. (Also, when invoking the whoami command, the result is the name with a capital first letter).
[B] 
Thank you[/B].
Reading the Ubiquity bug report (invalid as it is) twigged me onto the idea the tty terminal was automatically lowercasing the username, just like the mail systems mentioned in the second reply. 
The main system (log in screen included) is a bit more tolerant of case than specialized utilities like tty terminals, and as a result can make for some interesting situations :).

Glad to hear you can now use the tty terminal. You're most welcome :-).

---

### Post by winh8r on 2012-03-06
Glad you got it solved!

I suppose I should have noticed when I discovered that Bob Smith became bobs, that in addition to removing spaces it also replaced upper case letters with lowercase.

Oh well, we live and learn.

Well spotted yetiman64!

---

