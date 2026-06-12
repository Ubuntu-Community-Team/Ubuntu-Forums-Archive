---
title: "HOWTO: Forward root/administrative emails to an external email address"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by jetpeach on 2006-06-25
Have you typed "mail" at the prompt lately and seen all this system mail you had no idea about?  Here is a simple guide for forwarding all of this mail to an external mail account.

--- install postfix and mailx to enable sending mail to external account, either open Synaptic or your package manager and search for postfix and install, or type "sudo apt-get install mailx" inside the terminal (postfix will be installed also since mailx depends on it)

--- Forward your root mail to your local mail by typing at the prompt ```
 sudo sh -c "echo $(echo -e $USER@localhost) > /root/.forward" 
``` (this will write the text YOURUSERNAME@localhost to the file /root/.forward).  Type your password if necessary...

--- Forward your local mail to the external mail account of your choice by typing ```
 nano ~/.forward 
``` and simply type your email address followed by a newline. Hit Control-X to quit nano and 'y' to save changes

Now, test it by typing 'mail' at the prompt, then hit 'm' and compose the message to root@localhost , (hit control-D when done with an input in the mail program) after you send it you should get the email in your regular inbox.

Let me know if this doesn't work/needs editing, because I've tweaked by system quite a bit in the past and don't know if it worked for me because I already have programs installed (e.g. if i have a mailserver installed already, i don't even know...)

Hope this helps some people.
jet

---

### Post by marcw on 2006-06-25
[QUOTE=jetpeach]Have you typed "mail" at the prompt lately and seen all this system mail you had no idea about?  Here is a simple guide for forwarding all of this mail to an external mail account.[/QUOTE]

This would not apply to default desktop installs, I believe.  I'm guessing that this would only apply to those who have installed mailx/postfix.  Default desktop installs won't have command line email capability.

For those that do have some sort of smtp installed, wouldn't configuring the aliases file be easier?  Not sure...

---

### Post by jetpeach on 2006-06-27
I'm not sure about the other ways to do this, I just found this one worked for me.  I just checked, I do have mailx and postfix installed.  I'll add installing those to the HowTo, if you do know an easier way to do this, please post, I haven't seen one though.

---

