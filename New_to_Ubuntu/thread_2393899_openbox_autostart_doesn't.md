---
title: "openbox autostart doesn't"
date: 2018-06-09
forum: New to Ubuntu
---

### Post by porphyry52 on 2018-06-09
I installed lubuntu on lenovo ideapad 110s, and it works perfectly, thank you.
Trying to have openbox autostart applications for me, not so good.
My ~/.config/openbox/autostart has only one uncommented command ```
xterm -g 80x57 -hold -e bash /home/q/cg.sh

``` It does not run (nor does it run if I terminate the line with ' &').
From [http://openbox.org/wiki/Help:Autostart](http://openbox.org/wiki/Help:Autostart)
> When you log in with the "Openbox" session type, or launch Openbox with the openbox-session command, the environment script will be executed to set up your environment, and the autostart script can launch any applications you want to run at startup. 

*When you run the **openbox command on its own, the autostart scripts will not run**.  They are run by openbox-session or when you log in graphically with the "Openbox" session type.* 

**Note:** Some **distributions ship an "openbox" session type  (for display managers) that simply calls the openbox binary**.  You want  to select the entry that mentions "session." 


Is Lubuntu such a distribution? If so, as I elected autologin, where can I change 'openbox' to 'openbox-session' in the start-up process?
If this is not the problem, what am I doing wrong?

---

### Post by again? on 2018-06-10
If you are logging in to the normal Lubuntu session, the file to edit is **~/.config/lxsession/Lubuntu/autostart** or use
the lxsession-default-apps GUI.
Tested in a live Lubuntu usb and the script runs at login.

Lubuntu also provides an openbox session selectable at the greeter.
The config for that session is at ~/.config/openbox/autostart

---

### Post by porphyry52 on 2018-06-12
> **guber2 said:**
> *_If you are logging in to the normal Lubuntu session,_* the file to edit is **~/.config/lxsession/Lubuntu/autostart** or use
the lxsession-default-apps GUI.
Tested in a live Lubuntu usb and the script runs at login.

Lubuntu also provides an openbox session selectable at the greeter.
The config for that session is at ~/.config/openbox/autostart

Thank you for your help. I was using autologin, and it seems as if you can do only one or the other, aotologin or autostart apps. I've tried perhaps six different approaches to this problem, but none gave me both options together.

I've marked the thread as solved, but actually I've returned to using Arch, its more difficult to install than *ubuntu, but much more amenable to fine-tuning thereafter.

---

