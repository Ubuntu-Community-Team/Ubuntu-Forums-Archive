---
title: "[SOLVED] Could not get lock /var/lib/dpkg/lock ?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-11-12
I went here [http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/]("http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/")and pasted the second code then my terminal displayed and end user agreement w/ an "<ok>" at the bottom.  I hit enter nothing happened I clicked on the screen nothing happened so I closed it.  Now I am getting this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Synaptic package manager is not open and neither is add/remove.

---

### Post by tuxxy on 2008-11-12
Open system monitor and kill any open package manager processes.

---

### Post by dizzy1kenobi on 2008-11-12
I have a x-session-manager, a volune manager and a power manager.  I know its not the second two what does the first one do?

---

### Post by dizzy1kenobi on 2008-11-12
What does apt-get install -f do?

---

### Post by jimmy the saint on 2008-11-12
-f attmepts to fix broken dependecies.  Your problem is that you have multiple package managers (synaptic, add remove, or apt-get in a terminal) running.  You must shut down ALL of them except one in order for it to be able to work.

---

### Post by Rocket2DMn on 2008-11-12
That error appears when a package manager is running.  If you had to cltrl-c on apt-get, aptitude, or dpkg, this error can appear, as well as with GUI package managers like Synaptic, Add/Remove, and Adept.  If you are sure you don't have any package managers running, you can delete the lock file
```
sudo rm /var/lib/dpkg/lock
```
A reboot will always solve this problem, but isn't really necessary unless you are worried.

---

### Post by dizzy1kenobi on 2008-11-12
I used ```
dpkg --configure -a
``` to regain control then an update but I still do not understand why a license agreement would show up in terminal and I could not interact with it.  What is the answer to this question incase I run into it in the future?  Did I miss something?

---

### Post by dizzy1kenobi on 2008-11-12
> **jimmy the saint said:**
> -f attmepts to fix broken dependecies.  Your problem is that you have multiple package managers (synaptic, add remove, or apt-get in a terminal) running.  You must shut down ALL of them except one in order for it to be able to work.

O K this is why that command brought up the same problem and I was faced with the java agreement again.

---

### Post by dizzy1kenobi on 2008-11-12
> **Rocket2DMn said:**
> That error appears when a package manager is running.  If you had to cltrl-c on apt-get, aptitude, or dpkg, this error can appear, as well as with GUI package managers like Synaptic, Add/Remove, and Adept.  If you are sure you don't have any package managers running, you can delete the lock file
```
sudo rm /var/lib/dpkg/lock
```
A reboot will always solve this problem, but isn't really necessary unless you are worried.

Apparently just closing the terminal with a license agreement leaves apt-get open waiting for response.  Though I could not respond.

---

### Post by Rocket2DMn on 2008-11-12
Has your problem been fixed?  If not, please elaborate.

---

### Post by dizzy1kenobi on 2008-11-12
> **Rocket2DMn said:**
> Has your problem been fixed?  If not, please elaborate.

Yes.  But I still am not sure I have accomplished what I set out to do.  Will you answer a few questions for me?

---

### Post by jimmy the saint on 2008-11-12
no need to ask to ask, just ask and recieve your answers!  :)

---

### Post by Rocket2DMn on 2008-11-12
If you have multiple questions, esp. ones that aren't immediately related, you really should start new threads for them.  This gives the community more opportunity to help - they see threads that don't have many (if any) responses, and those with specific skills can help you troubleshoot certain problems.

---

### Post by dizzy1kenobi on 2008-11-12
> **Rocket2DMn said:**
> If you have multiple questions, esp. ones that aren't immediately related, you really should start new threads for them.  This gives the community more opportunity to help - they see threads that don't have many (if any) responses, and those with specific skills can help you troubleshoot certain problems.

Good idea.  I just wanted to know how I could accept license agreements if they show up in terminal.

---

### Post by Rocket2DMn on 2008-11-13
If anything appears in terminal, it should either be a yes/no questions to which you type out yes or no (or simply y or n).  In the case that it presents a pseudo-graphical interface, you can move between options with TAB and press Enter or Spacebar to select.  Hope that helps.

---

