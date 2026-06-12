---
title: "Ubuntu 14.04: Red Exclamation Point In Taskbar"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by wpwend42 on 2016-05-26
I have a red exclamation point in my taskbar. When I click, it says "The update information is out of date....this may be caused by a repository that is not available anymore." It suggests to click "show updates" to see if any fail, but when I do a box comes up and says the computer is up to date.

What could be wrong here?

---

### Post by grahammechanical on 2016-05-26
Have you installed any PPAs? Like the message says, it could be caused by a repository that is not available. Run

```
sudo apt-get update
sudo apt-get upgrade
```

And look for any indication that a repository URL cannot be accessed (IGNored). Or post the output in code tags and some of us may be able to advise you.

Regards.

---

### Post by wpwend42 on 2016-05-27
> **grahammechanical said:**
> Have you installed any PPAs? Like the message says, it could be caused by a repository that is not available. Run

```
sudo apt-get update
sudo apt-get upgrade
```

And look for any indication that a repository URL cannot be accessed (IGNored). Or post the output in code tags and some of us may be able to advise you.

Regards.

It was an install of Vivaldi causing the problem. Thanks!

---

