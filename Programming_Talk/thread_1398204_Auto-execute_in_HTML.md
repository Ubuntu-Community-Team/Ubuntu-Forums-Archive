---
title: "Auto-execute in HTML"
date: 2010-02-04
forum: Programming Talk
---

### Post by schmidtbag on 2010-02-04
I'm not really a web developer, but I did make a program that would be useful for web browsers.  The program uses fingerprint readers to log into websites, and currently its only started by keyboard shortcuts or launchers.

What I wanted to do is make it so you could create a bookmark in a web browser that will run my program WITHOUT the run/save dialog.  With browsers like Firefox, Konqueror, and Opera, you can have the launcher on a bookmark bar where someone could quickly and easily click on that and not have to minimize or use up space on their panels.

So, does anyone know if this is possible?  Although I don't make web sites, I am comfortable with HTML and Javascript.  If it isn't possible, does anyone have any alternative ideas that wold work just as well?

---

### Post by tturrisi on 2010-02-04
I don't believe there's any way of bypassing that "run-save" dialog in browsers.  Browsers should not be able to install or run system software without user interaction.  If there was a way to do this then malware would not have to exploit system-browser vulnerabilities, any site could then install anything on a system.  And's that's bad.

The other thing to consider is that the secure site must somehow support this type of login.  The fingerprint must POST to the server application which interprets the fingerprint value as true or false.

I don't see this type of application as valuable on the WWW but perhaps has some value on Intranets.  But don't let my opinion discourage you.

---

### Post by Hellkeepa on 2010-02-04
HELLo!

The only way[COLOR="Blue"]*[/COLOR] I know of to get a HTML-page to be able to execute local files, is by using IE, storing the page on your computer, and editing the registry to set up a new zone for localhost only. Anything else would be a prime vector for worms, and other malware, to abuse readily.

What I'm really curious about, however, is how this system of your work. I'm having a little trouble seeing how this could actually be secure, seeing as it relies upon an application run on the client by the client. How have you implemented this, exactly? Any server-side components in the works here, or is it all JS and this app of yours?

*[COLOR="Blue"]*[/COLOR] Only way without exploiting bugs in certain browsers and/or plugins, which may or may not be patched.*

Happy codin'!

---

### Post by SemiBuz on 2010-02-04
Java ? Once you authorize it ( just once in a *lifetime* ) to run, it can do whatever you need ..

[COLOR=Gray]** I know, the topic says HTML but as far as I know, it's impossible.[/COLOR]

---

### Post by schmidtbag on 2010-02-04
> **SemiBuz said:**
> Java ? Once you authorize it ( just once in a *lifetime* ) to run, it can do whatever you need ..

[COLOR=Gray]** I know, the topic says HTML but as far as I know, it's impossible.[/COLOR]

i heard about that but idk java that well

---

