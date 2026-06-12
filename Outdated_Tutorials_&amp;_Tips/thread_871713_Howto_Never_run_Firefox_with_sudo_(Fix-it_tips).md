---
title: "Howto: Never run Firefox with sudo (Fix-it tips)"
date: 2008-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by daltonlaffs on 2008-07-27
Hello people,

Yesterday, I tried to run Firefox as another user with the sudo command. However, I got the syntax wrong (put the option in the wrong place) and Firefox opened as root.

Normally, that wouldn't be too bad... I mean, just close it and try again later, when I have the syntax down.

Wrong. When I opened Firefox again from the top menu bar, it opened to a blank page. I clicked my Home button and it took me to the Firefox Start Page, when my homepage was Google.

I checked my bookmarks, and they were gone too, with a glitchy blank bookmark being the only one left.

Apparently, when you run Firefox as root, root takes ownership of several of your configuration files, including bookmarks, etc. And since the default permissions are 7/0/0, you lose your ability to open them. If you don't believe me, try running sudo firefox again. Hey look, there's your bookmarks and homepage!

How to fix the problem:

=First, find your .mozilla/firefox folder. It's almost always in your /home/username folder, but you'll need to go to View-->Show Hidden Files to be able to see it. Inside there's a firefox folder. Right-click and Copy that.

=Now, go to your Terminal. Type the following commands in order, but replace all instances of 'username' with your username:

```
sudo chown -R username:username /home/username/.mozilla/firefox
sudo chmod -R 775 /home/username/.mozilla/firefox
```

Now close Terminal and open Firefox normally. Huzzah, all your stuff is back! :guitar:

---

### Post by T3h_Dohtem on 2008-09-23
I had this exact same problem. I had tried to do the chown already, but the chmod was what finally fixed it. Thanks for the report.

---

### Post by itisbasi on 2008-10-25
Yep, that fixed it. I had this problem of a lot of buttons being disabled after updating to the latest firefox. Now I understand the problem and ahve fixed the problem. Thank you.

---

