---
title: "cp - cannot create regular file : permission denied"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Serdar_Goksu on 2014-05-08
I want copy to /lib/udev but gives error
```
cp -f /tmp/ok_pcscd_hotplug.sh /lib/udev

cp:cannot create regular file /lib/udev/ok_pcscd_hotplug : Permission denied
```
i tried sudo cp , sudo cp -f etc.
I am root , but I can't understand . what can I do ?

---

### Post by papibe on 2014-05-08
Hi  Serdar_Goksu. Welcome to the forum ):P

The error you write is not consistent with the command you are running.

Could you run the command again and copy/paste the text from the terminal so we can better see what's going on?

Regards.

---

### Post by Serdar_Goksu on 2014-05-08
hi papibe , thanks 

> 
[FONT=Verdana]sudo - [/FONT]
[FONT=Verdana]Password:[/FONT][FONT=Verdana]
sudo c[/FONT]p -f /tmp/ok_pcscd_hotplug.sh /lib/udev
cp:cannot create regular file /lib/udev/ok_pcscd_hotplug : Permission denied


can u help me? i'dont understand

---

### Post by papibe on 2014-05-08
Thanks.

Are you running Ubuntu? I don't think 'sudo -' does what you want on Ubuntu.

Open a new terminal and run this:
```
sudo cp -iv /tmp/ok_pcscd_hotplug.sh /lib/udev/
```
Hope that helps. Copy/paste the command and results if that does not work.

Regards.

---

### Post by Serdar_Goksu on 2014-05-08
my bad , not sudo - it's su - 

yes , os version is ubuntu 10.04 and this pc is thin client.

output:
> 
sudo cp -iv /tmp/ok_pcscd_hotplug.sh /lib/udev

'/tmp/ok_pcscd_hotplug.sh' -> '/lib/udev/ok_pcscd_hotplug.sh'
cp:cannot create regular file '/lib/udev/ok_pcscd_hotplug.sh': Permission denied


---

### Post by Danger_Monkey on 2014-05-08
Can you check and make sure there isn't already a file with that name there?  It might have 000 for permissions (----------).  

```

ls -l /lib/udev/ok_pcscd_hotplug.sh

```

---

### Post by jdeca57 on 2014-05-08
In line with the remark of DM - can you copy that file to -say- your home directory?

---

### Post by keithimyers on 2014-05-08
Can you also copy the output of the command "whoami" so we can see if you are indeed being elevated to root.

---

