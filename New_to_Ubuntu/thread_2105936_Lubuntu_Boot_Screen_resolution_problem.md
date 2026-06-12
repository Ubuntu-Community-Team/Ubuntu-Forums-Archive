---
title: "Lubuntu Boot: Screen resolution problem"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by rashidaa on 2013-01-17
I am new to lubuntu but has been a windows lover for almost 10 years. Now I find my computer has very low configuration with *newer* windows and beyand xp3 any thing is impossible. I basically have been a developer writing web programs and my recent interest is in 3D modelling (Blender) which I am learning my own. I think lightweight linux such as lubuntu can offer me better choices. I am trying it at present from USB. 
However, I face a problem:
when lubuntu boots, I am not able to see the desktop and just a message which indicates that either I should change screen resolution to 2048*1152 or should change the monitor.
I am able to overcome this using following trick 
[B][COLOR="Red"]step1[/COLOR]. Alt +F2
[COLOR="red"]step2[/COLOR]. xrandr -s 1[/B]
and the xdesktop appears, thereafter I do not have any problem, but this trick I have to repeat at every time.

My question to expert ubuntuers ("Exubuntuers")is whether I can fix it so that I do not need to use this rick after every boot.

I have read somewhere that one can create .xprofile at home directory and setting screen resolution in it by following command
**[COLOR="RoyalBlue"]xrandr --output ('default' in my case) --mode 1680x1050 60[/COLOR]**
however, I don't know how to create .xprofile.
Hope I have posed the problem properly.

---

### Post by audiomick on 2013-01-17
I am guessing, but going by your description you need to create a text file in your /home/user directory. The point before the file name .likethis would make it a hidden file, which is typical for user configuration files. It certainly shouldn't break anything if you create such a file, so I think you can try it out and see.

Open your text editor. I don't know for sure, but I think that is leafpad on lubuntu. Enter that text, and save as /home/user/.xprofile where "user" is your user name.

---

### Post by rashidaa on 2013-01-17
thanks for the reply, I face another problem creating .xprofile
it is not saved in next boot here it differs from puppy linux, which gives an offer before shutdown that session is to be saved or not. How to save the file created in a particular session.

---

### Post by audiomick on 2013-01-17
I've done a bit of searching, but not found anything that is exactly the same. I think I have the principle right, though.

Look here
[http://askubuntu.com/questions/142822/how-can-i-change-the-default-screen-resolution]("http://askubuntu.com/questions/142822/how-can-i-change-the-default-screen-resolution")

The third post describes doing the same thing, but with a different text in the file to solve a different problem.

As I said, open the text editor, create the file and save it where I said. I will still be there the next time you boot. xrandr will apparently look for it and use it when you boot up.

What I didn't know can be seen in that post. You have to make it an executable file. There is a command for that in that post.
```
chmod +x .xprofile
```

I'm not sure with the file manager in lubuntu, but I think you should also be able to right click on the file once you have created it, look at "properties" and look for the tab with "permissions". See if you can make it executable there. This is possible in standard Ubuntu.

---

### Post by rashidaa on 2013-01-18
chmod +x .xprofile 
does'nt makes the file executable
How I can activate this file at command prompt, not from terminal but from command prompt

---

