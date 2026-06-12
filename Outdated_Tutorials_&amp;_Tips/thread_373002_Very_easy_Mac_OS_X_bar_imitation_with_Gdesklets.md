---
title: "Very easy Mac OS X bar imitation with Gdesklets"
date: 2007-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Bossieman on 2007-02-28
I have tried for a long time to get a Mac OS X animated applicationbar with no success. Then I managed with gdesklets to achieve this.

[http://www.youtube.com/watch?v=VgAp4XaYCFI](http://www.youtube.com/watch?v=VgAp4XaYCFI)

It works just like I want it and it is extremely easy to achieve and it is very nice looking IMO.

Start with

```
sudo apt-get install gdesklets
```

Start up gdesklets and choose Toolbar/Launchers, dubbelclick on StarterBar and place the desklet at your prefered place on your desktop.
[IMG]http://img216.imageshack.us/img216/8004/deskletsug0.png[/IMG]
Now drag applications to the desklets and they will appear there (you might need to restart the desklet to see the new application).

If that doesnt work you can try with the following. Rightcklick on the deskletbar and choose "New starter". That will yield
[IMG]http://img216.imageshack.us/img216/3356/startky1.png[/IMG]
Now just fill in the information and dont forget to add a icon.

Rightclick on the deskletbar and choose Configure desklets and make it look like the picture below to achieve what was shown in the video. 
[IMG]http://img214.imageshack.us/img214/3908/confol2.png[/IMG]

Dont forget to make gdesklets start automatically if you want it to start when you log into gnome.

---

### Post by kpagpa on 2007-03-01
Thanks very much for this, I kinda figured it out through trial and error with gdesklets.

Just one question:  how do you make gdesklets boot automatically at start up?  I wasn't aware that you could.

Thanks for your help:)

---

### Post by timjayko on 2007-03-01
system>preferences>sessions add "gedesklets shell" in commands

---

### Post by kpagpa on 2007-03-01
thanks timjayko.........done! :)

---

### Post by timjayko on 2007-03-02
nice.. yah I read how to do that in a guide it was called 13 things to do right after installing ubuntu or something like that.. really good article.. had everything you needed to know about gdesklets

---

### Post by kpagpa on 2007-03-02
I found the article and it looks really good.  For anyone else who might be interested:

[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

Thanks for the pointing me in the right direction.\\:D/

---

### Post by timjayko on 2007-03-02
np hehe i believe i found that article through a previous thread i viewed lol woot these forums rock

---

### Post by kpagpa on 2007-03-02
Yeah, it's what I really like about the open source mentality and the spirit of Ubuntu - it's all about helping others.  I can relate to that.  These forums really rock :)

---

### Post by acmarfil31 on 2007-03-30
Very nice.. Thank you guys for the wonderful inputs.

---

### Post by r81gsr95 on 2011-01-17
can anyone please help me get this installed? I'm running fedora and am having some problems. This is my first time on linux btw.


So i got gdesklets installed. I downloaded the starter bar and it is showing up in gdesklets.

When i click on run this desklet though it says

Could not find sensor 'StarterBar'
/home/AniZer/.gdesklets/Displays/starterbar-desklet/starterbar.display



A sensor could not be found. This usually means that it has not been installed.



so then i found this

[B]extract the file you downloaded and copy over the new starterbar.  (The code assumes you extracted it to your home folder.)

[B]tar -xvzf ~/34782-starterbar-desklet.tar.gz 
sudo cp ~/starterbar-desklet/starterbar.display .[/B][/B]


__i managed to get the first command to work, i extracted it. But when i do the 2nd one it asks me for my password which i enter. It then says 

AniZer is not in the sudoers file.  This incident will be reported.
[AniZer@localhost ~]$ 


So then i try it at superuser and it says

[root@localhost ~]# sudo cp ~/starterbar-desklet/starterbar.display
cp: missing destination file operand after `/root/starterbar-desklet/starterbar.display'


I have my flamesuit on, i'm a linux noob but if anyone could please help me get this installed i would really appreciate it. Thanks

---

