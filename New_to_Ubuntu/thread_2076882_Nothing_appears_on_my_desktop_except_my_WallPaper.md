---
title: "Nothing appears on my desktop except my WallPaper"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by Paari on 2012-10-27
Hi. I'm currently using ubuntu 12.10 quantal and i'm loving it. I tried to install infinity conky. I followed the instructions correctly from here...

[http://www.unixmen.com/infinity-a-stunning-theme-for-conky-ubuntu-linuxmint-fedora/](http://www.unixmen.com/infinity-a-stunning-theme-for-conky-ubuntu-linuxmint-fedora/)

Everything went on well and finally when i ran it using the code below in terminal, an error appeared and it kept filling the terminal forever... repeating "Error: No Battery found Bat-1".

```

chmod a+x ~/.conky/startconky.sh
sh ~/.conky/startconky.sh

```I minimized all the applications and found Conky running good. After a while the entire conky appeared with a White background, instead of my ubuntu background. Also i've added Conky to the start up applications as said in the instructions. I closed the terminal killling the code, and i restarted.
When i logged in, nothing was visible except my desktop background. I used "ctrl+alt+T" to run terminal and opened firefox through it. Now i'm typing from it. Any help !!!:( Kind of Freaky...

Thanks in advance:)

---

### Post by zombifier25 on 2012-10-27
Perhaps the 15 seconds delay is not enough for your system to start before Conky does. Modify the script and increase the startup time (try 40 seconds)

EDIT: About the error you keep receiving in the terminal, it's because the Conky config has an object for displaying battery, while your computer doesn't run on battery (or it doesn, but it doesn't use BAT1)

---

### Post by larrys4227 on 2012-10-27
> **Paari said:**
> Everything went on well and finally when i ran it using the code below in terminal, an error appeared and it kept filling the terminal forever... repeating "Error: No Battery found Bat-1".



Not really anything to worry about ..... the config file as it stands simply cant find your battery.  Your battery may be on bat0, but if it really bothers you, just open the .conkyrc file and comment out (#) the battery line

Follow the advice given above. Conky needs to be delayed until the startup process is completely done ....hence, the delay. Unusual things will happen otherwise.

[IMG]http://www.pbase.com/lakebiker/image/146504778/medium.jpg[/IMG]

---

### Post by Paari on 2012-10-27
Thank you larrys4227 and zombifier25:) As you have said i've deleted the  battery block and the "name=," block. Now the errors are gone and conky  starts very well. But Still my sidebar, menubar(at top) and my  beautiful dock are not visible. Only the wallpaper and conky are  visible. Well i can also open all the other applications through  terminal like usual. For example: firefox, nautilus, gedit, etc. But as a  beginner i greatly need my sidebar to open stuff easily.  Any help !!!

Again Thank you for your help :)

---

### Post by zombifier25 on 2012-10-27
What happens if you run "killall conky" in the terminal?
Also, it would be helpful if you attach a screenshot of your current desktop.

---

### Post by Paari on 2012-10-28
I have attached the screen shots of my desktop before and after I ran your code...

```

killall conky

```I tried ubuntu Tweak. Then I cleared all the unnecessary files in my home folder(The attempts which i had given before to install conky)  And i had given many attempts to restore my desktop. But couldn't resolve. Any Suggestions.... :popcorn:

Thanks:)

---

### Post by NikTh on 2012-10-28
Hi , 

try ```
setsid unity
```If nothing happens , then open compizconfig-settings-manager and enable Unity Plugin. 

```
ccsm
```You can open a terminal with CTRL+ALT+T keys combo 
You can install ccsm with this command ```
sudo apt-get install compizconfig-settings-manager
```Thanks

---

### Post by zombifier25 on 2012-10-28
> **NikTh said:**
> Hi , 

try ```
setuid unity
``` 

If nothing happens , then open compizconfig-settings-manager and enable Unity Plugin. 

```
ccsm
``` 

You can open a terminal with CTRL+ALT+T keys combo 
You can install ccsm with this command ```
sudo apt-get install compizcofig-settings-manager
```

Thanks

Err what is the point of
```
setuid unity
```
?

And it's compizco**n**fig-settings-manager. Also, you **can't** disable Unity in CCSM.



OP, run this command to determine if Compiz is indeed running:
```
ps x | grep compiz
```
If it only outputs "grep --color=auto compiz", then Compiz is not running. Try launching it manually.

You should reset all Compiz settings to their original values.
```
gconftool --recursive-unset /apps/compiz-1 
```

