---
title: "Texmaker install throwing dependency errors, but I have all the dependencies."
date: 2012-02-03
forum: New to Ubuntu
---

### Post by vancinas on 2012-02-03
Hi, I've only been using Ubuntu for a few days, and I'm trying to install Texmaker. I downloaded an i386.deb package of the latest version from the Texmaker website, and the instructions said to install it by typing "sudo dpkg -i <package name>.deb in the terminal. When I try this, I get a list of dependencies that I supposedly don't have. However, I checked the Software Center and it says I have every one of the dependencies that the package manager says I'm missing. Can anyone tell me what the problem is? I like a lot of things about Ubuntu, but I run into a lot of cryptic error messages, which is very frustrating. I've posted the error message from the terminal below. Thanks for your help!
```

Selecting previously deselected package texmaker:i386.
(Reading database ... 184230 files and directories currently installed.)
Unpacking texmaker:i386 (from texmaker_ubuntu_11.10_3.2.2_i386.deb) ...
dpkg: dependency problems prevent configuration of texmaker:i386:
 texmaker:i386 depends on libpoppler-qt4-3 (>= 0.16).
 texmaker:i386 depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network:i386 is not installed.
 texmaker:i386 depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml:i386 is not installed.
 texmaker:i386 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4:i386 is not installed.
 texmaker:i386 depends on libqtgui4 (>= 4:4.7.0~beta1); however:
  Package libqtgui4:i386 is not installed.
 texmaker:i386 depends on libqtwebkit4 (>= 2.2~2011week36); however:
 texmaker:i386 depends on libstdc++6 (>= 4.1.1); however:
  Package libstdc++6:i386 is not installed.
dpkg: error processing texmaker:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 texmaker:i386
```

---

### Post by joetait on 2012-02-03
Perhaps not very helpful, but have you tried installing it via Synaptics, or is there a reason you don't want to? I just installed in the above method, and it seems to be exactly the same.

---

### Post by vancinas on 2012-02-03
No, I haven't tried installing via Synaptics. I'm not sure what that is. How would I go about trying that?

---

### Post by joetait on 2012-02-03
Synaptics is a more powerful version of software centre. If you search "synaptics" in the dash, then "Synaptics package manager" should come up.

Once you have opened Synaptics (should require your password), search "texmaker", and there will only be two entries - "texmaker" and "texmaker - data". Install the former. It should sort out dependencies for you.

Let me know if any of that doesn't make sense/doesn't work.

Edit: Just remembered that synaptic is no longer installed by default - you will have to install synaptic package manager via the software centre, then proceed as above. Sorry!

---

### Post by vancinas on 2012-02-03
Awesome! That worked great. Thanks for your help! Why can't the default software center work that smoothly?

---

### Post by joetait on 2012-02-04
I don't know why it wouldn't work in this case, does seem odd. By the way, you should mark the thread as solved (under thread tools at the top) so that people know it worked. 

Glad to have helped :)

---

