---
title: "Where can i view my installed Applications?"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by rami5 on 2013-10-04
^ Topic

---

### Post by slickymaster on 2013-10-04
Open a terminal window and run the following command:```
dpkg --get-selections
```If don't feel comfortable seeing the entire list in the terminal, you can always output the result of the said command into a txt file, like this:```
dpkg --get-selections > installedApps
```

---

### Post by deadflowr on 2013-10-04
The dash.

It's the top icon in the left side panel thingy(also called the launcher)
If you simply click on the dash and go to the bottom area of the opened windows screen, you'll see several icons.
The first is the home icon and then several others. I forget which one is which, but one of them is for the apps menu. You can click on that to show just apps. Then it'll show apps in 3 area, recently opened. all apps installed(what you want), and downloadable apps. Click the arrow next to installed and it will expand the list, apps are listed alphabetically.

Two more methods to get to the apps screen are.
1) right click on the dash icon and select the entry applications.
2) use the ketboard shortcut super(the windows key button) + A.

---

### Post by newb85 on 2013-10-04
There's a slight difference. Slickymaster's method will show all installed packages, while deadflowr's will show all installed apps. The second won't show technical packages that you probably don't want to see.

---

### Post by rami5 on 2013-10-04
Holy smokes, thats a long list! ( the one in terminal )
The one one in Dash Home was more what i was looking for :)

I notice there is also a Tab for Documents, Music/ Audio, Movies/ Video
Why no Tab for Picture/ Images?

---

### Post by deadflowr on 2013-10-04
I don't know which version of Ubuntu you're running, but as of right now on the development release aka saucy I have a home, apps,file/folder, music, video, PHOTO, and something called social networking tabs.

I, however, have set the privacy setting to not show most files in the dash, with a few exceptions.

---

### Post by rami5 on 2013-10-04
I have version 12.04 LTS
Downloaded from the official download page i believe

---

