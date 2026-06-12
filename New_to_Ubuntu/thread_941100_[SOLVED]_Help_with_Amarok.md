---
title: "[SOLVED] Help with Amarok"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by DFord425 on 2008-10-07
I need help starting Amarok. I click on it, the icon appears like its loading. Then i stops and amarok does not start. Any ideas why its not working.

---

### Post by christianvaldes on 2008-10-07
run it in a console
then type amarok

what are the error messages?

---

### Post by karlr42 on 2008-10-07
Are you sure it's not just running in the system tray(upper right corner)?

---

### Post by DFord425 on 2008-10-07
> **christianvaldes said:**
> run it in a console
then type amarok

what are the error messages?

```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] amarokapp probably crashed!
```

---

### Post by AndyCooll on 2008-10-07
As a last resort you could open up Nautilus (the File Manager), click CTRL+H to show the hidden files, navigate to KDE and delete the Amarok folder. This will then start everything all over again.

:cool:

---

### Post by DFord425 on 2008-10-07
> **karlr42 said:**
> Are you sure it's not just running in the system tray(upper right corner)?

Its not in the system tray

---

### Post by Greyed on 2008-10-07
> **AndyCooll said:**
> As a last resort you could open up Nautilus (the File Manager), click CTRL+H to show the hidden files, navigate to KDE and delete the Amarok folder. This will then start everything all over again.

:cool:

What is this Nautilus you speak of?  I mean, yes, it is in the water like the Dolphin is, but it is unfamiliar to me.  ;)

---

### Post by DFord425 on 2008-10-07
Where is the file i should try deleting?

---

### Post by AndyCooll on 2008-10-08
> **DFord425 said:**
> Where is the file i should try deleting?
I've not used Amarok (or any KDE apps) for awhile, however it used to be in your home folder. 

Once in your home folder if you click CTRL+H, this should display all the hidden files. The Amarok folder used to be in .KDE > Apps IIRC. Anyway have a look around the KDE folder it's somewhere in there. Delete the whole Amarok folder. The next time you then start up Amarok it should open as if for the first time and ask you for settings etc.

:cool:

---

### Post by Linux&amp;Gsus on 2008-10-08
> **Greyed said:**
> What is this Nautilus you speak of?  I mean, yes, it is in the water like the Dolphin is, but it is unfamiliar to me.  ;)

Nautilus is a file manager for Gnome like Dolphin for KDE.
To see the hidden files in Dolphin hit <alt> + <.> - the dot like you see it as first character that marks hidden files & folders. Alternatively in Dolphin you can click on the menu "view" and then tick "Show Hidden Files". BTW, if you prefer Konquerer as file manager both ways are working just the same.

I guess the folder that is talked about is in: /home/.kde/share/apps/amarok
But don't just trust me on this. Some expert should confirm that this is the correct folder to delete.

Cheers.

---

### Post by Greyed on 2008-10-08
> **Linux&Gsus said:**
> Nautilus is a file manager for Gnome like Dolphin for KDE.


I know.  But since we're talking about Amarok, a KDE app, and the topic is marked KUbuntu I was making light of  the fact that someone suggested he use the GNome file manager when it most likely is not installed on the OP's machine.  ;)

---

### Post by mc4man on 2008-10-08
> Where is the file i should try deleting

home folder -> .kde/share/config/amarokrc

To make 'show hidden files' persistent
first open dolphin -> settings -> configure dolphin -> click on box 'save view properties'
then close and reopen dolphin -> view -> click on 'show hidden files'

What I would do is delete the amarokrc, enable medibuntu as a source and run 
```
sudo aptitude reinstall amarok
```

adding medibuntu for 8.04

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by DFord425 on 2008-10-09
I do not see the amarokrc file. I am trying to install rather than reinstall. 

And it works now.

Thanks

---

