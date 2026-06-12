---
title: "installation location"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-06-30
Hello,

I have installed a theme using the appearance menu. Now i want to know if I delete the theme file I downloaded, is there gonna be any problem?:confused:

I also want to know where the softwares I am installing via synaptic r installed. For example, I installed sun-java6 and now I can't find where it is in my computer.

Thanks.

---

### Post by brian_p on 2008-06-30
> **Louis de Broglie said:**
> Hello,

I have installed a theme using the appearance menu. Now i want to know if I delete the theme file I downloaded, is there gonna be any problem?:confused:

No.

> I also want to know where the softwares I am installing via synaptic r installed. For example, I installed sun-java6 and now I can't find where it is in my computer.

Thanks.

/var/cache/apt

---

### Post by bhadotia on 2008-06-30
/var/cache/apt/archives is the place where the downloaded packages are stored (if you have enabled that option).
The installed executable is usually in /usr/bin
If you want the java browser plugin or the jre it will work automatically for you whenever needed. Sun java web-start creates shortcuts in system>preferences

---

### Post by bhadotia on 2008-06-30
If you need clarification I can detail it.

---

### Post by Louis de Broglie on 2008-06-30
I can see "Sun Java 6 Policy Tool" in System->Preferences

But when I click on the O(n) button in the upper left corner of this site:

[http://www.topcoder.com/tc?module=Static&d1=pressroom&d2=index](http://www.topcoder.com/tc?module=Static&d1=pressroom&d2=index)

A window appears requesting which program to use and by default there r Openjdk . The Other things that appear r download location(I am using firefox 3).

---

