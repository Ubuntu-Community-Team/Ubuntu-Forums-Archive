---
title: "Error Updating Ubuntu"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by xdweaver on 2013-07-30
im trying to install minecraft for the kids, I tried to update ubuntu and get this:
E: Type 'ro-Dock' is not known on line 2 in source list /etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How do I go about fixing this?

---

### Post by deadflowr on 2013-07-30
What is the output of the file?

I would assume there is a space in between cai and ro.

But that's just an assumption.

 run
```
cat [COLOR=#000000]/etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list[/COLOR]
```

and copy the output and paste it here.

---

### Post by xdweaver on 2013-07-30
E: Type 'ro-Dock' is not known on line 2 in source list /etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list

---

### Post by newb85 on 2013-07-30
> **xdweaver said:**
> E: Type 'ro-Dock' is not known on line 2 in source list /etc/apt/sources.list.d/cairo-dock-team-ppa-precise.list

That would not be the output of that cat command.  deadflowr is trying to find out the contents of the file cairo-dock-team-ppa-precise.list, which is probably the source of the problem.

I'm inclined to agree with deadflowr's assumption about the extra space.

---

### Post by Bhawani007 on 2013-07-30
remove cairo dock ppa and again add cairo dock ppa. That will solve your problem.
To remove cairo dock ppa:
**sudo apt-add-repository --remove [B]ppa:cairo-dock-team/ppa **[/B]to remove ppa from your system.

**sudo apt-add-repository [B]ppa:cairo-dock-team/ppa **[/B]to add it again to ypur system.

Be sure to update your system before adding back the repository.

---

