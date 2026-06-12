---
title: "Opera not working"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by JoyceBabu on 2008-05-02
I installed Opera in my new Ubuntu system (Hardy), but I can't use it. When I open the program from Applications > Internet, the program window doesn't show up. System Monitor confirms that it is running. Can someone plz help me? Opera is my favorite browser.

I had installed Kestrel (Opera 9.5 Beta 2) before I installed Opera, using a debian package from Opera.com, it also showed the same problem(but it atleast used to show up before vanishing) and I have removed it and installed the current stable version using Synaptic Package Manager.

---

### Post by TeoBigusGeekus on 2008-05-02
How did you remove the beta version?

---

### Post by JoyceBabu on 2008-05-02
> **TeoBigusGeekus said:**
> How did you remove the beta version?

By running the following command in Terminal
> $ dpkg -r opera

---

### Post by TeoBigusGeekus on 2008-05-02
When you install deb packages, you can uninstall them from synaptic. 
Go to synaptic and search for opera. Uninstall them - [COLOR="Red"]completely[/COLOR] - and then try to install opera again.
I hope this helps...

---

### Post by JoyceBabu on 2008-05-02
No. It is still not working :(

---

### Post by TeoBigusGeekus on 2008-05-02
Did you remove all instances of Opera (beta and normal)?

---

### Post by JoyceBabu on 2008-05-02
Yes, I first removed Opera 9.27 completely. 

Then reinstalled opera beta from the debian packages and then uninstalled it completely from Synaptic Package Manager.

Then I once again installed Opera 9.27.

---

### Post by eriqjaffe on 2008-05-02
You might need to do...

```
sudo dpkg -r --purge opera
```

...to make sure all the config files are removed as well.

---

### Post by gandaran on 2008-05-02
very simple, just delete the .opera folder in you hidden home folder!

---

### Post by JoyceBabu on 2008-05-03
> **gandaran said:**
> very simple, just delete the .opera folder in you hidden home folder!
That did it :D

Thanks to all for helping :)

---

