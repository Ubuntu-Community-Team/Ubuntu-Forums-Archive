---
title: "Unable to remove vm.swappiness=10 from sudo nano /etc/sysctl.conf"
date: 2020-08-27
forum: New to Ubuntu
---

### Post by imon57 on 2020-08-27
I had changed swappiness value one week ago using vm.swappiness=10 in sudo nano /etc/sysctl.conf. But now I want to remove it and increase the value to 50. I have tried to remove it but unable to do it. Please help me to solve this issue.

---

### Post by T6&amp;sfpER35% on 2020-08-27
in terminal type
```
[COLOR=#000000][FONT=&amp]sudo sysctl vm.swappiness=50[/FONT][/COLOR]
```

then to check it changed ,type
```
[COLOR=#000000][FONT=&amp]cat /proc/sys/vm/swappiness[/FONT][/COLOR]
```
 but everytime you reboot it'll revert back to default value of 60

to set it permanently to 50 , in terminal type 
 ```
sudo su


```
```
gedit  /etc/sysctl.conf


```

an editor will open ,scroll to end and add [COLOR=#474B51][FONT=Tahoma]**vm.swappiness=50**
and save.

(if you dont have gedit,install it 
[/FONT][/COLOR]```
sudo apt install gedit
```

[FONT=Tahoma][COLOR=#474b51]not sure why you'd want to set it to 50,if the default is 60. not going to make much of a difference.[/COLOR][/FONT]

---

### Post by imon57 on 2020-08-28
@[[COLOR=#000000]3nd[/COLOR]]("https://ubuntuforums.org/member.php?u=2146576")
Thank you very much. These codes helped me to solve my problem.

---

### Post by ActionParsnip on 2020-08-28
Could have used vi / nano too. It's just a text file. Nothing fancy

---

### Post by poorguy on 2020-08-28
This is what I use scroll down to **Swappiness **

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by T6&amp;sfpER35% on 2020-08-28
> [COLOR=#000000]This is what I use scroll down to [/COLOR]**Swappiness**

yes that code actually looks easier , didn't know about it .
thanks!


to make swap permanent :

```
[COLOR=#000000][FONT=&amp]sudo sed -i '$ a\vm.swappiness = 10' /etc/sysctl.conf[/FONT][/COLOR]
```

replace 10 with whatever(or better yet,leave it at 10)

---

