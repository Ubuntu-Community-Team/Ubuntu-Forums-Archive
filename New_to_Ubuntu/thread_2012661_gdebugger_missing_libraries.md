---
title: "gdebugger missing libraries"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by joshpunb on 2012-06-29
I get the following error when trying to run gdebugger58-x86_64:

"The following system libraries are missing: 
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri/../libGL.so.1
Please ask your system administrator to install the missing libraries or create symbolic links from the above paths to the place where the libraries are installed."

Can someone please tell me what libraries or links are missing, as I can't make sense of the files listed above. 

Thanks in advance.

---

### Post by SchighSchagh on 2012-07-13
*bump*

Same problem here. Ubuntu 11.10.

I checked the paths, and they exist. The puzzling thing though is that the first path is actually just a directory, not a library.

Any ideas?

---

### Post by Lars Pensjö on 2012-08-17
Running gDEBugger as root got me past this point.

---

### Post by SchighSchagh on 2012-09-06
Aaah, this is wonderful! I should have thought of the solution myself, hah!

---

