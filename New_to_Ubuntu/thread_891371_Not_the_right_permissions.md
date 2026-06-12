---
title: "Not the right permissions?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by darren884 on 2008-08-16
I am logged into my Ubuntu and I am the only user and I have a var/www/ folder for Apache 2 for development purposes however I cannot edit any files or create any folders because it says I have inadequate permissions. Am I not logged in as the admin user? How can I get pass this? Thanks.

---

### Post by iaculallad on 2008-08-16
> **darren884 said:**
> I am logged into my Ubuntu and I am the only user and I have a var/www/ folder for Apache 2 for development purposes however I cannot edit any files or create any folders because it says I have inadequate permissions. Am I not logged in as the admin user? How can I get pass this? Thanks.

On your terminal:

```
cd /var/www
sudo mkdir folder_name
gksudo gedit filename_of_file_you_want_to_edit.extension
```

---

### Post by darren884 on 2008-08-16
oh thanks i didnt know i had to go through terminal

---

### Post by iaculallad on 2008-08-16
> **darren884 said:**
> oh thanks i didnt know i had to go through terminal

Or if you want the GUI way, you could just input the command below on your terminal and you could just browse your /var/www folder using the nautilus window and create the folder you like or open the file you want for editing:

```
gksudo nautilus
```

But very careful with what you edit and delete when in this mode.

---

