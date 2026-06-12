---
title: "Using a custom desktop environment for one user"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by indigenous71 on 2008-05-25
Hi,

I've had the idea to have a user account that will launch straight into VirtualBox and load Windows XP I've heard it can be done but I'm not sure how. I know that I'll need to have a much lighter WM than GNOME but I have a few things I'm not sure on.

1. If I edit the .xinitrc file in the user account I create, will the changes only apply to the account I'm in or will the apply to all users of the machine?

2. I've found a couple of Window Managers that are billed to be very light but I'm not sure which is best, as I will login to a virtual machine I don't need much. At the moment I'm looking at 'Equinox' (or EDE), 'Enlightenment', 'Fluxbox' and XFCE. Which of those would everyone say is best for my scenario?

3. In VirtualBox is there a way of loading straight into a machine rather than starting with the selection screen first?

4. It would also be cool, but not necessary, if I was automatically logged out when VirtualBox closed.

Sorry for so many questions but I don't wanna muck anything up.

All help is much appreciated :)!

Thanks

---

### Post by unutbu on 2008-05-25
Hello indigenous71,

> **indigenous71 said:**
> 
1. If I edit the .xinitrc file in the user account I create, will the changes only apply to the account I'm in or will the apply to all users of the machine?

The file you want to edit is called /home/newuser/.Xclients. newuser's .Xclients script will not affect any other user. Once you've created the new user, at the gdm login screen press F10 or go to the lower left corner an click on "Options>Run Xclients script".

> **indigenous71 said:**
> 
2. I've found a couple of Window Managers that are billed to be very light 

You can set it up with no window manager at all. That way, when you quit Virtual Box, you'll be kicked right back to the gdm login window.

> **indigenous71 said:**
> 
3. In VirtualBox is there a way of loading straight into a machine rather than starting with the selection screen first?

Edit the file ~/.Xclients to look like this:
```

virtualbox  # or whatever command you use to launch virtualbox.

```

> **indigenous71 said:**
> 
4. It would also be cool, but not necessary, if I was automatically logged out when VirtualBox closed.

I think this is exactly what will happen if you don't run a window manager.

Hope this helps.

---

### Post by indigenous71 on 2008-05-25
Thanks unutbu, I think this could help there was one problem so far though.

> **unutbu said:**
> 
The file you want to edit is called /home/newuser/.Xclients. newuser's .Xclients script will not affect any other user. Once you've created the new user, at the gdm login screen press F10 or go to the lower left corner an click on "Options>Run Xclients script".

I can't find any file or folder called .Xclients, I've done ctrl+h to show hidden files and its not there either, should I create one myself? If so what should be in the file?

Thanks

below is a screenshot of the home/newuser (or in this case home/windows)

[IMG]http://www2.picturepush.com/photo/a/722820/640/722820.png[/IMG]

---

### Post by unutbu on 2008-05-25
Yes, just create the file .Xclients in windows' home directory.

I don't use virtualbox so I'm not entirely sure what command you use to launch it. Do you know what the command is? Whatever that command is, put it in .Xclients. That's all you have to do.

---

