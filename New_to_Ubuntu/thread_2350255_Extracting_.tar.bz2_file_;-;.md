---
title: "Extracting .tar.bz2 file ;-;"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by spurkl3z on 2017-01-22
hai, 

so i'm like a week-old Xubuntu user and i'm beginning to dislike the default theme, so i've been searching for a nice theme and came to Rele. 
thing is, i do not entirely know how to extract the file of this theme to my /usr/share/themes folder. this dir needs root/superuser, and i thought sudo command would work

the theme 77260-rele-xfce4.tar.bz2 is in my downloads folder. i heard you need to put x for extracting, specify the file, give the directory. with a little help from a friend and a ****** guide i came to this command: 

sudo tar -xj 'home/user/Downloads/77260-rele-xfce4.tar.bz2' -o '/usr/share/themes' 

well this is all i can do as of now. please help me use root/su to extract the theme file into the themes folder so i can use it? much thanks already! 
and btw, if you know of or can recommend of a simple theme tool for Xubuntu 16.04 that i can use to set certain themes for the buttons and layers etc, please do tell me ! would help a lot apparently, i just hear about the need

greets, Spurkl3z

---

### Post by &amp;KyT$0P# on 2017-01-23
The easy way is to just extract it "normally" (right-click > Extract Here), then use a [FONT=Courier New]sudo cp[/FONT] command to copy the result to [FONT=Courier New]/usr/share/themes[/FONT].

For example -
```
sudo cp -vR ~/Downloads/77260-rele-xfce4 /usr/share/themes
```

---

### Post by Yellow Pasque on 2017-01-23
Put it in ~/.themes (unless you have multiple users on the system that want the theme).

---

### Post by &amp;KyT$0P# on 2017-01-23
> **Temüjin said:**
> Put it in ~/.themes 
Nope, then it won't theme applications run as root (e.g. Synaptic package manager) and so they'll look weird and out-of-place.

---

### Post by Yellow Pasque on 2017-01-23
^Thanks. I was wondering why Synaptic wouldn't respect my theme.

---

### Post by spurkl3z on 2017-01-23
thanks! the copying worked. 
though no the theme doesn't appear in the Appearance program and i can't set it ? could you pls help me fix this lol

---

### Post by Impavidus on 2017-01-23
> **halogen2 said:**
> Nope, then it won't theme applications run as root (e.g. Synaptic package manager) and so they'll look weird and out-of-place.

Actually, that may be just what you want. It will remind you it runs with root privileges.

---

### Post by steeldriver on 2017-01-23
Your friend got the letter option wrong - it is 

```

     -C, --directory DIR
           change to directory DIR

```

e.g.

```

sudo tar -xf /home/user/Downloads/77260-rele-xfce4.tar.bz2 -C /usr/share/themes/

```

---

### Post by &amp;KyT$0P# on 2017-01-23
> **spurkl3z said:**
> though no the theme doesn't appear in the Appearance program and i can't set it ? could you pls help me fix this lol
Can you please post the link where you downloaded this tar.bz2?

---

