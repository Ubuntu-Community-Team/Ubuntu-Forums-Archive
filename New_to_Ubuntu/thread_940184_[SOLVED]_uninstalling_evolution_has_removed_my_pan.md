---
title: "[SOLVED] uninstalling evolution has removed my panel and bricked Ubuntu"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Irishpolyglot on 2008-10-06
Hey people!

I stopped using Evolution so I decided to uninstall it and it's dependencies. Other than that I changed the network.dns.disableIPv6 setting in Firefox. And I emptied the trash since I was low on space. No other major changes that I can remember.

Now I can't access anything. Ever since I rebooted, it logs in and I see my background and I can move the Compiz cube around, but that's it. I can't see the Panel and no key combinations do anything. I tried to bring up the command line terminal but CTRL or ALT or CTRL+ALT and ALL letters, numbers and Function keys do nothing (I went through all combinations), with the exception of Print-Screen and being able to log out and lock the screen, and CTRL+Alt+backspace probably works too, but I didn't try.

I imagine uninstalling Evolution did this although I have no idea why. The question is... how do I get back to normal?? How can I even access ANYTHING? (I've had to go to an Internet café to send this message...). Even bringing up the terminal to run firefox would be a start...

I'm on 8.04 and am an "advanced novice" in terms of Linux...

Thanks in advance for saving my skin as always guys!!

(P.S. Sorry for posting this twice (also in General Help), but only 2 views there in 45 minutes seems weird... if I don't fix this tonight I can't work tomorrow :(

---

### Post by kansasnoob on 2008-10-06
Can you open the terminal by pressing Alt > F2?

If so the only thing I can think to do is:

```
sudo apt-get install --reinstall ubuntu-desktop
```

and then:

```
 sudo apt-get -f install
```

to resolve unmet dependencies.

---

### Post by Irishpolyglot on 2008-10-06
Thanks for the hint! I found related threads and they gave me the general solution.
Alt+F2 didn't work, but Ctrl+Alt+F1 brought me to the full screen prompt and I did
```
sudo apt-get install gnome-panel
```
and I could see that it was installing some evolution dependencies. Now it's working :)

---

