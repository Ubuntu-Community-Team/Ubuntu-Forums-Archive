---
title: "Login Goes to Terminal Window"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by freedomAboveAll on 2012-11-24
Hello,
Having problem with the following symptoms:

Ubuntu 12.04 boots to the login screen.

Logging in goes to a terminal window instead of Unity desktop

The Netbook is an ASUS Eee PC 1215T-MU10-BK RT

Have been using netbook connected to a big screen TV and pressed Fn+F8 to toggle computer desktop to TV. 

From login screen, the guest account works!  

From regular account, the terminal window appears. :(

Thank you for any assistance.


Tried CTL+ALT+F8. 

Am doing this remote over phone for my parents, so step by step assistance appreciated, as I can not experiment.

---

### Post by freedomAboveAll on 2012-11-24
We also tried these 

```
Ctrl+Alt+F7

or

Alt+F7

or

Ctrl+Alt+F8
```


as described here:

[http://askubuntu.com/questions/157617/reverting-from-ctrl-alt-f1](http://askubuntu.com/questions/157617/reverting-from-ctrl-alt-f1)



Still get the $ prompt for the main user.

---

### Post by Bashing-om on 2012-11-24
login to the system from that terminal (username + password)
and:
what is the result of terminal code :
```
sudo service lightdm start
```?
lightdm is the desktop manager to start the GUI environment.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by RoosterHam on 2012-11-24
By terminal window do you mean that there's mouse pointer and windows but just a terminal like xterm rather than unity or any Desktop Environment? or is it going to a completely black window with text and no mouse pointer?

---

### Post by freedomAboveAll on 2012-11-24
Hello, and thank you for replies.  

My understanding is that lightdm, the screen you see here [http://en.wikipedia.org/wiki/LightDM](http://en.wikipedia.org/wiki/LightDM)  does comes up on boot.  (this image: [http://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/LightDM_1.2.1_on_Ubuntu_12.04.png/800px-LightDM_1.2.1_on_Ubuntu_12.04.png](http://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/LightDM_1.2.1_on_Ubuntu_12.04.png/800px-LightDM_1.2.1_on_Ubuntu_12.04.png)

It is the next step - after login - that the user sees the terminal window.    So the user has done something to their session to disable Unity.

I have a scheduled phone session with them in 12 hours, and will try the suggested command, and ask if there is a mouse or not.

---

### Post by freedomAboveAll on 2012-11-25
When user logs in from lightdm, gets an XTerm window that can not be minimized.

If we run this code:
```
unity --reset
```

( description found here: [http://ubuntuforums.org/showthread.php?p=12370451](http://ubuntuforums.org/showthread.php?p=12370451) )


then his desktop is restored !  The XTerm window is still there but is nice and windowed and can be minimized.

But this only works for as long as he is logged in.  If shutdown then log in again, the XTerm window appears again.

So how to keep his Unity desktop so he can log off & log on and it will still be there?

---

### Post by freedomAboveAll on 2012-11-25
This netbook was upgraded from 11.x series of Ubuntu, if that helps anyone.  It was not a clean install.  

It had been working fine until user did (**** mystery action ****).  I suspect was some keyboard variation of Fn F8 .

---

### Post by mcduck on 2012-11-25
Make sure the session is still set to Unity (or Ubuntu, I can't remember which name is used).

This is selected in the login screen by clicking on the Ubuntu logo right of the username.

---

### Post by freedomAboveAll on 2012-11-25
> **mcduck said:**
> Make sure the session is still set to Unity (or Ubuntu, I can't remember which name is used).

This is selected in the login screen by clicking on the Ubuntu logo right of the username.
Awesome!  Thank you!  I have not tried reboot yet, but found the session was set to xterm.  This looks like the issue.

This is what I found and what I did.  ( I currently have remote software installed but works on in user session, so have to locate and edit session preferences.)

According to: [http://askubuntu.com/questions/145359/how-can-i-make-unity-2d-the-default-session-at-start-up](http://askubuntu.com/questions/145359/how-can-i-make-unity-2d-the-default-session-at-start-up)


> Per-user settings are stored in either $HOME/.dmrc or in /var/lib/AccountsService/users/$USER . According to this post, the latter file may overwrite your .dmrc.


So in $HOME/.dmrc found this:

```

[Desktop]
Session=xterm

```

changed it to:

```

[Desktop]
Session=ubuntu

```

And in 

```

$ more /var/lib/AccountsService/users/$USER

[User]
Language=en_US
XSession=xterm
XKeyboardLayouts=

Changed to:

 sudo more /var/lib/AccountsService/users/$USER

[User]
XSession=ubuntu
XKeyboardLayouts=


```

---

