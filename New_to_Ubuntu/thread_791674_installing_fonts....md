---
title: "installing fonts..."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-12
i came across a lot of things..
but which is the standard-proper way to install them?

---

### Post by oedha on 2008-05-12
you may believe me or not.....
i just copy the font file ( *.ttf ) to /usr/share/fonts
and reload openoffice.....walah..new fonts appears...

if you need windows fonts.....in terminal :==> sudo apt-get install msttcorefonts
CMIIW :)

---

### Post by Kapitän Rotbart on 2008-05-12
Or get your Windows fonts from the "ubuntu-restricted-extras" package.

To install fonts in Ubuntu, put them all in a folder (for instance on the desktop in a folder called myfonts), then in the terminal:
```
sudo su
cp -a '~/Desktop/myfonts' '/usr/share/fonts/truetype/'

```
to copy the fonts to the Fonts directory on the file system. (Alternatively, open nautilus as root doing Alt+F2 then type gksudo nautilus and go to /usr/share/fonts/, then do some drag and drop).
To refresh the fonts, in the terminal use the command:
```
fc-cache -f -v
```

Enjoi!:KS

---

### Post by lunaluna on 2008-05-12
its not the m$ fonts by the way...

---

### Post by lunaluna on 2008-05-12
so i go /usr/share/fonts
and i just create a new folder and put them in?

---

### Post by oedha on 2008-05-12
yup...that's what i did when i installed dustismo :)

---

### Post by ataraxia on 2008-05-12
I came across a weird problem. I'm unable to create folders or copy/paste anything in usr/share/fonts

any ideas?

---

### Post by lunaluna on 2008-05-12
> **ataraxia said:**
> I came across a weird problem. I'm unable to create folders or copy/paste anything in usr/share/fonts

any ideas?

sudo nautilus 
and then.. try again

---

### Post by lunaluna on 2008-05-14
some fonts i downloaded include a readme file noting that this fonts were e-mailware
what is this?

---

### Post by SunnyRabbiera on 2008-05-14
> **lunaluna said:**
> some fonts i downloaded include a readme file noting that this fonts were e-mailware
what is this?

well dont use them, even though they will probably not harm your system it might be best to be rid of those said fonts.

---

### Post by dizee on 2008-05-14
If you just want the fonts to be used by your user, you can make a folder called .fonts in your home directory and put them in there.

---

### Post by Perfect Storm on 2008-05-14
> **dizee said:**
> If you just want the fonts to be used by your user, you can make a folder called .fonts in your home directory and put them in there.

+1

and it's safer to do so, I wouldn't recommend installing 100s of fonts into the system. Do what dizee suggested.

---

### Post by lunaluna on 2008-05-14
> **SunnyRabbiera said:**
> well dont use them, even though they will probably not harm your system it might be best to be rid of those said fonts.

ok but what are they?

---

### Post by HotShotDJ on 2008-05-14
> **dizee said:**
> If you just want the fonts to be used by your user, you can make a folder called .fonts in your home directory and put them in there.+1
~/.fonts is the best way to go.

---

