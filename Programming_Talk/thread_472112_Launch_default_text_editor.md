---
title: "Launch default text editor"
date: 2007-06-12
forum: Programming Talk
---

### Post by drlock on 2007-06-12
I am writing a BASH script that needs to run on multiple machines.  In the script I would like to be able to open a file using the systems default text editor.  For Ubuntu that would be gedit, for XUbuntu that would be mousepad, I don't know what KUbuntu uses.

I could check to see if each one is installed, but Ubuntu already has a default editor setting.  How do I access that information and launch whatever the default editor is?

Thanks

---

### Post by merinda on 2007-06-26
For gnome desktop, you can check /etc/gnome/defaults.list to find default text editor.

---

### Post by Ramses de Norre on 2007-06-26
> **merinda said:**
> For gnome desktop, you can check /etc/gnome/defaults.list to find default text editor.

He's asking how to generally find the default text editor, if he'd now he was on gnome he'd just use gedit...

I don't know a specific answer though, I'd go with the EDITOR env variable if I were you but many people don't set it by themselves.

---

### Post by cwaldbieser on 2007-06-26
> **Ramses de Norre said:**
> He's asking how to generally find the default text editor, if he'd now he was on gnome he'd just use gedit...

I don't know a specific answer though, I'd go with the EDITOR env variable if I were you but many people don't set it by themselves.

Don't a lot of applications check the VISUAL variable before EDITOR?

---

### Post by Ramses de Norre on 2007-06-27
> **cwaldbieser said:**
> Don't a lot of applications check the VISUAL variable before EDITOR?

No idea... VISUAL is unset here, I hadn't heard about it yet.

---

### Post by s1ightcrazed on 2007-06-27
Just launch xterm and pass pico as a command to it. :-)

xterm -e pico yourfile.txt

You think I'm kidding...... I'm not. :-)

---

### Post by Ramses de Norre on 2007-06-27
> **s1ightcrazed said:**
> Just launch xterm and pass pico as a command to it. :-)

xterm -e pico yourfile.txt

You think I'm kidding...... I'm not. :-)

I'd choose nano then, pico isn't installed by default in every distro while nano mostly is.

---

### Post by merinda on 2007-06-27
> **Ramses de Norre said:**
> He's asking how to generally find the default text editor, if he'd now he was on gnome he'd just use gedit...

I don't know a specific answer though, I'd go with the EDITOR env variable if I were you but many people don't set it by themselves.

There is always a possibility that gedit has been uninstalled by admin. You never know.

---

### Post by drlock on 2007-06-27
Thank you all.  Neither the EDITOR or VISUAL env. variables seem to be set on my computer (set | grep EDITOR returns nothing).  I suppose I could set them, but that kind of defeats the purpose of having it work on any Ubuntu flavor.

For now, I am using s1ightcrazed's suggestion coupled with the Debian Alternatives system:
```
/etc/alternatives/x-terminal-emulator -e /etc/alternatives/editor 
```

This does not give me a GUI editor, like I wanted, but it closer than what I had before.

Thanks again for your help.   I am still open to better options if any one finds one.

---

### Post by s1ightcrazed on 2007-06-27
As an FYI, here's the LONG way to do it. 

for i in gedit mousepad kedit; do
if [ $(which $i > /dev/null 2>&1)$? -eq 0 ]; then
MY_EDITOR=$i
fi
done

This will set MY_EDITOR to a value equal to the LAST valid editor in the for list

It's ugly, but it should work.

---

