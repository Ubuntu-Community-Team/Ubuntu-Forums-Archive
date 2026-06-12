---
title: "How to use sed?"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by vperaino on 2013-09-03
Please move this thread if it is in the wrong section. 

I would appreciate if someone would give me a very quick explanation as to how I can use the "sed" command to modify the line of a file (I'm assuming that sed is the easiest way to do this). I have to do a lot of reformatting/reinstalling of Linux systems and having to manually enter in a lot of information is very tiresome. 

For example, we use Google DNS here at my office, so every time I set up a system I have to change a line in /etc/dhcp/dhclient.conf from:

```

#prepend domain-name-servers 127.0.0.1;
```

To:

```

prepend domain-name-servers 8.8.8.8, 8.8.4.4;
```

To be able to do this without having to nano in would be very convenient, as well as a host of other things.

---

### Post by Frogs Hair on 2013-09-03
There is man page for sed , but don't know if it is what you are looking for. ```
man sed
```

---

### Post by prodigy_ on 2013-09-03
```
sed -i -e 's/#prepend domain-name-servers 127\.0\.0\.1;/prepend domain-name-servers 8.8.8.8, 8.8.4.4;/' /etc/dhcp/dhclient.conf
```

[Sed tutorial](http://www.grymoire.com/Unix/Sed.html#uh-0)

---

### Post by vperaino on 2013-09-03
> **Frogs Hair said:**
> There is man page for sed , but don't know if it is what you are looking for. ```
man sed
```

The manual is very dry and not very intuitive for someone who is just barely getting into the concept of scripting, like me. :( 

> **prodigy_ said:**
> ```
sed -i -e 's/#prepend domain-name-servers 127\.0\.0\.1;/prepend domain-name-servers 8.8.8.8, 8.8.4.4;/' /etc/dhcp/dhclient.conf
```

[Sed tutorial]("http://www.grymoire.com/Unix/Sed.html#uh-0")

Thank you! 

Off hand, do you know if sed allows you to replace things by line number, instead of having to specify the exact text to search?

---

### Post by Vaphell on 2013-09-03
yes

```
$ echo "1 abc
2 def
3 ghi" | sed '[COLOR="#0000FF"]2[/COLOR] s/.*/xxx/'  # 2 = 2nd line
1 abc
xxx
3 ghi

$ echo "1 abc
2 def
3 ghi" | sed '[COLOR="#0000FF"]/def/[/COLOR] s/.*/xxx/' # /def/ = lines matching 'def' regex
1 abc
xxx
3 ghi
```

---

### Post by prodigy_ on 2013-09-03
Yes, you can specify line number:
```
sed -i -e '20s/.*/prepend domain-name-servers 8.8.8.8, 8.8.4.4;/' /etc/dhcp/dhclient.conf
```

---

### Post by SeijiSensei on 2013-09-03
> **vperaino said:**
> For example, we use Google DNS here at my office, so every time I set up a system I have to change a line in /etc/dhcp/dhclient.conf

That problem is more easily solved by fixing the DHCP server so it gives out the Google DNS addresses automatically.

---

### Post by vperaino on 2013-09-03
Thanks a lot, guys! :)

---

### Post by vperaino on 2013-09-03
> **SeijiSensei said:**
> That problem is more easily solved by fixing the DHCP server so it gives out the Google DNS addresses automatically.

True, but I don't think I have the authority to tinker with it.

---

### Post by BrunoLotse on 2013-09-03
Hi, in re manual try also this```
info sed
```I installed info2www to read info pages.Cheers,Bruno

---

