---
title: "Can't make Waterfox Classic a &quot;favorite&quot; on launcher in Ubuntu 20.04.1"
date: 2020-08-14
forum: New to Ubuntu
---

### Post by kate.t on 2020-08-14
Hello everyone,

Early this week I installed Ubuntu 20.04.1, a fresh installation. I then began installing my browsers. Chrome gave me no trouble, and I can mark it as a "favorite," which allows me to rearrange its position on the launcher.

However, Waterfox Classic 2020.07.1 has given me a big problem. In order to start the program initially, I had to go into the Waterfox files and click the executable. Thereafter it's been on the launcher at the very bottom, and right-clicking shows I cannot make it a favorite. It's also stuck in that position at the very bottom of the launcher. When I ran the "gsettings" command to show the order of all my launcher icons so that I could rearrange the order via terminal, the Waterfox Classic program did not show up at all.

I did some reading and discovered I had to create a file called waterfox-classic.desktop and place it in the folder .local/share/applications. I read the instructions on how to do this, and here is the file I created:

 1 [Desktop Entry]
 2 Version=1.0
 3 Name=Waterfox Classic
 4 Comment=This is a web browser.
 5 Exec=/home/kathleen/waterfox-classic/waterfox
 6 Icon=/home/Kathleen/Pictures/waterfox icon.jpeg
 7 Terminal=false
 8 Type=Application
 9 StartupWMClass=Waterfox Classic
10 Categories=Utility;Application;

It's not working. Waterfox Classic will still not permit me to make it a favorite by right-clicking on the icon. The only choices there are "All Windows" and "Quit."

Did I do something incorrect when I made the .desktop file?

Any and all help is greatly appreciated!

All the best,
Kathleen

---

### Post by kurt18947 on 2020-08-15
Somebody more knowledgeable should be along to correct me if I give you bad advice, I'm not an expert. I suspect the exec line should show the path to the executable, something like 

5 Exec=/home/kathleen/.local/share/applications/waterfox_executable. 

Can you launch Waterfox if you manually navigate to that location?

---

### Post by kate.t on 2020-08-15
Hi Kurt,

Thanks for your reply! 

That is the name of the executable, "waterfox." Going to that executable in the program files is how I have to start up Waterfox Classic each time I restart the computer. It's mighty annoying. Does the .desktop file otherwise look okay?

If you or anyone else have further ideas, you will earn my undying gratitude. ):P

All the best,
Kathleen

---

### Post by Dennis N on 2020-08-15
```
1 [Desktop Entry]
2 Version=1.0
3 Name=Waterfox Classic
4 Comment=This is a web browser.
5 Exec=/home/kathleen/waterfox-classic/waterfox
6 Icon=/home/Kathleen/Pictures/waterfox icon.jpeg
7 Terminal=false
8 Type=Application
9 StartupWMClass=Waterfox Classic
10 Categories=Utility;Application;
```
The lines should not begin with numbers.
One kathleen is capitalized, the other isn't. Capitalization matters in Linux. The icon file name shouldn't contain a space. I'd remove the entire line beginning: **StartupWMClass=** and see it that makes any difference. 
The Category used for a web browser is usually **Network**.
**Application** is not a valid category.

---

### Post by kate.t on 2020-08-15
Dennis, 

Thanks for your reply! I will follow your suggestions...except, there's a problem with one thing. The lines begin with numbers because that's the way gedit lists the lines. That's why I thought I should put the numbers in my post. So you're saying I shouldn't have, right?

Best,
Kathleen

---

### Post by Dennis N on 2020-08-16
> **kate.t said:**
> Dennis, 

Thanks for your reply! I will follow your suggestions...except, there's a problem with one thing. The lines begin with numbers because that's the way gedit lists the lines. That's why I thought I should put the numbers in my post. So you're saying I shouldn't have, right?

Best,
Kathleen

The automatic line numbers in gedit would not be saved as part of the file itself. I just wanted to be sure you had not typed those numbers in yourself and saved them with the file. You can turn them off in the Preferences if you want.

---

