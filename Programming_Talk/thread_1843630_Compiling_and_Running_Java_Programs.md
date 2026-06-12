---
title: "Compiling and Running Java Programs"
date: 2011-09-13
forum: Programming Talk
---

### Post by anotherusernametoforget on 2011-09-13
Original thread: [thread=713622]here[/thread]
/EDIT

The following does not, in fact, install anything for me. I imagine the file is obsolete... but I'm a newb so I'll dust off a years-old thread




This package installs the essential tools needed to write and run Java programs.

 	Code:
 	sudo aptitude install sun-java6-jdk

---

### Post by t1497f35 on 2011-09-13
So? What's your problem?

---

### Post by anotherusernametoforget on 2011-09-13
Code:
     sudo aptitude install sun-java6-jdk[/QUOTE]

only gets me this:
No candidate version found for sun-java6-jdk

---

### Post by JD8182 on 2011-09-13
Applications/Ubuntu Software Center - type in the search Windows at the top "Java" with out the quotations and hit enter, install it using the GUI.. 



> **anotherusernametoforget said:**
> Code:
     sudo aptitude install sun-java6-jdk

only gets me this:
No candidate version found for sun-java6-jdk[/QUOTE]

---

### Post by karlson on 2011-09-13
> **JD8182 said:**
> Applications/Ubuntu Software Center - type in the search Windows at the top "Java" with out the quotations and hit enter, install it using the GUI.. 


Do you have these in your /etc/apt/sources.list
```

deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

```

---

### Post by t1497f35 on 2011-09-13
Or you can enable the partner repos from the update manager as on screenshot.

---

### Post by nmaster on 2011-09-13
i think that you want to the openJDK package.  
```
sudo apt-get install openjdk-6-jdk
```

---

