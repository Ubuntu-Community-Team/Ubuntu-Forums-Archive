---
title: "Navigating backwards"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Gela on 2012-07-28
The use of ALT+left arrow to go to the previous page on the web works 80% of the time but on occasion it does not do so and the only way to navigate out of the page you are on is to close down access to the web completely and start all over from scratch -  which is a pain to say the least, and it seems to have got worse since upgrading to version 12.04.   Is there any icon or tool which I can't find which just does "previous page" please?

---

### Post by vasa1 on 2012-07-28
Usually, the OS, in this case 12.04, doesn't have much to do with navigating within a browser.

Could you explain your problem in a little more detail?

---

### Post by HeroOfCanton on 2012-07-28
+1 for more details.

If you can't navigate anywhere then something may be locking up your browser. Often this is bad DOM interaction by the site designer. And there's not a darn thing you can do about that...

Is it happening on the same site? Same page? Is your web connection steady? Can you open a new tab or is the entire browser locked? Which browser are you using?

---

### Post by anewguy on 2012-07-28
I don't know if this is your scenario or not, but I have had this happen in the following situation several times:

- you're on a page and either you or a pop-up opens a page in a new window.

- the new page only has the "X" available - no address line, etc., and since it's a new windows you can't go back.  This has always been some sort of ad.

- you close the original window and find yourself "stuck" on this new window with no way to navigate.

I have only had this happen on a few site that have popped something under my current window so when I close my current window the thing is there.

So, you might want to be sure popups (or if there even is such an option - pop-under).

---

### Post by mcduck on 2012-07-29
> **anewguy said:**
> I don't know if this is your scenario or not, but I have had this happen in the following situation several times:

- you're on a page and either you or a pop-up opens a page in a new window.

- the new page only has the "X" available - no address line, etc., and since it's a new windows you can't go back.  This has always been some sort of ad.

- you close the original window and find yourself "stuck" on this new window with no way to navigate.

I have only had this happen on a few site that have popped something under my current window so when I close my current window the thing is there.

So, you might want to be sure popups (or if there even is such an option - pop-under).
If that's the problem , the solution is available in your browser's JavaScript settings.

If you are using Firefox, go to Options, and on the Content-tab next to the checkbox for enabling JavaScript you'll find and "Advanced" button. Click that, and disable the options for "Raise or lower windows" and "Disable or replace context menus".

---

### Post by Gela on 2012-07-29
> **vasa1 said:**
> Usually, the OS, in this case 12.04, doesn't have much to do with navigating within a browser.

Could you explain your problem in a little more detail?
My browser is Firefox but when I go on the web I am taken direct to Google and this forum is bookmarked so that is how I get here. Most occasions  while searching through Google I  investigate something over several pages, I find one which turns out not to be as helpful as I had hoped and wish to return to the previous page and continue on another tack which is when I find I am unable to do so, have to exit the web completely and then start all over.  At this point, I usually find that I cannot repeat the previous "journey" and never get back to where I had been before.

---

### Post by Gela on 2012-07-29
> [QUOTE=anewguy;12135695]I don't know if this is your scenario or not, but I have had this happen in the following situation several times:

- you're on a page and either you or a pop-up opens a page in a new window.

- the new page only has the "X" available - no address line, etc., and since it's a new windows you can't go back.  This has always been some sort of ad.

- you close the original window and find yourself "stuck" on this new window with no way to navigate.

I have only had this happen on a few site that have popped something under my current window so when I close my current window the thing is there.

So, you might want to be sure popups (or if there even is such an option - pop-under).[/QUOTE]

This sounds remarkably familiar - I don't quite understand what you mean in your last paragraph - how can I be sure popups? But thank you all the same

---

### Post by Gela on 2012-07-29
> **mcduck said:**
> If that's the problem , the solution is available in your browser's JavaScript settings.

If you are using Firefox, go to Options, and on the Content-tab next to the checkbox for enabling JavaScript you'll find and "Advanced" button. Click that, and disable the options for "Raise or lower windows" and "Disable or replace context menus".

 Thank you  very much for the advice. I have gone to Firefox but for the life of me I cannot find Options to carry out your suggestion. The only headings I could find were Desktop, Mobile, Releases, Add-ons. Support and About. I looked under all these, and Options did not feature. I think that my hope that there were some magic bullet that would solve the problem does not exist! Thank you all the same.

---

### Post by Gela on 2012-07-29
[QUOTE=HeroOfCanton;12135580]+1 for more details.

If you can't navigate anywhere then something may be locking up your browser. Often this is bad DOM interaction by the site designer. And there's not a darn thing you can do about that...

