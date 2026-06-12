---
title: "ubuntu 11.10 - administrator desktop blank"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Stefano G on 2011-10-17
Hi all,

I just updated my ubuntu 11.04 to 11.10 on sunday.

At first restart it works properly, but this morning after I log-in as administrator, the desktop become blank (purple) and system just asked me the pw to connect at wireless and just keep showing me the twitts.

I can see any icon.

so I tried the command ctrl+alt+delete and try to log-in as Guest. It works fine and all functions works properly.

I ve a laptop HP Compaq nc6400 and installed Ubuntu/win xp

Looking forward to receive suggestions :)

Thanks in advance to all

Stefano

---

### Post by CurtisB on 2011-10-21
A similar problem occurred on my friends computer, we found that the unity plugin was switched off in CCSM. We were able to open the terminal with ctl+alt+t, and the command $ ccsm opened the settings manager. We turned on Unity, and it appears to have fixed the problem.

Hope this helps.
~Curtis

---

### Post by Stefano G on 2011-10-21
Hi Curtis,

thanks for your suggestions, but unfortunately ctrl+alt+t command doesn't work (or maybe it works but it not appears the terminal)

I checked with Guest, and it seems CCSM package is not installed; i tried to open synapctic with guest account, but it not works .

Thanks anyway for sharing your experience.

Any idea how to force a re-installation with guest account?

Looking forward  an help, since now I'm "forced" to back at xp .

Regards to all

Stefano

---

### Post by lolpenguin on 2011-10-22
Wait a moment, what is the "Administrator" account? Is this your account name, or is it the root user?
Unity did not work in a upgrade to oneiric on my computer, but Unity 2D works. You can get around this by install GNOME Shell (which I find more productive than Unity).
For some reason on my computer, sometimes Unity works, sometimes it does not.

---

### Post by Stefano G on 2011-10-22
> **lolpenguin said:**
> Wait a moment, what is the "Administrator" account? Is this your account name, or is it the root user?
Unity did not work in a upgrade to oneiric on my computer, but Unity 2D works. You can get around this by install GNOME Shell (which I find more productive than Unity).
For some reason on my computer, sometimes Unity works, sometimes it does not.

Administrator account is my own one (got only one).
The issue is that with guest account I cant install anything, and with administrator I cant see anything.
I was thinking to go back installing the 11.04 cd and avoid the update of 11.10.

I see no other solution :( 

BTW, Thanks for your advise ;)

---

### Post by Stefano G on 2011-10-24
update:


Just for record, I re-installed Ubuntu 11.04 on my laptop Compaq nc6400 and forgot 11.10.

BTW, 11.10 seems stable on my other laptop IdeaPad s10, which I've updated in meantime.

Regards to All and keep Ubuntu! ;)

Ciao

Stefano

---

