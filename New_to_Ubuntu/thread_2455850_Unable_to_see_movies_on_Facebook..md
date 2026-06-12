---
title: "Unable to see movies on Facebook."
date: 2020-12-29
forum: New to Ubuntu
---

### Post by krzychszew on 2020-12-29
Hello all

The problem is as described in the title. Browser used for facebook - firefox.
There is no issue on windows 10 on the same PC.
I guess the solution is somewhere on this forum, but I was unable to find it.

Any help will be appreciated.

Kindest regards

Krzysztof

---

### Post by ActionParsnip on 2020-12-29
What do you mean by "movies"? Do you mean Netflix? YouTube? What does "movies" mean in this context please?

---

### Post by llamakc on 2020-12-29
```
sudo apt install ffmpeg
```

My issue was on Twitter w/embedded videos not viewable/playable. Perhaps this will help. ffmpeg was not installed by default.

---

### Post by krzychszew on 2020-12-29
Thank you for the reply. Probably I have answer beneath. There are rather you tube and mp4 files which people implement to their posts.

---

### Post by krzychszew on 2020-12-29
> **ActionParsnip said:**
> What do you mean by "movies"? Do you mean Netflix? YouTube? What does "movies" mean in this context please?

 			 				[INDENT] 					Thank you for the reply. Probably I have answer beneath. There are  rather you tube and mp4 files which people implement to their posts. 				[/INDENT]

---

### Post by krzychszew on 2020-12-29
> **llamakc said:**
> ```
sudo apt install ffmpeg
```

My issue was on Twitter w/embedded videos not viewable/playable. Perhaps this will help. ffmpeg was not installed by default.

Thank you for the effort of helping me.

I'll try to do that whenever I'll have a spare while.

Kindest regards

Krzysztof

---

### Post by grahammechanical on 2020-12-29
You may need to activate the multiverse repository. Open Software & Updates>Ubuntu Software tab and make sure that the box is ticked that says: Software restricted by copyright or legal issues (multiverse). You may need to refresh the repositories.

```
sudo apt update
```

This command will install Ubuntu Restricted Extras which is a package that contains several useful audio and video codecs.

```
sudo apt install ubuntu-restricted-extras
```

[https://linuxhint.com/install_multimedia_codecs_ubuntu/](https://linuxhint.com/install_multimedia_codecs_ubuntu/)

Regards

---

### Post by llamakc on 2020-12-29
> **grahammechanical said:**
> You may need to activate the multiverse repository. Open Software & Updates>Ubuntu Software tab and make sure that the box is ticked that says: Software restricted by copyright or legal issues (multiverse). You may need to refresh the repositories.

```
sudo apt update
```

This command will install Ubuntu Restricted Extras which is a package that contains several useful audio and video codecs.

```
sudo apt install ubuntu-restricted-extras
```

[https://linuxhint.com/install_multimedia_codecs_ubuntu/](https://linuxhint.com/install_multimedia_codecs_ubuntu/)

Regards

This is a **better suggestion** than mine above. I did not have that meta-package installed due to an installer bug, and forgot to. Installing ffmpeg fixed my specific issue.

---

