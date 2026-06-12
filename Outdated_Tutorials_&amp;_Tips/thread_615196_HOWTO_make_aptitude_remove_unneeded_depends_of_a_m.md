---
title: "HOWTO: make aptitude remove unneeded depends of a metapackage"
date: 2007-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by maybeway36 on 2007-11-16
- Bug report: [https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681")
- Workaround: edit the file.
Here is the default /etc/apt/apt.conf.d/01autoremove:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };

  Never-MarkAuto-Sections
  { 
	"metapackages";
        "restricted/metapackages";
        "universe/metapackages";
        "multiverse/metapackages";
  };
};


```
You need to change it to:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };
};


```

---

### Post by frodon on 2007-11-20
Nice guide, thanks.

May i suggest to just comment the lines rather than deleting them as it would be easier in this case to revert back the changes for those you want to do it ?

---

### Post by maybeway36 on 2007-12-01
How do you comment lines in the APT directive files? Do you just begin them with #? I tried that and got:
```
E: Syntax error /etc/apt/apt.conf.d/01autoremove:11: Extra junk after value
```

---

