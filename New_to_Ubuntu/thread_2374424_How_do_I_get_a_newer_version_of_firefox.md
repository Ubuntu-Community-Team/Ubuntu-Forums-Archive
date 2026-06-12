---
title: "How do I get a newer version of firefox?"
date: 2017-10-16
forum: New to Ubuntu
---

### Post by eliyahu22 on 2017-10-16
I have 16.04, but it has an old version of firefox, and it is acting up.  How do I get the latest version of firefox?   In the repositories is only the old one I have.

---

### Post by deadflowr on 2017-10-16
what version is it?

---

### Post by eliyahu22 on 2017-10-16
> **deadflowr said:**
> what version is it?

I think 41, but I'm not sure.  How can I see that?

---

### Post by Impavidus on 2017-10-16
In Firefox, click Help -> About Firefox. That should tell you which version you run. On 16.04 automatic updates should ensure you get the latest version of Firefox a few days after release. You should have Firefox 56 by now. What does```
apt-cache policy firefox
```show you?

---

### Post by Autodave on 2017-10-16
Out of all my 13 machines, only 3 of them update themselves. All are set to do that, but just don't.  In a terminal:

sudo apt-get update
sudo apt-get upgrade

---

### Post by eliyahu22 on 2017-10-16
In help it says I have 55.0.2, so I guess I do have now the latest version.   But a few months ago when I checked, I had 41 or so.  

I'll see if it behaves now.

---

### Post by vasa1 on 2017-10-16
> **eliyahu22 said:**
> ... I have 55.0.2, so I guess I do have now the latest version. ...
No, you don't. Please run the commands Autodave suggested.

---

