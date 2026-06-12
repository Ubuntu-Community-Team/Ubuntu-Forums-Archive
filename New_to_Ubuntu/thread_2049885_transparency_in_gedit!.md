---
title: "transparency in gedit!"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-08-29
okay, that's my gedit and terminal! (screenshot) 
now i want the same transparency in my gedit's background as in my terminal's. how is it possible?? please help.

---

### Post by Frogs Hair on 2012-08-29
There are Gedit themes available , but not transparent. I can suggest one that matches your current terminal color a little better.[http://gnome-look.org/content/show.php/Gmail+colour+scheme+for+Gedit?content=122775](http://gnome-look.org/content/show.php/Gmail+colour+scheme+for+Gedit?content=122775)

---

### Post by tojonukokhadush on 2012-08-29
thank you very much! if i can add transparency in that then hope it turns more nice! :-D

---

### Post by tojonukokhadush on 2012-08-30
okay, how can i now change the transparency of the background of the gedit? i am talking of only the background within the gedit not the window borders! anyway i can't do so then i can manage with the transparency of the whole window as well but if somebody gonna help me here! regards

---

### Post by Toz on 2012-08-30
Please do not create separate threads for the same issue. I have merged the two threads and removed the [SOLVED] heading.

---

### Post by tojonukokhadush on 2012-08-30
okay! i am sorry i did not realize it!! 

still transparency issue is not solved! somebody help me! 
i would then mark it as solved!

---

### Post by Frogs Hair on 2012-08-30
Use the thread tool on the top right of your post.

---

### Post by tojonukokhadush on 2012-08-30
now can nobody help how would i change the transparency of gedit?

---

### Post by spezticle on 2013-03-22
I have a solution for you. You can install and use compiz to make any program have transparency.

If you want help, reply and ask, i'll provide a more thorough explanation but i suggest googling something like 
"ubuntu compiz transparency" or something along those lines.

---

### Post by tojonukokhadush on 2013-03-27
thanks spezticle. sorry for the late response. okay i expect thorough explanation :-D

---

### Post by spezticle on 2013-03-27
so first you need to have the compiz settings manager installed:
```
sudo apt-get install compizconfig-settings-manager
```

once it is installed, you need to start the manager.
in the terminal window type
```
ccsm --category=Accessibility
```

Check the box next to Opacity, Brightness and Saturation
[IMG]http://i.imgur.com/rptuxok.png[/IMG]

Now you have some flexibility here. You can set up transparency for any and all windows. The way I have it set up is by default nothing is transparent, but while holding alt I can scroll with my mouse to increase or decrease any windows transparency. But if you just want to force gedit to be transparent, i'll also show you how to do that.

To make gedit transparent:
After making sure the box is checked, click on the icon next to the checkbox to open up the configuration settings.
[LIST]
[*]Under the Opacity tab click on New. a new window opens. 
[*]Click the + and another window opens. 
[*]type or copy/paste: ```
name=gedit
``` and modify "window values" to be the level of opacity. 
[*][IMG]http://i.imgur.com/nBpvLu3.png[/IMG] 
[/LIST]

as you see here, I have simply added button assignments for my mouse so that I can use my scroll wheel while holding alt so that i may make any window i'm focused on transparent to a level of my liking at any given moment. Personally I think this is the better option, but hey, to each his/her own, right? :)
[IMG]http://i.imgur.com/158dmND.png[/IMG]

---

### Post by spezticle on 2013-03-27
[http://youtu.be/OB3IrXAD9EA](http://youtu.be/OB3IrXAD9EA)

I had a little fun making a video demonstrating why the alt scroll for any window transparency is cool.
check it out if you like :)

---

### Post by tojonukokhadush on 2013-03-27
okay. thank you very much spezticle for your help. i'll try this :-D

---

