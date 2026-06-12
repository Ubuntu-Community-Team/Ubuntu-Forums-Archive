---
title: "HOW-TO: Deal with the black screen problem after logging in to KDE 4.+"
date: 2009-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Sysero on 2009-03-02
**[SIZE="4"]Forward[/SIZE]**

Hello all.  I'm new to the forum, but not Linux, so I hope you do not think me presumptuous for posting a HOW-TO so early on in my involvement with the Ubuntu community.  

That being said, this short HOW-TO looks at the black or white screen with mouse pointer problem in KDE 4.+ as it relates to Desktop Effects and is aimed at beginners. 

**[SIZE="4"]The Problem[/SIZE]**

So you're using your shiny new installation of KDE 4.+ and you have been playing around with it, setting up the desktop just right.  You log out.  You go do some things; maybe go get some lunch or have some root canal work done that you've been looking forward to.  When you come back, you boot up.  At the login screen you enter your username and password.  KDE begins to load.  Then suddenly, nothing but a white or a black screen and a mouse cursor greets you. You wait for a minute.  Then two.  Then three.  Then you panic.  No matter how many times you reboot and login the same screen greets you.  What now?

**[SIZE="4"]The Possible Cause[/SIZE]**

You or somebody you know (or don't know for that matter) has enabled Desktop Effects while a hardware, driver or configuration problem exists.

**[SIZE="4"]The Solution[/SIZE]**

Log in.  After KDE 4.+ loads and the black screen appears, in the following order press and hold: 

[COLOR="Navy"]Alt-Shift-F12[/COLOR]

Your screen should return instantly.  However, it may or may not be fixed.  If you leave it this way, upon the next login you could be visited with a blank screen and the mouse pointer again.  Let's check and see if Desktop Effects is still enabled, and if so, disable it.

Click on the "K" button at the bottom left of your screen.  From the menu select:

[COLOR="Navy"]System Settings - Desktop - Desktop Effects[/COLOR]

From here, make sure the box "Enable Desktop Effects" is unchecked.

Now you should be good to go.

**[SIZE="4"]Further Information[/SIZE]**

**Events Mentioned By Other Users In Relation To This Problem**

Other users have reported that when logging in to a different account, that account's KDE 4.+ desktop appears whilst the account in question remains at a black screen.  If such is the case, then one can reasonably assume that the problem is user specific, and therefore the user's settings are afoul.   
 
**[SIZE="4"]Closing Thoughts[/SIZE]**

There are several reason why your screen could go black: This is a solution to one of them.  Try it first and see if it helps.  

Perhaps you may have information to offer to this simple HOW-TO, or maybe you know the many other reasons why such a situation could occur and their solutions.  If you do, please feel free to add on!

---

