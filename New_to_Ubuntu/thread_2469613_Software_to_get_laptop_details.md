---
title: "Software to get laptop details"
date: 2021-12-03
forum: New to Ubuntu
---

### Post by fifii69 on 2021-12-03
Hi all , I am looking for software for ubuntu which can display hardware information, procesr type speed, ram hdd etc. And want to save this details to csv format excel format. I know hardinfo but do you know any others programs?

---

### Post by GhX6GZMB on 2021-12-03
lshw

---

### Post by tea for one on 2021-12-04
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

[COLOR="#0000FF"]inxi[/COLOR] available via Universe repository

Edit: Probably a bit fiddly to save in a spreadsheet format

---

### Post by T6&amp;sfpER35% on 2021-12-04
**stacer**

don't know about saving to csv format with it though...

---

### Post by ActionParsnip on 2021-12-04
sudo lshw > /tmp/output.csv

---

### Post by ajgreeny on 2021-12-04
Is there are reason for needing a csv file of the output, as having just done it that way for the first time ever, I find it almost unreadable and useless.

I would suggest you use html output and open it in your web-browser; it's much more readable.
```
sudo lshw -html > /home/$USER/hardware.html
```
then double click the hardware.html file in your homr.

---

### Post by kc1di on 2021-12-04
install inxi ```
sudo apt install inxi
```
It's a teminal tool that can analyze your sysetem and tell you just about anything you need to know. 
More info here: [https://www.tecmint.com/inxi-command-to-find-linux-system-information/]("https://www.tecmint.com/inxi-command-to-find-linux-system-information/")

---

### Post by fifii69 on 2021-12-06
Hi all , thanks for very helpfull info, still not perfect because can't save in excel csv format but should be ok for me this command looks ok: 
sudo lshw -html > /home/$USER/hardware.html

I got many laptops and I have to get details from them, is it possible to run this command automaticly from startup when linux loading and automaticly save to file for example "hardware1" then i want to run this on second laptop and auto save to file for example "hardware2" next laptop "hardware3"etc. ??

---

