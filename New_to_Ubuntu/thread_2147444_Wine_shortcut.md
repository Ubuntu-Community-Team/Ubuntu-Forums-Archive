---
title: "Wine shortcut"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2013-05-22
Wondering if you all can help. 

I want to create a shortcut on my desktop to run Ultima. 
I've created it but it doesn't run correctly
wine /home/buzz/.wine/drive_c/Program Files/Electronic Arts/Ultima Online Classic/client.exe

But here's the thing. When I run this program I right click I have 2 options to "open with" One is wine, But that throws an error. I have to open with "Wine Windows Program loader" then it will open like it should. 

Question is, How do I make a shortcut to "Wine Windows Program Loader"?

---

### Post by Tjkhan on 2013-05-22
[LIST=1]
[*]Open Terminal. To open terminal click the Dash home from Unity  launcher. And type terminal in the search field. And click Terminal.

[*]Type the below code in terminal and hit enter.
  
sudo apt-get install --no-install-recommends gnome-panel 
[*]Then type below code in terminal and hit enter

gnome-desktop-item-edit ~/Desktop/ --create-new 
[*]The create launcher window will pop-up,Type application name in  the name field and type application name or path or browse in the  command field. And click OK button. (See Cinepaint example in second attachment below.)

[*]Now check your desktop for the shortcut. (First attachment below.)

[*]If you want your shortcut to appear in the Unity launcher panel  (the pop-out one on the left), you can drag it there from the desktop.

[/LIST]

---

### Post by Tjkhan on 2013-05-22
let me know if it helps

---

### Post by Bucky Ball on 2013-05-22
@ Tjkhan: Please, spare a thought for those with low speed connections and vision issues; refrain from posting large images in the body of your post. Attach them instead by editing post>Go Advanced>attach using the paperclip icon. Thanks.

(PS: You can do this yourself or I can check back shortly and do it myself and edit the post text logically. Cheers. ;))

---

### Post by dodo3773 on 2013-05-22
Wine Windows Program Loader command is: 
```

wine start /unix /path/to/exe

```

See for yourself:
```

$ cat /usr/share/applications/wine.desktop

```

---

### Post by BuzzStPoint on 2013-05-22
> **dodo3773 said:**
> Wine Windows Program Loader command is: 
```

wine start /unix /path/to/exe

```

See for yourself:
```

$ cat /usr/share/applications/wine.desktop

```

dodo. That is what I was looking for!! Thank you!
Changed my short cut from "wine /path/to/prog" to "wine start /unix /path"

Other then the obvious command change. What's the difference between the two?

---

### Post by Tjkhan on 2013-05-22
@[**[COLOR=#C61919][B]Bucky Ball**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316") Thanks. I was about to do that. Thank you again

---

### Post by dodo3773 on 2013-05-22
> **BuzzStPoint said:**
> dodo. That is what I was looking for!! Thank you!
Changed my short cut from "wine /path/to/prog" to "wine start /unix /path"

Other then the obvious command change. What's the difference between the two?

Yeah no problem you're welcome. I'm not really sure what the big difference is. I don't see anything of particular interest in the man page either. I just know where application .desktop file shortcuts are. For me the solution for wine apps not loading from shortcuts was to change "wine /path/to/program" to "cd /path/to && wine program". I've had problems in the past as well. Maybe try that one too if you have issues.

---

