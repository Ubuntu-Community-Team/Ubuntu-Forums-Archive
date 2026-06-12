---
title: "Assembly 'nunit.framework, Version=2.5.5.10112, Culture=neutral, PublicKeyToken=96d09"
date: 2010-06-05
forum: Programming Talk
---

### Post by WitchCraft on 2010-06-05
Question:

I am implementing an OpenSource version of Microbosoft Sync framework,
[[http://www.microsoft.com/downloads/details.aspx?FamilyID=89adbb1e-53ff-41b5-ba17-8e43a2e66254&displaylang=en]](http://www.microsoft.com/downloads/details.aspx?FamilyID=89adbb1e-53ff-41b5-ba17-8e43a2e66254&displaylang=en])

(Checkout:
git clone [email]git@github.com:quandary/SyncFramework.git[/email])
but I ran into a unittest problem.

I added a nunit test-project to the C# project, but it's not compiling...

I created the project on Windows, and there it compiled well.
On Linux, the project compiles well, but compiling the unittest, I always get:
Assembly 'nunit.framework, Version=2.5.5.10112, Culture=neutral, PublicKeyToken=96d09


My problem now is I installed nunit and added a reference to it (on Linux with mono), but I still get this message, I take out 'require specific version', and I still get this message...

I also removed the windows reference to nunit, but still no change.

---

### Post by WitchCraft on 2010-06-05
bump.

---

### Post by WitchCraft on 2010-06-06
bump.

---

