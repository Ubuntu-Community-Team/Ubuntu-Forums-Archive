---
title: "Home network!?!?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Bog_Warrior on 2008-05-05
I am a recent convert to Ubuntu from Window XP Pro and I want to set up my home network with all Ubuntu machines.  I have a Linksys wireless/wired router, a laptop (Running great) and two desktops. Do I need Ubuntu server edition, or can I use the desktop version?  Should be an easy one, and thanks in advance for the replies.

Slainte,

BW

---

### Post by llamakc on 2008-05-05
You may use the desktop version.

---

### Post by SuperSon!c on 2008-05-05
what exactly are you trying to accomplish?  install the server edition if you want to save resources.  if you don't care, install the desktop version.  i'm assuming you're just wanting to share files, etc.

---

### Post by Tatty on 2008-05-05
Desktop version will be fine.  Both the server and the desktop editions use the same repos, they just have different things pre-installed.

---

### Post by Bog_Warrior on 2008-05-05
I would like to have roaming profiles and file shares.  I only have three users.  If roaming profiles are possible in the desktop version, I will head over to the networking thread to start.

Thanks again,

BW

EDIT... Okay, researching and found roaming profiles in the archive and I apologize for my Windowspeak...

---

### Post by Xiong Chiamiov on 2008-05-05
One thing to be aware of is that the server edition doesn't come with a GUI.  You have to install it after installation, which, although not particularly difficult, you may wish to avoid if you'd rather have that set up for you.

---

### Post by bodhi.zazen on 2008-05-05
> **Bog_Warrior said:**
> I would like to have roaming profiles and file shares.  I only have three users.  If roaming profiles are possible in the desktop version, I will head over to the networking thread to start.

Thanks again,

BW

EDIT... Okay, researching and found roaming profiles in the archive and I apologize for my Windowspeak...

There is no reason you could not do this with samba or nfs ...

[http://ubuntuforums.org/showthread.php?t=500752](http://ubuntuforums.org/showthread.php?t=500752)
[http://www.schmut.com/howto/home-directories-over-nfs](http://www.schmut.com/howto/home-directories-over-nfs)

Should work with a samba share mounted at /home or /home/username.

---

