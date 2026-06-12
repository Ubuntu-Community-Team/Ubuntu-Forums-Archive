---
title: "Enabling Hyper Threading"
date: 2006-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by nw15062 on 2006-04-05
[CENTER][CENTER][FONT="Arial Black"][SIZE="3"]**How To: Enable Hyper Threading**[/SIZE][/FONT][/CENTER]
[SIZE="1"][COLOR="DarkRed"][CENTER]
Hyper Threading by Default is disabled in Ubuntu Linux the ability is in the kernel but is not turned, The reason for this is due to a potential vulnerablity that would allow one thread to veiw another and access cyrptographic data such as passwords.

By enabling ti you do so at your own risk.[/CENTER][/COLOR][/SIZE]

The first step is to make sure you have the best kernel suited for your system, I suggest installing the 686 kernel and make sure you have all the headers.

The second step require you to drop to a command prompt and type 
[CENTER]"*sudo gedit /boot/grub/menu.lst*"[/CENTER]

Look for the line that says 
[CENTER]"*# kopt=root=/dev/hdb2 ro*"[/CENTER]
Leaving everything intact includign the pound symbol simply add
[CENTER] "**ht=on**"[/CENTER]
You should now have this
[CENTER] "*# kopt=root=/dev/hdb2 ro ht=on*"[/CENTER]

Save then file and run the command
[CENTER] "* sudo update-grub*"[/CENTER]

When you restart the system you should see a noticable diffrence in performance.[/CENTER]

---

### Post by testube_babies on 2006-04-07
How do I know if I have all the headers (whatever that means)?  I'm running dapper and the 686 kernel was install via apt-get upgrade.  I would really like to get the most out of my processor.

---

### Post by mozetti on 2006-04-07
Does this mean I don't need to install the 686-smp kernel on my P4 chip with HyperThreading?

--In my post [here](http://ubuntuforums.org/showthread.php?t=155950) I give details about my kernel upgrade and the resulting non-booting goodness the 686-smp kernel gives to me.

Also, forgive me if I'm in error, but I thought the pound signs (#) meant that the line was a comment. So, if the line you're editing is a comment, how does it effect how the kernel is booted?

---

### Post by Thiago on 2006-04-07
if i add in this line:

```

title		Ubuntu, kernel 2.6.12-10-386 
...
kernel		/boot/vmlinuz-2.6.12-10-386 ... *ht=on*

```

would work?

---

### Post by Rikostan on 2006-04-07
[QUOTE=mozetti]
Also, forgive me if I'm in error, but I thought the pound signs (#) meant that the line was a comment. So, if the line you're editing is a comment, how does it effect how the kernel is booted?[/QUOTE]

In most cases you would be right, but in the menu.lst file under automagics it reads "DO NOT UNCOMMENT THEM, Just edit them to your needs", so I took that to mean you do not remove the single # from the kopt line.

---

