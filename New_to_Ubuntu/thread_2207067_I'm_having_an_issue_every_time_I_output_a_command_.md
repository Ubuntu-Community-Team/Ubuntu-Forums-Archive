---
title: "I'm having an issue every time I output a command in a terminal or other things."
date: 2014-02-21
forum: New to Ubuntu
---

### Post by sean4598 on 2014-02-21
I am unable to take pictures due to the fact I cannot get Xauthoration to work or anything
I've read in other places to fix it but when I put in the command, the terminal just closes.

1. <alt>+<F2>
2. write: gksu nautilus
3. Find the partition in your system /
4. right click on that folder ---> properties ---> permissions
5. Set owner to user - you
6. Set access to 'Create and Delete files
7. You may click 'Apply Permission to Enclosed Files'.
8. exit/close the file browser
I've done this, from another tutorial. I think I did it on my main drive and then when so, I lost all sound, restarted and now I cant launch any applications, any help?
The error message is
Failed to run nautilus as user root.

Unable to copy the user's Xauthorization file.

---

### Post by papibe on 2014-02-21
Hi sean4598. Welcome to the forum ):P

I don't see any scenario where changing the default ownership of the root directory (/) would do any good.

Could you post a link to the tutorial you mention?

If you already change the ownership to another user other than root, you may need going to boot into recovery mode, and change them back on the command line.

Regards.

---

### Post by Impavidus on 2014-02-22
And if you also clicked 'Apply permission to enclosed files', there is no realistic way to fix all files/directories manually.

---

