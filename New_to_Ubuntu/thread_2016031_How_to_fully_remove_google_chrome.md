---
title: "How to fully remove google chrome"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by kelbizzle on 2012-07-04
How do I fully remove an application? I have already tried 
```
sudo apt-get --purge remove google-chrome-stable
```

That didn't seem to work. Upon re-installing chrome all of my extentions and setting and book marks are still there. I want everything removed so I can cleanly reinstall chrome.

---

### Post by vasa1 on 2012-07-04
You also need to delete or rename /home/your_name/.config/google-chrome

Also, I prefer just

```
sudo apt-get purge google-chrome-stable
```

---

### Post by deadflowr on 2012-07-04
You should be able to do what you did, and then remove the folder in /home/username/.config, like
```
rm -rf /home/username/.config/google-chrome
```

And to be safe, do the same thing to the .cache folder.(/home/username/.cache/google-chrome)
That should remove all chrome from your system.

---

### Post by kelbizzle on 2012-07-04
Thanks that did the trick. Now I need to find out why this web page I created only messes up on chrome on linux.

---

### Post by vasa1 on 2012-07-04
> **kelbizzle said:**
> Thanks that did the trick. Now I need to find out why this web page I created only messes up on chrome on linux.

Would this help?
[http://validator.w3.org/](http://validator.w3.org/)

---

### Post by kelbizzle on 2012-07-05
> **vasa1 said:**
> Would this help?
[http://validator.w3.org/](http://validator.w3.org/)

Thanks for the suggestion. That would help except the page passes validation. I've given up developing on my Ubuntu system for now. I'll just use the work supplied PC.

---

