---
title: "can't execute .sh file from desktop"
date: 2018-10-22
forum: New to Ubuntu
---

### Post by otlichnik73 on 2018-10-22
Hi there everyone! I wrote a little script, saved as .sh file on desktop and changed permission in right-click menu to make it executable. However, double-clicking only opens it in text editor. If I open Nemo, and double-click, it asks to execute or read, then I can execute it fine.  However, from the desktop - no execution, even though permission changed (ran chmod +x just in case as well) Any way to change that? Cheers! (Using Ubuntu 18)

---

### Post by dino99 on 2018-10-22
Have you followed these steps ? [https://askubuntu.com/questions/77929/how-to-run-a-script](https://askubuntu.com/questions/77929/how-to-run-a-script)

---

### Post by otlichnik73 on 2018-10-22
yes, thanks - like I said, I can run it from terminal. But I want to run it by double-clicking it on desktop. I can do it this way in Nemo file manager by double-clicking the file icon - but NOT from desktop. But i really want to do it from desktop. Cheers!

---

### Post by dino99 on 2018-10-22
Searched a bit more:

Type chmod ugo+x filename. This will set the file to execute.
[https://askubuntu.com/questions/138908/how-to-execute-a-script-just-by-double-clicking-like-exe-files-in-windows](https://askubuntu.com/questions/138908/how-to-execute-a-script-just-by-double-clicking-like-exe-files-in-windows)

---

### Post by otlichnik73 on 2018-10-22
Thanks, don't mean to be rude - please read my post again. I did chmod+x. I think the issue is with the desktop somehow?

---

### Post by again? on 2018-10-22
Even though you installed nemo, nautilus probably still controls the desktop
in which case you need to change the behaviour in nautilus preferences.

---

### Post by monosyllabicbabbling on 2018-10-22
Is it important to you that the script is actually on the desktop? I normally just create a Desktop file.

Create a text file on your desktop named coolscript.desktop and put this in it:

[Desktop Entry]
Name=My cool script
Exec=bash coolscript.sh
Type=Application
StartupNotify=true
Path=/home/user
Icon=Icon for cool script.jpg

Making appropriate changes of course. Then set the properties for the desktop file to be executable.
The actual script can be anywhere on your system.

---

### Post by otlichnik73 on 2018-10-23
> **guber2 said:**
> Even though you installed nemo, nautilus probably still controls the desktop
in which case you need to change the behaviour in nautilus preferences.

YES - thanks a lot, this is the answer. Nautilus controls the Desktop behaviour!! Perfect

---

### Post by otlichnik73 on 2018-10-23
> **monosyllabicbabbling said:**
> Is it important to you that the script is actually on the desktop? I normally just create a Desktop file.

Create a text file on your desktop named coolscript.desktop and put this in it:

[Desktop Entry]
Name=My cool script
Exec=bash coolscript.sh
Type=Application
StartupNotify=true
Path=/home/user
Icon=Icon for cool script.jpg

Making appropriate changes of course. Then set the properties for the desktop file to be executable.
The actual script can be anywhere on your system.
Thank you and excuse my ignorance - so this is exactly  how the file should look? Is this a bash script that will runa the file coolscript.sh in /home/user? Is that what you mean? 
What is "Icon for cool script.jpg" entry? Cheers!

---

### Post by again? on 2018-10-23
> **otlichnik73 said:**
> Thank you and excuse my ignorance - so this is exactly  how the file should look? Is this a bash script that will runa the file coolscript.sh in /home/user? Is that what you mean? 
What is "Icon for cool script.jpg" entry? Cheers!

It's a .desktop file or launcher.
What was posted is an example.
If you wanted a launcher on your desktop you can copy from /usr/share/applications 
eg for a nemo launcher...
```
cp /usr/share/applications/nemo.desktop ~/Desktop 
```

Then make the launcher executable.
You can do this in the file browser right click properties menu or
via terminal....
```
chmod +x ~/Desktop/nemo.desktop
```


If you want a launcher for a script use monosyllabicbabbling post as an example.
Tell me the name and location of your script and I'll create a launcher for you to make it clearer.

---

### Post by otlichnik73 on 2018-10-23
> **guber2 said:**
> It's a .desktop file or launcher.
What was posted is an example.


If you want a launcher for a script use monosyllabicbabbling post as an example.
Tell me the name and location of your script and I'll create a launcher for you to make it clearer.
Thanks for the offer! What I wanted to do is create a launcher on the desktop for the program I downloaded called DocFetcher. It did not add itself to the menu, for some reason (I guess you call it "portable"?).

So the file is here: /home/user1/Downloads/DocFetcher -1.1.22/DocFetcher-GTK2.sh

the script I wrote was simply this:
```
cd /home/user1/Downloads/DocFetcher -1.1.22
./DocFetcher-GTK2.sh

``` 
It works, now that I've worked out how to execute it. But you obviously have the "proper" way of doing it - so, yes, please show me how!:P

---

### Post by again? on 2018-10-23
If you want a launcher that shows in the applications menu and can be added to the launch bar 
create the .desktop file in ~/.local/share/applications
```
gedit ~/.local/share/applications/DocFetcher.desktop
```
Copy and paste in the following...
```
[Desktop Entry]
Version=1.0
Name=DocFetcher
Exec="/home/user1/Downloads/DocFetcher -1.1.22/DocFetcher-GTK2.sh"
Type=Application
Icon=[COLOR="#FF0000"]/home/glen/Downloads/docfetcher.png[/COLOR]
Comment=document fetcher
StartupNotify=false

```

Use your [COLOR="#FF0000"]own path to a downloaded icon[/COLOR].
Search google images for "docfetcher icon png"
Here's one [https://www.zwodnik.com/media/cache/eb/48/eb4807c34f23890cb992a3e428e27ce4.png](https://www.zwodnik.com/media/cache/eb/48/eb4807c34f23890cb992a3e428e27ce4.png)

For **Exec=** I just used the path to your script and enclosed in quotes because there appears to be a space in the name.
If you need to run the script in that directory change to
```
Exec=bash -c 'cd "/home/user1/Downloads/DocFetcher -1.1.22"; ./DocFetcher-GTK2.sh'
```

Do some tests you may be able to use as in monosyllabicbabbling's example.
```
Path="/home/user1/Downloads/DocFetcher -1.1.22"
Exec=bash DocFetcher-GTK2.sh
```

Save the file and make executable...
```
chmod +x ~/.local/share/applications/DocFetcher.desktop
```

Should show in application menu where you can add to favourites.

---

### Post by again? on 2018-10-23
I downloaded docfetcher to take a look and this launcher works.
(there is no space in folder name)
Just change for [COLOR="#FF0000"]your paths[/COLOR]
```
[Desktop Entry]
Version=1.0
Name=DocFetcher
Exec=[COLOR="#FF0000"]/home/glen[/COLOR]/DocFetcher-1.1.22/DocFetcher-GTK2.sh
Type=Application
Icon=[COLOR="#FF0000"]/home/glen[/COLOR]/DocFetcher-1.1.22/img/docfetcher128.png
Comment=document fetcher
StartupNotify=false
```

---

### Post by otlichnik73 on 2018-10-23
Amazing! Thanks a lot!=d>

---

### Post by monosyllabicbabbling on 2018-10-23
> **otlichnik73 said:**
> Thank you and excuse my ignorance - so this is exactly  how the file should look? Is this a bash script that will runa the file coolscript.sh in /home/user? Is that what you mean? 
What is "Icon for cool script.jpg" entry? Cheers!


The icon is just any graphic file, it's not required but the default icon is quite dull, and if you have more than one you probably want them to look different.

---

