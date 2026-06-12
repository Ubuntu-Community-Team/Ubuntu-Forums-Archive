---
title: "Add comment to file"
date: 2008-10-13
forum: Programming Talk
---

### Post by aliahsan81 on 2008-10-13
I want to add comment to reslove.conf,at the beginning of line.i need to do it with sed,I there any way i can add comment in the existing file reslove.conf.Please let me know if i can.and if any one can provide me the sed command to add comment at beginning of the line

thx

---

### Post by WW on 2008-10-13
```

sed -i~ '1i# This is a comment' myfile

```
That command will add the line **# This is a comment** to the beginning of the file **myfile**. A backup file will be created called **myfile~**.

Change the text after 1i inside the quotes to be whatever you want to add to the file.  If you change myfile to /etc/resolve.conf, you'll have to use sudo to run the command.

---

### Post by aliahsan81 on 2008-10-13
Thx

---

### Post by dwhitney67 on 2008-10-13
Bear in mind that changes to /etc/resolv.conf are not permanent.  The file will be overwritten the next time you reboot your system and your network device is activated.

---

### Post by mike_g on 2008-10-13
aliahsan81: To mark a thread as solved you can click on "Thread Tools" and select to mark the thread as solved. Also, to thank WW you can click on the little medal at the base of his post ;)

---

