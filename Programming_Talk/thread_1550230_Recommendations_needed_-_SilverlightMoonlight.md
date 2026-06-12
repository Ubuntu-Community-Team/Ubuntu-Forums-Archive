---
title: "Recommendations needed - Silverlight/Moonlight"
date: 2010-08-10
forum: Programming Talk
---

### Post by Newbie2910 on 2010-08-10
I have a desktop LOB app that I developed in WPF to run on Windows.  I now need to support both Windows and in the near future, Linux.

So, I am leaning toward moving the application to Silverlight/Moonlight.

Here's where I need some recommendations, and some problems I think I'll encounter:
1. The app won't be "hosted" by a server anywhere, it will just be loaded and run from the desktop (via shortcut) in IE or Firefox.  Other than a spot on a shared drive to install the app from, there won't be any server to do anything.  (the program doesn't required this to operate).  So, question #1 is can a Silverlight/Moonlight app be simply loaded from a shared drive.

2. I don't think Silverlight/Moonlight support DataTable objects, which my core code uses to show data in datagrids.  From what I have read, the thinking today is to use WCF to get the data.   But since I won't have a server, should I modify my code to output some other type of collection that can be bound to a datagrid.

3. The core CLR code uses several .XML configuration files to store data.  On the desktop WPF app, I just copy them over when the app loads.  I think I can copy them to isolated storage for Silverlight/Moonlight but I need to users to be able to manually edit and add/delete those files... will that be a problem?

It is a requirement that this app have a single code base that can run cross-platform (Windows and Linux) [also, Wine is not an option].  Is what I am attempting to do the right way to achieve this?

Thanks.

---

