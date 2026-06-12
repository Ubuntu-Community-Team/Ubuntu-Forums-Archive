---
title: "Online game and Ubuntu?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by iphigeneia5 on 2008-11-24
Hi,
I am a complete beginner when it comes to using Ubuntu. I recently started playing this online game for fun in my spare time (haha, when is that ever? :) ) and it required Java. So, I got the Sun Java package and then it worked. When I went back to play it a second time, it didn't work!! So I did a little research and got the Java JRE package. Again, it worked once, and now it isn't working again! It has no graphics, no sound..so that isn't the issue. Its a text based MUD and I've never had any issues with it on other computers running Windows XP...any thoughts? Suggestions?

---

### Post by taurus on 2008-11-24
How did you install java?  Did you install it by running something similar like these?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

