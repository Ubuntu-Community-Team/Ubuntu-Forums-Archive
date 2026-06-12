---
title: "Installing QT4 For Development - Where Is It?"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by JTeagle on 2013-05-11
I'm trying to install QT4 so that Code::Blocks can use it, but I'm stuck. 

I used apt-get to install libqt4-core, libqt4-dev, libqt4-gui and qt4-dev-tools. I have to assume these *are* installed since trying to repeat the install tells me they're already at the latest version. 

The problem is, I can't find anything. Code::Blocks says it needs the directory at the root of (presumably) the QT4 installation, the one that has include and lib beneath it. That makes perfect sense to me - except that I can't find it. 

If I use locate qt, I get very few entries (but they do have /qt4/ in them, so encouraging) but none of them contain include or lib subdirectories. 

If I use locate include, whilst I do get a lot of entries (as you might expect), none of them look even remotely relevant. And yet Dash says there are a couple of QT4 programs in there - but won't tell me where.

I did try entering /usr for the path (since it has include and lib below it), but Code::Blocks said 'yes, that's a real directory but I can't find what I need there'. So it's obviously not the right one. 

Any ideas? I don't understand why I don't have a qt4 directory somewhere with everything below it... wouldn't that make sense? How on Earth do you folks find anything in Linux? I struggle to see any logic in the way things are arranged, with the exception of /home/<my-user-name>! 

Thanks.

---

### Post by Archit88 on 2013-05-11
try to install Qt from software center .

---

