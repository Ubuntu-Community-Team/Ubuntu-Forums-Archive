---
title: "Default browser"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by cheatos on 2013-01-26
Hi all,

I have observed that if you install Firefox and chromium on lubuntu, chromium gets chosen by default of all my application, such as Thunderbird or pdf-viewer when I open a link directly.
How can I configure my system to open links in FF by default?

Thanks for any help!

---

### Post by jorok_tupur on 2013-01-26
Type this in terminal:

```
sudo update-alternatives --config x-www-browser
```From the list of options, choose Firefox' number, then press enter.

[See this thread on Stack Exchange]("http://askubuntu.com/questions/225700/stop-google-chrome-being-the-default-browser-in-lubuntu-12-04") for better example.

---

### Post by gifford on 2013-01-26
In 12.04 Ubuntu you can go to System settings, Details, and then Default applications. Just change chromium to firefox for your browser.

---

### Post by cheatos on 2013-01-29
So first of all, thanks for your advice.

I am running LXDE (Lubuntu) so I don't have the GNOME default-applications thin gifford mentioned.

However I tried jorok_tupurs advice but this didn't work either. Still my stuff gets opened in chromium :(

Does anybody have some other ideas?

---

### Post by cheatos on 2013-01-31
bumpitybump

---

### Post by monkeybrain2012 on 2013-01-31
Open the menu by clicking  the arrow like thingy on the leftmost end on the Lubuntu panel, then choose Preference > Preferred  Applications. A window will open, from which you can choose your default browser.

---

### Post by cheatos on 2013-02-02
Thanks alot, this fixed it!

---

