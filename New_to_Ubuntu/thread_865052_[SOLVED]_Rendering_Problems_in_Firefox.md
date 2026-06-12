---
title: "[SOLVED] Rendering Problems in Firefox"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Unstuck on 2008-07-20
I'm not sure if this is the correct forum...forgive me if it is not.

Elements of some...maybe all...webpages bleed together in my main Firefox profile.  I disabled each extension, one at a time, to see if they were causing the bleeding...they are not...nor is the profile I'm using.  I created a new profile and didn't add an extension or theme and pages seem to render correctly.  Any ideas?

Pics of renderings and list of extensions are attached.

---

### Post by Unstuck on 2008-07-20
bump

---

### Post by Unstuck on 2008-07-22
bada-bump

---

### Post by northern lights on 2008-07-22
I don't quite get what you mean by "webpages bleeding together", even after checking the attached screenshots. I suppose a lot of people didn't.

Anyhoo, could you go into a bit more detail of what is wrong with how firefox displays websites?
--> That is what's wrong, right? (pun intended)

---

### Post by redfox1160 on 2008-07-22
I think I know what your talking about. I think that is happening to me too (look at the ubuntu logo on the[IMG]http://img507.imageshack.us/img507/919/screenshotmd8.png[/IMG] screenshot).


Sorry for the image size, I didn't know how to do it the same way you did.

---

### Post by northern lights on 2008-07-22
Nope redfox, that's not it, I think.

Checked the two pics again and noticed the filenames of the .pngs for the first time.

Understood.

Which version of firefox are you running?

Does it happen on all websites, or only on some?
--> try to notice a pattern (only sites with flash content, java scripts, etc).

Is this the only graphical problem whatsoever? Only in firefox?

Have you tried a different browser?

---

### Post by Unstuck on 2008-07-22
Some elements of pages overlap.  If you look at the Properly Rendered pic, it reads "All Times are London Time" under the FT.com logo whereas on the Improperly Rendered pic, the element just below "All Times..." covers have the lettering.  I'll hunt for clearer visual aids.

---

### Post by Unstuck on 2008-07-22
I found more clear examples that should make what I'm talking about obvious.

---

### Post by northern lights on 2008-07-22
I got it. Notice the latter questions -

What firefox?

What browser are the properly rendered screenshots taken from?

etc, see above.

---

### Post by Unstuck on 2008-07-22
> Does it happen on all websites, or only on some?
--> try to notice a pattern (only sites with flash content, java scripts, etc).

Is this the only graphical problem whatsoever? Only in firefox?

Have you tried a different browser? 

Both screenshots are from FF 3.0.  The one that is rendering correctly has no extensions.  I disabled the extensions one at a time from the profile that isn't rendering correctly.  It seems to be the only graphical error.  Konqueror loads the pages correctly.  I'll be on the lookout for a pattern.

---

### Post by medley on 2008-07-22
> **redfox1160 said:**
> I think I know what your talking about. I think that is happening to me too (look at the ubuntu logo on the[IMG]http://img507.imageshack.us/img507/919/screenshotmd8.png[/IMG] screenshot).


Sorry for the image size, I didn't know how to do it the same way you did.

Your problem is not the same as his. To fix yours, Select View/Zoom/Zoom text only.

I had the same problem.

---

### Post by redfox1160 on 2008-07-22
thanks.

---

### Post by Unstuck on 2008-07-29
Are we out of ideas then?

---

### Post by northern lights on 2008-07-30
If with all extension disabled, FF displays all content fine, enable one extension at a time and eliminate the culprit. Uninstall that extension and find an alternative...

---

### Post by Unstuck on 2008-07-30
Problem persists when all extensions are disabled. :(

---

### Post by bmann11 on 2008-08-02
I'm having the same issue with ff 3.0.1, among other issues, and am having no luck coming up with options.

---

### Post by Jack M. on 2008-08-02
This might be caused by the page zoom feature in Firefox, then. See if pressing Ctrl+0 or going to View > Zoom > Reset corrects the problem. If it's not that, then I'm not sure what it could be...

---

### Post by Unstuck on 2008-08-03
> **Jack M. said:**
> This might be caused by the page zoom feature in Firefox, then. See if pressing Ctrl+0 or going to View > Zoom > Reset corrects the problem. If it's not that, then I'm not sure what it could be...

Thanks for the suggestion, unfortunately it did not work.  :(

---

### Post by Methuselah on 2008-08-03
Did you change the default size of the fonts?
I've seen some pages look peculiar with bigger fonts.

---

### Post by Unstuck on 2008-08-04
> **Methuselah said:**
> Did you change the default size of the fonts?
I've seen some pages look peculiar with bigger fonts.

I did...and when I changed the size back to default everything was copasetic.  Thanks, Methuselah!

---

