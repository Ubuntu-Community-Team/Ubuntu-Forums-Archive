---
title: "Global Menu Bar integration 1.06 - Bookmark problem"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Hakunka-Matata on 2011-08-05
I realize this is a 11.10 specific forum, but I do not find many posts about "Global Menu Bar extension" in other forums, so I've posted here.  I've just posted the following message in Launchpad.
While using Firefox 5, with "Global Menu Bar integration 1.0.6" Add-On Extension enabled, and I click on Bookmarks, then type a letter, the cursor does not move, normally it would JUMP to the first entry having the letter I typed.


Anyone else experiencing this same ***problem***?  Or maybe it's not a problem, if so, I'll just disable the Add-on



11.04 (natty)
2.6.38-10-generic
GNOME 2.32.1
Firefox 5 - 1.0  Add on Extension "Global Menu Bar integration 1.0.6" enabled
 Problem, when I click on Bookmarks, and then type a letter, say "M",  the cursor does not JUMP to the first entry that starts with M, the  cursor does nothing.  If the "Global Menu Bar extension" is disabled,  Bookmarks tab responds to a letter typed on the keyboard as I am used to  seeing.
 Is this extension intended to operate this way?

---

### Post by Hakunka-Matata on 2011-08-05
I got an answer from Launchpad:

Your question #167088 on Global menubar extension changed: [https://answers.launchpad.net/globalmenu-extension/+question/167088](https://answers.launchpad.net/globalmenu-extension/+question/167088)      Status: Open => Answered  Chris Coulson proposed the following answer: This needs to be implemented in whatever renders the menu - in your case, this is most probably Unity. However, I think this is actually a limitation of GTK anyway, so the functionality would need to be added to GTK first

---

