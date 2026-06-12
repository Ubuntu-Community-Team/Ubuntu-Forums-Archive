---
title: "Open website in browser using terminal?"
date: 2007-12-14
forum: Programming Talk
---

### Post by mdpalow on 2007-12-14
Is there a terminal command that would allow you to open a browser and go to a specific website?

thank you...

---

### Post by cnr437 on 2007-12-14
lynx or curl

---

### Post by Natr0n on 2007-12-14
```
[insert browser of choice here] "www.thewebsite.com"
```
Should work pretty much the same for any browser as far as I know. Do not include the brackets.

---

### Post by mdpalow on 2007-12-14
thank you Natr0n...

Geez... I did that, but just realized when I scrolled through my previous commands I had a space in the name that was messing it up.

hmm, I'm wondering though - what if you didn't want the command to be browser specific? I have a feeling that's not going to work without a script checking to see what browser you're running..

Any thoughts?

---

### Post by LaRoza on 2007-12-14
For Ubuntu, expect Firefox to be installed, so you can use:

```

firefox http://ubuntuforums.org

```

---

### Post by engla on 2007-12-14
The command ```
x-www-browser
``` should point to the user's preferred browser.

---

### Post by mdpalow on 2007-12-14
Thanks LaRoza...

I'm just wondering how many people don't use Firefox and therefore might uninstall it in favor of say.... opera.

---

### Post by mdpalow on 2007-12-14
> **engla said:**
> The command ```
x-www-browser
``` should point to the user's preferred browser.

now that's what I was hoping for... thanks.

One question about this command. I ran it and it brought up Opera, which surprised me a bit. Granted, I had downloaded Opera the other night just to take a look at it.

Do you think 'x-www-browser' brought up Opera because it was the last browser I installed?

thanks...

---

### Post by LaRoza on 2007-12-14
> **mdpalow said:**
> Thanks LaRoza...

I'm just wondering how many people don't use Firefox and therefore might uninstall it in favor of say.... opera.

I didn't know of x-www-browser.

I use Opera myself, and have uninstalled Firefox on Ubuntu before.

You might have made Opera your default.

---

### Post by pedro_orange on 2007-12-14
Browser companies like you using their browser, so usually in the install somewhere it says "Make x default browser"

Would be interesting to know where 'buntu saved this information.

---

### Post by jpkotta on 2007-12-15
You can change x-www-browser with update-alternatives.  The setting is implemented as /usr/bin/x-www-browser symlinked to the desired browser binary, IIRC.  I think any package that uses the Debian alternatives system makes that package the default when it is installed.

You can set it with ```
sudo update-alternatives --config x-www-browser
```

I've seen a few programs that look at the BROWSER environment variable.

---

### Post by engla on 2007-12-17
Yes well I think I was wrong. That would start the **system's** preferred browser.

I'll go back and make it even simpler. I think this command is really going to respect the user's settings

```
gnome-open <uri>
```

