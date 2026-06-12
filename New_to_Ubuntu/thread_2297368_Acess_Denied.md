---
title: "Acess Denied"
date: 2015-10-03
forum: New to Ubuntu
---

### Post by abhik2 on 2015-10-03
I have just installed Ubuntu 15.04 LTS with windows 8. My windows 8 is NTFS and Ubuntu is ext4. 
When i am running a program in Codeblocks it is showing sh : 1:/home/abhik/code/sql1: Permission denied

is there any way to save my c programs in root ?

Please help me to fix this program . 
Thanks in Advance :D

---

### Post by grahammechanical on 2015-10-03
I do not understand exactly what you are doing. I have no idea what codeblocks is. But it looks to me that the code folder is not in root. It is in the abhik folder which in turn is in the home folder. The only reason I can think of getting a permission denied response when trying to save a file into that code folder is because the folder was created by you when you were working as root.

If we normally work as standard user (which is the default method in Ubuntu) we can create folders in /home and we become the owner and we have permissions to create & delete files in the folder we have created. So, you should not be having this trouble.

I suggest that you view the ownership & permissions of that folder. Use the File Manager. Select the folder, Right click and from the drop down menu select Properties and open the Permissions tab. I will give an example of a folder that I have created in my /home/user folder

Owner   Me
Access Create & Delete files
Group   Graham
Access Create & Delete files
Others
Access files

I can change the permissions for Others but I would need to be working as the Administrator to do that. 

Regards.

---

### Post by abhik2 on 2015-10-03
Can you please explain me how to change the permissions ?

---

### Post by yancek on 2015-10-03
You would use the 'chmod' command to change permissions or the 'chown' command to change the owner:group.  I don't know what you want to change it from/to so doing an online search for changing permissions on Linux or giving more details on what you want and what the current permissions are would help.

---

