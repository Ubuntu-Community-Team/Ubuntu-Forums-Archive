---
title: "Standard cout and cerr do not show in console"
date: 2007-10-18
forum: Programming Talk
---

### Post by qgranfor on 2007-10-18
I'm developing a program in wxGTK 2.8.6 under Xubuntu and have a very stange issue.

wxPrintf will display in the console.  Standard cout, cerr, printf do not.  Could this be related to the fact the program is unicode?

I did not have this issue (same code) with my Gentoo boxes.

---

### Post by qgranfor on 2007-10-22
Well, I simply cheated and re-routed cout/cerr to test files which seems to be working ok.  Back to debugging....  :popcorn:

---

