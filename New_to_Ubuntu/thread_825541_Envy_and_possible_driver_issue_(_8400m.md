---
title: "Envy and possible driver issue :( 8400m"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by burakerenn on 2008-06-11
I got 8400M g nvidia graphic card. I had tried to install my drivers with envy and couldn't make it long ago. I decided to give it another try today and installed my drivers with envy. Well now, it managed to open X but there's no window borders :S. Now I have some strange issues with firefox too. Like when I write something to address bar it's flashing and can't manage combo box. 

Here's a screenshot.

Any idea about fixing it?  :(

EDIT: It becomes normal when I close desktop effects. :(

---

### Post by forestpixie on 2008-06-11
I always have to run this command to get the windows working properly. 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Do Alt+F2 and paste command in then run, restart X - Ctrl+Bkspace

---

### Post by sdennie on 2008-06-11
What is the output of this command:

```

glxinfo | grep direct

```

I run nvidia drivers from the nvidia website and occasionally an Ubuntu update will overwrite a file and cause direct rendering to stop working.  In that case, I get the exact behavior you are describing.  The fix is to simply re-install the driver (it may be possible to prevent this but, I'm not sure how).

---

### Post by burakerenn on 2008-06-11
Yes, just as described direct rendering has stopped working. Thanks for replies. It's really pain with these drivers :/

---

