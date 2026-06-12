---
title: "Porting Gtk3 apps back to Gtk2 ?"
date: 2012-06-10
forum: Programming Talk
---

### Post by troutrou on 2012-06-10
Hi everyone,

Using XFCE/XUbuntu. Now that (some) applications have been ported from GTk2 to Gtk3, theming is broken beause Gtk3 apps are apparently unable to apply Gtk2 themes (and maybe engines too, haven't figured out yet), so I would like to know what does a Gtk2 -> Gtk3 port involve, so I can maybe revert it and bring for example Rhythmbox, Gedit, Abiword etc etc etc... back to Gtk2 where they belonged, and keep using my Gtk2 theme ("hybrid" Gtk themes are few and none of them suit me).


Does the source code of the apps need to be altered, if so in which way ?

I had a quick/superficial look at the source code of one Gtk2 app and one Gtk3 app, and it appears the Gtk stuff looks similar in both cases : the library and function name prefixes are a generic 'gtk' string, it never mentions Gtk2 or 3. So maybe all the Gtk2 calls are still compatible with the Gtk3 lib,  and that all is needed is to link the existing code to the Gtk2 lib instead of the Gtk3 one, and recompile without even touching the source code of the app.

If someone who knows this stuff could either confirm or deny or shed some more light on this subject and educate me, I would be most grateful.


--
Vince

---

### Post by MG&amp;TL on 2012-06-10
With respect, it's a really bad idea. It's a lot of effort to switch from Gtk2 to Gtk3 and while it's superficially similiar, there is a lot of differences and incompatibilities. 

A better idea might be to port the Gtk2 themes to Gtk3, as is happening now. Gtk3 is the future!

---

### Post by troutrou on 2012-06-10
Ok so let's forget about backporting then, I trust you if you say it's more work than meets the eye.

Maybe another solution would be to install the last/most recent Gtk2 version of a given Gtk3 app, hoping it would install without drama onto Ubuntu 12.04.  Worth a try I guess, nothing to lose.

I was only considering this idea because small alterations to the source code and recompiling was about at my reach technically, and would have been a quick way to fix things for a given few apps, whereas developping themes seems so awkward, there doesn't seem to exist any high-level programming "language" to develop themes, or is there ?!

I will have to either wait and pray that my prefered GTk2 theme gets ported sometime soon.. or pay some theme developper to do it for me :-/

I don't know what improvements does Gtk3 bring, but to the humble user that I am, all I see is that it breaks the desktop looks with no immediate solution (Gtk2 compatibily layer).  So I assume that the changes must be "under the hood", directed to developpers not users, and that said changes must be bloody valuable to justify breaking the user experience this tremendously. Any idea/link about what these changes are ?! Just curious...

---

### Post by vasa1 on 2012-06-10
> So I guess my best bet is to find a dark theme I sort of like the shape of the controls of, and modify the colours by hand in the definition files, as I guess it's about the only customization a clue-less user like me can do to a theme, by hand, without any "theme programming" knowledge.

That suggestion [you made]("http://ubuntuforums.org/showpost.php?p=11998406&postcount=7") makes more sense.

---

### Post by troutrou on 2012-06-10
> **vasa1 said:**
> That suggestion [you made]("http://ubuntuforums.org/showpost.php?p=11998406&postcount=7") makes more sense.


Wow, I must say I am impressed ! ;-)

Yes, maybe it would be a starting point to try to modify the colours of this 'Newlooks' Gtk3 theme to mimic the Gtk2 "Gilouche" theme which is close enough. But I am still not sure who 'hybrid' themes work : I replaced the "Gtk2" folder from an existing hybrid theme ("bluebird", supplied with XUbuntu) with my own/Gilouche theme, then applied this hybrid. Doing this made my gtk2 thme apply correctly, however the Gtk3 theme did not apply correctly anymore (but it did BEFORE I replaced its existing Gtk2 theme by Gilouche).  Hoping the above is not too confusing ! ....

So I am still a bit in the vague as to how this hybrid theming is supposed to work exactly in practice, but I guess I should open a new topic for this, as it doesn't fit here.

---

