---
title: "Vmware not starting."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-06
when i start my virtual machine its just closeing with the following in a winddow

```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

---

### Post by spiderbatdad on 2008-06-06
What command are you using to launch the VM? Have you tried launching it with admin.```
sudo vmware
```

---

### Post by rraj.be on 2008-06-06
i solved starting vmware.

But after starting when power on 


its displaying the erroe

```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

---

### Post by diablo75 on 2008-06-06
Open your Home Folder, hit CTRL-H to reveal hidden folders, find the ".vmware" folder, Right-Click and hit Properties, and then change the owner (in the permissions tab) to yourself and make sure you have read-write access to the folder and all subfolders (there's a checkbox to make the change recursive to all sub folders and files).

---

### Post by spiderbatdad on 2008-06-06
It sounds like you are not running vmware as admin...like the error is the result of some permissions issue.

Possible solutions:
1. run vmware with sudo
2. check permissions and ownership of /home/username/.vmware. You may have to chown that directory.```
sudo chown -R you:you /home/you/.vmware
```

---

### Post by rraj.be on 2008-06-06
I tried all the ideas provided by you.

But the error remains the same without a single change.

Plz any other ideas

---

### Post by diablo75 on 2008-06-06
> **rraj.be said:**
> I tried all the ideas provided by you.

But the error remains the same without a single change.

Plz any other ideas

When you tried the suggested code that spiderbatdad posted (the chown command), what exactly did you type into terminal?  I just want to make sure you didn't type it exactly as he typed it, because your user name is not "you".  You have to replace the word "you" with whatever your username is.  For example, if my username on my computer was diablo75, I'd type:

```
sudo chown -R diablo75:diablo75 /home/diablo75/.vmware
```

I could even type this:

```
sudo chown -R diablo75:diablo75 ~/.vmware
```

---

### Post by rraj.be on 2008-06-06
:):)

I changed it .

sudo chown -R raj:raj /home/raj/.vmware



this is what i typed.

---

### Post by diablo75 on 2008-06-06
If that didn't work, you might try starting over by uninstalling VMware, then re-install.  Type this in terminal:

```
sudo vmware-uninstall.pl
```

It will not delete any virtual machines you have created, but after re-installing, you'll have to add your existing machine back into VMware's inventory.

Follow this guide to reinstall:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by rraj.be on 2008-06-06
Already i reinstalled vmware two hours ago.



```
raj@raj-workstation:~$ sudo vmware-uninstall.pl
[sudo] password for raj: 
sudo: vmware-uninstall.pl: command not found
raj@raj-workstation:~$ 

```

---