This general command will handle any file path or url, file paths being opened in their default applications of course. (And OTOH, this is gnome-specific :( )

Edit: Hehe, one more try?

```
xdg-open <uri>
```

This should be desktop-independent since that is what freedesktop and xdg stand for. However, this is from the package 'xdg-utils' and I'm not certain it is universally available.

---

### Post by mdpalow on 2007-12-18
hi engla,

Thank you for this post. 

I had actually unsubscribed from it because I thought it had been resolved (hence the late thank you), but I just came back and saw your solution and it's actually a very good one.

thanks again...

---

### Post by Endolith on 2008-12-12
Wait.  Which is the correct way to open the browser, if you're writing a system script?

[LIST]
[*]**x-www-browser** is a symlink to a symlink to a symlink and is global for all users
[*]**gnome-open** is for gnome only
[*]**exo-open** is for XFCE only?
[*]**kde-open** is for KDE only?
[*]**xdg-open** is supposed to be cross-desktop, and apparently calls all of the above depending on your desktop
[/LIST]
      Are there others?  Which is the canonical way to open a URL in the user's preferred browser?

---

### Post by mssever on 2008-12-12
> **Endolith said:**
> Wait.  Which is the correct way to open the browser, if you're writing a system script?

**x-www-browser** is a symlink to a symlink to a symlink and is global for all users
**gnome-open** is for gnome only
**exo-open** is for XFCE only?
**kde-open** is for KDE only?
**xdg-open** is supposed to be cross-desktop, and apparently calls gnome-open if you use Gnome?

Are there others?  Which is the canonical way to open a URL in the user's preferred browser?
My preference is xdg-open, since it's the most flexible. x-www-browser isn't user-configurable. The others are desktop-specific. xdg-open seems to be the best of all worlds.

---

### Post by zeezam on 2008-12-15
Trying to open a website with opera over ssh but got failed to open the X server.

I try with 
```

/path/opera -fullscreen -display=user:0 &

```

any ideas?

---

### Post by mssever on 2008-12-15
> **zeezam said:**
> Trying to open a website with opera over ssh but got failed to open the X server.

I try with 
```

/path/opera -fullscreen -display=user:0 &

```any ideas?
Just use the same command to open opera as you would if you were opening it on the local machine. SSH automatically sets $DISPLAY to the correct value, so you don't need to manually specify it. Of course, this presupposes that you're using the SSH option ForwardX11.

---

### Post by zeezam on 2008-12-16
> **mssever said:**
> Just use the same command to open opera as you would if you were opening it on the local machine. SSH automatically sets $DISPLAY to the correct value, so you don't need to manually specify it. Of course, this presupposes that you're using the SSH option ForwardX11.

Just got;

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: cannot connect to X server 
opera: Fatal error on creating Qt application object

---

### Post by Endolith on 2008-12-16
You are using ssh -X, right?

---

### Post by nathand28 on 2008-12-16
Simple, use
```

gnome-open "website" 

```
Without the quotes and use http:// or https:// at the start.

(EDIT) Looked at the post above by Engel, and he already posted this.

---

### Post by Endolith on 2008-12-16
> **nathand28 said:**
> Simple, use
```

gnome-open "website" 

```Without the quotes and use http:// or https:// at the start.

xdg-open does the same thing, but works in Gnome, KDE, etc.

---

### Post by mssever on 2008-12-16
> **nathand28 said:**
> Simple, use
```

gnome-open "website" 

```Without the quotes and use http:// or https:// at the start.
Better to leave the quotes there. Many URLs include characters that have special meaning to the shell and will cause problems if not quoted.

---

### Post by zeezam on 2008-12-17
> **Endolith said:**
> You are using ssh -X, right?

No, I tried with that and then opera starts on my computer even if I run the command in terminal via ssh on another computer. I want to start the browser on the remote computer.

---

### Post by mssever on 2008-12-17
> **zeezam said:**
> No, I tried with that and then opera starts on my computer even if I run the command in terminal via ssh on another computer. I want to start the browser on the remote computer.
Wait. You're trying to make the window for the opera installed on your local machine appear on a remote machine? If so, I have no idea how to do that. My instructions were for opening a remote opera's window on the local machine.

---

### Post by zeezam on 2008-12-29
> **mssever said:**
> Wait. You're trying to make the window for the opera installed on your local machine appear on a remote machine? If so, I have no idea how to do that. My instructions were for opening a remote opera's window on the local machine.

Ok.
With firefox is it this parameter:

```

/usr/bin/firefox --display=:0.0

```

---

### Post by zeezam on 2009-01-05
> **zeezam said:**
> Ok.
With firefox is it this parameter:

```

/usr/bin/firefox --display=:0.0

```

Any?

---

### Post by Zugzwang on 2009-01-05
> **zeezam said:**
> Any?

You're in the wrong forum here (this one is about programming). Anyway, for security, you might need to be the user who is logged in at that machine locally at the moment.

---

### Post by junke1990 on 2009-09-15
you can if you add -Y to the -X ;)

---

### Post by Fhernd on 2010-08-01
I prefer this method (using Google Chrome):

*Alt + F2*

Type the next command on the textfield:

*google-chrome [http://www.feedly.com/](http://www.feedly.com/)*

Then activate the *Run in terminal* checkbox.

Lastly, click on *Run* button (Alt+R).

Regards.

---

### Post by shantiq on 2011-12-15
an intersting trick if you have compiz [can also be done with metacity and no doubt unity] installed is to open your favourite website from a hotkey



open CCSM    to install   ```
sudo apt-get install ccsm
```


in General tick commands box    then double-click commands


and enter for example  ```
firefox  http://facebook.com
```


then click on key-bindings and now pick a hotkey say F4 or CTRL+F4


now simply click F4 or CTRL+F4 when you want to see facebook

---

### Post by samarthmath on 2012-10-17
One more command to open the system's preferred browser is:


sensible-browser [www.google.com](www.google.com)

This works.

---

