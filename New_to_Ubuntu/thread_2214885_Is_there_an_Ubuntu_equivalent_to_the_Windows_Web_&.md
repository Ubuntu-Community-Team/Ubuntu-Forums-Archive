---
title: "Is there an Ubuntu equivalent to the Windows Web &quot;shortcut&quot;?"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by WB0HYQ on 2014-04-03
I have a directory that is shared by both Ubuntu and Windows machines.  I sometimes store shortcut URL's by selecting (in Windows) the context menu item of "New -> Shortcut", add the URL and a name and it gets stored.  When I double-click it, my browser opens and I get taken there.

If I click it under Ubuntu, I get asked to locate something that can 'open' it.  Using a text editor, I can see that the URL is present, along with some other information, but apparently the URL is not used to send the browser there.  Is there an equivalent file under Ubuntu that does the same thing?  If so, how is it created?

Thanks,

Bill

---

### Post by PartisanEntity on 2014-04-03
Here is one solution being offered that I personally have not tried as I don#t use Windows at home:
[https://ubuntugenius.wordpress.com/2009/12/09/how-to-open-url-internet-explorer-shortcuts-in-ubuntu-using-firefox/](https://ubuntugenius.wordpress.com/2009/12/09/how-to-open-url-internet-explorer-shortcuts-in-ubuntu-using-firefox/)

---

### Post by Dave_L on 2014-04-03
One way is to manually create a file with the extension .desktop and contents similar to this:

```
[Desktop Entry]
Encoding=UTF-8
Icon=text-html
Type=Link
Name=xyz.desktop
URL=http://ubuntuforums.org/showthread.php?t=2214885
```

Depending on your Ubuntu version, desktop environment and file manager, there are shortcuts available.

---

### Post by WB0HYQ on 2014-04-03
@PartisanEntity:  My attempt, like most of the comments in the original blog didn't work.  I fiddled with it, but still couldn't make it work.

@Dave_L:  I'll give that a try.  I'm using Ubuntu 12.04LTS(64-bit).  I was hoping for something that would open it with a single (or double) click.

Let me play around a bit and see if I can come up with something that makes it happen.  If not, then I'll have to go the 'favorites' route and build up a FX folder full of them and sync with my Windows machine.  On reflection, that's probably a better way to go anyway.

Note: I didn't realize until just today that Windoze doesn't allow anyone to create a directory that contains a leading 'period (".").  Strange.  It can 'see' them, just not create them.

Bill

---

### Post by mcduck on 2014-04-05
you can just drag a tab or the favicon from the url bar of your browser to the desktop and it'll create a shortcut for you...

As far as I know there's there's no (easy) way of sharing the web shortcut between Windows and Linux though, as they use a a different syntax.

---

### Post by WB0HYQ on 2014-04-05
That was pretty much my conclusion also.  Without some sort of scripting (in either/both of the OS's) there isn't a way to do it.

Thanks everyone for your help.

Bill

---

### Post by oldfred on 2014-04-05
Oldfred used to keep his notes in a textfile and have to copy links into Firefox and lots of bookmarks. But since converting to Zim, I can just click on a link in the text file and it works. Not sure if you could just open the Windows file with Zim or other similar editors.

I used to share my Firefox with XP, but now do not use XP. That made all bookmarks the same in Windows & Ubuntu. I put profile in a shared NTFS partition.

---

