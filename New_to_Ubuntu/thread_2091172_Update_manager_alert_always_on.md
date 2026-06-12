---
title: "Update manager alert always on ?"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Greg Mueller on 2012-12-04
The triangular orange alert icon with the exclamation mark in it is always showing in my tray. When I click on it and have it check for updates it looks like it is starting to download and then stops and says.....

**Failed to download repository information**

Check your Internet connection.

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead. 


What's going on?

---

### Post by howefield on 2012-12-04
Natty is end of life.

So your version is unsupported hence no repositories for you to download.

You could point your sources.list to old-releases or upgrade to something better supported.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Greg Mueller on 2012-12-04
Well I'm pretty happy with the way the computer is running etc.

How can I turn off the update warning icon?

---

### Post by howefield on 2012-12-04
Try loading the update manager application, and set the options as required.

---

### Post by monkeybrain2012 on 2012-12-04
Actually it happens in Precise too, it started only recently. The triangle appears whenever there is an update even though I have configured it to notify updates once a week. 

@OP the fail to load repository info just means that the repositories have been removed because Natty has expired.

---

