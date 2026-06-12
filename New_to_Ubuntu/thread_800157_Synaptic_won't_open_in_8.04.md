---
title: "Synaptic won't open in 8.04"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Peter K Nicol on 2008-05-19
I am having lots of problems with 8.04. Synaptic and Update manager start to open then the clock icon disappears and nothing else happens. I have managed to update via the terminal but the fault persists. I have no access to wireless although the connection can be seen. I had very few problems with 7.04 but wireless connection dropped frequently in 7.10 hence the move to 8.04. Any suggestions would be appreciated. (Thinkpad X30 with Windows XP partition)

---

### Post by Inxsible on 2008-05-19
Synaptic and Update Manager will not start at the same time. You have to use one or the other. Close Synaptic and then try update manager or vice versa.

Also you will not be able to use apt-get or aptitude in the terminal if you have Synaptic or update manager or add/remove programs open

---

### Post by Peter K Nicol on 2008-05-19
Thanks for the reply. I don't think that is the problem as I have not attempted to open them at the same time.

---

### Post by Inxsible on 2008-05-19
> **Peter K Nicol said:**
> Thanks for the reply. I don't think that is the problem as I have not attempted to open them at the same time.In that case, do you get any errors?

If yes, what are they ?

---

### Post by Peter K Nicol on 2008-05-19
Absolutely no errors are posted that I can see - that is the frustrating bit.

---

### Post by ajgreeny on 2008-05-19
See what errors you get if you open the apps using the terminal ```
synaptic
```or ```
update-manager
```and report back.

---

### Post by freebird54 on 2008-05-19
Not sure if this might be the same problem - but this thread

[http://ubuntuforums.org/showthread.php?t=783763](http://ubuntuforums.org/showthread.php?t=783763)

might hold a potential answer for you... it did for me!

Good luck! :)

---

### Post by Peter K Nicol on 2008-05-20
Thanks for the replies. I will try again tonight and report back.

---

### Post by Peter K Nicol on 2008-05-20
> **ajgreeny said:**
> See what errors you get if you open the apps using the terminal ```
synaptic
```or ```
update-manager
```and report back.

That appears to have cured it. Both opened from the Terminal but this time a password was asked for. This did not happen last time. Synaptic now appears to work from the menu and asks for a password before opening. I looked at the other possibilities but I have no domain name listed.

---

### Post by khernandezpardo on 2008-06-07
Hi Peter... I'm having the same problem... After trying "update-manager" on a terminal I got this:
current dist not found in meta-release file

After a while, I use Ctrl-c to try and kill the window and this appeared:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 777, in on_button_install_clicked
    self.invoke_manager(INSTALL)
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 798, in invoke_manager
    time.sleep(0.05)
KeyboardInterrupt

which I think it's just because of the Ctrl-C command, I had to try it once more:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 109, in <module>
    app.main(options)
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 1077, in main
    gtk.main()
KeyboardInterrupt

---