Is it happening on the same site? Same page? Is your web connection steady? Can you open a new tab or is the entire browser locked? Which browser are you using?[/QUOTE


thank you for your reply. I don't think this is the problem as I can usually navigate and am only unable to do so on infrequent occasions, but thank you all the same.

---

### Post by vasa1 on 2012-07-29
> **Gela said:**
> Thank you  very much for the advice. I have gone to Firefox but for the life of me I cannot find Options to carry out your suggestion. The only headings I could find were Desktop, Mobile, Releases, Add-ons. Support and About. I looked under all these, and Options did not feature. I think that my hope that there were some magic bullet that would solve the problem does not exist! Thank you all the same.

Try Edit, Preferences, Content tab.

(In some systems we have Tools, Options; in others, it's Edit, Preferences.)

---

### Post by vasa1 on 2012-07-29
> **Gela said:**
> My browser is Firefox but when I go on the web I am taken direct to Google and this forum is bookmarked so that is how I get here. Most occasions  while searching through Google I  investigate something over several pages, I find one which turns out not to be as helpful as I had hoped and wish to return to the previous page and continue on another tack which is when I find I am unable to do so, have to exit the web completely and then start all over.  At this point, I usually find that I cannot repeat the previous "journey" and never get back to where I had been before.
If you don't mind my asking, how familiar are you with Firefox? Do you take advantage of tabbed browsing?
Let's say you do a Google search, then I'd suggest you **control+click** on a link in the search result page that interests you so that the resulting page opens in a **new tab**. You can do that for each link in the search result page that you find interesting.

---

### Post by Gela on 2012-07-30
> **mcduck said:**
> If that's the problem , the solution is available in your browser's JavaScript settings.

If you are using Firefox, go to Options, and on the Content-tab next to the checkbox for enabling JavaScript you'll find and "Advanced" button. Click that, and disable the options for "Raise or lower windows" and "Disable or replace context menus".

Ahhh!   At last - I have managed to follow your instructions to the hilt. Thank you very much for your patience.  I am hoping this will do the trick and ALT+left arrow will work on everything again. Cheers - Angela

---

### Post by Gela on 2012-07-30
> **vasa1 said:**
> If you don't mind my asking, how familiar are you with Firefox? Do you take advantage of tabbed browsing?
Let's say you do a Google search, then I'd suggest you **control+click** on a link in the search result page that interests you so that the resulting page opens in a **new tab**. You can do that for each link in the search result page that you find interesting.

Wow! What a wonderful idea!  I shall certainly do that in future as at preent I get completely lost trying to retrace my steps when searching.  To answer your question - I have used Firefox for ages but am completely unaware of what goes on under the bonnet. I shall now consider this problem as solved. So many thanks.  :P Have I registered this as solved just by telling you? :confused: or do I have to make a separate submission - and if so , how??

---

### Post by greenpeace on 2012-07-30
> **vasa1 said:**
> ....then I'd suggest you **control+click** on a link in the search result page that interests you so that the resulting page opens in a **new tab**.

If you have a clickable scroll wheel on your mouse ("middle click"), then that will also open the page in a new tab as well.

---

### Post by critin on 2012-07-30
> am hoping this will do the trick and ALT+left arrow will work on everything again. Cheers - AngelaDon't you have back and forward arrows at the left of the address bar?  If not, go into "View" menu on browser.   click on "Toolbars" and make sure the "Navigation Toolbar" has a check mark next to it.
You wouldn't have to ALT+left arrow anymore.

You can also right click a link and choose  'open in new tab' so you don't lose your page.  You can just close the tab when you're done with that linked page.

Right click anywhere on a page and choose 'Back' will take you to the previous page too.  ALT+left arrow seems awkward to me.

---

### Post by Gela on 2012-08-05
> **greenpeace said:**
> If you have a clickable scroll wheel on your mouse ("middle click"), then that will also open the page in a new tab as well.

Thank you very much - I do have a clickable-scroll mouse and this sounds extremely practical - thank you again. I have tried to put a smiley in to show my appreciation but they just appear in the wrong places. Sorry

---

### Post by Gela on 2012-08-05
> **critin said:**
> Don't you have back and forward arrows at the left of the address bar?  If not, go into "View" menu on browser.   click on "Toolbars" and make sure the "Navigation Toolbar" has a check mark next to it.
You wouldn't have to ALT+left arrow anymore.

You can also right click a link and choose  'open in new tab' so you don't lose your page.  You can just close the tab when you're done with that linked page.

Right click anywhere on a page and choose 'Back' will take you to the previous page too.  ALT+left arrow seems awkward to me.

I checked on "Navigation Toobar" and it was unchecked so I checked it. Thank you for the advice. Thank you also for the right-click information. I am learning all the time and am so grateful for the Absolute Beginners Forum - I am an absolutely absolute beginner!  thank you again.

---

