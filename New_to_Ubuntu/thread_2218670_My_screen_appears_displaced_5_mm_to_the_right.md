---
title: "My screen appears displaced 5 mm to the right"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by G._Gino on 2014-04-21
...uuuhhmmmm.... I have a problem. My screen appears displaced 5 mm to the right. I use nouveau drivers but I already installed the Nvidia drivers, the problem persists! Whenever I turn on the monitor, I have to press the AUTO button configuration. How can I indicate to the system that the screen will scroll 5 mm to the left? :cry: OMG!!!! :confused:

---

### Post by Vladlenin5000 on 2014-04-21
Hi, welcome.

I'm afraid you already found the only solution. Some monitors misbehave.

---

### Post by G._Gino on 2014-04-21
[COLOR=#000000][FONT=Arial]It is [/FONT][/COLOR][COLOR=#000000][FONT=Arial]strange..[/FONT][/COLOR][COLOR=#000000][FONT=Arial].[/FONT][/COLOR][COLOR=#000000][FONT=Arial]And [/FONT][/COLOR][COLOR=#000000][FONT=Arial]more [/FONT][/COLOR][COLOR=#000000][FONT=Arial]strange [/FONT][/COLOR][COLOR=#000000][FONT=Arial]that [/FONT][/COLOR][COLOR=#000000][FONT=Arial]there[/FONT][/COLOR][COLOR=#000000][FONT=Arial] is [/FONT][/COLOR][COLOR=#000000][FONT=Arial]no [/FONT][/COLOR][COLOR=#000000][FONT=Arial]application [/FONT][/COLOR][COLOR=#000000][FONT=Arial]that [/FONT][/COLOR][COLOR=#000000][FONT=Arial]will allow [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the[/FONT][/COLOR][COLOR=#000000][FONT=Arial] "[/FONT][/COLOR][COLOR=#000000][FONT=Arial]correction"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]of [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]screen[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]On [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Windows[/FONT][/COLOR][COLOR=#000000][FONT=Arial] it [/FONT][/COLOR][COLOR=#000000][FONT=Arial]all [/FONT][/COLOR][COLOR=#000000][FONT=Arial]works [/FONT][/COLOR][COLOR=#000000][FONT=Arial]perfect[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Please[/FONT][/COLOR][COLOR=#000000][FONT=Arial], [/FONT][/COLOR][COLOR=#000000][FONT=Arial]if [/FONT][/COLOR][COLOR=#000000][FONT=Arial]any one [/FONT][/COLOR][COLOR=#000000][FONT=Arial]know s[/FONT][/COLOR][COLOR=#000000][FONT=Arial]how [/FONT][/COLOR][COLOR=#000000][FONT=Arial]to [/FONT][/COLOR][COLOR=#000000][FONT=Arial]move [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]screen [/FONT][/COLOR][COLOR=#000000][FONT=Arial]to [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]left[/FONT][/COLOR][COLOR=#000000][FONT=Arial], [/FONT][/COLOR][COLOR=#000000][FONT=Arial]I appreciate [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]information[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Best regards. PS: Thanks Vladlenin5000! [/FONT][/COLOR]):P

---

### Post by Adrian_Valor on 2014-04-24
Hi, 

I had the same problem with my old computer; but only when dual booting with windows, i solved it but adjusting the screen refresh rate. There is an option in the nvidia display panel if you have the proprietary drivers installed.

Hope it helps!

---

### Post by G._Gino on 2014-04-27
I partially solved the problem with the following:

xrandr --newmode "GL930"     85.50   1366 1452 1595 1792    768  771  774  798 +hsync +vsync
xrandr --addmode VGA-1 GL930
xrandr --output VGA-1 --mode GL930

But... [COLOR=#000000][FONT=Arial]I put [/FONT][/COLOR][COLOR=#000000][FONT=Arial]the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]commands [/FONT][/COLOR][COLOR=#000000][FONT=Arial]in autostart archive and does not work when I log... [/FONT][/COLOR]:(

[COLOR=#000000][FONT=Arial]Why[/FONT][/COLOR][COLOR=#000000][FONT=Arial]?[/FONT][/COLOR]

---

### Post by G._Gino on 2014-04-28
UPDATES: I solved my "previous" problem with a script and put the archive in the "bin" directory...

My screen OK in the left right.
But now.... I see that my screen cut off 1 mm approx. in the right side, why? :confused::confused::confused:

The resolution is 1366x768
    
What can I do? ](*,)


[[IMG]http://www7.pic-upload.de/thumb/28.04.14/gwrkvhmte63d.jpg[/IMG]]("http://www.pic-upload.de/view-23018767/2014-04-28-00.12.07.jpg.html")

---

