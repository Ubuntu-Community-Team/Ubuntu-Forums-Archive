---
title: "Ubuntu 12.04 - Give access to WWW folder to user"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by gaurihspatil on 2013-09-03
Hey Folks,

I want to try the Ubuntu. I installed stable version Ubuntu 12.04.

While installation I created the user - user1 .
I am able to logn using same username & password.

When I try to create file in /var/www/ .. it not allowing to do ... gives error access denied...

How can add permission my User1.. so I can add,edit, delete files. 

I don't want give 0777 permission to WWW folder, as that is not standard.  
Can I add my user to apache group or to root group... .. I am not sure what is the correct way to.



Thanks,
Gaurish

---

### Post by rai_shu2 on 2013-09-03
The usual thing to do IMO is to make a symlink from the www folder to whatever folder you want shared.

So...

```
sudo -i
cd /var/www
ln -s /home/user/path/to/shared shared
```

At that point, you can go to localhost/shared and see for yourself whatever you put in that folder.

---

### Post by cariboo on 2013-09-03
Personally I just create the file in my home directory, then use:

```
sudo mv <file_name> /var/www/
```

and change the ownership to root:

```
sudo chown root:root <file_name>
```

---

### Post by nativehound on 2013-09-03
```
sudo usermod -a -G www-data putusernamehere
```

need more info

```
man usermod
```

---

