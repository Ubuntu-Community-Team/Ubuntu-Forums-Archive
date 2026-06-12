---
title: "[SOLVED] .dmrc"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by clauswilson on 2008-12-01
I am greeted by every boot with a message saying that the file .dmrc prevents that some settings are stored. The file was completely empty but is now renamed to ._dmrc. What is all this about? I would like to get rid of the "greeting" - running a brand new ubuntu 8.10 but with files copied over from my old kubuntu 8.10 (which I disliked obviously and changed the system)

---

### Post by marshall.robert on 2008-12-01
could you tell us more? or get a screenshot of the error?

---

### Post by kpkeerthi on 2008-12-01
> **clauswilson said:**
> I am greeted by every boot with a message saying that the file .dmrc prevents that some settings are stored. The file was completely empty but is now renamed to ._dmrc. What is all this about? I would like to get rid of the "greeting" - running a brand new ubuntu 8.10 but with files copied over from my old kubuntu 8.10 (which I disliked obviously and changed the system)

Are you asking about the error that says .dmrc and /home/<user>  does not have proper permission - 644 for .dmrc and 700 for /home/<user>?

This is how I fixed it yesterday after I installed GDM.

Write the commands in a terminal window.
```

touch .dmrc

```
```

sudo chown 644 .dmrc

```
```

sudo chown 700 /home/<user>

```
* Replace <user> with your login Id.

[[More Info]("https://answers.launchpad.net/ubuntu/+question/7296")]

---

### Post by clauswilson on 2008-12-06
Thank you for some help. I tried it and I still get this annoying start-up screen. If it could just go straight into the desktop and write this silly things somewhere else. Although I know that this is a problem for storing the language settings.

- Why should 700 own my home directory? Do you mean chmod 700 ?

---

### Post by Nepherte on 2008-12-06
It should be chmod indeed. Check out this page for the ownership & permission settings for .dmrc: [https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

On that same page, [https://help.ubuntu.com/community/dmrcErrors#The%20.dmrc%20File](https://help.ubuntu.com/community/dmrcErrors#The%20.dmrc%20File), you will also read that the file can be empty indeed or with the specified content (be sure to set the correct language and not simply copy/paste it)

---

### Post by clauswilson on 2008-12-06
Okay now it works! Hurrah! How to I put this subject as solved?

---

### Post by kpkeerthi on 2008-12-06
> **clauswilson said:**
> Okay now it works! Hurrah! How to I put this subject as solved?

Look in the link that reads 'Thread Tools' just above Post# 1

---

