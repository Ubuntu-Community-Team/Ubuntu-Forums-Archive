---
title: "[SOLVED] cairo-dock"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by davarse on 2008-06-02
does anyone know how to install cairo-dock on hardy???

---

### Post by Kobalt on 2008-06-02
[Yes]("https://help.ubuntu.com/community/CairoDock")

---

### Post by davarse on 2008-06-04
i've installed it and it's went alright, but i got the problem that i just have 'default' option for the view.
i had cairo dock on gusty before and i was just awesome...
do you know how to fix it???

---

### Post by fabounet on 2008-06-06
in the config panel, click on the rendering plug-in to activate it, then re-open the config panel, there should be many views you can choose (or you can also choose a view for 1 particular sub-dock)

---

### Post by sayakb on 2008-06-06
You might also try AWN. Add this to your repository:
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```And then:
```
sudo apt-get update
sudo apt-get install avant-window-navigator-trunk libawn0-trunk awn-manager-trunk python-awn-trunk vala-awn-trunk
```

---

### Post by scope on 2008-06-08
Can someone tell me how to change the language of cairo? In all the wikis and howtos that I've read, it seems that the menus layout is different than the version I've got (the one from the repositories),and there is no option to change the language. 
Almost everything is in french.

---

### Post by fabounet on 2008-06-10
CD is based on gettext, that means it guesses your language based on LC_LANGUAGE variable.
what does "echo $LC_LANGUAGE" and "echo $LC_LANG" give ?

the strange thing is that CD is written in english, and then translated into french ^_^

---

### Post by davarse on 2008-06-10
> **fabounet said:**
> in the config panel, click on the rendering plug-in to activate it, then re-open the config panel, there should be many views you can choose (or you can also choose a view for 1 particular sub-dock)

hi fabounet, which "config panel" do you mean???

---

### Post by onero on 2008-06-23
> **davarse said:**
> hi fabounet, which "config panel" do you mean???

Right click on the dock, select Cairo-Dock, then Configure, that should bring up the configuration panel.

---

### Post by CheeseEatingBulldog on 2008-07-04
> **onero said:**
> Right click on the dock, select Cairo-Dock, then Configure, that should bring up the configuration panel.

I can get to the config panel, but where, pray tell, is the render plugin that you speak of?

Nevermind, found it, for others it is under the "Applets" option and then "Add functionality to your dock!" select "rendering" ...talk about hidden.

---

### Post by billgoldberg on 2008-07-04
I haven't read the thread, but you'll need the "plugin" .deb file.

That will install all the other features/skins, ...

It can be downloaded here:

[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by phoric on 2008-07-05
I've installed cairo-dock on fresh install of 8.04, and I want to run the dock in "parabolic" view. However when I use this view it doesn't register my mouse clicks properly. When I click on an icon, it registers as if I clicked on the icon *below* the one I'm actually clicking on. This happens especially with icons closest to the top of the menu. In other words if I have a Firefox icon with a Terminal icon above it, when I click on the terminal icon it will load Firefox instead. :confused:

It's unfortunate as I kinda like this program, but not being able to actually open the programs you want is kind of a deal-breaker.

I've tried different themes, and deleting and reinstalling cairo-dock, with the same results. Any suggestions?

---

### Post by onero on 2008-07-05
> **phoric said:**
> I've installed cairo-dock on fresh install of 8.04, and I want to run the dock in "parabolic" view. However when I use this view it doesn't register my mouse clicks properly. When I click on an icon, it registers as if I clicked on the icon *below* the one I'm actually clicking on. This happens especially with icons closest to the top of the menu. In other words if I have a Firefox icon with a Terminal icon above it, when I click on the terminal icon it will load Firefox instead. :confused:

It's unfortunate as I kinda like this program, but not being able to actually open the programs you want is kind of a deal-breaker.

I've tried different themes, and deleting and reinstalling cairo-dock, with the same results. Any suggestions?

Have you tried views other than parabolic? I find that view gets out of sync sometimes, especially with certain applets, but it usually goes back after an autohide or restart of cairo-dock. Try changing the view settings for parabolic or try another view (the new curve view is pretty), or otherwise try deleting your .cairo-dock folder in your home directory (so that all the settings are reset).

---

### Post by phoric on 2008-07-05
> **onero said:**
> Have you tried views other than parabolic? I find that view gets out of sync sometimes, especially with certain applets, but it usually goes back after an autohide or restart of cairo-dock. Try changing the view settings for parabolic or try another view (the new curve view is pretty), or otherwise try deleting your .cairo-dock folder in your home directory (so that all the settings are reset).

Yes I have, although I admit I'm most interested in the parabolic view. Restarting or hiding doesn't seem to reset it, nor does deleting the .cairo-dock folder, or reinstalling the program. It's like it doesn't know how to align the clickable regions with the icons rendered on the screen.

Edit: I switched to AWN and that seems to work much better and much less buggy than cairo-dock.

---

