---
title: "[SOLVED] Frequest host file modification"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-29
Me and my coworkers have a problem.  We're web developers. Three machines: development, maintenance, and live.  Each time we want to test code on one of them, we have to point the domains for the project to the appropriate machine (development->maintenance->live is the flow) in the hosts file.

Example:

```

## DEVELOPMENT ENVIRONMENT ######
127.0.0.1    blah.example.com
127.0.0.1    blah2.example.com

## MAINTENANCE ##################
#999.0.0.1    blah.example.com
#999.0.0.1    blah2.example.com

## LIVE #########################
#888.0.0.1    blah.example.com
#888.0.0.2    blah2.example.com

```

Obviously I made up the IPs and domains, but you get the idea. To switch, we uncomment the ones we want, and comment out the old ones.

I was wondering if there might be a more automated/easy way of doing this, as it is something we do (very) often.  Of concern is that, while in the development environment there is usually only one IP, the others can have many for the various sub-domains (especially live servers), and there are often many more domains associated with a project (upwards of 20).

Also of concern is that we need to be able to keep separate entries for each project, so, for example, we can have the domains pointing to the development server for project A, but the live servers for project B, so we can't just swap out the entire host file (well, we could, but it doesn't seem very graceful).

Any ideas?

---

### Post by Potatoj316 on 2008-07-29
might not be the best way but it is easy and works.

Create 3 files, call them hosts.live, hosts.maint. host.test and configure each of them to be the live, maintenence, and testing hosts files.  Now create a 3 scripts (or 1 that asks you which to use) that copies the correct one to host
ex (makelive.sh)
```
cp hosts.live hosts
```

---

### Post by caljohnsmith on 2008-07-29
You could write a short bash script that uses "zenity": it presents you with your three choices of "development", "maintenance", and "live", you click one (say "development" for example), and then the script just simply does a "sudo mv development.hosts /etc/hosts". That would replace your /etc/hosts file with the development.hosts file that you create which of course has the development lines uncommented.

Do you need more details, or do you see what I mean? Would be really easy. :)

---

### Post by Potatoj316 on 2008-07-29
thats exactly what I said, except that you want to use cp not mv.  mv will move the file thereby deleting it next time you mv a file on top of it.  cp will keep all 3 master files intact and just overwrite the one you want to change

---

### Post by Sydius on 2008-07-29
Ok, so if I want to use Zenity (I never have before), how do I capture the standard error string that it returns in a bash script so that I can use it to do an if/then thing to see which script to copy?

---

### Post by caljohnsmith on 2008-07-29
Here's the syntax, you can easily modify to suite your needs:
```
ans=$(zenity  --list  --title="Choose the Host File" --text "Choose the host file:" --radiolist  --column "" --column "Hosts" TRUE "Development" FALSE "Maintenance" FALSE "Live")
```
Run that at the CLI, and if you chose "Live" for example, then if you do "echo $ans" you will see it is "Live".

Then all you have to do is write a few if-then statements, and like Potatoj316 said, be sure to use "cp" not "mv" since that was my mistake--you want to replace the /etc/hosts while leaving the original files intact. :)

---

### Post by Sydius on 2008-07-29
Alright, I solved my problem with a simple script as suggested, and added it to my taskbar at the top.  Works nicely, and my coworkers are happy with it, too.  Thanks. :-)

---

