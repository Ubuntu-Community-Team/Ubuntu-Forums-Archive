---
title: "[SOLVED] Sharing a file in memory?"
date: 2009-01-01
forum: Programming Talk
---

### Post by Zeotronic on 2009-01-01
C++: I have two pieces of code in my application, one which writes files with fstream, and another which reads them with stdio. Rather than rewriting one or both, or writing to the hard driver unnessisarily, how could I go about writing the file into ram and then reading it, or otherwise converting the file between fstream and stdio?

---

### Post by dwhitney67 on 2009-01-01
Reading/writing files with fstream and stdio is not an issue; the only thing that differs between the two is the API.

It seems from your post that you have a single application.  If you need two parts of this application to have access to the data, then I don't see the need to use a file.  Could you not just use a class object to hold the data (e.g. a singleton)?

Anyhow, if you have a moment, please specify your application's requirements a little more concisely so that proper advice can be given.

---

