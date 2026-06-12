---
title: "&quot;Your preferences can not be read&quot; message pop up when running nw.js from ubuntu"
date: 2017-02-13
forum: New to Ubuntu
---

### Post by dk1979 on 2017-02-13
Hi all, I'm trying to run nw ([https://nwjs.io/](https://nwjs.io/)) with a folder that contains my html front as following :

```
./nw /home/frontend
```

and I get the following message in terminal :

[11798:11798:0207/154100.026830:ERROR:desktop_window_tree_host_x11.cc(1131)] Not implemented reached in virtual void views DesktopWindowTreeHostX11::InitModalType(ui::ModalType)

and in the application the pop up message :

"Your preferences can not be read. Some features may be unavailable and changes to preferences won't be saved."

when I run the above command with sudo or gksu everything seems ok . The same happened for the 0.19.5 version as well.
I also found that this problem was happening on chrome browser as well. I contacted with the nw.js forum and they responded that "It should be that the file in the user data dir was changed to wrong permission/ownership. " without any further explanation.
Since I don't want to run it with root access and I'm quite new in using Ubuntu , could you give some more detailed hint on how to solve it?

---

### Post by QIII on 2017-02-13
Hello!

Please do not add formatting tags to your posts.  Use the default font and format, code tags and quote tags.

Thanks.

---

