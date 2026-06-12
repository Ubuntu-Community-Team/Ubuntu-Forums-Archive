---
title: "Remove unwanted piece of software  - especially from Message Indicator?"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by CFJensen on 2012-12-10
Cheers!

For some reason I have a Reddit app that  features on the Message Indicator, which really frustrates me.

I have tried to remove it the following ways:
Removed the Unity Webapp for Reddit from Software Centre
dconf-editor>com>canonical>unity>webapps (removed everything)
Removed/installed the mail indicator, but the icon is still there.

If I print a list of software installed, I can't find it either. I downloaded Unsettings to check, and all webapps are off. The app is not found in usr/share/applications either, which makes me wonder whether or not it's an app at all. I guess it's not a webapp since I've done so much to remove those. 

For more info: It's just a Reddit icon that opens reddit.com in Firefox when clicked. However, the Reddit app/software is found when searching the panel start page and  is just named "Reddit", but I can't really get any info on it.

So, what is the type of software I am dealing with? How do I make it go away?

Thanks a lot!




[I had another thread containing this as a subproblem, but since the main question was answered, I chose to mark it as Solved, and create this one separately.]

---

### Post by agxryt on 2012-12-10
> **CFJensen said:**
> Cheers!

For some reason I have a Reddit app that  features on the Message Indicator, which really frustrates me.

I have tried to remove it the following ways:
Removed the Unity Webapp for Reddit from Software Centre
dconf-editor>com>canonical>unity>webapps (removed everything)
Removed/installed the mail indicator, but the icon is still there.

If I print a list of software installed, I can't find it either. I downloaded Unsettings to check, and all webapps are off. The app is not found in usr/share/applications either, which makes me wonder whether or not it's an app at all. I guess it's not a webapp since I've done so much to remove those. 

For more info: It's just a Reddit icon that opens reddit.com in Firefox when clicked. However, the Reddit app/software is found when searching the panel start page and  is just named "Reddit", but I can't really get any info on it.

So, what is the type of software I am dealing with? How do I make it go away?

Thanks a lot!




[I had another thread containing this as a subproblem, but since the main question was answered, I chose to mark it as Solved, and create this one separately.]

See [https://answers.launchpad.net/ubuntu/+source/unity/+question/212703](https://answers.launchpad.net/ubuntu/+source/unity/+question/212703)

1) Make sure the webapp is removed:

```
sudo apt-get purge unity-webapps-reddit
```2) Remove the icon file, which is NOT removed in the purge.

```
rm /home/*user*/.local/share/applications/redditredditcom.desktop
```:)

---

### Post by CFJensen on 2012-12-10
Worked! Thank you! I am no longer losing my mind! ):P

---

### Post by agxryt on 2012-12-10
> **CFJensen said:**
> Worked! Thank you! I am no longer losing my mind! ):P

No problem! I get really frustrated over stuff like that too :P

---

