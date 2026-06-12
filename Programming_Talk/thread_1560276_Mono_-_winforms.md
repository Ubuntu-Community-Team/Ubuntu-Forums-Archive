---
title: "Mono - winforms"
date: 2010-08-24
forum: Programming Talk
---

### Post by bprins on 2010-08-24
Hi,

Does anybody know if winforms look&feel will get better in linux?

I'm writing an app which will run on both ubuntu and linux, but god is the look&feel of winforms ugly on ubuntu...

Thanks in advance.

Bas

---

### Post by vamega on 2010-08-26
You mean both linux and Windows right?

And I sincerely doubt that the winforms API will improve it's appearance.
It's not a priority for Mono. GTK# is much more important for them.

You might want to consider using GTK for the application. It works pretty well.

---

### Post by bprins on 2010-08-26
Hi,

But then I'll have to support 2 UI's I guess?

GTK for linux and winforms for windows?

Assuming that GTK wont run on linux.

Thanks for the reply

Rgds, Bas

---

### Post by KdotJ on 2010-08-26
GTK will work on windows and look native. You will only have to support the GTK gui in your program. Though you may be have to package the GTK libs with your program on windows? (someone will be able to correct me here)

---

### Post by bprins on 2010-08-26
Thanks for the help. Saves me endless googling and some possible frustrations :).

I'll just start developing in GTK, and try to run something trivial on windows. If that works, I'll just extend iteratively and see if I run into problems. If so, I'll post back here.

Thanks again.

Cheers.

Bas

---

