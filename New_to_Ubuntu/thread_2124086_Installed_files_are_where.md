---
title: "Installed files are where?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Cheesenacho on 2013-03-09
Well, there's a lot to Ubuntu...I managed to get Ubuntu 12 installed on an old AMD machine today, and managed to get XBMC running with the help of some forum help...Soooooo....once you install a program like Teamviewer....where does it go? I would have thought it would on the desktop, but I can't seem to find out. XBMC gave me a nice launch icon on the desktop, so maybe I didn't get Teamviewer installed like I thought...Can somebody point me in the right direction? Thanks in advance!  CN

---

### Post by Paqman on 2013-03-09
You can launch any application by hitting the Windows key and typing its name. Alternatively, hit the top button on the launcher to open the "dash" and click on the second icon at the bottom, which will show all the apps that are installed. Once a program is running you can pin it to the launcher from a right click.

---

### Post by c2tarun on 2013-03-09
well what Paqman told you is exactly what you should to do. But just an FYI if you wan't to see where the files of a particular package are installed you can issue following command in terminal:

```
dpkg -L <package-name>
```

Example

```
dpkg -L vim 
```

Output:
```

/.
/usr
/usr/bin
/usr/bin/vim.basic
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/vim
/usr/share/doc
/usr/share/bug
/usr/share/bug/vim
/usr/share/bug/vim/script
/usr/share/bug/vim/presubj
/usr/share/doc/vim

```

---

### Post by ibjsb4 on 2013-03-09
I do not use Teamviewer, but this may help.

[http://www.ubuntugeek.com/how-to-install-team-viewer-version-7-on-ubuntu-12-04-precise-pangolin.html](http://www.ubuntugeek.com/how-to-install-team-viewer-version-7-on-ubuntu-12-04-precise-pangolin.html)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Teamviewer&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Teamviewer&sa=Search&cof=FORID:9)

Another way to find out what files are installed is Synaptic Package Manager.

example:

[ATTACH=CONFIG]239991[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by Cheesenacho on 2013-03-10
So I've been reading on using the Termnal command in the Ubuntu Community, but I didn't see how to bring up a terminal...I've been searching inside of the desktop and I don't see a launcher for it. According to the teamviewer webpage, it must be run from within a terminal...hence, my problem. I have verified that it's installed, but I still don't know how to execute it.

---

### Post by Laobi on 2013-03-10
To bring up a terminal press CTRL ALT T keys.
Or open the Dash by pressing Super(windows) key and then type "terminal" in there.

---

### Post by Cheesenacho on 2013-03-10
Oh that worked! I have been typing TeamViewer in the dash and it wouldn't show up, but the post by ibjsb4 indicated Team Viewer in the link, and sure enough..it popped up. I was able to get it pinned so that helps quite a bit. Thanks for the help everyone! I'm at day 2 of Ubuntu!  CN

---

