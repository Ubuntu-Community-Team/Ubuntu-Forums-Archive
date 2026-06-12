---
title: "How to install VLC theme"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by abhilash1989 on 2008-09-11
i hava dwnld vlc theme from gnome-look.org...........
but im unable to install it.......
HOW TO INSTALL THE THEME

---

### Post by ds[de] on 2008-09-11
I'm guessing you downloaded a file with a .vlt extension.

Open VLC, then choose 'Properties' from the menu, then 'properties' from the submenu that just popped up.

In there, go to 'Interface' -> 'Main interface' -> 'Skins'. 
In the bottom right corner check 'advanced options'. Now you should be able to choose the skin (i.e. the .vlt file) you desire. Just copy the entire path to said .vlt file in the upmost textline and it should adjust after a click on 'Save'.

Hope this works for you.

PS: A clearer description of the problem at hand will get you help sooner in most cases (for example: what's the name of the file you downloaded, where'd you save it etc..)

If this does the trick for you, please mark this thread as solved using the thread tools. Thank you.


Regards,
ds[de]

---

### Post by abhilash1989 on 2008-09-12
i have done what all u have told n got the theme.........
but whenever i close VLC and again start it, the defult theme is getting displayed......shud v change the theme everytime v start the program??

---

### Post by DaEMoN390 on 2009-01-31
> **abhilash1989 said:**
> i have done what all u have told n got the theme.........
but whenever i close VLC and again start it, the defult theme is getting displayed......shud v change the theme everytime v start the program??

I know this is a little old but, I was having the same problem. 
To fix this, you need to go to preferences> Interface > Main interfaces > check "Skinnable Interface" and "Skins loader demux" and save.

---

### Post by nvjopsddhapnv on 2010-07-24
> **abhilash1989 said:**
> i have done what all u have told n got the theme.........
but whenever i close VLC and again start it, the defult theme is getting displayed......shud v change the theme everytime v start the program??

Try the following it will fix the problem ... 
Download and save the xxx.vlt files in /home/user-name/.local/share/vlc/skins2/  folder.
Then hit Alt+F2+Enter 
write vlc and then press enter. 
Then press right-click on vlc screen and follow interface -> preference or directly you can type the keyboard shortcut Ctrl+P it will do the job. Then the following window will pop-up. Now you have to change the interface type from native to skins then brows the .vlt file from /home/user-name/.local/share/vlc/skins2/ folder. Generally if you click brows it will not show the .local folder then you have to do the following 
1)click brows one window will pop-up
2)in that window press right-click and choose show hidden files option it will do the job

[IMG]http://img375.imageshack.us/img375/7958/screenshot1fd.png[/IMG]


restart the vlc you will see your desired screen 
 e.g. 

[IMG]http://img830.imageshack.us/img830/4771/screenshots.png[/IMG]

and it will not go if you restart vlc for several number of times

---

