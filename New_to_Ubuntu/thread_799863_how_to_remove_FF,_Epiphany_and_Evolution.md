---
title: "how to remove FF, Epiphany and Evolution"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by beanco on 2008-05-19
I have been having problems with the three programs listed.

I want to remove them and then reinstlal them.

I tried it via synaptic it did not work. I really prefer the command line, though I do not know the commands... help me here folks.

thanks

robi

---

### Post by yogo on 2008-05-19
sudo apt-get --purge autoremove

will remove all configuration as well

---

### Post by stchman on 2008-05-19
> **beanco said:**
> I have been having problems with the three programs listed.

I want to remove them and then reinstlal them.

I tried it via synaptic it did not work. I really prefer the command line, though I do not know the commands... help me here folks.

thanks

robi

Try this.  I will assume hardy.

```

sudo apt-get -y autoremove firefox-3.0
sudo apt-get -y autoremove epiphany
sudo apt-get -y autoremove evolution

```

The autoremove removes all unused dependencies.

After that remove the residual config in synaptic.

---

### Post by beanco on 2008-05-20
sorry, i am on fiesty still....


robi

---

### Post by hyper_ch on 2008-05-20
the ```
-y
``` switch is not recommended when you do it for the first time as you will not be prompted about what will be removed in the end... use it with caution.

---

### Post by beanco on 2008-05-20
> **yogo said:**
> sudo apt-get --purge autoremove

will remove all configuration as well


yogo,

all the cinfigureation on this ubuntu box?

hyper_ch

what should I do then?

robi

---

### Post by hyper_ch on 2008-05-20
leave teh "-y" switch away... you will then be presented with what will be removed and you can then say yes or no.

---

### Post by beanco on 2008-05-21
> **stchman said:**
> Try this.  I will assume hardy.

```

sudo apt-get -y autoremove firefox-3.0
sudo apt-get -y autoremove epiphany
sudo apt-get -y autoremove evolution

```

The autoremove removes all unused dependencies.

After that remove the residual config in synaptic.


got htis```


rob@rob-desktop:~$ sudo apt-get - autoremove evolution
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get - autoremove firefox
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get - autoremove epiphany
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$
```

---

### Post by stchman on 2008-05-21
> **beanco said:**
> got htis```


rob@rob-desktop:~$ sudo apt-get - autoremove evolution
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get - autoremove firefox
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get - autoremove epiphany
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$
```

You are typing the wrong thing.  Do not type "- autoremove", type each of these in a terminal.

```
sudo apt-get autoremove evolution
```

```
sudo apt-get autoremove firefox
```

```
sudo apt-get autoremove epiphany
```

This is the same command except the removal of -y switch.

---

### Post by beanco on 2008-05-21
Yeah I left the - in when retyping the code... sorry,

but I tired it the way you suggest and got this


```
rob@rob-desktop:~$ sudo apt-get autoremove evolution
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get autoremove firefox
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ sudo apt-get autoremove epiphany
Reading package lists... Done
Segmentation fault (core dumped)
rob@rob-desktop:~$ 

```

I am on fiesty as I have said before, fi that makes any difference.

Aslo, while messing round I have managed to remove FF to some degree. at least the icon in the menubar is gone and in the applications/internet there is no FF....

robi

---

