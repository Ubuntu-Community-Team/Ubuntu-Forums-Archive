---
title: "Can't update my system"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by bdemirel on 2013-01-02
Hi all,
I am new in Ubuntu and I have seen that Ubuntu didn't install my graphics driver when it's set up. I searched for Internet and it recommended me to add a source link through Ubuntu Software Center.([http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu))
After adding it update manager has detected some but gives an error(Attachment 1). When I click on 'Partial Upgrade', and enter my password, it gives another error(Attachment 2). What is the problem?

---

### Post by TheFu on 2013-01-02
> **bdemirel said:**
> Hi all,
I am new in Ubuntu and I have seen that Ubuntu didn't install my graphics driver when it's set up. I searched for Internet and it recommended me to add a source link through Ubuntu Software Center.([http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu))
After adding it update manager has detected some but gives an error(Attachment 1). When I click on 'Partial Upgrade', and enter my password, it gives another error(Attachment 2). What is the problem?

I don't know what the problem is. Not enough information plus APT is not always clear about real issues.

Drop to a terminal. The GUI is too hard for this stuff. run
* sudo apt-get update
* sudo apt-get install -f
*if everything seems to have been fixed, then run*
* sudo apt-get upgrade

What are the results - please copy/paste relevent **text**.

---

### Post by bdemirel on 2013-01-02
I already tried them but it gave me errors too, but I solved my problem. Using Synaptic Package Manager solved my problem. Thanks.

---

### Post by TheFu on 2013-01-02
> **bdemirel said:**
> I already tried them but it gave me errors too, but I solved my problem. Using Synaptic Package Manager solved my problem. Thanks.

When you find the solution, **please** come back to this thread, explain the solution, and mark it **SOLVED** to help the next guy.

---

