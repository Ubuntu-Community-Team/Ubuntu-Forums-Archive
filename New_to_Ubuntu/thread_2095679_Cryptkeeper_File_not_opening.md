---
title: "Cryptkeeper File not opening"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2012-12-17
I have files in a Cryptkeeper folder on a 10.04 system.  Trying to open it, I see the attached screenshot.  
What does it mean and how do I open the Cryptkeeper file?

---

### Post by s1baker on 2012-12-17
probably your folder (dwhelper) was left hanging open the last time you used cryptkeeper. Check that your hidden encrypted folder ( probably called .dwhelper_encfs ) is still there in home/michael
and then if there is an open folder called dwhelper, chunk dwhelper into the trash can ( assuming you don't have anything in dwhelper that you want to save. )

You can actually go into .dwhelper_encfs and see the files and folders, all garbled up of course.

---

### Post by Dumpy Dumpster on 2012-12-18
Thanks s1baker, as you said a garbled open folder.
Deleted and all runnning OK.  Thanks again.

---

