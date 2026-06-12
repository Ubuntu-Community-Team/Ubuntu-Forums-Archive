---
title: "FTP Server"
date: 2008-10-07
forum: Philippine Team
---

### Post by zanda on 2008-10-07
Hi, Guys :popcorn:

Again I just want to ask you Guys, from Desktop want to explore the server now :D,

So I'm asking for you suggestion/advice on what FTP Server to use on my Ubuntu Server Edition, So far I'm experimenting with proftpd, but had a problem with the web GUI proftpd-admin.

This is what i want to achieve
1. Easy to create user
2. Easy to create user home directory/with subfolder- ftpuser is                               locked to their home directory
3. Lastly, it must be accessible to windows network
 so i know i have to format it using fat32 :D

and by the way , Im using 2 hard drive, first drive for the system, 2nd drive probably the ftp users home directory


So any suggestion guys on what Do you think should I try, thanks and more power to you Guys

---

### Post by jsgotangco on 2008-10-07
SFTP or if you want, SCP

[http://en.wikipedia.org/wiki/SSH_file_transfer_protocol](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol)
[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

---

### Post by jerryheavyarms on 2008-10-08
Try mo po yung GProFTPD. Madali pong mag configure ng ProFTPD dyan. Yan po yung ginamit ko nung nagconfigure po ako ng FTP server sa office namin.:)

---

### Post by zanda on 2008-10-08
> **jsgotangco said:**
> SFTP or if you want, SCP

[http://en.wikipedia.org/wiki/SSH_file_transfer_protocol](http://en.wikipedia.org/wiki/SSH_file_transfer_protocol)
[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

Hi, jsgotangco

okay sana yung SCP, kaso sa client side bka mahirapan eh :D, so prefer lang talga yung FTP :D

---

### Post by zanda on 2008-10-08
> **jerryheavyarms said:**
> Try mo po yung GProFTPD. Madali pong mag configure ng ProFTPD dyan. Yan po yung ginamit ko nung nagconfigure po ako ng FTP server sa office namin.:)

Sir, correct me if im wrong, yung Gproftpd, is kailangan ng gui, tama ba ? so if ever kailangan ko mag install ng GUI for server, so medyo madadagan na yung load ng server ko kasi mag lo-load pa sya ng GUI, tama po ba or meron webbased Gproftpd :D

---

### Post by jerryheavyarms on 2008-10-09
Opo. GUI sya. Nung nag configure po kasi ako ng FTP server namin, nilagyan ko rin po ng GUI yung server. Tapos yung GProFTPD is Gui din. Newbie kasi, kaya ganun po yung ginawa ko. Kung gusto mo po ng web based, try installing WEbmin..

---

### Post by loell on 2008-10-09
GProFTPD is only for configuration purposes, so ok lang yun, after the configuration just exit it, then run proftp deamon on the backgound. you can even exit from X if you just want the console.

---

### Post by zanda on 2008-10-09
> **loell said:**
> GProFTPD is only for configuration purposes, so ok lang yun, after the configuration just exit it, then run proftp deamon on the backgound. you can even exit from X if you just want the console.


Sir, ask ko lang po, pano mag exit sa gui ng server, kasi pag start is = "startX" tama po ba ?

---

### Post by loell on 2008-10-09
> **zanda said:**
> Sir, ask ko lang po, pano mag exit sa gui ng server, kasi pag start is = "startX" tama po ba ?

yep, tama po yun.

normally, to exit

alt + ctrl + backspace

pero kung sa gnome, ano nga ba yun? teka lang..

---

### Post by zanda on 2008-10-10
> **loell said:**
> yep, tama po yun.

normally, to exit

alt + ctrl + backspace

pero kung sa gnome, ano nga ba yun? teka lang..


hehehe , sige sir update mo ko ha pag alam mo na yung cmd ha, kahit ako still googling it :D, kasi so far yan na lang ang kailangan ko para pag start ng server ko, wag agad tumuloy sa GUI :D

Update lang pla sa inyo Guys, working na ang first ever FTP Server ko , using Ubuntu Server, Proftpd, configure it without GUI :D, CLI lang talga and enjoy ,

---

### Post by loell on 2008-10-11
> **zanda said:**
> hehehe , sige sir update mo ko ha pag alam mo na yung cmd ha, kahit ako still googling it :D, kasi so far yan na lang ang kailangan ko para pag start ng server ko, wag agad tumuloy sa GUI :D

Update lang pla sa inyo Guys, working na ang first ever FTP Server ko , using Ubuntu Server, Proftpd, configure it without GUI :D, CLI lang talga and enjoy ,

hala, pasensya na at ako'y nakalimot. :oops:

ang command pala ay

```
sudo /etc/init.d/gdm stop
```

---

### Post by zanda on 2008-10-14
> **loell said:**
> hala, pasensya na at ako'y nakalimot. :oops:

ang command pala ay

```
sudo /etc/init.d/gdm stop
```

hehehe okay lang sir, :D,

---

