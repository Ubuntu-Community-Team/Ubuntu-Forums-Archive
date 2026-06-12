---
title: "Chrubuntu and Wine on Acer C7 Chromebook"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by stevenbunting on 2013-10-15
Hello All,
   I am absolutely new to anything non windows based so please bear with me.  My son had an Acer C7 Chromebook bought for him and he cant play any of his windows based games etc that he is used to or things like minecraft.  I have managed to install chrubuntu onto his chromebook and that seems to be working fairly ok and he can play minecraft.  However i have tried to install wine so he can play other things but it wont work.  
When i do it from the terminal i cant get the APt Update thing working and when i try and do it from the software centre i get "failed to download repository information?"

Can anyone help?

---

### Post by stevenbunting on 2013-10-15
It says E The method driver /usr/lib/apt/methods/https could not be found

---

### Post by Gabriele_Magi on 2013-10-15
Hello...

I have found this on Google, maybe it can help you :)

[http://askubuntu.com/questions/104160/method-driver-usr-lib-apt-methods-https-could-not-be-found-update-error](http://askubuntu.com/questions/104160/method-driver-usr-lib-apt-methods-https-could-not-be-found-update-error)

---

### Post by stevenbunting on 2013-10-15
Thank You, I did that and got E: Unable to locate package-apt-transport-https

---

### Post by Gabriele_Magi on 2013-10-15
I think it is a problem with your sources list.

Did you try to run ```
sudo apt-get update
``` before installing?
It should give you more info on the error.

Anyway, here it is someone with a trouble similar to yours:
[http://superuser.com/questions/602287/trouble-with-subversion-cntlm-sources-list](http://superuser.com/questions/602287/trouble-with-subversion-cntlm-sources-list)

---

### Post by stevenbunting on 2013-10-15
[COLOR=#000000]When  i try and run [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update i get [/FONT][/COLOR][COLOR=#000000] E: Unable to locate package-apt-transport-https[/COLOR]

---

### Post by Gabriele_Magi on 2013-10-15
Check your sources list and see if you get any error:
```
cat /etc/apt/sources.list
```

To edit the list:
```
sudo gedit /etc/apt/sources.list
```

You could also try to check synaptic package manager. Go to Preferences-Repositories and
check your sources.
Also, check on Status and then on Not installed (residual configuration).

By the way, have you considered installing VirtualBox? Personally I prefer to use it
instead of Wine, it's a lot easier...

---

