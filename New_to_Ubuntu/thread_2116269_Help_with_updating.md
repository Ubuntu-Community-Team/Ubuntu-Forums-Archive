---
title: "Help with updating"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by jeringeorge on 2013-02-15
I'm a new user of ubuntu. my OS  is  Ubuntu 10.04 LTS              - the Lucid Lynx - released in April 2010 and it is supported until April 2013.
i just wanna update my OS and dont want to UPGRADE to next version until april 2013.
Please help me!

---

### Post by snowpine on 2013-02-15
Here are the terminal commands to apply security/stability updates to your existing 10.04 system (but NOT take you to 12.04):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You can also use the Update Manager if you prefer a GUI interface (but DON'T click on the "a new release of Ubuntu is available...." button ;)).

---

### Post by jeringeorge on 2013-02-15
Thanks

---

### Post by ibjsb4 on 2013-02-15
If you want to stop that behavior go to the update tab and under release upgrade just change it to never.

 [https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

---

