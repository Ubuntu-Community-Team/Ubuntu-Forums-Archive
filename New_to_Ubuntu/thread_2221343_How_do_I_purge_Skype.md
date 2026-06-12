---
title: "How do I purge Skype?"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Toni_Vines on 2014-05-01
I'm having some horrendous problems with getting Skype to work in Ubuntu 14.04 LTS 64 bit. I have no sound and it won't see my webcam. I think I need to completely purge Skype and then start again from the ground up! 
Could anyone please tell me the best way to clean it off my machine? 
Thanking you,
Toni.

---

### Post by LastDino on 2014-05-01
> sudo apt-get purge skype

Should do it.

---

### Post by monkeybrain20122 on 2014-05-01
Remove the hidden folder .skype from your home. To find it open the file browser and press ctrl+h or from the menu choose view hidden files. This is where your configurations are stored, if your problem is caused by corrupt configuration reinstalling skype is not going to fix it, you must remove the configuration.

---

### Post by Toni_Vines on 2014-05-01
Grateful thanks, job done! Now I have to try and sort out re-installing to make it work!!!

---

### Post by LastDino on 2014-05-02
> sudo apt-get install skype

As easy as that :P

---

### Post by ranger1021994 on 2014-05-02
As Goten007 stated:
```
sudo apt-get purge skype
```

To completely clean all files created/used by Skype:
```
sudo find / -name skype
```
Delete skype files as listed

To reinstall, as Goten007 mentioned:
```
sudo apt-get install skype
```


Please mark the thread as solved if your queries have been answered.

---

