---
title: "I dont understand the new GUI"
date: 2013-12-31
forum: Recurring Discussions
---

### Post by Alienspecimen on 2013-12-31
I recently got a new laptop  and graduated from 10.04 to 12.04. So far, not so good...
 

 In 10.04 I had menus such as: “Applications” and “Places” on the bar at the top and also was able to           choose different themes from including window shapes and fonts.  
 

 When I start 12.04, I am faced with the same bar, but the menus are no longer there and there is no way to start an application unless it is in the launcher to the left and I do know there are tons more applications, because I can see their list in the “Software Center”. Also the “Themes” menu in the “Systems Settings” is very limited.
 

 I  did some search and thought that downloading and running the “The GNOME Desktop Environment, with extra components might be my solution, but unfortunately, upon restart I was faced once again, with the same launch bar on the left.
 

 Can you help me with my request to make my 12.04 look more like and be as flexible as the 10.04?
 

 Thank you in advance.

---

### Post by carl4926 on 2013-12-31
In 12.04 you can install unity-2d

Other than that the ubuntu relative Mint with Mate desktop is next best or Xubuntu

---

### Post by Frogs Hair on 2013-12-31
Mate is a fork of the Gnome 2 desktop in 10.04 which Gnome ended support for . See the Ubuntu manual link in my signature if you want to learn more about Unity. See the following link for gnome session fallback customization .    [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by 3rdalbum on 2013-12-31
Ubuntu is a fast-paced distro, things change. It is progress. In the opinions of most people who have learnt the new desktop, it is a vast improvement over Gnome 2.

You can access your applications by clicking the Ubuntu button and then clicking the second icon along the bottom. Or right-click the Ubuntu button and choose Applications. You can filter results by category (including if you do a search).

Greater theme support is available if you install Gnome Tweak Tool.

---

### Post by Odyssey1942 on 2013-12-31
Like you, I find Unity very unhelpful. I have replaced Unity with Gnome and now my desktop looks just like it did in 10.04. Here is the code:

sudo apt-get install gnome-session-fallback

After installing, reboot and before you put in your password, click on the little icon just above and to the right of the password box. Choose "'Gnome Desktop (no effects)" (or similar words). Then login.

Voila. You are back home.

Let us know how this worked for you if you try it.

---

### Post by whitesmith on 2013-12-31
I made the switch from 9.10 to 12.04 and was unhappily surprised by appearance of the childish (and childlike) Unity. I could cite examples, but that would only pile more bromides on an overheated subject. This does a far better job:
-    I do not like thee, Doctor Fell,
-    The reason why - I cannot tell;
-    But this I know, and know full well,
-    I do not like thee, Doctor Fell
I immediately used a procedure like the one cited by #Odyssey1942 and have enjoyed my Gnome DT every second of every minute of every hour of every day. Here's hoping the OP does, too.

[EDIT] In response to subsequent posts, I happily concede that Unity is Mac-like by design. Now have a look at the webpage in my sig line and see what the author has to say about features in one product that are designed to make it appear like something in another.

---

### Post by craig10x on 2013-12-31
The Unity launcher (as it is called) is really just a dock...have you ever seen or played with a mac in a store that sells those? Well, Unity works the same way (except it's on the left instead of the bottom)...the idea is to "pin" your favorite apps and most used ones to the dock for quick (1 click) access...simple and easy!  And the "dash" search on the top button is to look for programs and files....you can use that to bring up apps you don't use often and don't add to the dock...isn't that easy?

You should work with it for about a week or two to see if you get to like it...then, if not, do one of the other options that was mentioned...

Gnome went to the the Gnome Shell since they discontinued gnome 2 that you were using on your old 10.04...i think Ubuntu's version of it is much sleeker and nicer to use....you should give it  a try....
why be stuck in the past?  The problem is some just can't stand to see anything change...but sometimes change can actually be for the better...providing you give it a chance and keep an OPEN MIND about it...

---

### Post by Dave_L on 2013-12-31
I kept an open mind and used Unity for nine months. I finally got fed up with it and am now experimenting with xfce, which I like much better.

Sometimes change is good, sometimes it isn't. Seeing that requires an open mind too. :)

Here's a nice list of alternatives to Unity: [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

---

### Post by craig10x on 2013-12-31
@Dave_L: I think it really mostly comes down to whether one likes working with a "dock-centric" (icon based) desktop or a text based (the older style) menus...and if one doesn't like docks he is probably not going to like unity...Having worked with both windows and mac...I like both ways, so that's why i am fine with it, personally :)

---

### Post by buzzingrobot on 2014-01-01
Personal preference is personal preference. There's really no objective way to grade one interface against another.

I'd recommend the OP at least make a bit of an effort to use Unity as it is intended to be used, rather than try to shoehorn it into another model. Better to know what it is you like or don't like, and why, than just walk away because it is different.

In the end, adding icons to the Launcher in Unity is directly analogous to adding icons to a panel.  Unity does not need to put a window list applet in a panel because clicking on an running app's icon in the window switches to it.

Mate is the obvious choice for anyone who prefers the straight Gnome 2 interface. (Gnome fallback is somewhat different.) It's fine and stable. Ubuntu users should install it per the instructions at mate-desktop.org. 

When the OP installed gnome-shell and did not see it on a reboot, he probably did not realize he needed to set it as the default DE when he logs in.  If he's opted for automatic login, he won't be able to do that on a reboot. He needs to logout, and select Mate instead of Unity when LightDM prompts for log in.

---

### Post by The Spectre on 2014-01-01
I also would definitely recommend giving Unity a chance.
 
Don't dismiss it just because it is different and try it out for a couple of weeks.

When I first switched from Windows to Linux I went with another Distro that had the KDE Desktop because I could not stand the Unity interface.

Probably because it was so different from the Windows interface that I was so accustomed to.

I had installed Ubuntu into VirtualBox just to mess around with it from time to time and I found myself liking the Unity interface the more that I used it.

After about a month I decided to switch to Ubuntu and I could not be happier.

Not only have I come to really like the Unity interface but I also love the fact that it is different.

I have ended up liking the Unity interface so much that I have moved the Windows task bar to the left on my computer at work to mimic the Unity interface and keep the workflow the same... 

[ATTACH=CONFIG]249076[/ATTACH]

Some people do not like change and that is fine because that is one of the great things about Linux if you don't like the Desktop Environment that it comes with just install one that you do like or go with another *buntu that has the Desktop Environment that you do like.

---

### Post by Irihapeti on 2014-01-01
This thread is no longer a support request, but has turned into a discussion on preferred desktop environments, which has been discussed many times over.

Therefore, *thread moved to **Recurring Discussions**.*

---

### Post by bmcgonag on 2014-01-01
I agree with ohters.  Unity is different, but given a chance it is rather fast.  I highly suggest some Youtube tutorials on it's use.  It can help turn you into a power user quickly.  If you still hate it, that's fine.  Just install Cinnamon, Gnome, KDE, XFCE, or any other desktop environment you like.  Install a few and try  them out.  That's the great thing about Linux.  You make it what you want it to be, so it's the best for you.

---

