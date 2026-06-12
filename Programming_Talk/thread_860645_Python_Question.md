---
title: "Python Question"
date: 2008-07-15
forum: Programming Talk
---

### Post by moberry on 2008-07-15
Hi all, I have been working on a media player for some time now, and wanted to butt some heads on something i'm thinking of implementing. Basically, auto update. I have no questions at all on how to actually implement it, I just want some advice from more of a design perspective.

1st idea:
Use gksudo, a setuid script, etc (not sure on windows) to poll a server and fetch updated python sources before the application loads.

2nd idea, and kind of dramatic:

Program ships with the most up-to-date code. PYTHONPATH will have ~/.nemo/runtime as part of its search path and load code from there. when the updater runs, it downloads updated modules to that location.

I see pros and cons with both approaches, and wanted some opinions.

---

### Post by mssever on 2008-07-15
If you can use either the package versions that are available by default or persuade your users to enable a repository containing updated packages, you'll save yourself a headache, I suspect.

---

### Post by moberry on 2008-07-15
The player is designed to work with windows also

---

### Post by gfa on 2008-07-16
> **moberry said:**
> The player is designed to work with windows also

Your player will be public? How can I test it? 
(Using Ubuntu).

Thanks

---

### Post by moberry on 2008-07-16
It will be yes, although I'm not quite ready to let people start playing with it right yet. I need a couple major things finished, and to write some documentation on how to write plugins.

---

