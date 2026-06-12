---
title: "Global menu, right click support"
date: 2011-05-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-05-05
Something that really bugs me is that there is no right click support in the global menu.

If i want to remove a bookmark i have to now load up the bookmark manager rather than simply right clicking and deleting.

Anyone else bugged by that?

---

### Post by RJ12 on 2011-05-05
Yeah, I'm hoping it's fixed soon, it annoys the everything out of me too!

---

### Post by terry_gardener on 2011-05-05
yes it is annoying and hope it is fixed for 11.10

---

### Post by tubunu on 2011-05-05
+1

---

### Post by chrisccoulson on 2011-05-05
-1, adding context menus inside menus isn't going to happen. We'll add support for modifier keys so you can use ctrl/shift to open bookmarks in firefox in a new tab or new window. The menu is not a bookmarks editor though (it's just a menu), so the context menu won't be coming back

---

### Post by ELD on 2011-05-06
> **chrisccoulson said:**
> -1, adding context menus inside menus isn't going to happen. We'll add support for modifier keys so you can use ctrl/shift to open bookmarks in firefox in a new tab or new window. The menu is not a bookmarks editor though (it's just a menu), so the context menu won't be coming back

I seriously don't understand that at all, i don't see why giving users an easy choice of something they had before won't be considered?

---

### Post by chrisccoulson on 2011-05-06
> **ELD said:**
> I seriously don't understand that at all, i don't see why giving users an easy choice of something they had before won't be considered?

Because we want menus to behave consistently between applications, rather than containing surprises. Previously, right-clicking a menu item in the Firefox menu opened a context menu, whereas in every other application it performed the action pointed to by the cursor. A user has no way of predicting what is going to happen before they click their mouse button. In addition to that, right-clicking in the Firefox menu would open a context menu relevant for the selected menuitem in some cases, and the toolbar context menu in other cases. We don't want those sorts of inconsistencies...

---

### Post by ELD on 2011-05-06
Hmm while it does make sense when you explain it like that, it's still an inconvenience i guess i will just have to get used to.

Will there be any plans to lets us re-organise stuff, like currently you can grab a bookmark and move it around, i take it that won't be implemented either?

---

### Post by beew on 2011-05-06
Consistency is for the small minded (Dickenson?) That explains the approach of pulling everything down to its lowest  common denominator,--consistent mediocrity. Guess we will have to wait for third party hacks.

---

### Post by ELD on 2011-05-06
> **beew said:**
> Consistency is for the small minded (Dickenson?) Guess we will have to wait for third party hacks.

Heh i have to agree to a certain point. Easy of use should always be above consistency where it makes sense, in this case i feel it makes sense which is why i'm not happy it has been removed.

---

### Post by beew on 2011-05-06
Yeah I am not even sure what is the point of soliciting feedbacks (maybe they didn't) while they 'consistently' shoot down most suggestions based on ideology.

---

### Post by ELD on 2011-05-06
They go on their "experts" rather than their users which is causing me to seriously look at other distros :(

---

### Post by seeker5528 on 2011-05-06
> **ELD said:**
> If i want to remove a bookmark i have to now load up the bookmark manager rather than simply right clicking and deleting.

Anyone else bugged by that?

Don't know about other browsers but in Firefox 'View --> Sidebar --> Bookmarks' and it's keyboard shortcut 'Ctrl'+'B' still work, so no I'm not bugged about not being able to right click a bookmark on the bookmark menu. 

Right clicking an item in the Firefox bookmarks menu to delete it is something I have been used to using, but having a context menu for a menu item doesn't seem that typical, or maybe it just doesn't typically occur to me to look, if there is a need for right click to work in an application's menu other than just being a minor convenience that seems like poor design to me.

Later, Seeker

---

### Post by arpanaut on 2011-05-06
Exactly why I disable the Global Menu Bar Extension in Firefox.

Otherwise the global menus are working okay for me, 
I guess I have some "bad" habits as far as browsing goes.  :biggrin:

---

### Post by Rustybolts on 2011-05-24
I have also disabled the Global Menu bar extension. Seriously you need to re-look at this, otherwise people will end up with a very long list of bookmarked sites and no _easy_ way to sort them. When using a mouse on a computer left mouse button is always to select a file or window (a object) , right click is used to manipulate said object in some way (copy, rename, move etc) whats inconsistent about that? Why go against the grain? Why alienate the hardcore (more technical) users? Nintendo did this with the Wii, and they found out its the hardcore audience that stick around the casual user is not there for the long haul. How many novice users are going to install another OS?....Not many.
Linux Mint is looking more and more tempting whereas Ubuntu is now looking less attractive to me.

---

### Post by Mr. Picklesworth on 2011-05-25
I think the ideal solution here is to recognize that masses of bookmarks (as people tend to have) don't really belong in a menu (a menu is best thought of as a static index of functions), and once we reach the point where regularly sorting / deleting bookmarks is *a thing people do* it's time to look at other ways for presenting them. Ways with more dimensions.
If we want a menu item to do something more than a menu item is meant to do, it isn't a menu item and it shouldn't be in a menu. (And yes, I'm looking at you, [IDO]("https://launchpad.net/ido") / indicator-*).

It should be mentioned that Gtk+ doesn't actually support context menus inside menu items, and I'm pretty sure Qt doesn't, either. The context menu in the Gnome Main Menu applet, for example, was a hack and (if I recall correctly) it doesn't work in GTK3. There is no way to pipe such a hack mechanically over dbusmenu without exposing a lot of other stuff that shouldn't be exposed.

And if that makes me an elitist ideologue, I'm proud of it.

---

### Post by ELD on 2011-05-26
Since when is a menu best thought of as a static list? Any kind of menu i know of should always incorporate change. A menu is a list of items, end of. Not a static list of items - why do we have to think like that?

You said it yourself "once we reach the point where regularly sorting / deleting bookmarks is *a thing people do* it's time to look at other ways for presenting them" people have been doing it this way since i have been using browsers, people are used to it, want it and expect to be able to do this.

Yes it does make you seem like an elitist ideologue since you aren't compromising at all for what users actually *want.*

---

### Post by Mr. Picklesworth on 2011-05-26
> **ELD said:**
> Since when is a menu best thought of as a static list? Any kind of menu i know of should always incorporate change. A menu is a list of items, end of. Not a static list of items - why do we have to think like that?

You said it yourself "once we reach the point where regularly sorting / deleting bookmarks is *a thing people do* it's time to look at other ways for presenting them" people have been doing it this way since i have been using browsers, people are used to it, want it and expect to be able to do this.

Yes it does make you seem like an elitist ideologue since you aren't compromising at all for what users actually *want.*

I'll try to make my theory more clear…

At risk of sounding like a caricature, I don't think it is what people want. Really! I think users want an easy to reach button that, when clicked, provides immediate access to all of one's favourite bookmarks with all the other bookmarks somewhere nearby. The bookmarks menu does this reasonably well because you can open the menu and open a bookmark in a click, but the more complex bookmarks library is nearby, presented just in case the bookmarks menu doesn't do the job. There is a silly competition between these two, where they both provide approximately the same feature in differently broken ways. One is better at handling lots of bookmarks (with searching and the ability to browse through folders without filling the entire screen in a precarious mess of arrows and rectangles) while the other lets you open a single bookmark with minimal mouse movement. IE9, for what it's worth, attempted to amalgamate the two. It is possible.

As for the menu, I think what is being proposed here springs from grouping stuff by implementation instead of by function. I should have been clearer when I said “menu”; I meant window menus, more specifically. GTK+ and Qt both encourage developers to build window menus using high level Action classes, which represent functions in an application and are also used to build toolbars. They encourage developers to use high level classes to create application windows which automatically manage menus and toolbars. Of course, any developer worth his salt knows it's a really bad idea to rely on a high level interface being implemented a particular way, so…

This isn't just the API being funny: it's about semantics. These menus are fit for a particular purpose. The global menu, and this particular problem, only makes it clearer why developers should try to respect those semantics. We can do interesting things when we know what particular objects aim to achieve. A sane operating system needs that kind of integrity.

Okay, and with regards to the purpose of a menu in general, I poked at the GNOME and MacOS HIG and various others and I agree: nothing really explicitly says it either way and I was clearly imagining the “static” part. One thing is the same everywhere, though: menus are strictly text with icons arranged in rows that you can click on (and they will probably stay that way because it makes them inherently accessible), and menus are typically designed to favour consistency and help muscle memory. It's odd to expect a complex user interface like bookmarks management to survive on that kind of framework.
Strangely, 30 or so years of WIMP interfaces and we still don't really know what menus are for :)

---

### Post by ELD on 2011-05-26
I know you probably mean well but that all comes off as - well rubbish.

At the end of the day Rustybolts said it best, you're going against the grain. The global menu in my eyes serves no purpose but to look a bit more err mac like - i used to think of Ubuntu as the one stop shop for Linux but not anymore. I'm not even sure i wish to use Linux anymore due to the changing landscape of my other options - Unity (the lack of customization is horrific), Gnome 3 (some people like me do like to minimize stuff you know - again who the hell did they test that on!?), global menu (ergh!!).

Global Menu makes accessibility a nightmare if you have multiple windows open *not *maximised. You have to manually click each one, then move again up to the menu - awful. It really does make me wander who exactly you test these features on.

As long as it's an addon we can keep disabling it in firefox to have our "normal" and *wanted *behavior back. If i even stick around on Linux anymore that is.

Really is sad since i have run a dedicated Linux gaming website for quite some time now, that i may be forced to give it up because of my severe distaste for what Linux is turning into.

---

### Post by seeker5528 on 2011-05-26
> **Rustybolts said:**
> I have also disabled the Global Menu bar extension. Seriously you need to re-look at this, otherwise people will end up with a very long list of bookmarked sites and no _easy_ way to sort them.

'View --> Sidebar --> Bookmarks' or 'Bookmarks --> Show all bookmarks', then right click 'Bookmarks Toolbar', 'Bookmarks Menu', or 'Unsorted Bookmarks' and choose sort by name, both seem pretty easy to me.

Later, Seeker

---

