---
title: "What Language(s)?"
date: 2012-03-18
forum: Programming Talk
---

### Post by Cerastes on 2012-03-18
Hello,

I am a bit of a newbie to both Linux and programming.

I would like to accomplish the following goals:

1. Build a Linux based web-server.

2. Develop a website that allows users to create accounts where they will be able to create files and share those files with other users.

3. Develop applications for Android and iOS that will share data in both directions with the website.

I have begun learning C++.  I'm not sure if it is the best choice for my objectives.  I would appreciate any advice the community may have for me about the best way to start toward my objectives.

Thanks in advance!

---

### Post by schauerlich on 2012-03-18
> **Cerastes said:**
> I would like to accomplish the following goals:

1. Build a Linux based web-server.


Do you mean *write* web server software, or maintain a web server that uses linux based software? Either way, use [Apache](http://httpd.apache.org/) or something, don't write it yourself.

> 
2. Develop a website that allows users to create accounts where they will be able to create files and share those files with other users.


Sounds like you're asking for a lawsuit for copyright infringement.

> 
3. Develop applications for Android and iOS that will share data in both directions with the website.

I have begun learning C++.  I'm not sure if it is the best choice for my objectives.  I would appreciate any advice the community may have for me about the best way to start toward my objectives.


Android uses Java and iOS uses Objective-C. You also can't (realistically) develop for iOS on Linux. You need to use Apple's IDE, Xcode, which requires running OS X, which in turn requires owning a Mac (OSx86 notwithstanding). You also need to pay a $99/year fee to test code on real devices and submit apps to the app store. If you're looking for an open/Linux based solution, you'd better go with Android. They have pretty good Eclipse integration, so if you're already using that it shouldn't be too hard of a transition.

---

### Post by Cerastes on 2012-03-18
> **schauerlich said:**
> Do you mean *write* web server software, or maintain a web server that uses linux based software? Either way, use [Apache]("http://httpd.apache.org/") or something, don't write it yourself.



Sounds like you're asking for a lawsuit for copyright infringement.



Android uses Java and iOS uses Objective-C. You also can't (realistically) develop for iOS on Linux. You need to use Apple's IDE, Xcode, which requires running OS X, which in turn requires owning a Mac (OSx86 notwithstanding). You also need to pay a $99/year fee to test code on real devices and submit apps to the app store. If you're looking for an open/Linux based solution, you'd better go with Android. They have pretty good Eclipse integration, so if you're already using that it shouldn't be too hard of a transition.


Schauerlich, thanks for your response.

1. I did mean maintain a web server that uses linux based software.  As I understand it, there is an Ubuntu server edition.  Is that the best choice for a linux based operating system for a server or should I be considering something else?

2. :)  I guess that based on my very general description, it certainly could sound that way.  But I am confident that my idea would not be breaching any copyrights.  My idea is to create something like google documents but for a very specialized purpose.  The users would input data in forms available on the site which then would be shared with other users (so, it wouldn't be a "file-sharing site" like those that get in so much legal trouble).  

3. Again, Thanks!  That is exactly the kind of information I need.  As a follow up to your answer: If I program an app for android and it looks like my idea has legs (i.e. can make enough money to justify an investment in a Mac and the other expenses), how much carry over would there be between the programming work I have done on an android app and an iOS app?  Or would I be starting from scratch?

Thanks again!

---

### Post by schauerlich on 2012-03-18
> **Cerastes said:**
> how much carry over would there be between the programming work I have done on an android app and an iOS app?  Or would I be starting from scratch?

Having never ported between Android and iOS, I can't say for sure, but my suspicion is very little. Certainly the GUI of the app would have to be completely rewritten, as Android and iOS are incompatible in that regard. You might be able to port some of the back end logic by wrapping your model in a java/objc library and including it in the project - but again, having never done this myself, I'm not sure of the viability of such an endeavor.

---

### Post by ibrahimtawbe on 2012-03-18
> **Cerastes said:**
> Hello,

I am a bit of a newbie to both Linux and programming.

2. Develop a website that allows users to create accounts where they will be able to create files and share those files with other users.

3. Develop applications for Android and iOS that will share data in both directions with the website.
!
 
develop web applications they can easily be ported 
use new HTML5 APIs , PHP , JavaScript

---

### Post by Some Penguin on 2012-03-18
> **ibrahimtawbe said:**
> develop web applications they can easily be ported 
use new HTML5 APIs , PHP , JavaScript

This.  The simplest way to ensure that multiple disjoint platforms will be able to access your own system is to write the user interface as HTML + JavaScript + whatever server-side languages you care to use.  This means that while you still need to care about browser compatibility issues, you don't need to rewrite everything from the ground up.  It won't be as beautiful as a dedicated app can be, but...

All logic should be on the server as much as possible.  Java is pretty convenient for the back-end systems since there's a large number of existing libraries which can significantly simplify your life - e.g. Jetty for an embedded web server, Jersey for web resources, Jackson for JSON serialization and deserialization, all the concurrency primitives to make multithreaded systems much easier to implement, and so forth.

---

### Post by Jacks0n on 2012-03-19
> I am a bit of a newbie to both Linux and programming.

Welcome to the world of Linux and programming :).


> 1. Build a Linux based web-server.
You can do this two ways. Make a server that does all of the work (create sockets, handle each query, headers, etc). Or build it on top of a framework. For example Python has a built in web server. Basically any language will let you create a web server. My recommendation's Python if you want a language to get started with.


> 2. Develop a website that allows users to create accounts where they will be able to create files and share those files with other users.
If you're doing this to learn, then great. Maybe look into basic HTML/PHP, or built it on top of a platform like Drupal/Joomla. Otherwise I'd recommend Googling around for existing open source solutions which already do this. None come to mind, but there's likely many out there.


> 3. Develop applications for Android and iOS that will share data in both directions with the website.
Hm, this is more difficult. You can build a web app, which is essentially a website on Android/iOS, that communicates with a central server. Or you could build a native application for each platform, and use a server to sync the data. I'd recommend [CouchDB]("http://couchdb.apache.org/"). Basically you have a central server in every device, and it will sync to "the cloud" for you.


> I have begun learning C++. I'm not sure if it is the best choice for my objectives. I would appreciate any advice the community may have for me about the best way to start toward my objectives.
C++ is quite a learning curve, and is mostly targeted for desktop applications. If you want to develop for mobile platforms or the web, you might want to look elsewhere. Just my opinion ;). Good luck!

---

### Post by Habitual on 2012-03-19
> **Cerastes said:**
> ...But I am confident that my idea would not be breaching any copyrights....


Don't be confident, be **certain**.

[http://www.osnews.com/story/25647/US_ISPs_to_launch_massive_copyright_spying_scheme_July_12](http://www.osnews.com/story/25647/US_ISPs_to_launch_massive_copyright_spying_scheme_July_12)

---