### Post by kate.t on 2020-08-16
Hey Dennis, I'm in Arizona, too! [Good luck to both of us in this pandemic.]

I tried following all your suggestions and this is my current .desktop file:

Version=1.0
Name=Waterfox Classic
Comment=web browser
Exec=/home/kathleen/waterfox-classic/waterfox
Icon=/home/kathleen/waterfox-classic/browser/chrome/icons/default/default64.png
Terminal=false
Type=Application
Categories=Network

Unfortunately, the problem is still exactly the same. Can you think of what else I might be doing wrong, or what else I might try? Others are also welcome to chime in with ideas.

Thank you,
Kathleen

---

### Post by Dennis N on 2020-08-16
I test installed Waterfox on this computer. Like yours, when in the Dock, 'add to favorites' was missing. I added to favorites by using the search in the overview window, right-clicking on the icon, and the 'add to favorites' option was there. It worked and the icon is on the dock. See attached image (it says 'remove from favorites' since I previously added it).
 
I didn't see any supplied icon in the directory, so I found one via google search.

But, I realize now you installed the Classic version? I installed the Current version which appeared to be the main choice. 

When I launched from the dock icon, another icon appeared. To fix that, the StartupWMClass line was needed. 

For current version this works:
```
StartupWMClass=waterfox-current
```

Note: I did the install in obsolete Ubuntu 19.10 to test, but that shouldn't matter.

---

### Post by kate.t on 2020-08-16
Hello Dennis,

It was kind of you to test it out for me. The reason why I need Waterfox Classic is because it allows me to use some needed older extensions that don't work in Current.

I added the piece of code you showed in your last message and tested it out here.

It initially appeared to work, meaning when I right clicked on the icon in the overview window, the choice "Add to favorites" was there. Hooray, I thought. I added it to favorites and could move the icon where I wanted it.

At this point, I was quite excited at the prospect of success. However. When I clicked on the icon in the launcher, it proceeded to bring up the "rogue" icon at the bottom of the launcher, the one that can't be moved or favorited. The window was there, not up at the top of the launcher. 

So now I have a movable, favorited icon which does nothing but call up the program elsewhere.

Clearly, something is wrong. Any more thoughts?

Thanks for hanging in here,
Kathleen

---

### Post by Dennis N on 2020-08-16
> At this point, I was quite excited at the prospect of success. However. When I clicked on the icon in the launcher, it proceeded to bring up the "rogue" icon at the bottom of the launcher, the one that can't be moved or favorited. The window was there, not up at the top of the launcher.
You mean when the rogue icon appeared, the one you added as favorite disappeared?
 I was getting both at the same time, and only the rogue icon showing as active. Adding the **StartupWMClass=waterfox-current** prevented the rogue icon from appearing and now the the favorite icon is the active one.

I guess I will keep the Waterfox as an alternate browser. I've heard of it before, but never used it. Just now been reading up on it.

I located mine in /opt folder. For what it's worth, here's my desktop file:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Waterfox
Comment=Waterfox Browser
Icon=/home/dmn/.local/share/icons/waterfox.svg
Exec=/opt/waterfox/waterfox %u
Path=/opt/waterfox
NoDisplay=false
Categories=GNOME;GTK;Network;WebBrowser;
StartupWMClass=waterfox-current
StartupNotify=false
Terminal=false

```

---

### Post by kate.t on 2020-08-17
Dennis, good news!

Everything works perfectly now. Just one Waterfox-Classic icon, positioned just where I want it as my favorite.

Yes, I was also getting the regular icon plus the "rogue" icon at the same time. Now it's fixed. My most recent hiccup was due to having more than one .desktop file and being confused as to which one was operative. I finally figured that out, and that was the one where I hadn't yet included the "StartupWMClass" line. It's included now and all is well.

Thank you so much for your help and patience! This forum, with kind people such as yourself volunteering to help us newbies, is such a precious resource.

Now I can relax.

Hope your week is great!
Kathleen

---

### Post by Dennis N on 2020-08-17
Good news and thank you. Keep safe and cool wherever you are in Arizona.

---

