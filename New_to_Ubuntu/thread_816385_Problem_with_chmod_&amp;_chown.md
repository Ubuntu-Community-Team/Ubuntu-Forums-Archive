---
title: "Problem with chmod &amp; chown"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by tmhartsr on 2008-06-02
Running 8.04 both 32 & 64 bit versions. When I run sudo chmod (or chown) -R username:tmhartsr ~/googleearth so I can run Google Earth as user says my username is not valid. I have root enabled and can run Google Earth from root, also by running sudo googleearth. Other than root tmhartsr is the only user account enabled. What am I doing wrong?
Thanks much
Terry

---

### Post by didac on 2008-06-02
Try:

```
chown tmhartsr:tmhartsr ~/googleearth
```

---

### Post by Sukarn on 2008-06-02
> **tmhartsr said:**
> Running 8.04 both 32 & 64 bit versions. When I run sudo chmod (or chown) -R username:tmhartsr ~/googleearth so I can run Google Earth as user says my username is not valid. I have root enabled and can run Google Earth from root, also by running sudo googleearth. Other than root tmhartsr is the only user account enabled. What am I doing wrong?
Thanks much
Terry

The username in the code is not for preceeding your username.
Its actually like this - username:group
Try this instead -
```

sudo chown -R tmhartsr:tmhartsr ~/googleearth

```

---

### Post by didac on 2008-06-02
Try:

```
chown tmhartsr:tmhartsr ~/googleearth
```

---

### Post by stchman on 2008-06-02
> **tmhartsr said:**
> Running 8.04 both 32 & 64 bit versions. When I run sudo chmod (or chown) -R username:tmhartsr ~/googleearth so I can run Google Earth as user says my username is not valid. I have root enabled and can run Google Earth from root, also by running sudo googleearth. Other than root tmhartsr is the only user account enabled. What am I doing wrong?
Thanks much
Terry

Try this, login under your account and do this in a terminal:

```
sudo chown -R $USER:$USER ~/googleearth
chmod -R 755 ~/googleearth

```

---

