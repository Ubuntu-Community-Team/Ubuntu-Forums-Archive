---
title: "GNotes on the Top Bar"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Wheel on 2012-05-27
I see that GNotes has replace Tomboy.  That's fine.

How can I get GNotes on my Top Bar?

And once it's up there, what is the exec command in Add Startup Dialog to get it to autostart?

---

### Post by Wheel on 2012-05-28
I'll grant that this is a minor issue.

But, anyone?

---

### Post by Nytram on 2012-05-28
the command to start it is simply **gnote**
i don't know how to add it to the panel as i don't use unity, but you can open the **start here** note with the keyboard shortcut **alt+f11**

---

### Post by stinkeye on 2012-05-28
This terminal command gives you your current apps whitelisted for the indicator.
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
eg default output...
```
[COLOR="Green"]glen@Precise:~$[/COLOR] gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'Update-notifier']
```


Then add gnote in the same format and run in the terminal.
eg
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', '**gnote**']"
```

Set gnote to **Use Status Icon** in gnote preferences.

The startup command is just **gnote**.
Log out/in.

---

### Post by Wheel on 2012-05-28
> **stinkeye said:**
> This terminal command gives you your current apps whitelisted for the indicator.
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```eg default output...
```
[COLOR=Green]glen@Precise:~$[/COLOR] gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'Update-notifier']
```
Then add gnote in the same format and run in the terminal.
eg
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', '**gnote**']"
```Set gnote to **Use Status Icon** in gnote preferences.

The startup command is just **gnote**.
Log out/in.

Perfect.  Exactly what I was looking for.  Thanks!

---

### Post by stinkeye on 2012-05-28
No problem.
You can also add other apps that use indicators like guake or artha, but some don't play nicely with the unity panel.
You just have to test.

---

### Post by Wheel on 2012-05-28
> **stinkeye said:**
> No problem.
You can also add other apps that use indicators like guake or artha, but some don't play nicely with the unity panel.
You just have to test.

Thanks again for that.
I do a bit of writing (just for fun, mind ya).
Now I have Artha on the top bar as well.

---

### Post by LumbeeNDN on 2012-07-19
Anyone know how to do this for xchat? Same deal, I would like xchat to show up in the top bar, rather than just on the mail icon, as mentioned here [http://askubuntu.com/questions/157966/where-is-x-chat-when-it-is-minimized-to-tray](http://askubuntu.com/questions/157966/where-is-x-chat-when-it-is-minimized-to-tray).

---

### Post by critin on 2012-07-19
> **LumbeeNDN said:**
> Anyone know how to do this for xchat? Same deal, I would like xchat to show up in the top bar, rather than just on the mail icon, as mentioned here [http://askubuntu.com/questions/157966/where-is-x-chat-when-it-is-minimized-to-tray](http://askubuntu.com/questions/157966/where-is-x-chat-when-it-is-minimized-to-tray).


Hello, this thread issue has been solved, and is a couple of months old;  you would get more help if you started your own thread.  It would be noticed quicker.  :)

---

### Post by bwinfrey on 2012-07-19
> **stinkeye said:**
> This terminal command gives you your current apps whitelisted for the indicator.
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
eg default output...
```
[COLOR="Green"]glen@Precise:~$[/COLOR] gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'Update-notifier']
```


Then add gnote in the same format and run in the terminal.
eg
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', '**gnote**']"
```

Set gnote to **Use Status Icon** in gnote preferences.

The startup command is just **gnote**.
Log out/in.

Thanks.  I had this on my todo list.  I can now mark it completed.
B

---

