---
title: "Rewrites are a drag"
date: 2008-07-12
forum: Recurring Discussions
---

### Post by kko1 on 2008-07-12
Just about when an application gets in a near-working polished state, they abandon it in favor of a rewrite, and stop trying to fix bugs in the old version. :p

I'm mostly talking about *Amarok*, although the same applies to *KDE 4*, since I like and prefer *KDE 3.5.9*. (I haven't really given *KDE 4* a proper try yet, although I do have it installed, so I won't go bashing it yet. ;) )

Having recently upgraded from Kubuntu Dapper to Hardy, it's frustrating that *Amarok 1.4.9.1* is so close yet so far. In Dapper *Amarok* was working fine for me (after fixing the *flac* issue), in Hardy it keeps regularly crashing on shutdown/startup with the play mode (a dynamic playlist) I've chosen, and leaving behind a stripped backtrace to dispose of.

At the same time, *Amarok* development efforts apparently go towards version 2. Ah, the dilemmas of *progress*.

I suppose I'll do without the dynamic playlist, or configure my *mpd / pygmy* combo properly.

*

(Other frustrations after the Dapper -> Hardy upgrade:
- Matrox *mga* driver in the newest xorg will not display 1600x1200 anymore. (Bug #112238.) (I also had a surprising "X11 error: BadAlloc (insufficient resources for operation)" playing a movie, but the error disappeared after logging in again, most probably to reappear when least expected. ;) )

- *Firefox* will no longer do a Google "I'm feeling lucky" search for text written in the address bar, and I can't remember how to activate this feature. (Neither will it open PDFs in a tab.)

- For *T-bird* I had to update the new mail icon extension, I'm glad that at least has been kept up to date. :)

That said, I'm kind of impressed that the actual process of upgrading from one LTS release to another went by quite painlessly, even if it did leave a couple issues behind to deal with.)

*

Just venting, this is not a "Ubuntu sux, I'm leaving unless you help me" -post. :p

kko1

---

### Post by Polygon on 2008-07-12
i could of swore that if you typed something into the address bar it does a google 'im feeling lucky' search, because it usually brings up a page thats semi relevant to what you typed in, and how else would it know what you were looking for without a google search?

---

### Post by kko1 on 2008-07-12
> **Polygon said:**
> i could of swore that if you typed something into the address bar it does a google 'im feeling lucky' search, because it usually brings up a page thats semi relevant to what you typed in, and how else would it know what you were looking for without a google search?

Ha! It used to, but doesn't do it for me anymore in *Firefox 3*. Could be something to do with the new security emphasis in the newest *Firefox*, for all I know. I miss it already, since I used to (ab)use that feature to find random interesting things. ;)

---

### Post by Polygon on 2008-07-12
i think your wrong

i typed compaq into teh firefox 3 address, bar, took me to the compaq home page

i then went into google, typed "compaq' and clicked "im feeling lucky" and it took me to the same page. same thing with the search queries "ubuntu wiki" and some random other ones

although i do notice with more obscure search queries, like searching "polygon89", in firefox it takes me to the google search page with polygon89 already entered....so in a way i think firefox's method is better =P

---

### Post by kko1 on 2008-07-12
That's what I'm trying to tell you. **My** Firefox won't do that anymore, and I don't remember the option to make it so (and am too tired now to search for it) and it makes me :( .

Instead, whatever I write, it tries to complete it by adding a *www* to the front and a *com* to the back. So for *compaw* I get *[www.compaw.com](www.compaw.com)* (it's an actual typoed address), and for *polygon89* I get "Server at *[www.polygon89.com](www.polygon89.com)* not found."

---

### Post by Superkoop on 2008-07-12
Whenever I type something in the address bar in FF3, it takes me here: [http://blastsearch.net/](http://blastsearch.net/)
No matter the word, that's where it takes me.

---

### Post by kko1 on 2008-07-13
A new day, new thoughts.

The *Firefox* drag was easy, just one search and I found the option needed.

For your convenience, I'll reproduce it here, credits to Kryve @ [www.gamingforce.org](www.gamingforce.org).
[QUOTE=Kryve]Here's a way to restore Google's "I'm feeling Lucky" as the default search option:

1. Open a new tab in Firefox.
2. In the address bar, type "about:config" (without the quotes) then press Enter.
3. In the *Filter* field, type "keyword".
4. Locate the option *keyword.enabled* and set its value to "true" by double-clicking on it.
4. Locate the option *keyword.URL* and double-click on it.
5. In the input box, replace the old value by this new URL:
[http://www.google.com/search?hl=en&b...eling+Lucky&q=](http://www.google.com/search?hl=en&b...eling+Lucky&q=)
6.Press Enter to finish.[/QUOTE]

*Amarok*, meanwhile, still keeps crashing on just about every login, or at least one out of two. And I'm stuck with 1280x1024. :-k

---

### Post by barbedsaber on 2008-07-13
cough banshee cough, but wait, thats not ready yet, I don't think. just swap media applications for a while, you never no, you might like the new one.

---

### Post by kko1 on 2008-07-13
> **barbedsaber said:**
> just swap media applications for a while, you never no, you might like the new one.

Indeed, good to try something else every once in a while.

(Methinks you should have something for the cough, mate. ;) )

---

### Post by barbedsaber on 2008-07-13
> **kko1 said:**
> 

(Methinks you should have something for the cough, mate. ;) )

:) nothing that bit of bacon and eggs cant fix. (not that they have anything to do with cough helping ness. nothing wrong with an excuse fo bacon and eggs.)

---

### Post by kko1 on 2008-07-13
Woo, *mpd* + *pygmy* + *mpc* rock. :-)

(Of course, *pygmy* and *mpc* are not both needed, but they can be used interchangeably.)

Except that *mpd* doesn't see all of my music... :-k

(It does now. File permissions, eh... EDIT: A couple files remained unseen to *mpd* still - noticed by comparing the number of files seen by *Amarok* and by *mpd*. The cause: the filenames contained peculiar characters and were apparently named using another encoding. Renaming them (or, in the case of some, first renaming them to something else and then back, with the new encoding) with *easytag*, recreating the *mpd* database and restarting *mpd* solved this.)

EDIT: Another plus for *mpd*. It plays gapless *flac*, whereas *Amarok* doesn't.

---

