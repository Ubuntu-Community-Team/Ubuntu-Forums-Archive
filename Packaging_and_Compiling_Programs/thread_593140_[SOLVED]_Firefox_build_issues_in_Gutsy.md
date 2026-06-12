---
title: "[SOLVED] Firefox build issues in Gutsy"
date: 2007-10-26
forum: Packaging and Compiling Programs
---

### Post by glennric on 2007-10-26
I am trying to compile Firefox 2.0.0.8 from source and am having some issues.

The first issue I had was a compilation error while it was building the canvas stuff for Firefox.  Then I found this
[http://live.gnome.org/JhbuildIssues/mozilla#head-65db9063bcddde7c04521924fcdecd6393972a5f]("http://live.gnome.org/JhbuildIssues/mozilla#head-65db9063bcddde7c04521924fcdecd6393972a5f")
which resolved that issue and Firefox compiled.

I installed the resulting build into the opt directory and tried to run /opt/firefox/firefox from a terminal.  All that happened was I got a message saying, "Cannot find mozilla runtime directory. Exiting."  Inspecting the files in the /opt/firefox directory I noticed that run-mozilla.sh did not have read and execute permissions for everyone.  So I added those.  Now I don't get the above message, but nothing happens.  Firefox doesn't start.  "ps aux" doesn't show any firefox processes running.  It just exits the startup scripts.

I was able to compile Firefox 2.0.0.7 while I was still running Feisty and that build still runs fine in Gutsy.  I also tried compiling Firefox 2.0.0.7 in Gutsy with the exact same .mozconfig file and method that worked in Feisty, and had the same problems I am having with 2.0.0.8.  I want to have a build of Firefox that is optimized for my processor.  Has anyone else had this issue?  Does anyone know how to solve it?

I have attached my .mozconfig file if this helps.

---

