---
title: "Can't Open Package Manager in Ubuntu 11.04 version"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by warfreak92 on 2011-12-29
[SIZE=4]Uhmmm, guys, a little help here please... 
I am just a beginner in this site and also a novice programmer. I've been encountering this problem in my Ubuntu Linux 11.04 version. Everytime I open my Package manager, this error code message appears:[/SIZE] 	  [SIZE=4]Could not initialize the package information [/SIZE]
  
 [SIZE=4]An unresolvable problem occurred while initializing the package information. [/SIZE]
  
 [SIZE=4]Please report this bug against the 'update-manager' package and include the following error message: [/SIZE]
  
 [SIZE=4]'E:Type 'multiverse' is not known on line 8 in source list /etc/apt/sources.list'[/SIZE]




[SIZE=4]Could somebody please help me in this problem, I'll be very glad to hear it from you either in this forum or via my email [email]ralph_andalis@yahoo.com.ph[/email][/SIZE]


[SIZE=4]Your help would be well appreciated! Good day!
[/SIZE]

---

### Post by wildmanne39 on 2011-12-29
Hi, welcome to the forum! please use normal fonts and post the results of:
```
cat /etc/apt/sources.list
```
is that the only error message you get when you run:
```
sudo apt-get update
```
click on new reply and click # and paste the information between the brackets.

Thanks

---

