---
title: "Eclipse C++ IDE error!"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by gchmverhaag on 2013-11-15
Hi,

I installed **Eclipse IDE for C++ developers** and ended up with the following error:
**Could not create the view: org.eclipse.jdt.ui.PackageExplorer**

I've six menus: File Edit Navigate Project Window Help.

However most submenu items are grayed out!

I **didn't** install the **Eclipse Standard 4.3.1**!

What's wrong?

Regards,
Gerard

---

### Post by gchmverhaag on 2013-11-15
After removing the .eclipse in my home directory and creating a new workspace everything worked as aspected!

---

### Post by J0nDaFr3aK on 2014-04-08
I know this thread may be old, but I just wanted to share what caused this problem for me. I have Eclipse both for Java and C++ and they shared the same workspace. I ran Eclipse Java at first and it worked. When I started Eclipse C++, I didn't change the default workspace directory - which was the same as that of Eclipse Java - and the error mentioned above would occur. I renamed the workspace directory for Eclipse C++ (named it 'workspace_cpp') and it worked.

thanks for the help

---

