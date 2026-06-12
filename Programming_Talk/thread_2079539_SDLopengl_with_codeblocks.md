---
title: "SDL/opengl with codeblocks"
date: 2012-11-02
forum: Programming Talk
---

### Post by doyleman on 2012-11-02
I've built a project to open and setup a basic opengl window which works perfectly fine in windows, and when trying to rebuild it in ubuntu, it just hangs on build. no window pops up, no errors show in the log, nothing. under Build, the only option available is abort; which is greyed out. funky part? the project builds fine and I can run the debug program after i close codeblocks. anyone know whats going on and why I cant get the app to run through c::b?

---

### Post by doyleman on 2012-11-02
bump; has anyone at least experienced a similar issue and or might know a cause?

---

### Post by SuperCamel on 2012-11-02
Make sure your build target is set to console, so you can see any terminal messages. 

In the 'Project' menu, go to 'Properties'. On the build targets tab, make sure your build target type is set to 'console application'.

---

