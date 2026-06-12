---
title: "Odd error running apt-get upgrade"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-14
Hi all,

I was running apt-get upgrade, following apt-get update, and was just sitting back watching the output in terminal when I saw the following error:
```

Warning in file "/usr/share/applications/gnumeric.desktop":
usage of MIME type "zz-application/zz-winassoc-xls" is discouraged
("zz-application/zz-winassoc-xls" should be replaced with "application/vnd.ms-excel")

```

Im sorry but I don't understand this. Can someone please explain this message.

Thanks.

---

### Post by Senior_Buckethead on 2012-06-15
Bump

---

### Post by Senior_Buckethead on 2012-06-16
Bump

---

### Post by Shadius on 2012-06-16
Seems to be a bug...
[Gnumeric Bug]("https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/570836")

---

### Post by sudodus on 2012-06-16
I think you are recommended to edit the file [FONT="Courier New"]/usr/share/applications/gnumeric.desktop[/FONT] according to the tip. To do that I suggest that you make a copy of the file for example [FONT="Courier New"]/usr/share/applications/gnumeric.desktop.backup[/FONT] before you start editing, so that you can restore the present situation, if something would go wrong. Furthermore, I guess that the file must be edited with superuser privileges
```
sudo gedit /usr/share/applications/gnumeric.desktop
```

Just for comparison, I have the file
[FONT="Courier New"]~/.local/share/applications/gedit-usercreated.desktop[/FONT]
which contains the following text
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
NoDisplay=true
Name=gedit
Exec=/home/olle/pck/gedit %F
MimeType=text/plain
```

In this case the MimeType is [FONT="Courier New"]text/plain[/FONT] meaning that plain or text files should be opened with gedit when you [double]click on it in the file browser on in the desktop.

*Edit: While I was posting, [I]Shadius* gave us a better answer. (The system recommends that you edit that desktop file, but it's a bug. I hope you can solve your problem after reading the link to the Gnumeric Bug.)[/I]

---

