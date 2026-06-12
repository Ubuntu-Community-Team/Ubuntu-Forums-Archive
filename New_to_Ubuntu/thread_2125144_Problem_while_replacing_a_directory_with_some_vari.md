---
title: "Problem while replacing a directory with some variable"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by ankitarajdev on 2013-03-13
I have written some script under the path root/c4/build and in that script I have mentioned the path /home/cdot/c4. I want to replace /home/cdot with some variable. I have to make a  script in the root directory so that I could replace the path /home/cdot inside root/c4/build with the variable. Can you plaese help me?

Thanku

---

### Post by Impavidus on 2013-03-13
You want a script that modifies a script? Try using **sed**:```

sudo sed -i s:/home/cdot:your_variable:g /root/c4/build
```

---

### Post by schragge on 2013-03-13
You also may consider passing the path to the script as parameter on command line if you need a more flexible solution. Just change the line suggested by **Impavidius** like this:
```
sudo sed -i 's:/home/cdot:[COLOR=#ff0000]$1[/COLOR]:g' /root/c4/build
```You also may need to quote it properly if there's possibility of the parameter containing space characters.

---

