---
title: "[SOLVED] remove opera tray icon"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-16
is there a function in opera that allows this?

---

### Post by iaculallad on 2008-06-16
Try to edit Opera's launcher command and replace it with:

> opera %u -notrayicon

man opera maybe?

---

### Post by Zopiac on 2008-06-16
> **iaculallad said:**
> Try to edit Opera's launcher command and replace it with:



man opera maybe?

um...what?

---

### Post by iaculallad on 2008-06-16
Right-click on your Opera launcher icon, select "Properties" and under the "Command:", replace whatever is in there with **opera %u -notrayicon**. Click on close.

If you don't have the Opera launcher on your panel, try creating it: Application->Internet and right-click on Opera and select "Add this launcher to Panel".

---

### Post by shebuwa on 2008-06-27
I use Xubuntu, with Xfce instead of gnome or kde, and so I can't select properties on the Opera tray icon to change them.

Opera does not show up in autostart either.

So how do I STOP Opera from loading at startup, and how do I also get rid of that tray icon in Xubuntu?

---

### Post by shebuwa on 2008-06-28
Anybody know? :(

---

### Post by Elfy on 2008-06-28
I can't as such help you - but this will bump the thread for a short while. This is the problem with hijacking a thread - especially one which is marked as solved, as it is your issue isn't even the same as the original one :)

It would probably help you if you started a new thread.

---

### Post by shebuwa on 2008-06-28
You're right forestpixie. I should have known better. I will start a new thread.

Please pardon me.

---

### Post by Elfy on 2008-06-28
> **shebuwa said:**
> You're right forestpixie. I should have known better. I will start a new thread.

Please pardon me.

There's certainly no need to apologise , just trying to help you achieve what you need.

I have only looked at xubuntu a few times, so am not even sure where to start looking.

---

### Post by shebuwa on 2008-06-29
You were so very right though, and so I do feel my apology was called for. I really do thank you, most sincerely, for your kind reproof and guidance forestpixie. :)

I took your good advice, and I started a thread on my Opera icon issue. It can be [found right here]("http://ubuntuforums.org/showthread.php?t=843907"). I think it may even be of help to other Xubuphiles out there.

PS

Xubuntu is working out very nicely for me. Great stuff Xubu.

---

### Post by Elfy on 2008-06-29
Glad you're happy - I've posted in that thread, maybe it will help you.

---

### Post by dark_harmonics on 2009-09-01
All,

Sorry if this is reviving an old thread but since a google pulled up this as a result for this issue I wanted to post an alternate solution.

This solution will work no matter how opera is launched:

Modify the /usr/bin/opera file to have the -notrayicon switch with 
```
sudo gedit /usr/bin/opera
```
Scroll to the bottom of the file where it says:

```
exec "$OPERA_BINARYDIR/opera" "$@"
```

and comment that line by adding a # to the beginning

```
#exec "$OPERA_BINARYDIR/opera" "$@"
```

Finally make a new line but with the notrayicon as the argument so that the end of the file looks like this:
```
#exec "$OPERA_BINARYDIR/opera" "$@"
exec "$OPERA_BINARYDIR/opera" "-notrayicon"
```

save and close the file. The bad thing is that this kinda disables other arguments from being used, so you might have to revert back to the original file if you need to run it with other arguments.

---

### Post by Götz on 2009-10-17
It works with other arguments with this:

```
exec "$OPERA_BINARYDIR/opera" -notrayicon "$@"
```

Also, modifying the same file dark_harmonics said, /usr/bin/opera

---

### Post by dark_harmonics on 2009-10-27
> **Götz said:**
> It works with other arguments with this:

```
exec "$OPERA_BINARYDIR/opera" -notrayicon "$@"
```

Also, modifying the same file dark_harmonics said, /usr/bin/opera

Exactly! I just figured that out today and came back here to repost only to find your addition. I had problems launching links because opera wouldn't take command-line arguments without that in the script. So use that code there people to modify the file correctly!

---

### Post by dario7 on 2010-08-26
Sorry for the gravedigging but I've had the same problem today and discovered a better and faster solution:

Open opera and put this in the address bar:
```
opera:config
```

Search "Show tray icon" and deselect it :)

---

