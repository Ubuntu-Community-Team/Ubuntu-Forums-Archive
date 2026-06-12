---
title: "Do you want to open XDG-open"
date: 2022-10-13
forum: New to Ubuntu
---

### Post by nowyoumadememad on 2022-10-13
Hello everyone o/,
Since i have been a Vivaldi browser user for years i downloaded the Linux version to use in Ubuntu once i decided to try this out. Always loved vivaldi and made it my preferred browser and got this popup thing going everytime since: "Do you want to open xdg-open? A website wants to open this app", then "Cancel" or "Open xdg-open", what i choose does not make any apparent change. Is there someone out there in the interweb that can, in laymans terms, explain to me what this xdg-open nag is/mean/does. Is it an app? A bug? O just a plain pain in the posterior?
Otherwise, just to be a bit on the positive side i'm running a clean install Ubuntu on a former Win10 computer, Freaky fast multicore Intel (don't ask me), Radeon GTX 970, 32GB memory and a 270GB SSD - and it works a treat, takes off in seconds, Minor hiccups, easy fixes, loads of software and games, fantastic forums and support. Havent missed my old, geriatric mac one day since.

---

### Post by grahammechanical on 2022-10-13
> "Do you want to open xdg-open? A website wants to open this app"

Why does the website want to open an app? What app? What file or URL does this website want to open?

Please run this command and read about xdg-open.

```
man xdg-open
```

> xdg-open opens a file or URL in the user's preferred application. If a URL is provided the URL will be opened in the user's preferred web browser. If a file is provided the file will be opened in the preferred application for files of that type. xdg-open supports file, ftp, http and https URLs.

Do you trust the website? Have you clicked some button to allow the website to perform some action?

Regards

---

### Post by TheFu on 2022-10-13
xdg-open is a standard method that lets the GUI know you want to have the system look at mime types to decide which application should be used to open the data. That data can be a file, a stream or something else. In Unix, since almost everything is "a file", it is very flexible.  

There are other xdg-whatever methods too.  For example:
xdg-desktop-icon      xdg-mime              xdg-user-dir
xdg-desktop-menu      xdg-open              xdg-user-dirs-update
xdg-email             xdg-screensaver       
xdg-icon-resource     xdg-settings          
is the list on one of my desktop systems.  If you use a "Desktop Environment", they have all pretty much standardized on the xdg-whatever set of functions to make integration between applications, data, and the DE across many different installs work similarly ... er ... mostly.

I've assumed you either know what a MIME type is or can use wikipedia to learn it or any other term that isn't familiar. 

Alas, there's always an exception and some tools being push by Canonical corporate can break all this wonderful work in the name of security and Canonical-only standardization.  But most of the time, xdg-open just works and it stays out of our way.  

As an example, this is why we can use any email client, ask to open an attachment from the email and have whatever program is needed open and read the attached file.  If this doesn't work correctly, that usually means there isn't a program installed that supports the mime-type of the file or that some snap package integration is broke and won't be fixed.  The workaround for the 2nd is to save the file to the file system and open it using the program you wish. 

There definitely ARE security problems with having multiple programs integrate into a seamless interaction, so Canonical isn't completely wrong, but not providing a way for you and I to override this mandated separation for our own convenience is a bug, IMHO.

---

### Post by nowyoumadememad on 2022-10-13
I just get this popup window, no indication of what app or whatsit. There is some indication around www that some people out there have the same problem on chrome based browsers. And it started after i made vivaldi my preferred browser. Some have tried to open a thread about it on the vivaldi forums and it seem like they have a bug report on it somewhere on the back burner. It looks like it's been an item for some years now without anyone really cares. Me? I'm just curious about what this thing is, whether it may be harmful in any way or just a nag. It' just irritating something like that pops up leaving me clueless about what it is about.

---

### Post by QIII on 2022-10-13
If it is a known Vivaldi bug, then that is probably the trail to follow and to add your voice to the bug report.  Neither Canonical nor any of us can do more that add our voices to a bug.  That's for the developers of Vivaldi to address.

However, there may be another offender:  Microsoft Teams requires XDG.  Do you have Teams and if so have you elected to "stay connected" in a previous session?  That would immediately invoke xdg-open.

---

### Post by #&amp;thj^% on 2022-10-13
> **nowyoumadememad said:**
> I just get this popup window, no indication of what app or whatsit. There is some indication around www that some people out there have the same problem on chrome based browsers. And it started after i made vivaldi my preferred browser. Some have tried to open a thread about it on the vivaldi forums and it seem like they have a bug report on it somewhere on the back burner. It looks like it's been an item for some years now without anyone really cares. Me? I'm just curious about what this thing is, whether it may be harmful in any way or just a nag. It' just irritating something like that pops up leaving me clueless about what it is about.
last I used it around a year ago, I remember Just a change of the start page fixed it for me. (Note the time frame of my last usage)
If that don't work please show the output from:
```
xdg-open "https://duckduckgo.com/"
```

---

### Post by nowyoumadememad on 2022-10-14
What i did? I was guided to and read a lot about xdg-open, enough to know it's not a threat but just a bug (in my case) and as changed my startpage from vivaldi's start-page the popup-window went away. Out of sight-out of mind, didn't even think about that. I did not close the tab i opened in vivaldi forum so i will skip over to  nag a bit, just to keep'em warm. Once again, thank all for reaching out and calm my frustration. Fantastic forum!

---

