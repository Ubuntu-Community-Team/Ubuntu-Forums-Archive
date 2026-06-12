---
title: "Install issues"
date: 2018-07-27
forum: New to Ubuntu
---

### Post by holdingfire20 on 2018-07-27
[COLOR=#6E6E6E][FONT=Helvetica]Cách tr&#7883; m&#7909;n b&#7857;ng công ngh&#7879; cao [/FONT][/COLOR]
[http://trietlong.net/tri-mun](http://trietlong.net/tri-mun)[COLOR=#6E6E6E][FONT=Helvetica]/[/FONT][/COLOR]
[COLOR=#6E6E6E][FONT=Helvetica]N&#7857;m t&#7841;i v&#7883; trí Top 1 c&#7911;a các cách tr&#7883; m&#7909;n hi&#7879;u qu&#7843;, tr&#7883; m&#7909;n b&#7857;ng công ngh&#7879; cao luôn là ph&#432;&#417;ng pháp &#273;&#432;&#7907;c nhi&#7873;u ng&#432;&#7901;i tin t&#432;&#7903;ng và s&#7917; d&#7909;ng. Trong &#273;ó, theo &#273;ánh giá c&#7911;a các chuyên gia, m&#7897;t trong nh&#7919;ng công ngh&#7879; tr&#7883; m&#7909;n nhanh nh&#7845;t, an toàn và hi&#7879;u qu&#7843; cao &#273;ó là Acne Remove.[/FONT][/COLOR]
[Tr&#7883; thâm môi]("http://trietlong.net/tri-tham-moi/")
[COLOR=#6E6E6E][FONT=Helvetica]Acne Remove v&#7899;i c&#417; ch&#7871; ho&#7841;t &#273;&#7897;ng thông minh, &#7913;ng d&#7909;ng n&#259;ng l&#432;&#7907;ng ánh sáng quang h&#7885;c, tia Laser hay các tinh ch&#7845;t th&#7849;m th&#7845;u sâu vào bên trong t&#7871; bào da &#273;&#7875; phá v&#7905; c&#7891;i nhân m&#7909;n, tri&#7879;t tiêu nguyên nhân gây m&#7909;n, các công ngh&#7879; tr&#7883; m&#7909;n mang l&#7841;i hi&#7879;u qu&#7843; cao &#273;&#7891;ng th&#7901;i rút ng&#7855;n li&#7879;u trình cho khách hàng.[/FONT][/COLOR]
[http://trietlong.net/xoa-nep-nhan](http://trietlong.net/xoa-nep-nhan)[COLOR=#6E6E6E][FONT=Helvetica]/[/FONT][/COLOR]

---

### Post by bodhin2 on 2018-07-27
hate to say anything around here because i always seem to get in the dog house.  but pick a drive and do the write over everything and do the simple install.  also do 18.04.1  the newest.  hope this helps.

---

### Post by Taylz on 2018-07-29
I agree with bodhin2.

Why do you feel the need to configure manual partitions instead of using the default standard install/auto partitioning? It doesn't really make any difference for general use and the install menu for the latest LTS release (18.04.1 is fairly simple and easy to follow).

Gnome's a desktop environment. These are specifically down to personal preference. Gnome is one of the most commonly used interfaces. You have KDE which is very candified with pretty icons and colours/themes but can be extremely laggy (from my personal experience) due to all the graphics it uses.

Grubs a boot loader. Don't really need to mess with this unless running various versions/installs/operation systems?

If, like me, you like the minimalist desktop looks I actually downloaded and installed "xubuntu". Offers quite a nice simplistic feel to Ubuntu (using the XFCE interface) and seems very quick due to not having such heavy graphics on the icons and such!

Regards,

Tayl.

---

### Post by oldfred on 2018-07-29
Partitioning is very personal. Everyone has different preferences.
Very new user should just use / (root) or default install.
the 18.04.1 installer uses a swap file, so even a swap partition is not required.

If you installed with full drive encryption, you had to use the very advanced LVM - logical volume system. Unless you absolutely have to have encryption better to start with standard partitions. LVM may have some advantages, often used with servers, but does not use standard partitioning tools like gparted, but LVM tools.

Bit more advanced and requiring Something Else install option is separating operating system from data. User that has some idea of partitions can use / (root) and /home. Typically root only needs to be 25GB or so, and /home rest of space desired for Ubuntu. 

Even more advanced is separate /mnt/data partition. More often used with multiple installs of Ubuntu so you can have same data in all installs, where multiple installs should not share /home.

Ubuntu has its Software manager, but I prefer installing synaptic. You do not get pretty graphics, but do get more detail and exact names of packages you may want to install.
sudo apt install synaptic

---

### Post by Taylz on 2018-07-30
> **oldfred said:**
> 
Ubuntu has its Software manager, but I prefer installing synaptic. You do not get pretty graphics, but do get more detail and exact names of packages you may want to install.
sudo apt install synaptic

Nice one for that, thank you. Just installed that myself and it's a lot more useful than the standard software manager. As you say, you get more detail and see exact packages!

Regards,

Tayl.

---

