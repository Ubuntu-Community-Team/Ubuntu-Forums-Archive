---
title: "New Xubuntu 11.10 Install (no problems)"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Joreus on 2011-10-20
Just installed Xubuntu 11.10 as a clean install with absolutely no problems. 

I just have a few small questions:

1. Is there any way to permanently display "technical items" in the Ubuntu Software Center? Normally the programs I'm looking for are buried in that list. It's not a problem to open the list, just a minor annoyance.

2. Is there any substantial difference between running Thunar as my file manager instead of Nautilus? Should I stay with Thunar since I have a Xubuntu install?

3. Lastly, is there anyway I can update my current Ubuntu version in the forums? It still says I'm running Maverick and I'd like to update it. Is this a new forum mechanic? [SOLVED]

Any help would be appreciated. :D

---

### Post by kaldor on 2011-10-20
1) Not on an Oneiric PC right now, unsure. 

2) I recommend you stick with Thunar due to technical reasons as well as keeping things "pure".

3) It should be available in your user control panel. However, if you have less than 50 posts, see [_here_]("http://ubuntuforums.org/showthread.php?t=1836816").

Enjoy 11.10 :)

---

### Post by thatguruguy on 2011-10-20
> **Joreus said:**
> Just installed Xubuntu 11.10 as a clean install with absolutely no problems. 

I just have a few small questions:

1. Is there any way to permanently display "technical items" in the Ubuntu Software Center? Normally the programs I'm looking for are buried in that list. It's not a problem to open the list, just a minor annoyance.
Not that I know of, although that would be a helpful feature.

> **Joreus said:**
> 2. Is there any substantial difference between running Thunar as my file manager instead of Nautilus? Should I stay with Thunar since I have a Xubuntu install?
Try each and see what you like.  There are pros and cons to each, although Thunar is probably a little lighter.  I use Nautilus on my two computers running Ubuntu and Thunar on my Mythbuntu (based on Xubuntu) box.  Both file managers are perfectly serviceable.

> **Joreus said:**
> 3. Lastly, is there anyway I can update my current Ubuntu version in the forums? It still says I'm running Maverick and I'd like to update it. Is this a new forum mechanic?
You need to have at least 50 posts to change your profile.  This is an anti-spam measure.

---

### Post by mike555 on 2011-10-20
Thunar has a different search that uses catfish , good , but more clicks...

---

### Post by Joreus on 2011-10-20
Ah, anti-spam, that explains a lot. I normally just browse the forums for information and I'm not a heavy poster. I logged in a week or so ago and noticed I was locked out of my profile. I never thought the Ubuntu forums had a big problem with spam since I don't see it all that often. In hindsight, I guess that's mostly due to awesome admins keeping the forums clean and tidy. Thanks for the info! [SOLVED]

I'm not particularly concerned about my file manager. So far Thunar works great. I just never worked with it before and so far I can't tell the difference between it and Nautilus (which is a good thing). I just saw the option in my Settings window about being able to switch to Nautilus if I preferred. 


That just leaves me with a quest to find a way to enable permanent technical items in USC.

---

### Post by ubu_dynamite on 2011-10-20
Only things in Thunar i mis so far are "Connect to server" and "Extra Pane"

---

### Post by Morbius1 on 2011-10-20
There is one thing about the latest Xubuntu that you might have noticed and that is it's missing a package that allows ( among other things ) the availability of the "Network" link in Thunar ( allowing samba browsing ) and may enable the "Connect to Server" as well.
```
sudo apt-get install gvfs-backends
```Then reboot.

---

### Post by ubu_dynamite on 2011-10-20
> **Morbius1 said:**
> There is one thing about the latest Xubuntu that you might have noticed and that is it's missing a package that allows ( among other things ) the availability of the "Network" link in Thunar ( allowing samba browsing ) and may enable the "Connect to Server" as well.
```
sudo apt-get install gvfs-backends
```Then reboot.

gvfs-backends is installed and the Network link is there but Thunar does not have a option to "Connect to server" as far as i have seen so far.
I use it allot to connect to multiple computers running ssh/sftp.

---

### Post by ubu_dynamite on 2011-10-20
Not 100% sure if it,s part of xfce but just found "Gigolo" in Applications->System->Gigolo not tried it yet but seems to be able todo what i want.

**Edit:** Still would be nice to have this directly in thunar after connecting to the ssh server with Gigolo it opens Thunar anyway.

---

### Post by Morbius1 on 2011-10-20
You are absolutely correct. Sorry. I guess that's why Gigolo is installed.
[COLOR=Blue]EDIT: looks like we posted past each other.[/COLOR]

Gigolo is a great little utility and can be used to automount remote shares ( samba, ssh, etc... ) without having to go through the grief of setting up fstab entries: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

