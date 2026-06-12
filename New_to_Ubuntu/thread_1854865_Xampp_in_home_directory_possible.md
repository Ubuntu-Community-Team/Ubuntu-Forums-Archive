---
title: "Xampp in home directory possible?"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by kramer65 on 2011-10-05
Hello,


I've got Xampp installed in my /opt/ directory. Since I need to create very large testing databases however (about 150GB) I want to move the installation to my home directory. Is this possible by simply moving the complete lampp folder to /home/mysuername, or would I break something with that?

All tips are welcome!

---

### Post by lovinglinux on 2011-10-05
You can move the entire xampp folder to your home, then create a symbolic link to the /opt folder. This way the files will actually be stored in your home partition, but the system will see them in the opt folder.

Assuming your xampp installation is located at /opt/lampp

```
sudo mv /opt/lampp $HOME/lampp
sudo ln -s $HOME/lampp /opt/lampp
```

---

