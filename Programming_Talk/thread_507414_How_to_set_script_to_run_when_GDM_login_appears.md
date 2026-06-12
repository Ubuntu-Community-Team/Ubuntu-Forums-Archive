---
title: "How to set script to run when GDM login appears?"
date: 2007-07-23
forum: Programming Talk
---

### Post by weblordpepe on 2007-07-23
Hi guys & girls. Just a quick query.
How can I make a script run when the login screen appears? I have a nice .sh script that says the date & stuff over text-to-speech using felicity.

I'm lost in all the documentation here. Can someone give me a quick pointer as to where I can put this script? Or where I can write a reference to it in a config etc? Cheers.

---

### Post by mckryptyk on 2007-07-23
You can either have it run when Xorg starts up or have it run after you log in.

For Xorg startup try editing ~/.bashrc.

For Gdm, from the menu go to System -->> Preferences --> Session
and add the path to your script. (don't forget to secure the permissions and make executable!)

permissions:
for example chmod 755, then chmod +x.

Cheers

---

### Post by weblordpepe on 2007-07-23
Yay! Thanks. I want the computer to say the date / time and pass 'fortune' to the speakers :)

---

### Post by weblordpepe on 2007-07-23
Hmm this seems to be user specific. Are you sure this is what I should be editing? Why would I be editing something in a user's home folder?
I want to have a script run when the login prompt appears, not after i've logged in.

---

### Post by mckryptyk on 2007-07-25
You need to add you script to /opt/yourscript
and then symlink (ln -s ) /etc/rc5.d/ to /opt/yourscript .
This will make your script run on startup everytime before login appears.

I may be wrong about the runlevel (rc5.d) so you may want to try a different runlevel 
(I'm tired from work and can't think)  :)

Try looking on [http://www.slackbook.org/](http://www.slackbook.org/) for the run level.
Also be sure to name your script correctly for example (S99yourscript) and have that symlink to /opt/yourscript.

Hope that helps, If not let me know.

Cheers

---

### Post by weblordpepe on 2007-07-26
Ubuntu said that the real scripts should be in /etc/init.d/ but the simlink should be in /etc/rc5.d/

It wont work. I have called it **S99startuptalker**

Where can I see the errors if any?

---

### Post by DoktorSeven on 2007-07-26
Default runlevel is 2, actually, so symlink should be in **/etc/rc2.d** called S99[whatever].  (TIP: to see what runlevel you're in, type **runlevel**.)

Also make sure your script (what you're linking to) is set executable:

**sudo chmod 755 /path/to/script**

Also note that this only works when the system is booted, not every time you go to the login screen.

---

### Post by weblordpepe on 2007-07-26
Ahh!!! :)

---

