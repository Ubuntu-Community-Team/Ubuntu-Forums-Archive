---
title: "[SOLVED] get rid of all file permissions?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by hammer v2 on 2008-09-03
How do I get rid of ALL permissions on a file? I want it to be accessible to everybody on on any computer anywhere and I want them to be able to do whatever they want with it? 

The file was created under sudo su.

Help?

---

### Post by jemate18 on 2008-09-03
> **hammer v2 said:**
> How do I get rid of ALL permissions on a file? I want it to be accessible to everybody on on any computer anywhere and I want them to be able to do whatever they want with it? 

The file was created under sudo su.

Help?

```
sudo chmod 777 [file]
```

---

### Post by iaculallad on 2008-09-03
> **hammer v2 said:**
> How do I get rid of ALL permissions on a file? I want it to be accessible to everybody on on any computer anywhere and I want them to be able to do whatever they want with it? 

The file was created under sudo su.

Help?

```
chmod ugo+rwx filename
```

or

```
sudo chmod ugo+rwx filename
```

---

### Post by Tatty on 2008-09-03
Or if you want to do it the graphical way, type:
```
gksu nautilus
```
This will bring up a file browser with root permissions.  You can then locate the file, right-click on it and select properties.  Then you can edit the permissions from there.

Make sure you close the file browser window afterwards though - you dont want to leave root privilages open unessesarily.

---

### Post by hammer v2 on 2008-09-03
Woah thanks guys! I need it done in terminal, this is for a special (horribly programmed) BASH script that will be delivered over the internet to other ubuntu users (that's the idea anyways).

so er wehich one is it?

chmod 777 or chmod ugo+rwx ?

Will they both do the same job? 

Thanks so much for your help guys!

---

### Post by jemate18 on 2008-09-04
> **hammer v2 said:**
> Woah thanks guys! I need it done in terminal, this is for a special (horribly programmed) BASH script that will be delivered over the internet to other ubuntu users (that's the idea anyways).

so er wehich one is it?

chmod 777 or chmod ugo+rwx ?

Will they both do the same job? 

Thanks so much for your help guys!

Yup it will.... I prefer 777 because it is shorter than the ugo+rwx

777 is the octal permission for u=rwx g = rwx o=rwx

---

### Post by Corrupt3d on 2008-09-04
> **hammer v2 said:**
> Woah thanks guys! I need it done in terminal, this is for a special (horribly programmed) BASH script that will be delivered over the internet to other ubuntu users (that's the idea anyways).

so er wehich one is it?

chmod 777 or chmod ugo+rwx ?

Will they both do the same job? 

Thanks so much for your help guys!

They both do the same,
ugo+rwx ---> u=user, g=group, o=other, r=read, w=write, x=execute
or you can convert it to numbers,

-rwx rwx rwx
-111 111 111

2^2+2^1+2^0 = 4+2+1 = 7 ----> 777

Heres a website, if you want to learn more: [http://catcode.com/teachmod/numeric.html](http://catcode.com/teachmod/numeric.html)

---

### Post by hammer v2 on 2008-09-04
that's great! That's for the explanations. I'll remember that. 

One last thing, in my script in the beginning of the script I invoke sudo -su to do some dpkg stuff (that was the only way I could get it to work) how do I get out of super user mode and back to normal user in the terminal?

---

### Post by jemate18 on 2008-09-04
> **hammer v2 said:**
> that's great! That's for the explanations. I'll remember that. 

One last thing, in my script in the beginning of the script I invoke sudo -su to do some dpkg stuff (that was the only way I could get it to work) how do I get out of super user mode and back to normal user in the terminal?

type 
```
exit
```
Please mark this thread SOLVED and THANK the useful Posts

---

### Post by hammer v2 on 2008-09-04
brilliant. tanks so much! It all works great now.

---

### Post by iaculallad on 2008-09-04
Use whatever you are comfortable with, it's your choice of preference either to use:

> **chmod 777 filename**

or 

> **chmod a+rwx filename** = **chmod ugo+rwx filename**

Commands above perform the same action.

---

### Post by jemate18 on 2008-09-04
> **hammer v2 said:**
> brilliant. tanks so much! It all works great now.

PLease mark this THREAD AS SOLVED so that other users may see that the solutions given to this works.... Dont forget to THANK all the useful POST by click the small medal icon on the lower right part of the post.... This will allow users who read this thread on which reply was useful........

---

