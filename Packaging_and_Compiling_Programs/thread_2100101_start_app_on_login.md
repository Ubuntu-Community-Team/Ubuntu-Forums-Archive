---
title: "start app on login"
date: 2012-12-31
forum: Packaging and Compiling Programs
---

### Post by slimjimmrtim on 2012-12-31
Hey all,

I'm in the process of creating my first .deb package which also happens to be an indicator that should start when the user logs in.

I have successfully made a .deb package, and I know how to include init and upstart scripts, but this isn't to be run as a service, but instead it is to autostart on boot.

I could modify my (python) script to drop the necessary files in the the user's home the first time they run the indicator to allow for autostarting, but if I do that the autostart commands will be left there if the user decides to remove the application.

What can I do? Thanks!

---

