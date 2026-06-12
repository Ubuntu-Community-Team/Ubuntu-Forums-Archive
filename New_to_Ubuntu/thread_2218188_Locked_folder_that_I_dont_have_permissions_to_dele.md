---
title: "Locked folder that I dont have permissions to delete"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by NA3OH on 2014-04-19
So I installed open office by following a video guide (linux noob) and now I'm stuck with a folder called en-us on my desktop and I cant delete it because it says I dont have permission. I'm admin by the way.

How can I delete this folder?

---

### Post by NA3OH on 2014-04-19
Found in a different thread to try typing 
gksudo nautilus

Didn't work. Shows no files on desktop

---

### Post by deadflowr on 2014-04-19
```
ls -al Desktop
```

should show you who owns what in the Desktop folder, which is where in the file system desktop folders are located.

an easy way to remove it is
```
sudo rm -rf ~/Desktop/en-us

```
or you can change ownership, if you want to feel extra safe.
```
sudo chown -R you:you ~/Desktop/en-us
```
then click to delete.

If you think you might need that folder, then maybe moving it somewhere else
```
sudo mv ~/Desktop/en-us ~/Downloads
```

Should work fine.

Hope one of these helps you.

Edit: I should also point out that when you use gksu nautilus, you are opening /root, and not your normal home folder.
(root has it's own home folder)
Which is why it was empty.

You can open nautilus in your home folder by adding its path to the command
```
gksudo nautilus /home/you
```
And you'll be in your home folder instead of root.

Somehow, I think I'm over-complicating a very simple task.

---

### Post by NA3OH on 2014-04-19
The first commands worked. Thanks for the help

---

