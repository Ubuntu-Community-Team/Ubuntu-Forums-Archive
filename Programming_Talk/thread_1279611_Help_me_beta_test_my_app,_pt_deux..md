---
title: "Help me beta test my app, pt deux."
date: 2009-10-01
forum: Programming Talk
---

### Post by jeremykross on 2009-10-01
So, earlier today I put the app I've been working on for the last few months on the web.  Initially I was hit with a number of small but unforeseen technical issues.  I've been working diligently since, and I think I've got everything straightened out.  So, here we go again.

Let me expound for a moment on what I've written.  Its a web browser that allows you to see and interact with the other users on a web site.  You're represented by a small avatar overlaid onto the site.  All the other users also have avatars.  When you click about the page, to indicate what you're reading or interested in, your avatar will move there.  In this way, users can arrange themselves spatially and much like in a real world gathering, break off into smaller conversations within a larger context.

A note: you do have to sign up.  I know some people have an aversion to that.  Feel free to type rubbish for now, I don't care.  Just remember the email address and password you enter so that you can sign in.

Anyway, any advice or admonishment, questions or comments are welcome.

Get it here:  [http://www.jeremykross.com]("http://www.jeremykross.com")

---

### Post by staticextasy on 2009-10-01
Haha! Thats pretty cool man!

I used to use a program called Voodoo Chat, its exactly the same concept. Very cool dude! What P.L. is it?

I'm interested in doing something similar to your work only i want to have my program connect to servers on an older program called ThePalace. [http://www.thepalace.com](http://www.thepalace.com) 

Not trying to hijack your thread just relating to your work and I admire it.


*EDIT*

Tested on jaunty 64bit seems to work fine, loads are a little sluggish. 

Avatar support didn't work out to well, it cropped my avatar smaller than it should have been and appeared in the small corner of your avatar box.

Also i think you should setup some forums on your webspace for program support and general talk related to your program.

---

### Post by jeremykross on 2009-10-01
> **staticextasy said:**
> Haha! Thats pretty cool man!

I used to use a program called Voodoo Chat, its exactly the same concept. Very cool dude! What P.L. is it?

I'm interested in doing something similar to your work only i want to have my program connect to servers on an older program called ThePalace. [http://www.thepalace.com](http://www.thepalace.com) 

Not trying to hijack your thread just relating to your work and I admire it.


*EDIT*

Tested on jaunty 64bit seems to work fine, loads are a little sluggish. 

Avatar support didn't work out to well, it cropped my avatar smaller than it should have been and appeared in the small corner of your avatar box.

Also i think you should setup some forums on your webspace for program support and general talk related to your program.

Yes, actually.  I remember ThePalace quite well.  ZDTV, which later became TechTV, which later became G4 used to have graphical chat room based on the aforementioned.  Although I was under the impression that it was defunct, that was part of the inspiration for Trek.

The Client and Server are both written in C++ (of course :-) ) with Qt.  Also, server side, I used a mysql database. 

As for the Avatar cropping, I know its a little funky.  It doesn't do any bounds checking to make sure the selection rectangle is actually contained within the image --which naturally leads to undefined behavior.  Color me remiss.  Its the next thing on my todo list.

---

### Post by staticextasy on 2009-10-02
> **jeremykross said:**
> Yes, actually.  I remember ThePalace quite well.  ZDTV, which later became TechTV, which later became G4 used to have graphical chat room based on the aforementioned.  Although I was under the impression that it was defunct, that was part of the inspiration for Trek.

The Client and Server are both written in C++ (of course :-) ) with Qt.  Also, server side, I used a mysql database. 

As for the Avatar cropping, I know its a little funky.  It doesn't do any bounds checking to make sure the selection rectangle is actually contained within the image --which naturally leads to undefined behavior.  Color me remiss.  Its the next thing on my todo list.

thanks for the info jeremy! it is a well thought out program. glad you are working on it :) i hope my client will be comparable to yours someday for thepalace.

i first used palace back in the 90's. i still use it to this day and others have started developing newer clients for thepalace eg palacechat and phalanx clients.. the problem is they dont really support linux.  you can wine the 32 original client but i want to do a native client

and that is were me learning python comes into play. eventualy i plan to start my own client.

i have tried linpal an old source which was to be the future native linux client. guess the author bunked out. i will eventually try to do my own servers for it and probably branch out to its own instead of being based off the palace.

i will keep track of trek. if you are ever interested in trying palace again i recommend you visit my server called palacequadrant visit the link in my sig.

like you i too have an interest in star trek. i recreated the voyager starship on my palserver using images from elite force. its a work in progress. anyway keep in touch jeremy.

l8r g8r

---

