---
title: "Grub2 in ubuntu . problem with the security."
date: 2014-02-04
forum: New to Ubuntu
---

### Post by Pituso on 2014-02-04
Hello.
Actually I had a problem with the security of my ubuntu.
I want to secure the boot with a password. 
Now I hab my hash password. The grub only can be edited by super user, but when I arrive to the last pass, in the manual puts that I have to look for the entri 
printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}" , but I don't have that line. in etc/grub.d/10_linux
where is the problem?
What line must I change?. There are others , but they begin with "echo" 

The Ubuntu is 13.10

thanks

---

### Post by kajoky on 2014-02-04
I would recommend making a copy of the files before editing them in case you need to restore the originals.  Also make a copy of **/boot/grub/grub.cfg**
Do you have a bootable USB or LiveCD? That would be nice too.

The lines you need to edit should be
```

echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"

```
try changing them to
```

echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} --users '' \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} --users '' \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"

```

---

### Post by Pituso on 2014-02-05
):Pthanks. I'll try it. .

---

### Post by Pituso on 2014-02-05
> **kajoky said:**
> I would recommend making a copy of the files before editing them in case you need to restore the originals.  Also make a copy of **/boot/grub/grub.cfg**
Do you have a bootable USB or LiveCD? That would be nice too.

The lines you need to edit should be
```

echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"

```
try changing them to
```

echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} --users '' \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} --users '' \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"

```

[HTML]<del>Excuse me. Don't run. I have changed the file with for example - - users alvaro''. I update the grub. It doesn't put any errors. 
Then, I reboot the system and it doesn't ask for by a username. The system shows the main screen for introduce any user in the system. 
Any idea? 
Thanks</del>[/HTML]

Thanks. Run fine. , only one thing. It work whiout '' . I have put --user name and run fine. 
Thanks again

---

### Post by kajoky on 2014-02-05
Did you also complete the edits for **/etc/grub.d/00_header** and **/etc/grub.d/30_os-prober**?
I performed the edits and now when I select an item from the grub menu, I am asked for a username and password.

---

### Post by Pituso on 2014-02-05
> **kajoky said:**
> Did you also complete the edits for **/etc/grub.d/00_header** and **/etc/grub.d/30_os-prober**?
I performed the edits and now when I select an item from the grub menu, I am asked for a username and password.

Thanks. 
I prefered to edit /etc/grub.d/40_custom. In that way I'm sure I won't lose my changes in a actualization

---

