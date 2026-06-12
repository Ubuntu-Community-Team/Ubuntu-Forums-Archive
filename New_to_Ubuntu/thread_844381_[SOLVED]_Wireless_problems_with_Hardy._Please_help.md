---
title: "[SOLVED] Wireless problems with Hardy. Please help."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by ElTesorillo on 2008-06-29
Hello, I am brand new to ubuntu and have been enjoying it for the most part. When I first installed it, my wireless was working fine but about 5 days later, ubuntu wont connect to the wifi. It reads the network and tries to connect but never makes it. I have a Dell Vostro 1500 with a Intel-N wireless card. Thank you for all of your help in advance.

---

### Post by kansasnoob on 2008-06-29
I know very little about wifi, so little that everytime I set one up I have to go to the following section of forum help to find an answer:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Sorry I can't really help, but think of it as a free bump:)

---

### Post by ConMan318 on 2008-06-29
Are you using Network Manager?  If so, I'd recommend switching to Wicd, since many people have problems with the wireless on Network Manager.  You can read up on it here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

To install it open up Synaptic and go to Settings > Repositories > 3rd-party Software > Add, then put in
```

deb http://apt.wicd.net hardy extras

```

If you aren't using Hardy, change 'hardy' to 'gutsy' or whatever you are using.  Then search 'wicd' in Synaptic and check the box for Wicd, then click apply.  It will then appear in Applications > Internet.

You can wait for other users to post their input, too, maybe someone knows of a solution within Network Manager.  But I've known of a lot of people that had trouble with wireless using Network Manager, and a lot of times it works fine in Wicd.

Since your card is detected and you are picking up networks, the only thing that I can think of that would be screwed up is the program you're using to connect.

---

### Post by ConMan318 on 2008-06-29
Are you using Network Manager?  If so, I'd recommend switching to Wicd, since many people have problems with the wireless on Network Manager.  You can read up on it here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

To install it open up Synaptic and go to Settings > Repositories > 3rd-party Software > Add, then put in
```

deb http://apt.wicd.net hardy extras

```

If you aren't using Hardy, change 'hardy' to 'gutsy' or whatever you are using.  Then search 'wicd' in Synaptic and check the box for Wicd, then click apply.  It will then appear in Applications > Internet.

You can wait for other users to post their input, too, maybe someone knows of a solution within Network Manager.  But I've known of a lot of people that had trouble with wireless using Network Manager, and a lot of times it works fine in Wicd.

Since your card is detected and you are picking up networks, the only thing that I can think of that would be screwed up is the program you're using to connect.

EDIT: Don't know why that double-posted...

---

