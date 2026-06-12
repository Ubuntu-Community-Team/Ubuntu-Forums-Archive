---
title: "help in using lubuntu"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by speedman2202 on 2012-08-23
hello guys

finally , i installed ubuntu or lubuntu and can now try linux :D ..... happy for that but now i wanna asking about things


1st , how to add another language to ur system that u can change by keyboard (alt+shift) 

2nd how control ur screen resolution (letters too small)

3rd how to add icons to my desktop like my computer , networks ..etc

4rd can u give me some books to learn  terminals commands , and want to know what the extensions that work on linux and what extension type that only work on linux or lubuntu like what the programs extension for Linux???


that's for now , happy that i am finally work on linux sys .... 

thx

---

### Post by Gaygerbil on 2012-08-23
1. There should be a way to shortcut changing a language but I'm not entirely sure what it is, maybe I'll look into it. However to change the language, I know there is an option under Preferences called 'Language Support', you will have to download the language you want supported however.

2. This is also under Preferences at 'Monitor Settings'.

3. This is pretty simple as well, if you want to add things from your file manager or copy them on the desktop, you can simply go into your file manager (PCManFM) and drag w/e file on the desktop, or copy it and paste it on the desktop. For applications in your menu you can just right click on the application and click 'Add to desktop'.

4. Well this is really up to what you want out of Linux, whatever you can think of there is. For example if you like to create scripts to do certain things like change the wallpaper ever 15 mins and have a shortcut to turn it on and off you can do that. For me for example I use Openbox to put a 'Next Wallpaper' script in the menu, which is included in Openbox. Openbox is a great menu that can be completely customized for integrating scripts into it. The other thing that comes with Lubuntu is LXDE, which has functionality as well in its panel and other components to what you want it to be.

Tell me how things work out for you and if you need help, I'll do my best to help you out.

---

### Post by speedman2202 on 2012-08-23
i cant type in arabic beside english (like windows )

anybody can help

---

### Post by s3a on 2012-08-23
I think
```
setxkbmap ar
```
(as a regular user) should make your keyboard Arabic and
```
setxkbmap us
```
(as a regular user) should make it (American) English.

P.S.
I don't know how to do it with a GUI, assuming there is a way.

---

### Post by speedman2202 on 2012-08-24
> **s3a said:**
> I think
```
setxkbmap ar
```(as a regular user) should make your keyboard Arabic and
```
setxkbmap us
```(as a regular user) should make it (American) English.

P.S.
I don't know how to do it with a GUI, assuming there is a way.

ur codes set language just arabic or english ... cant switch between them but i have this post and work for me fine
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar


i wanna ask about my screen contrast too poor , i wanna increase :|

thx

---

### Post by Gaygerbil on 2012-08-24
You can save those commands in scripts and assign them as keyboard shortcuts if you'd like to switch between through them. 

To do this BTW simply show your hidden files in PCManFM by hitting Ctrl + H, and go to the folder '.config' from your home folder and then to the folder 'openbox'. There should be a file called 'lubuntu-rc.xml'.


Scroll down until you find the keybindings in the config file, which should look similar to what I'm about to post, you can then copy and paste these somewhere at the end of another keybinding key:

```
<keybind key="W-Left">
      <action name="Execute">
        <command>setxkbmap us</command>
      </action>
    </keybind>

<keybind key="W-Right">
      <action name="Execute">
        <command>setxkbmap ar</command>
      </action>
    </keybind>
```

This will let you switch between Arabic and English from the keyboard when you hit the two keys "Window Key and Left/Right", you can change it to what you want of course. Just make sure to use two hotkeys one is a controller and must be either Alt, Control or Windows though, which are typed as either C-, A- or W- and then the key you want. So if you wanted to make it Alt+1 it would be 'A-1', Ctrl+Alt+T = 'C-A-t' and so on.

Save your config file and either right click on your desktop and click reload through openbox or logout/login to see if it works for you.

Contrast settings are usually found on the monitor itself and are not done through an operation system. Look at the buttons on your monitor.

Good luck.

---

### Post by speedman2202 on 2012-09-03
it's not works for me

have alook

[[img]http://s11.postimage.org/s1foxexjj/2012_09_03_084617_1024x768_scrot.jpg[/img]](http://postimage.org/image/s1foxexjj/)


even spell checker for firefox not working aswell cuz every word i type seemed be spelled worng

any idea plz?

thx

---

### Post by speedman2202 on 2012-09-03
i have do small search and find this code

> echo '@setxkbmap -option grp:alt_shift_toggle "us,ar"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart

and works fine for me


thx

---