---

### Post by stinkeye on 2012-10-29
**NikTh** just had a couple of typos and
you can disable/enable unity in ccsm.
The disable button just isn't available until you enter the Ubuntu Unity Plugin.

In Quantal to set compiz back to defaults use
```
dconf reset -f /org/compiz/
```

Then reload with...
```
setsid unity
```

To install ccsm use...
```
sudo apt-get install compizconfig-settings-manager
```

and to run, alt+f2 or open the dash, and enter
```
ccsm
```


**@ Paari**...other commands you may find useful.
wmctrl is a useful little program which among other things can show your
current window manager.
```
sudo apt-get install wmctrl
```

Check window manager
```
wmctrl -m
```
eg my output```
[COLOR="YellowGreen"]glen@Quantal:~$[/COLOR] **wmctrl -m**
Name: [COLOR="Red"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

Also the conky your using uses a bash script to delay the start of your conky config which is at ~/.conkyrc.
You can delay the start of conky using it's in built pause function (-p [COLOR="DimGray"]<secs>[/COLOR])
So instead of using the bash script in startup applications you could just use
as the command...
```
conky -p 20
```

---

### Post by NikTh on 2012-10-29
**Sorry for the typos.** Corrected. 

[zombifier25]("http://ubuntuforums.org/member.php?u=1251447") , [stinkeye]("http://ubuntuforums.org/member.php?u=684510") answered :)

---

### Post by Paari on 2012-11-02
Thank you all That worked !! Thanks a lot !! :P :P :P

---

### Post by Paari on 2012-11-02
Thank you Stinkeye, that greatly helped. Thank you Nikth and Zombifier25. I just entered all the commands as listed and enabled it in compizconfig settings manager. Yes it worked ! Thank a lot !! Thank you all....

ps: Great help for a newbie ;)

---

### Post by stinkeye on 2012-11-02
> **Paari said:**
> Thank you all That worked !! Thanks a lot !! :P :P :P
Good. \\:D/
> After a while the entire conky appeared with a White background, instead of my ubuntu background. 
If you find this still happening and your config  includes...
```
own_window_type **override**
```

Change to...
```
own_window_type **normal**
```

and check this setting is also in your config..
```
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```

**own_window_type override** ignores **own_window_hints** but 
**own_window_type normal** needs **own_window_hints**

**own_window_type override** gave me problems in Quantal when used
with **own_window_transparent yes**

---

### Post by Paari on 2012-11-02
My conky get's that white background mostly when I run multiple applications or when I run some updates.  Now I've modified the .conkyrc file as suggested...

```

# Window specifications #

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

```

Thanks again  :)

---

### Post by tlan on 2013-04-01
this worked for me, 

when using 12.04 i used own_window_type overide so conky was transparent on desktop

now that i upgraded to 12.10 i need

own_window_type normal which makes conky transparent but you can see the background borders of conky :confused:

---

### Post by stinkeye on 2013-04-02
> **tlan said:**
> this worked for me, 

when using 12.04 i used own_window_type overide so conky was transparent on desktop

now that i upgraded to 12.10 i need

own_window_type normal which makes conky transparent but you can see the background borders of conky :confused:
When using own_window_type **override** conky windows **are not** under the control of the window manager.
When using own_window_type **normal** conky windows **are** under the control of the window manager so you need to exclude conky from having shadows drawn by the window manager (compiz).

ie
In ccsm > effects > window decoration
change the shadow windows box to...
```
(any) & !(class=Conky)
```
The "**!**" reads as "not" .

---

### Post by Deaner13 on 2013-04-02
> **larrys4227 said:**
> 
[IMG]http://www.pbase.com/lakebiker/image/146504778/medium.jpg[/IMG]

Larrys what is the application in this picture? That is a marvelous little toolbar you have there.

---

### Post by tlan on 2013-04-07
> **stinkeye said:**
> When using own_window_type **override** conky windows **are not** under the control of the window manager.
When using own_window_type **normal** conky windows **are** under the control of the window manager so you need to exclude conky from having shadows drawn by the window manager (compiz).

ie
In ccsm > effects > window decoration
change the shadow windows box to...
```
(any) & !(class=Conky)
```
The "**!**" reads as "not" .

This worked, I no longer have that border. Thanks

---

### Post by deadflowr on 2013-04-07
> **Deaner13 said:**
> Larrys what is the application in this picture? That is a marvelous little toolbar you have there.

Do you mean conky?

Look at this thread for inspirations:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

