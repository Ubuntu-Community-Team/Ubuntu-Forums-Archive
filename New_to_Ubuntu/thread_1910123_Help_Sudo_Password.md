---
title: "Help Sudo Password"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by slyohey75 on 2012-01-16
I was trying to install a cd using wine (I have done this before)  It acts like it is going to install but before it "finishes"  it give me a access denied error.  I went to check that I was signed in as user in terminal it asks for password but says wrong password.  I am absultly possitive my password is correct.  Please help.  I am  beginner with no admin help.  I have figured everything out on my own.  I was able to install easytether and get connected :-)

---

### Post by Rex Bouwense on 2012-01-16
First thing to check is make sure that your Caps Lock is off because as you know Linux is case sensitive.

---

### Post by Jake Sweeney on 2012-01-17
Does it ask for a sudo password or a root password?

---

### Post by Double.J on 2012-01-17
> **Jake Sweeney said:**
> Does it ask for a sudo password or a root password?

Ubuntu doesn't set a root password by default - just adds the user to the sudoers file.

---

### Post by Jake Sweeney on 2012-01-17
> **gnu/mirow said:**
> Ubuntu doesn't set a root password by default - just adds the user to the sudoers file.

I know. It's just that when I was trying to do some stuf fwith the terminal  other day I had to create a root password to complete the task.

---

### Post by Double.J on 2012-01-17
> **Jake Sweeney said:**
> I know. It's just that when I was trying to do some stuf fwith the terminal  other day I had to create a root password to complete the task.

Shh... the mods'll hear you...:-#

---

### Post by mcduck on 2012-01-17
> **gnu/mirow said:**
> Shh... the mods'll hear you...:-#

They'd just remove any instructions for doing that, and give advice how to work around such situations without having to enable the root account (I have yet to run into a single task that would *really* require the root account, pretty much everything can be done without it as long as you know how...)

It's not forbidden to have a root account in Ubuntu, just pretty much not necessary and strongly advised against which is why giving instructions for it is not allowed (most people asking for such instructions are highly unlikely to really need the root account)

---

### Post by QIII on 2012-01-17
If you got a message that said "you must be root to complete this task", then it is pretty close to a sure bet that sudo would have done fine.

---

### Post by mcduck on 2012-01-17
> **QIII said:**
> If you got a message that said "you must be root to complete this task", then it is pretty close to a sure bet that sudo would have done fine.

yep, or root session through "sudo -i".

The only situation when I actually thought I might really need the root was compiling a kernel, and then I found out that using fakeroot works fine for that.

---

### Post by Double.J on 2012-01-17
It's all swings and roundabouts - when I was using deb as my primary, I was always told sudo wasn't strong enough because of the user password being used not root's.. but that old chestnut'll get us in recurring!

The fact is you can suitably mess up your system either way if you don't check what you're doing and just authorise something... I tend to use su and gksu out of habbit ... I always advise people to use sudo though! :)

---

### Post by mcduck on 2012-01-17
> **gnu/mirow said:**
> It's all swings and roundabouts - when I was using deb as my primary, I was always told sudo wasn't strong enough because of the user password being used not root's.. but that old chestnut'll get us in recurring!

The fact is you can suitably mess up your system either way if you don't check what you're doing and just authorise something... I tend to use su and gksu out of habbit ... I always advise people to use sudo though! :)

sure, root permissions used badly are equally likely to wreck your system no matter if you do it through sudo or directly logging in as root. On the other hand people who mostly run into such problems are the ones who aren't actually that familiar with Linux systems, and only think they need it becuase that's what they did in Windows. As long as they stick to Ubuntu's security model, helping them is a lot easier. (besides, all the admin tools are configured with sudo-to-root in mind, so enabling the actual root account can cause unexpected problems)

---

### Post by slyohey75 on 2012-01-20
Ok, I am more confused now then when I first asked my question!  I simply want to install a CD ROM Game using Wine.  It tells me access denied?  I tried using terminal to check I was logged in with my sudo password and it says password invalid.

---

