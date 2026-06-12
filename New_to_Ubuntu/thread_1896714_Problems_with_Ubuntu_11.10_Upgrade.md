---
title: "Problems with Ubuntu 11.10 Upgrade"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by kizzyaggots on 2011-12-17
Dear, Ubuntu users and mods, i've tried to upgrade ubuntu 11.04 to 11.10 and I get the following error message......

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/chris/main'./source/Sources](http://archive.ubuntu.com/ubuntu/dists/chris/main'./source/Sources)  404  Not Found [IP: 91.189.88.45 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can anybody tell me where I am going wrong please?

                 Kind Regards Kizzy.

---

### Post by yeats on 2011-12-17
```
http://archive.ubuntu.com/ubuntu/dists/chris/main'./source/Sources
```
is not a valid repo URL... did you manually edit the source list at one point?

In any case, either changing that URL to a correct one or commenting out (placing a # at the beginning of) that line should allow you to continue.

---

### Post by kizzyaggots on 2011-12-17
I edited some things from the repository but i'm not sure what now.

           Cheers Kizzy.

---

### Post by amjjawad on 2011-12-17
> **kizzyaggots said:**
> I edited some things from the repository but i'm not sure what now.

           Cheers Kizzy.

Hello and Welcome to Ubuntu Forum :)

```
gksudo gedit /etc/apt/sources.list
```

Please run the above command from Terminal and post the output of your sources.list here and please make sure to wrap up the text with "CODE" tags or select the text and click #.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


For more info: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

