---
title: "How to get real time information about how many user are logged in and their ips"
date: 2009-01-20
forum: Programming Talk
---

### Post by Grace.zhang on 2009-01-20
I use tomcat as my server platform in Ubuntu for a war file.

I know in order to get real time information about how many user are logged in, we can count how many active sessions exist by a SessionCounter code. However, I have to permit HttpSessionListener in web.xml of tomcat. From other users' experiences, the configuration is complexed and has some errors.

Here's the link:
[http://www.stardeveloper.com/articles/display.html?article=2001112001&page=1](http://www.stardeveloper.com/articles/display.html?article=2001112001&page=1)

In order to get users' ip, in jsp, use  request.getremotehost() or
request.getremoteaddress() by editing the jsp file.

I wonder if there's some open source software to use for these two purposes.

---

### Post by Tomosaur on 2009-01-20
One way would be to update an 'last active' time-stamp (in your user database, or whatever) when a logged in user performs an action (visits a new page, etc). Let's say your idle time-out is 10 minutes. When the website need to display who is logged in, just query the database and show only those users whose (currentTime - lastActive) time-stamp is lower than the idle timeout. This is much less complicated than the SessionCounter, but obviously relies on you making updates and queries every time the user does something. Overriding something which is called at every request would make this a hell of a lot easier than I'm making it sound.

---

