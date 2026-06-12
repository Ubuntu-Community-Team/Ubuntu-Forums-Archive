---
title: "Removing titles from launchers"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by El Lance-O on 2008-05-03
I made a thread about this awhile ago, but received no answer, so here we go again.

After the update to hardy, I noticed that my launchers on my desktop which previously had no titles at all (when I clicked on them, there was no text box under the icon or text whatsoever) now had .desktop at the end of them, and I cannot change it back to how it originally was.

If this does not make sense, I can try and slap some screenshots together to show what I am talking about.

But basically I just want icons on my desktop, no text. Just icons.

---

### Post by SunnyRabbiera on 2008-05-03
you may have to re add your desktop shortcuts, I am more then sure this has something to do with your update and something might have got lost in transition.

---

### Post by sayakb on 2008-05-03
Try a dock or something that would give you just icons
```
sudo apt-get install avant-window-navigator
```

---

### Post by El Lance-O on 2008-05-03
Sorry, no interest in avant. If I were to have a dock, I would use kiba, but there are too many problems with Hardy to give that a go now.

I tried remaking the shortcuts and it still doesn't work. Before I could just make the title a space (" ") and it wouldn't show up as any characters at all. Now the space shows up, having an ugly little box pop up under the icon when I click it.

I really hope this can be solved, I loved the way my desktop looked, and it was PERFECT. 

Really, it was.

---

### Post by SunnyRabbiera on 2008-05-03
It might be something in tis version of gnome then, and with that I have no clue.
There were a lot of changes made to some stuff for the current gnome and who knows the full extent to what was edited...

---

### Post by El Lance-O on 2008-05-03
It makes me wonder if it is something that happened during the upgrade and it's just me?

Test it out.

Create a launcher and name it " " without the "'s and see what happens.

If you get the same, should this be considered a bug and registered on launchpad?

---

### Post by SunnyRabbiera on 2008-05-03
Yeh I am unsure about this, it looks like there is no way not to have a name under the icon.
but report it to the gnome development team instead of launchpad, this is more their territory.

---

### Post by El Lance-O on 2008-05-03
I see a lot of bugs involving launchers on the gnome dev bugzilla, but I don't see anything exactly like this.

Am I the only one that has a desktop like this or what?

---

### Post by SunnyRabbiera on 2008-05-03
> **El Lance-O said:**
> I see a lot of bugs involving launchers on the gnome dev bugzilla, but I don't see anything exactly like this.

Am I the only one that has a desktop like this or what?

I dont know, but make a report nonetheless.

---

### Post by El Lance-O on 2008-05-03
Done.

[http://bugzilla.gnome.org/show_bug.cgi?id=531237]("http://bugzilla.gnome.org/show_bug.cgi?id=531237")

---

### Post by mc4man on 2008-05-03
not sure if this is what you mean but if you right click on the icons ->properties you can change the name, you need to enter something though < . > works and is barely visible. not sure if this is what you mean

---

### Post by El Lance-O on 2008-05-03
No this is exactly what I mean, and "." doesn't work for me because that little text area is still highlighted when I click on the icon, when before it would just highlight the icon, which was perfect.

---

### Post by mc4man on 2008-05-03
The best I see atm is to make an entry in name that doesn't appear at all, doesn't resolve the 'lollipop' handle though. Use a unicode control character instead of anything from keyboard - at least the desktop is clean

---

### Post by El Lance-O on 2008-05-03
Hahahaha....lollipop handle, perfect way to describe it.

I've tried some blank unicode characters, and some work and some don't. It really doesn't like spaces anymore.

I noticed another bug with gnome where when a launcher was named just a space (" ") it created XML junk in the title for some reason.

[http://bugzilla.gnome.org/show_bug.cgi?id=365174](http://bugzilla.gnome.org/show_bug.cgi?id=365174)

I also noticed this was from 2006, and still unconfirmed. Makes me kind of lose confidence that anything will come out of even reporting it. :(

---

