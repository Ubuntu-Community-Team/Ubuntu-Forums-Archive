---
title: "gnome-shell problems"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shoot2kill on 2011-09-25
Hi, I have installed gnome-shell on top of Ubuntu 11.10 using
```
sudo apt-get install gnome-shell
```

I have also installed the gnome-tweak-tool.

My window titlebar and borders are not displaying correctly, and when I tried to use tweak tool to solve this, I got this problem and don't know how to overcome it. The image shows the state of the titlebars too.

[img]http://i.imgur.com/PRpN2.png[/img]

any help greatly appreciated

Thanks

---

### Post by kuvanito on 2011-09-25
sorry! can't help you but since the title of your post says gnome-shell problems,i have a problem too! isn't it funny...
how do i keep gnome as my default login when i reboot?
i can't have it on auto login or it will bring the unity shell,i must select it at login....
i like gnome shell better than unity :p :p :p

---

### Post by tista on 2011-09-25
Guys,

That's dup and already posted in other thread...
See it:
[http://ubuntuforums.org/showthread.php?t=1848516]("http://ubuntuforums.org/showthread.php?t=1848516")

cheers.

@kuvanito,

Check your /etc/lightdm/lightdm.conf out...
If you wanna do "automatic login" with gnome-shell, set it like this:
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=gnome-shell
autologin-user=YOUR_ACCOUNT_NAME
```

---

### Post by rbrick49 on 2011-09-25
are you using fglrx if so it has a bug that causes problems with gnome-shell title bar

---

### Post by shoot2kill on 2011-09-25
Thanks to thee link to the other thread, and a link from that thread, i managed to get it working fine.

I installed the ricotz PPA, and re-installed gnome-shell

```

sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install gnome-shell gnome-shell-extensions-user-theme

```

---

### Post by jbicha on 2011-09-25
The window border problem should be fixed with next mutter upload. See [bug 800315]("http://pad.lv/800315").

---

