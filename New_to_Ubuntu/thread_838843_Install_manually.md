---
title: "Install manually"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by thepwnerer on 2008-06-23
Ok so ive had ubuntu for about a month and i stuck to add remove for my programs.then i heard about games like urban terroretc.. but do not know how to install them (there is no tar for urban terror i think just zip)can someone tell me the best free fps for linux which has human players and give me very detailed instructions on how to install because i have virtually no experience with this, Thanks:KS

---

### Post by bhadotia on 2008-06-23
Can you please post the link from where you downloaded the game , I'm also looking for some games. 
Also I might be able to help you with your installation issue.

---

### Post by thepwnerer on 2008-06-23
here ya go :   [http://www.urbanterror.net/page.php?6](http://www.urbanterror.net/page.php?6)

---

### Post by bhadotia on 2008-06-23
Hey, this is what I found on the link you gave:

> Just unzip the zip and make a shortcut to the ioUrbanTerror executable.
Mac executable: ioUrbanTerror.app
Linux 32bits executable: ioUrbanTerror.i386
Linux 64bits executable: ioUrbanTerror.x86_64
In linux, you need to make it executable first: right click it, properties and tick the 'allow execution' box.
You just need to run the executable to play the game. First right-click on the file and make it executable (Properties>Permissions-tab>Allow executing file as program(check the box)).

I'm downloading the game and will let you know if it worked for me.

Also make link to to the executable in the games menu using the menu editor (if you want I can tell you how to).

---

### Post by thepwnerer on 2008-06-23
i tried but when i click even after allowing exec nothing happens. maybe im clicking the wrong one?

---

### Post by bhadotia on 2008-06-23
Try to run through the terminal:
First cd to the directory.
then ./file name , where file name is the executable.

---

### Post by thepwnerer on 2008-06-23
i was just clicking like an idiot and it worked, THX!

---

### Post by bhadotia on 2008-06-23
:)Glad to hear it!

How's the game?

---

### Post by angryfirelord on 2008-06-23
Someone made debs for it. If you're willing to trust some unknown packager, you can add this line to your sources.list file:
```
deb http://ppa.launchpad.net/jscinoz/ubuntu hardy main
```
I can't tell you if it works because I haven't tried it myself.

---

