---
title: "xorg.conf help for mouse scroll button"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-29
Hi Gang

I tried to set up my mouse using xbindkeys, didn't work out so well.

Then I ran across the following info in a search for doing multi-button mice like I used to have.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto?action=show&redirect=IntellimouseMousemanBackForwardButtons]("https://help.ubuntu.com/community/ManyButtonsMouseHowto?action=show&redirect=IntellimouseMousemanBackForwardButtons")

However, I think what I want to do is Simple, but the directions are way over my head.

I just want to make the Mouse Scroll Wheel BUTTON act as BACK in Firefox, it don't need to do anything else other than that.
The keyboard action is Alt+Left Arrow, haven't looked up the code for that yet.  But the examples I've seen don't use hexadecimal codes just plain English, if done right that is, hi hi.........

Can someone tell a senile OLDE man what lines to add to xorg.conf to accomplish this, PLEASE

TTUL
Gary

---

### Post by Kellemora on 2008-10-30
Bump

---

### Post by Kellemora on 2008-10-31
Bump

---

### Post by Sealbhach on 2008-10-31
Hi, sounds like a difficult question for the Beginners Forum.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto#Mapping%20More%20Buttons](https://help.ubuntu.com/community/ManyButtonsMouseHowto#Mapping%20More%20Buttons)


Have you had a look at this page - it may "point" you in the right direction?:)


.

---

### Post by Kellemora on 2008-11-01
Hi Seal

Thanks for responding, that's the page I have in my post, only further down.
I've also checked all the links there at the bottom of the page to.

I'm posting in Beginners, because their directions are over my head!

I HAVE played with some thoughts from there and CAN program each of the buttons for nearly anything EXCEPT going BACK, I can't see how to make the COMBINATION Keystrokes is where I'm failing in doing it.  I can make the button do ALT or I can make it do the Back Arrow, can't figure out how to make it do ALT-Back Arrow.

So, that's actually where I'm stuck at!

I really thought someone would have figured it out.  I've visited something like 20 offices over the past year and MOST of the employees at those places had the mouse scroll wheel button set to BACK and I had all of my windows boxes here set the same way.  It can save at least an hour a day in not making wasted movements!

Thanks for trying though, it's appreciated!

TTUL
Gary

---

### Post by crustache on 2008-11-01
> **Sealbhach said:**
> Hi, sounds like a difficult question for the Beginners Forum.



Yes, and that's a serious problem! Enabling a mouse to work correctly should not be reserved to advanced users. In fact it's one of the most basic functionality in an OS. The present situation is ridiculous.

An easy to use GUI has to come with this new HAL functionality.

---

### Post by Kellemora on 2008-11-02
Hi C

I've picked up and tried nearly every document that part of the Ubuntu files.  None of them even came close to working.  Programs they said to download, did NOT do what the instructions said they would do, such as imwheel.

Went to Mozilla support and MozillaZine both.
Everything refers to the scrollwheel not the scrollwheel button.
Changes to mousewheel in about:config is useless for the button!
They have an entry for middlemouse.paste that can be turned OFF (set to false).

I even posted the question at Mozilla, "can a NEW entry be made called middlemouse.back" along with the details, it has yet to be responded to.

I've tried quite a few things in xorg.conf and can get the mouse to do all kinds of things, as long as it's a single keystroke or an action that is available.

I can make the scroll button do lots of things.  Open a new Tab, Open a new Window, Jump Scroll Bars, Open a new Url, Paste to a page, etc.  
But the ONE SINGLE THING I need it to do, BACK in Firefox, requires adding Alt +left arrow, hold one key while pressing another.  Open new Tab requires that, Open new Window requires that, except, they HAVE those commands embedded somehow.

Oh well, just one more thing to add to my list of normal everyday common things that cannot be done in LINUX!  Or if it can, nobody has figured out how to yet!

I even went to gamers web sites where they get 7 button mice to do nearly everything they need.  But those things are part of the game set-up.

Firefox has Enable Mouse Button Alternatives in some issues of Firefox, but not in the Linux versions.  Wonder Why?

TTUL
Gary

---

### Post by Kellemora on 2008-11-02
Edited to remove another double post.

---

### Post by Kellemora on 2009-01-09
Bump

---

