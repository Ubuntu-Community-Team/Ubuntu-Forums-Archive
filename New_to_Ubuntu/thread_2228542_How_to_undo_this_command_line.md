---
title: "How to undo this command line"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by linuxmint7771 on 2014-06-08
trying to get a skype status icon on Ubuntu 14.04 I run this command line:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'Skype']"
```

then I realized I have to install  Skype tray / appindicator manually because it is not installed automatically like this:
```
sudo apt-get install sni-qt:i386
```

So the first command line is unecessary. How can I undo it :D

---

### Post by deadflowr on 2014-06-08
Are you sure you even did anything, because I don't think that
```
com.canonical.Unity.Panel
```
even exists on 14.04.

---

### Post by sameermw on 2014-06-09
I think you are trying too old blog post, if i am correct this is for Ubuntu 11.xx or below version. For Ubuntu 14.04 ```
sudo apt-get install sni-qt:i386
``` is enough. No need to worry about first command. follow [deadflowr]("http://ubuntuforums.org/member.php?u=1276577") 's idea.

---

