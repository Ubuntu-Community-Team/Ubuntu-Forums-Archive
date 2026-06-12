---
title: "cant install subclipse in Eclipse (ubuntu 8.10)"
date: 2008-12-19
forum: Programming Talk
---

### Post by chacham23 on 2008-12-19
when I try to check the box of subclipse I got this errors:
```

The current configuration contains errors and this operation can have unpredictable results.
  Eclipse BIRT Chart Runtime Feature (2.1.2.v20070205-1728) requires feature "org.apache.commons.codec (1.3.0)", or later version.
  Data Tools Platform Model Base (0.9.1.200609201) requires feature "org.eclipse.emf (2.1.0)", or later version.
  Eclipse BIRT Example (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.
  Eclipse BIRT Report Designer Framework (2.1.2.v20070205-1728) requires plug-in "org.eclipse.draw2d (3.2.0)", or compatible.
  Data Tools Platform SQL Development Tools (0.9.1.200609201) requires feature "org.eclipse.gef (3.2.0)", or compatible.
  Eclipse BIRT Chart Framework (2.1.2.v20070205-1728) requires feature "org.apache.commons.codec (1.3.0)", or later version.
  Data Tools Platform Open Data Access Designer (0.9.1.200609201) requires feature "org.eclipse.emf (2.1.0)", or later version.
  Eclipse BIRT Report Designer Feature (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.
  Eclipse BIRT Report Runtime Feature (2.1.2.v20070205-1728) requires plug-in "org.eclipse.tomcat (4.1.130)", or compatible.

```

I didnt ask for BIRT installation and dont found how to install the all components that missing(according to the error massage)

thanks :)

---

### Post by chacham23 on 2008-12-20
Bump..

Someone?

---

### Post by Ruhe on 2008-12-21
I recommend that you do not use the eclipse from apt. 
Just download last stable distribution (ganymede) from eclipse.org. This 'Ganymede' comes with subversive, a new svn integration module for eclipse. However you still can install subclipse on it.

---

