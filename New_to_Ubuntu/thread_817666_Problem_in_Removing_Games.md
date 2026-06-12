---
title: "Problem in Removing Games"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-03
I have ubuntu 8.04 along with KDE installed inside it.

I dont want any games inside my ubuntu.

But when i tried to remove any games its also displaying that KDE and other packages are to be removed.

How can i remove all games.

---

### Post by adobrakic on 2008-06-03
What i did was go to Applications > Add/Remove and just unchecked all the games.

---

### Post by rraj.be on 2008-06-03
When i tried this its displaying

```

One or more applications depend on kasteroids. To remove kasteroids and the dependent applications, use the Synaptic package manager.
```

Is there any way to remove the games alone.

---

### Post by Shazaam on 2008-06-03
What I do (unless you absolutely need the room on your drive) is to open "Main Menu" and uncheck applications there. This does NOT remove the app, it just removes it from the menu. You can also right-click your panel and choose "Edit menus".

---

### Post by rraj.be on 2008-06-03
I know about going with editing menu.
And you are correct.

But i am in need to remove entire games.

---

### Post by adobrakic on 2008-06-03
Not sure, sorry. I've never had this problem.
Have you tried removing kasteroids from synaptic first, and then going to add/remove and removing the games from there?

---

### Post by rraj.be on 2008-06-03
when i tried with S-P-manager its telling that i have to remove my KDE too.

I want Kde but not any games.

---

### Post by rraj.be on 2008-06-04
I am unable to remove my games without affecting KDE.

What can i do to uninstall all games.

---

### Post by kpkeerthi on 2008-06-04
```
sudo apt-get purge gnome-games
```
```
sudo apt-get purge kdegames
```
```
sudo apt-get autoremove
```

---

### Post by rraj.be on 2008-06-04
r u sure that it wont remove my KDE.

---

### Post by kpkeerthi on 2008-06-04
Why don't you try it? I'm sure it prompts for a confirmatory Yes/No option if it must remove.

---

### Post by tom56 on 2008-06-04
Kasteroids is a game. It is safe to remove it, KDE will be fine.

---

### Post by rraj.be on 2008-06-04
Again its asking to remove KDE

```
raj@raj-workstation:~$ sudo apt-get purge kdegames
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.4++ kdepim kdeprint kleopatra libxmmsclient2 kdebase kde-core ktron
  kwin4 kdeaddons libopensync0 konq-plugins portmap kitchensync
  libxmmsclient-glib1 ktuberling libmms0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
[COLOR="Cyan"] kde* kde-amusements* kdegames*[/COLOR]
0 upgraded, 0 newly installed, 3 to remove and 436 not upgraded.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by kpkeerthi on 2008-06-04
Thats strange. I don't use KDE. So I can't check for you. May be thats how kdegames package has been packaged.

I had no trouble removing gnome-games.

---

### Post by rraj.be on 2008-06-04
I have too removed Gnome games a long back.

But now these Kde games are not moving away.

---

### Post by Sef on 2008-06-04
Certain apps are tied into the Desktop Environment and cannot be removed without removing the desktop.  This applies to Ubuntu as well as Kubuntu.

---

