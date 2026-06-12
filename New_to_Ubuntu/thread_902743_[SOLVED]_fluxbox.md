---
title: "[SOLVED] fluxbox"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2008-08-27
I installed ubuntu server and fluxbox. I now need to learn how to get the programs I install via command line with apt-get to my fluxbox menu. and also get fluxbox to load as soon as I power my computer.

(currently, I can only start fluxbox by pressing startx in command line)

---

### Post by LunaticHiatus on 2008-08-27
... bump..

---

### Post by bodhi.zazen on 2008-08-27
Lots of fluxbox how to-s here : [http://community.fluxbuntu.org/index.php?board=18.0](http://community.fluxbuntu.org/index.php?board=18.0)

[http://community.fluxbuntu.org/index.php?topic=424.0](http://community.fluxbuntu.org/index.php?topic=424.0)

[http://community.fluxbuntu.org/index.php?topic=36.0](http://community.fluxbuntu.org/index.php?topic=36.0)

---

### Post by kerry_s on 2008-08-27
> **LunaticHiatus said:**
> I installed ubuntu server and fluxbox. I now need to learn how to get the programs I install via command line with apt-get to my fluxbox menu. and also get fluxbox to load as soon as I power my computer.

(currently, I can only start fluxbox by pressing startx in command line)

```
sudo apt-get install menu
sudo update-menus
click your fluxbox reload
```

can't help you with the auto login, i only know for debian, which doesn't work in ubuntu.

you can put the "startx" in ~/.bash_profile and as soon as you log in x will start. see pic

---

### Post by LunaticHiatus on 2008-08-27
I did 
sudo apt-get install menu
and then I
update-menus

but I dont know what you mean by click your fluxbox reload. currently, when I click startx it looks the same

---

### Post by LunaticHiatus on 2008-08-27
halp plez

---

### Post by bodhi.zazen on 2008-08-27
> **LunaticHiatus said:**
> halp plez

I posted two links on how to get a nice menu. Which one are you following and where did you get stuck ?

---

### Post by billgoldberg on 2008-08-27
I've written a guide about fluxbox you might find usefull.

Link in signature.

---

### Post by rockerphil on 2008-08-27
i did basically the same thing, and here's my best advice, try installing a login display manager, i personally use KDM from Kubuntu, it lets you choose your WM upon login, this can be installed with:

```
sudo apt-get install kdm
```

also, as stated before, Fluxbox doesn't auto update your menus, this has to be done with:

```
sudo update-menus
```

then simply right click on your desktop and your new program should be there with the exception of a few like Firefox, but you can simply put a desktop icon for it using idesk to create desktop icons, but you'll need somthing like feh to run idesk. all of these applications are supported in the repos, hope this helps,

Phil

edit: also, youcan add programs to your menu that aren't automatically put there with "sudo update-menus" by editing your ~/.fluxbox/menu file, and adding somthing like this for firefox:

[exec] (Firefox) {firefox}

right under the top line that says [begin]

---

### Post by LunaticHiatus on 2008-08-27
> **bodhi.zazen said:**
> I posted two links on how to get a nice menu. Which one are you following and where did you get stuck ?

I dont really need a nice menu. I'm wondering why systems is not showing which it apparently should be.

---

### Post by rockerphil on 2008-08-27
> **LunaticHiatus said:**
> I dont really need a nice menu. I'm wondering why systems is not showing which it apparently should be.

i personally love Fluxbox, but in order to get it working and looking the way you want it to it's gonna take some manual configuration and editing some config files on your part. just do some Google searching on Fluxbox, there's a lot of information out there, also, look under Apps>>System, i'm guessing that's what you're looking for.

Phil

---

### Post by LunaticHiatus on 2008-08-27
nothing seems to be working. Maybe I'm not clear as what I have been doing.. Basicly, I have been installing the latest ubuntu server with nothing on it but the base. Then when I enter command line. I typed
sudo apt-get install xorg fluxbox fluxconf
then I type startX and fluxbox shows up

I installed mplayer by sudo apt-get install mplayer
I went to add mplayer to fluxbox but there was no systems or tools.

So, I tried:
sudo apt-get install menu
sudo update-menus

no change.

I then 
sudo apt-get install kdm
sudo update-menus

No change.

---

### Post by LunaticHiatus on 2008-08-27
ok, nevermind, now kdm works.... don't ask me how. but.. well. now fluxbox loads on bootup... soo... yeah..

---

### Post by rockerphil on 2008-08-27
well, sudo update-menus should update your fluxbox menus and add just about any program you install via apt-get, and if you're not too keen on the command line to deal with package management you could always install Synaptic with:

```
sudo apt-get install synaptic
```

then of course:

```
sudo update-menus
```

and that will add Synaptic under Apps>>System. hope this helps, and please remember to mark your thread as solved if you've got the problem figured out.

Phil

---

